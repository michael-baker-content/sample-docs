---
sidebar_position: 2
title: Complete Docusaurus Guide
---

# Complete Guide to Using Docusaurus

This comprehensive guide covers everything you need to know about using Docusaurus effectively for your documentation projects.

## Getting Started

### Development Server

To start the development server and preview your site locally:

```bash
npm run start
```

This command starts a local development server and opens up a browser window. Most changes are reflected live without having to restart the server.

### Building for Production

To generate static content for production deployment:

```bash
npm run build
```

This command generates static content into the `build` directory and can be served using any static contents hosting service.

## Creating Content

### Documentation Pages

Documentation pages are written in Markdown and stored in the `docs/` folder. Each file automatically becomes a page on your site.

#### File Structure

```
docs/
├── intro.md
├── using-docusaurus.md
└── advanced/
    └── configuration.md
```

#### Front Matter

Each documentation page should include front matter at the top:

```markdown
---
sidebar_position: 1
title: My Page Title
---

# Page Content
```

Common front matter options:

- `sidebar_position`: Controls the order in the sidebar
- `title`: Sets the page title (overrides the H1 heading)
- `slug`: Customizes the URL path

### Blog Posts

Create blog posts in the `blog/` directory:

```markdown
---
slug: welcome-post
title: Welcome
authors: [author-name]
tags: [docusaurus, hello]
---

Blog post content here...
```

### Pages

Create standalone pages in `src/pages/` using React components or Markdown files.

### Content Structure for This Site

This website follows a specific content organization pattern:

#### Homepage Setup

- **Main page**: `docs/using-docusaurus.md` with `slug: /` to serve as homepage
- **Hero content**: Compelling value proposition with hero image
- **Call-to-action buttons**: Links to main guide and transformation story

#### Documentation Pages Structure

```
docs/
├── using-docusaurus.md        # Homepage (slug: /)
├── docusaurus-guide.md        # Complete technical guide
└── site-transformation.md     # Development journey documentation
```

#### Special Content Features

- **Hero images**: Using existing Docusaurus SVGs from `static/img/`
- **Styled prompts**: Custom div styling for copyable prompt examples
- **Dual CTAs**: Multiple button styles for different actions
- **Progress narrative**: Documentation that tells the development story

#### Front Matter Examples

```markdown
---
sidebar_position: 1
slug: /
title: Welcome Page
---
```

```markdown
---
sidebar_position: 2
title: Complete Docusaurus Guide
---
```

## Navigation and Sidebars

### Sidebar Configuration

Edit `sidebars.js` to customize your documentation navigation:

```javascript
const sidebars = {
  tutorialSidebar: [
    "intro",
    {
      type: "category",
      label: "Guides",
      items: ["guide1", "guide2"],
    },
  ],
};
```

### Autogenerated Sidebars

Use the autogenerated option to automatically create sidebars from your folder structure:

```javascript
tutorialSidebar: [{ type: "autogenerated", dirName: "." }];
```

## Customization

### Configuration

Main site configuration is in `docusaurus.config.js`:

- Site metadata (title, tagline, URL)
- Theme configuration
- Plugin settings
- Navigation bar items

### Styling

Customize the appearance using:

- `src/css/custom.css` for global styles
- CSS modules for component-specific styles
- Custom React components in `src/components/`

### Themes

Docusaurus comes with a default theme, but you can:

- Customize the existing theme
- Use community themes
- Create your own theme

### Creating a Book-Themed Design (Like This Site)

To recreate the elegant book-inspired design of this website, follow these specific steps:

#### 1. Update Package Dependencies

Ensure you're using the latest Docusaurus version to avoid React createRoot warnings:

```json
{
  "dependencies": {
    "@docusaurus/core": "3.8.1",
    "@docusaurus/preset-classic": "3.8.1",
    "@mdx-js/react": "^3.0.0",
    "clsx": "^2.0.0",
    "prism-react-renderer": "^2.3.0",
    "react": "^18.0.0",
    "react-dom": "^18.0.0"
  },
  "devDependencies": {
    "@docusaurus/module-type-aliases": "3.8.1",
    "@docusaurus/types": "3.8.1"
  }
}
```

#### 2. Configure Dark Mode

Add dark mode support in `docusaurus.config.js`:

```javascript
themeConfig: {
  colorMode: {
    defaultMode: 'light',
    disableSwitch: false,
    respectPrefersColorScheme: true,
  },
  prism: {
    theme: prismThemes.github,
    darkTheme: prismThemes.dracula,
  },
  // ... other config
}
```

#### 3. Implement Book-Style Typography and Colors

Replace the contents of `src/css/custom.css` with a comprehensive book-themed design system:

```css
/* Import elegant serif fonts */
@import url("https://fonts.googleapis.com/css2?family=Crimson+Text:ital,wght@0,400;0,600;1,400&family=EB+Garamond:ital,wght@0,400;0,500;0,600;1,400&display=swap");

/* Light theme (book pages) */
:root {
  /* Primary book-inspired colors */
  --ifm-color-primary: #8b4513; /* Saddle brown */
  --ifm-color-primary-dark: #7a3c11;
  --ifm-color-primary-lighter: #a75317;

  /* Book page colors */
  --ifm-background-color: #fefcf8; /* Cream paper */
  --ifm-background-surface-color: #faf8f3;

  /* Typography */
  --ifm-font-family-base: "Crimson Text", "Times New Roman", Times, serif;
  --ifm-heading-font-family: "EB Garamond", "Times New Roman", Times, serif;
  --ifm-line-height-base: 1.7;
  --ifm-font-size-base: 18px;

  /* Enhanced readability */
  --ifm-code-background: #f0ebe3;
  --ifm-border-color: #e6d7c8;
}

/* Dark theme (night reading) */
[data-theme="dark"] {
  --ifm-color-primary: #d4a574; /* Warm gold */
  --ifm-background-color: #1a1611; /* Dark brown */
  --ifm-background-surface-color: #211d17;
  --ifm-code-background: #2a241d;
}

/* Typography enhancements */
html {
  font-feature-settings:
    "liga" 1,
    "kern" 1;
  text-rendering: optimizeLegibility;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: var(--ifm-heading-font-family);
  font-weight: 600;
  letter-spacing: -0.02em;
}

p {
  text-align: justify;
  line-height: var(--ifm-line-height-base);
}

/* Container width for optimal reading */
.container {
  max-width: 800px;
}
```

#### 4. Style Component Modules

Create enhanced styling for feature components in `src/components/HomepageFeatures/styles.module.css`:

```css
.features {
  background: linear-gradient(
    135deg,
    var(--ifm-background-color) 0%,
    var(--ifm-background-surface-color) 100%
  );
  padding: 3rem 0;
}

.featureCard {
  background: var(--ifm-background-surface-color);
  border-radius: 8px;
  padding: 2rem 1.5rem;
  box-shadow: 0 4px 16px rgba(139, 69, 19, 0.15);
  transition: transform 0.2s ease;
}

.featureCard:hover {
  transform: translateY(-4px);
}
```

#### 5. Update Component Structure

Modify `src/components/HomepageFeatures/index.js` to use the new styling:

```javascript
function Feature({ Svg, title, description }) {
  return (
    <div className={clsx("col col--4")}>
      <div className={styles.featureCard}>
        <Svg className={styles.featureSvg} role="img" />
        <Heading as="h3" className={styles.featureTitle}>
          {title}
        </Heading>
        <div className={styles.featureDescription}>{description}</div>
      </div>
    </div>
  );
}
```

#### 6. Key Design Principles Applied

- **Serif Typography**: Uses Crimson Text and EB Garamond for book-like feel
- **Warm Color Palette**: Cream backgrounds with brown accents
- **Enhanced Readability**: Increased line spacing, justified text, optimal container width
- **Subtle Shadows**: Adds depth without being overwhelming
- **Responsive Design**: Maintains elegance across all device sizes
- **Print Optimization**: Includes print-specific styles

#### 7. Testing Your Book Theme

After implementing these changes:

1. Run `npm run start` to preview in development
2. Test both light and dark modes
3. Verify responsive behavior on different screen sizes
4. Test the print styles with browser print preview
5. Check color contrast for accessibility compliance

## Deployment

### Static Hosting

After building (`npm run build`), deploy the `build/` folder to:

- GitHub Pages
- Netlify
- Vercel
- Any static hosting service

### GitHub Pages

For GitHub Pages deployment:

```bash
npm run deploy
```

This command builds the website and pushes to the `gh-pages` branch.

## Advanced Features

### Search

Add search functionality using:

- Algolia DocSearch
- Local search plugins

### Internationalization (i18n)

Support multiple languages by:

1. Configuring locales in `docusaurus.config.js`
2. Creating translation files
3. Organizing content by locale

### Plugins

Extend functionality with plugins for:

- Analytics
- SEO optimization
- Content processing
- Custom features

## Best Practices

1. **Organize Content**: Use clear folder structures and meaningful file names
2. **Write Good Metadata**: Include descriptive titles and front matter
3. **Link Between Pages**: Use relative links to connect related content
4. **Test Builds**: Regularly test production builds before deployment
5. **Keep It Simple**: Start with basic features and add complexity as needed

## Useful Commands

| Command           | Description                    |
| ----------------- | ------------------------------ |
| `npm run start`   | Start development server       |
| `npm run build`   | Build for production           |
| `npm run serve`   | Serve production build locally |
| `npm run clear`   | Clear Docusaurus cache         |
| `npm run swizzle` | Customize theme components     |

## Resources

- [Official Docusaurus Documentation](https://docusaurus.io/)
- [Markdown Guide](https://www.markdownguide.org/)
- [React Documentation](https://react.dev/) (for custom components)
