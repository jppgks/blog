---
layout: post
title:  Research internship KU Leuven University (Summer 2018)
author: Joppe
permalink: /research-internship-summer2018/ 
header: src="/assets/research-internship-kul-summer18/post_header.svg"
---

<div class="post-intro">
<p>
After my bachelor thesis was delivered in June, I was eager to continue machine learning research. I interned on VeriFlix, which is a <b>joint project between academia</b> (professor Moens from the department of Computer Science, who was my thesis supervisor, and professor Tuytelaars from the department of Electrical Engineering) <b>and industry</b>. 
</p>
<p>
Given that this project is in close collaboration with industry, there is a clear use case. Journalists would be able to <b>search in a database of videos that users upload when they attend certain events</b>. The search queries are formulated in natural written language.
</p>
</div>

<br/>
<div class="post-line"></div>

## Task description
A postdoctoral researcher who was on this project before me implemented a system to embed video and text to the same space. The system would return the video closest to the search query in embedding space. The system at this time was relying on manual annotation of the key word in the search query. My task was to automatically extract the keyword in a search query for use in this video retrieval setting.

## Extractor approach
Our intuition was that we could use semantic information from a [dependency tree](http://universaldependencies.org) of the search query to define the keyword. The state-of-the-art dependency parser at the time was Google's [DRAGNN](https://arxiv.org/abs/1703.04474), which is built on the SyntaxNet framework for Natural Language Understanding.
Using the DRAGNN models, I constructed the dependency tree of the search query after which I implemented a post-processing step for filtering out words that would never occur as keyword.
The eventual keyword was then determined based on a few rules and passed on to the existing text embedding generator.

![](/assets/research-internship-kul-summer18/keyword_extraction.svg)

I experimented with another extraction method based on the PageRank algorithm. This yielded worse results compared to the dependency tree approach so we didn't continue down that path.

## Integration
After the extraction system was developed and evaluated, I went to the industry partner to help them incorporate the changes to the existing system. They successfully deployed these changes using Docker. The automatic keyword extractor now runs in production.

