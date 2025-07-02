---
layout: default
title: "Professional Digital Business Card"
---

<section class="hero">
    <div class="container">
        <div class="hero-content">
            <!-- Replace with your actual photo -->
            <img src="{{ '/assets/images/profile.jpg' | relative_url }}" alt="Your Name" class="profile-image">
            
            <h1 class="hero-title">Hoite Prins</h1>
            <p class="hero-subtitle">Docent ICT || Nerd</p>
            <p class="hero-description">
                I'm a passionate ICT educator at Alfa-college with a strong focus on practical, hands-on learning. With expertise in cybersecurity, system administration, and software development, I help students build real-world skills for today’s tech landscape. I thrive on bridging the gap between theory and practice, making complex topics accessible and engaging.
            </p>
            
            <div class="cta-buttons">
                <a href="#contact" class="btn btn-primary">
                    <i class="fas fa-envelope"></i>
                    Get In Touch
                </a>
                <a href="/blog" class="btn btn-secondary">
                    <i class="fas fa-blog"></i>
                    Read My Blog
                </a>
            </div>
        </div>
    </div>
</section>

<section class="experience">
    <div class="container">
        <h2 class="section-title">Professional Experience</h2>
        
        <div class="experience-grid">
            <div class="experience-item">
                <div class="experience-header">
                    <div>
                        <h3 class="experience-title">ICT Docent (ICT Lecturer)</h3>
                        <p class="experience-company">Alfa-college</p>
                    </div>
                    <span class="experience-period">2015 - Present</span>
                </div>
                <p class="experience-description">
                    Teaching and mentoring students in various ICT disciplines with a focus on practical, hands-on learning. 
                    Developed and implemented the "Excellentietraject Cybersecurity" program to provide advanced cybersecurity training. 
                    Bridging the gap between theoretical knowledge and real-world applications to prepare students for today's tech industry.
                </p>
                <div class="experience-skills">
                    <strong style="color: var(--text-primary); font-size: 0.9rem;">IT Expertise:</strong><br>
                    <span class="skill-tag">Cybersecurity</span>
                    <span class="skill-tag">DevOps</span>
                    <span class="skill-tag">Software Development</span>
                    <span class="skill-tag">Linux</span>
                    <span class="skill-tag">Networking</span>
                </div>
                <div class="experience-skills" style="margin-top: 1rem;">
                    <strong style="color: var(--text-primary); font-size: 0.9rem;">Educational Roles:</strong><br>
                    <span class="skill-tag">Curriculum Development</span>
                    <span class="skill-tag">Chair of Exam Board (2021-Present)</span>
                </div>
                <div class="experience-skills" style="margin-top: 1rem;">
                    <strong style="color: var(--text-primary); font-size: 0.9rem;">Key Projects:</strong><br>
                    <span class="skill-tag">Excellentietraject Cybersecurity</span>
                </div>
            </div>
        </div>
    </div>
</section>

<section class="blog-preview">
    <div class="container">
        <h2 class="section-title">Latest Blog Posts</h2>
        
        <div class="blog-grid">
            {% for post in site.posts limit:3 %}
            <a href="{{ post.url | relative_url }}" class="blog-card">
                <div class="blog-card-content">
                    <h3 class="blog-card-title">{{ post.title }}</h3>
                    <p class="blog-card-excerpt">{{ post.excerpt | strip_html | truncatewords: 20 }}</p>
                    <div class="blog-card-meta">
                        {{ post.date | date: "%B %d, %Y" }}
                    </div>
                </div>
            </a>
            {% endfor %}
        </div>
        
        {% if site.posts.size == 0 %}
        <div style="text-align: center; padding: 2rem; color: var(--text-secondary);">
            <p>No blog posts yet. Check back soon for updates!</p>
            <p style="margin-top: 1rem;">
                <a href="/blog" class="btn btn-primary">Start Reading</a>
            </p>
        </div>
        {% endif %}
    </div>
</section>

<section class="contact" id="contact">
    <div class="container">
        <h2 class="section-title">Get In Touch</h2>
        <p style="color: var(--text-secondary); font-size: 1.1rem; margin-bottom: 2rem;">
            I'm always open to discussing new opportunities, collaborations, or just having a conversation about the industry.
        </p>
        
        <div class="contact-info">
            {% if site.author.email %}
            <a href="mailto:{{ site.author.email }}" class="contact-item">
                <i class="fas fa-envelope"></i>
                {{ site.author.email }}
            </a>
            {% endif %}
            
            {% if site.author.location %}
            <div class="contact-item">
                <i class="fas fa-map-marker-alt"></i>
                {{ site.author.location }}
            </div>
            {% endif %}
            
            {% if site.author.linkedin %}
            <a href="https://linkedin.com/in/{{ site.author.linkedin }}" target="_blank" rel="noopener noreferrer" class="contact-item">
                <i class="fab fa-linkedin"></i>
                LinkedIn Profile
            </a>
            {% endif %}
        </div>
    </div>
</section>
