---
layout: post
title: 'h2o_jekyll����ҳͷhtml'
subtitle: '���Ŵ�Ҷ������˰ɣ��ҵ�links.html��AboutMe.html��ҳͷ���Ҳ��͵�ҳͷ�ġ�������ô�������أ�����һ���ɡ�'
tags: �̳� jekyll
keywords: �̳� jekyll 
cover:https://gitee.com/srsyrzz/repository/raw/master/blogfile/jekyllh2ohtml/cover.h2ojekyll-html.png'
---
�²���˵�����ڿ�ʼ��  
  
h2o�������ĺ�������`index.html`�����������ɵġ����򵥸�������������  
���ǣ�������������ֱ�Ӵ�`index.html`����������ɹ������ῴ��Դ���롣  
��Ϊ��`YAMLͷ`��Ե�ʡ�  
  
ѡ��github����Ϊgithub���`index.html`����֧��`YAML`��  
*���ڿ�ʼǰ�����ȷ�����jekyll������h2oģ�壡����*  
������������`index.html`������(��Ȼ˵��Ҳ�е㲻����һЩ����)
```css
---
layout: default
home-title: h20����
header-img: http://on2171g4d.bkt.clouddn.com/jekyll-banner.png
description: Maybe is the most beautiful of jekyll theme.
---
{% include header.html %}

<div class="g-banner home-banner {{ site.theme-color | prepend: 'banner-theme-' }}" data-theme="{{ site.theme-color }}">
    <h2>{{ page.home-title }}</h2>
    <h3>{{ page.description }}</h3>
    {% if page.header-img %}
    <img class="header-img" src="{{ page.header-img | prepend: site.baseurl }}" alt="">
    {% endif %}
</div>

<main class="g-container home-content">
    <div class="article-list">
        {% for post in paginator.posts %}
            <article class="article-item">
                {% if post.cover %}
                <div class="post-cover">
                    <a class="post-link" href="{{ post.url | prepend: site.baseurl }}" title="{{ post.title }}"></a>
                    <img src="{{ post.cover }}" href="{{ post.url | prepend: site.baseurl }}" alt="">
                </div>
                {% endif %}
                <section class="post-preview">
                    <a class="post-link" href="{{ post.url | prepend: site.baseurl }}" title="{{ post.title }}"></a>
                    <h2 class="post-title">{{ post.title }}</h2>
                    {% if post.subtitle %}
                    <h3 class="post-subtitle">{{ post.subtitle }}</h3>
                    {% endif %}
                    {% if post.subtitle.size==0 or post.subtitle==nil %}
                    <p class="post-excerpt">{{ post.excerpt | strip_html | strip_newlines | truncate: 126}}</p>
                    {% endif %}
                </section>
                <footer class="post-meta">
                    <div class="post-tags">
                        {% if post.tags.size > 0 %}
                            {% for tag in post.tags  %}
                            <a href={{ "tags.html#" | append: tag | pretend: site.baseurl}} class="post-tag">{{ tag }}</a>
                            {% endfor %}
                        {% endif %}
                    </div>
                    <time class="post-date" datetime="{{ post.date | date:"%y-%m-%d" }}">{{ post.date | date_to_string }}</time>
                </footer>
            </article>
        {% endfor %}

        {% if paginator.total_pages > 1 %}
            {% include pageNav.html %}
        {% endif %}

    </div>

    <aside class="g-sidebar-wrapper">
        <div class="g-sidebar">
            <section class="author-card">
                <div class="avatar">
                    <img src="{{ site.avatar | prepend: site.baseurl }}" alt="">
                </div>
                <div class="author-name" rel="author">{{ site.author }}</div>
                <div class="bio">
                    <p>{{ site.bio }}</p>
                </div>
                {% if site.sns.size > 0 %}
                <ul id="sns-links" class="sns-links">
                    {% for s in site.sns %}
                    <li>
                        <a href="{{ s[1] }}" target="_blank">
                            <i class="iconfont icon-{{ s[0] }}"></i>
                        </a>
                    </li>
                    {% endfor %}
                </ul>
                {% endif %}
            </section>

            {% if site.recommend-tags and site.tags.size>0 %}
            <section class="tags-card">
                {% for tag in site.tags %}
                    {% if forloop.index > site.recommend-condition-size %}
                        {% break %}
                    {% endif %}
                    <a href="{{ "tags.html#" | append: tag[0] | prepend: site.baseurl }}" class="tag">{{ tag[0]}}</a>
                {% endfor %}
            </section>
            {% endif %}
        </div>

        {% if site.search %}
        <div class="search-card">
            <input id="search_input" type="text" placeholder="Search...">
            <i class="iconfont icon-search"></i>
            <div class="search_result"></div>
        </div>
        {% endif %}

    </aside>

</main>

{% include footer.html %}
```
�������棬�и�`YAML`ͷ��  
�����Թ������������档  
```css
---
layout: default
home-title: h20����
header-img: http://on2171g4d.bkt.clouddn.com/jekyll-banner.png
description: Maybe is the most beautiful of jekyll theme.
---
{% include header.html %}

<div class="g-banner home-banner {{ site.theme-color | prepend: 'banner-theme-' }}" data-theme="{{ site.theme-color }}">
    <h2>{{ page.home-title }}</h2>
    <h3>{{ page.description }}</h3>
    {% if page.header-img %}
    <img class="header-img" src="{{ page.header-img | prepend: site.baseurl }}" alt="">
    {% endif %}
</div>
```
��һϵ����˵��
```css
---
*���ԣ��㶮��~*
---
{��ͷhtml}
����������ɫ_
��h2��ʾ����
��h2��ʾ����
{�����header-imgѡ�������ȥ��}
<����header-img>
```
�����������˼��  
���ǿ���ȥ������`post`ʲô֮���ѡ���ˡ����ԣ�����copy������롣  
�����h2o�������`xxxxxxx.html`����һ���ļ���  
Ȼ������`_config.yml`��nav����`xxxxxx: 'xxxxxx.html'`������  
�����`xxxxx.html`��Ȼ�������Ķ����ŵ����  
---
��һ��Ȼ���������`html����`��  
**��û�����أ�**����֮�󣬿�������`�����һ�У���һ��`��**��ס������Ҫ�ǵ�һ��**������`</main>`������������������д��롣  
�׻�˵����ʼ���գ���ǰ��������`{% include header.html %}`���ǣ��㻹���ڿ����У��ڶ�����д��`{% include footer.html %}`�ͳɹ���������Զ��塰h2oģ��ҳ�桱�Ĳ��á�  
---
�ύ��`https://github.com`�����ˣ�

> ByeBye,Enjoy your own h2o model page~