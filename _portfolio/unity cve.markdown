---
layout: post
title: unity cve
description: custom networking for unity 
img:
---

During my time an the University of Aizu I worked on a project to allow unity to use a custom networking system. 

Students in the Computer Arts Lab at the University of Aizu have been making demonstrations in a <a href="https://www.youtube.com/watch?v=4jauDFbTxgg">collaborative virtual environment</a> or CVE. CVE works by transfering Java serialized objects, and so all of the clients either ran Java or communicated through a bridge. Many of the 3D demos used Alice (<a href="http://web-ext.u-aizu.ac.jp/~mcohen/spatial-media/Tworlds/">like this one</a>) and so I worked to add a brige so that future projects could be made in unity. 

I did this with a bridge written in Java. The bridge communicated with the CVE server using Java serialized objects, then communicated with Unity using the <a href="https://google.github.io/flatbuffers/"> flatbuffers </a> serialization library. Serialized data was then sent in UDP packets. 

Encoding with flatbuffers was straightforward. The CVE system was for transfering spatial data so I encoded the data as: 

{% highlight fbs %}
namespace Unity_CVE;

table Position {...}

table Location {...}

table Orientation {...}

table ExtraParam {...}
{% endhighlight %}

In retrospect JSON serialization would have been a better choice. While flatbuffers may have a small performance benefit, the ease of understanding and expanding JSON is a bigger benefit than the performance increase. 

<div class="img_row">
<a href="{{ site.baseurl }}/cageOS">
<img class="col two" src="{{ site.baseurl }}/img/cageos_splash.png" alt="" title="example image"/>
</a>
</div>

 