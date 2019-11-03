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

## SWIG definition
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
