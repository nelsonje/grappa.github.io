---
layout: default
title: "Grappa: Scaling data-intensive applications on commodity clusters"

people:
  - title: Graduate Students
    names:
    - name: Jacob Nelson
      image: images/nelson.jpg
    - name: Brandon Myers
      image: images/myers.jpg
    - name: Brandon Holt
      image: images/holt.jpg
    - name: Vincent Lee
      image: images/lee.jpg
  - title: Faculty
    names:
    - name: Simon Kahan
      image: images/kahan.jpg
    - name: Preston Briggs
      image: images/briggs.jpg
    - name: Luis Ceze
      image: images/ceze.jpg
    - name: Mark Oskin
      image: images/oskin.jpg

publications:

  - title: 'Latency-Tolerant Software Distributed Shared Memory'
    link: http://sampa.cs.washington.edu/papers/grappa-usenix-2015.pdf
    authors: 'Jacob Nelson, Brandon Holt, Brandon Myers, Preston Briggs, Luis Ceze, Simon Kahan, and Mark Oskin'
    publication: 'USENIX Annual Technical Conference (USENIX ATC), July 2015 (Best Paper Award)'

  - title: 'Alembic: Automatic Locality Extraction via Migration'
    link: http://sampa.cs.washington.edu/papers/oopsla14-alembic.pdf
    authors: 'Brandon Holt, Preston Briggs, Luis Ceze, Mark Oskin'
    publication: 'OOPSLA 2014'

  - title: 'Radish: Compiling Efficient Query Plans for Distributed Shared Memory'
    link: 'ftp://ftp.cs.washington.edu/tr/2014/10/UW-CSE-14-10-01.pdf'
    authors: 'Brandon Myers, Daniel Halperin, Jacob Nelson, Mark Oskin, Luis Ceze, Bill Howe'
    publication: 'Tech report, October 2014'

  - title: 'Grappa: A Latency-Tolerant Runtime for Large-Scale Irregular Applications'
    link: http://sampa.cs.washington.edu/papers/grappa-wrsc-2014.pdf
    authors: 'Jacob Nelson, Brandon Holt, Brandon Myers, Preston Briggs, Luis Ceze, Simon Kahan, and Mark Oskin'
    publication: 'International Workshop on Rack-Scale Computing (WRSC w/EuroSys), April 2014'
    techreport: http://sampa.cs.washington.edu/papers/grappa-tr-2014-02.pdf

  - title: Flat Combining Synchronized Global Data Structures
    link: http://sampa.cs.washington.edu/papers/holt-pgas13.pdf
    authors: 'Brandon Holt, Jacob Nelson, Brandon Myers, Preston Briggs, Luis Ceze, Simon Kahan, and Mark Oskin'
    publication: 'International Conference on PGAS Programming Models (PGAS), October 2013'

  - title: Compiled Plans for In-Memory Path-Counting Queries
    link: http://sampa.cs.washington.edu/papers/myers-imdm13.pdf
    authors: 'Brandon Myers, Jeremy Hyrkas, Daniel Halperin, and Bill Howe'
    publication: 'International Workshop on In-Memory Data Management and Analytics (IMDM w/ VLDB), August 2013'

  - title: Crunching Large Graphs With Commodity Processors
    link: https://www.usenix.org/legacy/event/hotpar11/tech/final_files/Nelson.pdf
    authors: 'Jacob Nelson, Brandon Myers, A. H. Hunter, Preston Briggs, Luis Ceze, Carl Ebeling, Dan Grossman, Simon Kahan, Mark Oskin'
    publication: 'USENIX Workshop on Hot Topics in Parallelism (HOTPAR), June 2011'
  
---

<div class="page-header">
  <div class="pull-left" style="padding-left:20px">
    <img src="images/logo.svg" />
  </div>
  <h1>
    Grappa <br/>
    <small>Scaling data-intensive applications on commodity clusters</small>
  </h1>
</div>

<div class="btn-grp">

<a type="button" class="btn btn-default btn-lg" href="http://github.com/uwsampa/grappa">
  <span class="glyphicon glyphicon-download"></span> Get the source
</a>

<a type="button" class="btn btn-default btn-lg" href="http://sampa.cs.washington.edu/papers/grappa-usenix-2015.pdf">
  <span class="glyphicon glyphicon-file"></span> Read the paper
</a>

</div>

<br />
<b>Note:</b> Grappa is no longer under active development.

### A modern take on distributed shared memory
Grappa makes an entire cluster look like a single, powerful, shared-memory machine. By leveraging the massive amount of concurrency in large-scale data-intensive applications, Grappa can provide this useful abstraction with high performance. Unlike classic distributed shared memory (DSM) systems, Grappa does *not* require spatial locality or data reuse to perform well.

### Platform for data-intensive applications

<img class="img-responsive pull-right" src="images/system-stack.svg" />

Data-intensive, or "Big Data", workloads are an important class of large-scale computations. However, the commodity clusters they are run on are not well suited to these problems, requiring careful partitioning of data and computation. A diverse ecosystem of frameworks have arisen to tackle these problems, such as MapReduce, Spark, Dryad, and GraphLab, which ease development of large-scale applications by specializing to particular algorithmic structure and behavior.

Grappa provides abstraction at a level high enough to subsume many performance optimizations common to these data-intensive platforms. However, its relatively low-level interface provides a convenient abstraction for building data-intensive frameworks on top of. Prototype implementations of (simplified) MapReduce, GraphLab, and a relational query engine have been built on Grappa that out-perform the original systems.

<!--
- link to actual results?
- other page with more detailed descriptions of these implementations?
-->

### Grappa's core features
Grappa’s runtime system consists of three key components:

<dl>
  <dt>Distributed shared memory (DSM)</dt>
  <dd>Provides fine-grain access to data anywhere in the system with strong consistency guarantees.</dd>
<br/>
  <dt>Tasking system</dt>
  <dd>Supports millions of lightweight threads and global distributed work stealing for load balance.</dd>
<br/>
  <dt>Communication layer</dt>
  <dd>Supports high throughput even for extremely small messages by delaying and aggregating them into larger network packets.</dd>
</dl>

### Try it out now!
Grappa is freely available on [Github](http://github.com/uwsampa/grappa) under a BSD license. Anyone interested in seeing Grappa at work can follow the quick-start directions in the README to build and run it on their cluster. To learn how to write your own Grappa applications, check out the [Tutorial](https://github.com/uwsampa/grappa/blob/master/doc/tutorial/tutorial.md).

Grappa is still quite young, so please don't hesitate to ask for help if you run into problems. To find answers to questions or ask new ones, please use [Github Issues](https://github.com/uwsampa/grappa/issues). The developers hang out in the ```#grappa.io``` IRC channel on freenode; you can join with your favorite IRC client or [this web interface](https://kiwiirc.com/client/chat.freenode.net/#grappa.io). Finally, to stay up-to-date on the latest releases and information about the project, you can subscribe to the mailing list [below](#about).

### Publications

{% for pub in page.publications %}
{% if pub.link %}<a href="{{ pub.link }}" onclick="trackOutboundLink('{{ pub.link }}'); return false;">{{ pub.title }}</a>.{% else %}{{ pub.title }}.{% endif %} {% if pub.techreport %}<a href="{{ pub.techreport }}" onclick="trackOutboundLink('{{ pub.techreport }}'); return false;">(Expanded tech report)</a>{% endif %}<br/>
{{pub.authors}}<br/>
{{ pub.publication }}
{% endfor %}

### Other documentation
<p>
  <a href="http://grappa.io/docs/grappa-uwt-may2014.pdf"
     onclick="trackOutboundLink('http://grappa.io/docs/grappa-uwt-may2014.pdf'); return false;">Slides from a recent talk</a>
</p>
<p>
  <a href="http://sampa.cs.washington.edu/papers/grappa-osdi14-poster.pdf"
     onclick="trackOutboundLink('http://sampa.cs.washington.edu/papers/grappa-osdi14-poster.pdf'); return false;">Poster from OSDI 2014</a>
</p>
<p>
  <a href="http://grappa.io/doxygen"
     onclick="trackOutboundLink('http://grappa.io/doxygen'); return false;">Autogenerated API documentation</a>
</p>


### About the project
<a name="about"></a>
Grappa is a project group in the [Sampa Group](http://sampa.cs.washington.edu) at the [University of Washington](http://www.washington.edu).

<!-- grads and faculty (names/pics) -->
{% for p in page.people %}
<h4>{{p.title}}</h4>
<div class="row">
  <div class="col-sm-1" align="center"></div>
  {% for n in p.names %}
  <div class="col-sm-2" align="center">
    <img src="{{n.image}}" height="100" class="img-rounded" />
    <h5>{{n.name}}</h5>
  </div>
  {% endfor %}
</div>
{% endfor %}

