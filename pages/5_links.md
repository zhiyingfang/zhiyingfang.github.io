---
layout: page
title: 导航
permalink: /links/
icon: glyphicon-paperclip
---

* content
{:toc}

## 友情链接

-----

{% for contact in site.data.links.stock %}
	{% assign i = contact[1] %}
### {{ i.message }}
---
		{% for link in i.items %}
- [{{ link.text }}]({{ link.url }}) ：{{ link.note }}
		{% endfor %}

{% endfor %}

---

<div class="post-area post comment">
      <!-- 多说评论框 start -->
      
      <div class="ds-thread" data-thread-key="{{ page.id }}" data-title="{{ page.title }}" data-url="gaohaoyang.github.io{{ page.url }}"></div>
      
      <!-- 多说评论框 end -->
    </div>

