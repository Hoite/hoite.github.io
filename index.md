---
layout: default
title: "Professional Digital Business Card"
---

<section class="hero">
    <div class="container">
        <div class="hero-content">
            <!-- Replace with your actual photo -->
            <img src="{{ '/assets/images/profile.jpg' | relative_url }}" alt="Your Name" class="profile-image">
            
            <h1 class="hero-title">Your Name</h1>
            <p class="hero-subtitle">Your Professional Title</p>
            <p class="hero-description">
                Brief professional bio that highlights your expertise, passion, and what makes you unique. 
                This should be 2-3 sentences that give visitors a quick understanding of who you are professionally.
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
                        <h3 class="experience-title">Your Current Role</h3>
                        <p class="experience-company">Company Name</p>
                    </div>
                    <span class="experience-period">2020 - Present</span>
                </div>
                <p class="experience-description">
                    Brief description of your role, key responsibilities, and major achievements. 
                    Focus on impact and results you've delivered.
                </p>
                <div class="experience-skills">
                    <span class="skill-tag">Skill 1</span>
                    <span class="skill-tag">Skill 2</span>
                    <span class="skill-tag">Skill 3</span>
                    <span class="skill-tag">Skill 4</span>
                </div>
            </div>
            
            <div class="experience-item">
                <div class="experience-header">
                    <div>
                        <h3 class="experience-title">Previous Role</h3>
                        <p class="experience-company">Previous Company</p>
                    </div>
                    <span class="experience-period">2018 - 2020</span>
                </div>
                <p class="experience-description">
                    Description of your previous role and key accomplishments. 
                    Highlight growth, learning, and value you added to the organization.
                </p>
                <div class="experience-skills">
                    <span class="skill-tag">Skill A</span>
                    <span class="skill-tag">Skill B</span>
                    <span class="skill-tag">Skill C</span>
                </div>
            </div>
            
            <div class="experience-item">
                <div class="experience-header">
                    <div>
                        <h3 class="experience-title">Earlier Role</h3>
                        <p class="experience-company">Another Company</p>
                    </div>
                    <span class="experience-period">2016 - 2018</span>
                </div>
                <p class="experience-description">
                    Earlier career experience that shows your professional journey. 
                    Focus on how this role built the foundation for your current expertise.
                </p>
                <div class="experience-skills">
                    <span class="skill-tag">Foundation Skill 1</span>
                    <span class="skill-tag">Foundation Skill 2</span>
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
