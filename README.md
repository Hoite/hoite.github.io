# Personal Website - hoite.github.io

A modern, professional personal website and digital business card built with Jekyll and hosted on GitHub Pages.

## Features

✨ **Modern Design**: Clean, responsive design that looks great on all devices  
📱 **Mobile-First**: Optimized for mobile viewing with a responsive layout  
📝 **Blog Functionality**: Built-in blog with post management and navigation  
🎨 **Professional**: Perfect for showcasing your professional experience and skills  
🚀 **Fast & Secure**: Hosted on GitHub Pages with automatic HTTPS  
🔧 **Easy to Customize**: Simple configuration and content management  

## Getting Started

### 1. Customize Your Information

Edit `_config.yml` to update your personal information:

```yaml
title: "Your Name - Digital Professional"
author:
  name: "Your Name"
  email: "your.email@example.com"
  bio: "Your professional bio"
  location: "Your Location"
  linkedin: "your-linkedin-username"
  github: "hoite"
```

### 2. Add Your Profile Photo

- Add your professional headshot as `assets/images/profile.jpg`
- Recommended size: 400x400 pixels or larger, square aspect ratio
- The image will be automatically resized and styled

### 3. Update Your Experience

Edit `index.md` to update the experience section with your actual:
- Job titles and companies
- Employment dates
- Role descriptions
- Skills and technologies

### 4. Customize Content

- Update the hero section with your name, title, and bio
- Modify the contact information
- Add or remove social media links as needed

### 5. Write Blog Posts

Create new blog posts in the `_posts` directory with the naming convention:
`YYYY-MM-DD-title-of-post.md`

Each post should include frontmatter:
```yaml
---
layout: post
title: "Your Post Title"
date: YYYY-MM-DD
author: "Your Name"
tags: ["tag1", "tag2"]
---
```

## Local Development

To run the site locally for testing:

1. Install Jekyll and dependencies:
   ```bash
   bundle install
   ```

2. Serve the site locally:
   ```bash
   bundle exec jekyll serve
   ```

3. Open your browser to `http://localhost:4000`

## Deployment

The site automatically deploys to GitHub Pages when you push changes to the main branch. No additional configuration needed!

## Customization

### Colors and Styling
- Edit `assets/css/style.css` to customize colors, fonts, and layout
- The CSS uses CSS custom properties (variables) for easy theme customization

### Layout Changes
- Modify `_layouts/default.html` for site-wide layout changes
- Edit individual page layouts in the `_layouts` directory

### Adding New Pages
- Create new markdown files in the root directory
- Add frontmatter with `layout: default` and other metadata
- Link to new pages from the navigation or content

## Support

This website template is designed to be beginner-friendly while providing professional results. The structure is clean and well-documented for easy customization.

For GitHub Pages documentation, visit: https://docs.github.com/en/pages

## License

This template is open source and available under the MIT License. Feel free to customize it for your own use!

---

**Ready to make it yours?** Start by editing `_config.yml` and `index.md` with your information!
