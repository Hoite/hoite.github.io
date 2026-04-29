---
layout: default
title: "Blog"
permalink: /blog/
---

<section class="blog-header">
    <div class="container">
        <h1 class="section-title">Blog</h1>
        <p style="color: var(--text-secondary); font-size: 1.1rem; max-width: 600px; margin: 0 auto;">
            Write-ups from my homelab and professional work — Kubernetes, infrastructure, and everything in between.
        </p>
    </div>
</section>

<section class="blog-list">
    <div class="container">
        {% if site.posts.size > 0 %}
        <div class="blog-grid">
            {% for post in site.posts %}
            <a href="{{ post.url | relative_url }}" class="blog-card">
                <div class="blog-card-content">
                    <div class="blog-card-meta">
                        <time datetime="{{ post.date | date_to_xmlschema }}">
                            {{ post.date | date: "%B %d, %Y" }}
                        </time>
                        {% if post.author %}
                        <span>· {{ post.author }}</span>
                        {% endif %}
                    </div>
                    <h2 class="blog-card-title">{{ post.title }}</h2>
                    <p class="blog-card-excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
                    {% if post.tags.size > 0 %}
                    <div class="blog-card-tags">
                        {% for tag in post.tags limit:4 %}
                        <span class="tag">{{ tag }}</span>
                        {% endfor %}
                    </div>
                    {% endif %}
                </div>
            </a>
            {% endfor %}
        </div>
        {% else %}
        <div style="text-align: center; padding: 4rem 0;">
            <h3 style="color: var(--text-secondary); margin-bottom: 1rem;">No blog posts yet</h3>
            <p style="color: var(--text-light);">Check back soon for new content!</p>
        </div>
        {% endif %}
    </div>
</section>
