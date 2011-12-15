---
layout: default
title: LeafGrass
---
Archive
=======
{% for post in site.posts %}
* <span>{{ post.date | date_to_string }}</span> &#187; [{{ post.title }}]({{ post.url }})
{:.posts}
{% endfor %}

Projects
--------
* &#187; [Ousia][os]
* &#187; [QuadroCopter][qc]
* &#187; [World of Wumpus A.I. game][ww]
* &#187; [Othello game implementation][othello]
* &#187; [ArchLinux packages][pkg]
* &#187; [Hello, World! in every language repository][hw]
* &#187; [this blog][blog]
* &#187; [a parser for the CACM document collection using Java-Lucene lib][lucene-cacm]
* &#187; [zipf law for the Greek language][zipf]
* &#187; [varius everyday-use scripts][script]
* &#187; [personal dotfiles collection][dot]
{:.posts}

  [os]: http://github.com/LeafGrass/ousia
  [qc]: http://github.com/librae8226/QuadroCopter

click it ↓ comic [source]()
{:.meta}
<script type="text/javascript" src="/scripts/comic.js"></script>
![loading](/images/load.gif "downloading"){:#comic alt="comic"}
