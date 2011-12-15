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
{:.posts}

  [os]: http://github.com/LeafGrass/ousia
  [qc]: http://github.com/librae8226/QuadroCopter

click it ↓ comic [source]()
{:.meta}
<script type="text/javascript" src="/scripts/comic.js"></script>
![loading](/images/load.gif "downloading"){:#comic alt="comic"}
