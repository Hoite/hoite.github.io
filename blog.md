---
layout: default
title: "Blog"
permalink: /blog/
---

<section class="blog-header">
    <div class="container">
        <h1 class="section-title">Blog</h1>
        <p style="color: var(--text-secondary); font-size: 1.1rem; max-width: 600px; margin: 0 auto;">
            Thoughts, insights, and experiences from my professional journey. 
            I write about technology, career development, and industry trends.
        </p>
    </div>
</section>

<section class="blog-list">
    <div class="container">
        {% if site.posts.size > 0 %}
            {% for post in site.posts %}
            <article class="blog-post">
                <h2 class="blog-post-title">
                    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                </h2>
                
                <div class="blog-post-meta">
                    <time datetime="{{ post.date | date_to_xmlschema }}">
                        {{ post.date | date: "%B %d, %Y" }}
                    </time>
                    {% if post.author %}
                    <span class="post-author">by {{ post.author }}</span>
                    {% endif %}
                    {% if post.tags.size > 0 %}
                    <span class="post-tags-inline">
                        in 
                        {% for tag in post.tags %}
                        <span class="tag-inline">{{ tag }}</span>{% unless forloop.last %}, {% endunless %}
                        {% endfor %}
                    </span>
                    {% endif %}
                </div>
                
                <div class="blog-post-excerpt">
                    {{ post.excerpt | strip_html | truncatewords: 50 }}
                </div>
                
                <a href="{{ post.url | relative_url }}" class="read-more">
                    Read more →
                </a>
            </article>
            {% endfor %}
        {% else %}
        <div style="text-align: center; padding: 4rem 0;">
            <h3 style="color: var(--text-secondary); margin-bottom: 1rem;">No blog posts yet</h3>
            <p style="color: var(--text-light);">Check back soon for new content!</p>
        </div>
        {% endif %}
    </div>
</section>
