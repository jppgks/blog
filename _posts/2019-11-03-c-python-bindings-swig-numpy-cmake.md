---
layout: post
title: Python bindings for C using SWIG&#58; matrix multiplication and numpy.i
author: Joppe
permalink: /c-python-swig-matrix-multiplication-numpy/
---

<div class="post-intro">
<p>
</p>
</div>

<br/>
<div class="post-line"></div>

## C header

In `matrix_multiplication.h`:

{% highlight c %}
void multiply_naive(double *a, double *b, double *c, int n);
{% endhighlight %}

## Desired Python interface

{% highlight python 3 %}
out = np.zeros([3, 3], dtype=np.double)
multiply_naive(np.ones([3, 3], dtype=np.double), np.ones([3, 3], dtype=np.double), out)
{% endhighlight %}

## SWIG definition

Adapted from [`dot` example in the docs](https://docs.scipy.org/doc/numpy/reference/swig.interface-file.html?highlight=array#beyond-the-provided-typemaps).

`matrix_multiplication.i`:

{% highlight c %}
%module MatrixMultiplication

%{
#define SWIG_FILE_WITH_INIT
#include "matrix_multiplication.h"
%}

%include "numpy.i"

%init %{
import_array();
%}

%apply (int DIM1, int DIM2, double* IN_ARRAY2) {
  (int dim_a1, int dim_a2, double* a),
  (int dim_b1, int dim_b2, double* b)
}
%apply (int DIM1, int DIM2, double* INPLACE_ARRAY2) {(int dim_c1, int dim_c2, double* c)}
%rename (multiply_naive) my_multiply_naive;
%ignore multiply_naive;
%exception my_multiply_naive {
    $action
    if (PyErr_Occurred()) SWIG_fail;
}
%inline %{
double my_multiply_naive(
    int dim_a1, int dim_a2, double* a,
    int dim_b1, int dim_b2, double* b,
    int dim_c1, int dim_c2, double* c) {
  if (dim_a1 != dim_a2 && dim_b1 != dim_b2 && dim_c1 != dim_c2) {
    PyErr_Format(PyExc_ValueError,
                 "Matrices were of different dimension (need to be square): %i, %i, %i, %i, %i, %i",
                 dim_a1, dim_a2, dim_b1, dim_b2, dim_c1, dim_c2);
  }
  multiply_naive(a, b, c, dim_a1);
}
%}

%include "matrix_multiplication.h"

{% endhighlight %}

## CMake
Put [`numpy.i`](https://github.com/numpy/numpy/blob/master/tools/swig/numpy.i) in the project directory.

`CMakeLists.txt`:

{% highlight cmake %}
cmake_minimum_required(VERSION 3.10)
project(MatrixMultiplication C)

set(CMAKE_C_STANDARD 11)

include_directories(.)

add_executable(matrix_multiply
        matrix_multiplication.c
        matrix_multiplication.h)

# Python bindings:
# load SWIG
set(SWIG_EXECUTABLE "$ENV{HOME}/miniconda3/envs/bdap-assignment-1/bin/swig")
find_package(SWIG REQUIRED)
include(${SWIG_USE_FILE})

# load Python
set(PYTHON_INCLUDE_PATH "$ENV{HOME}/miniconda3/envs/bdap-assignment-1/include/python3.7m")
set(PYTHON_LIBRARIES "$ENV{HOME}/miniconda3/envs/bdap-assignment-1/lib/libpython3.7m.so")
find_package(PythonLibs)
include_directories(${PYTHON_INCLUDE_PATH})

include_directories(${CMAKE_CURRENT_SOURCE_DIR})

set(CMAKE_SWIG_FLAGS "")

# create SWIG library
set_source_files_properties(matrix_multiplication.i PROPERTIES SWIG_FLAGS "-includeall")
swig_add_library(MatrixMultiplication LANGUAGE python SOURCES matrix_multiplication.i matrix_multiplication.c)
swig_link_libraries(MatrixMultiplication ${PYTHON_LIBRARIES})
install(
        TARGETS ${SWIG_MODULE_MatrixMultiplication_REAL_NAME}
        DESTINATION $ENV{HOME}/miniconda3/envs/bdap-assignment-1/lib/python3.7/site-packages
)
{% endhighlight %}


