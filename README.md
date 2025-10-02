# Portfolio Website

A modern, responsive portfolio website built with Vue 3, Vite, and Tailwind CSS. Features beautiful animations, accessibility-first design, and optimized performance.

## 🚀 Quick Start

### Prerequisites

- Node.js 16+ and npm

### Installation

```bash
npm install
```

### Development

```bash
npm run dev
```

Visit `http://localhost:5173` to view the site.

### Build for Production

```bash
npm run build
```

Preview the production build:

```bash
npm run preview
```

## 📁 Project Structure

```
portfolio-website/
├── public/
│   ├── favicon.svg
│   └── screens/
│       ├── screen1.jpg  (placeholder - replace with real screenshots)
│       ├── screen2.jpg
│       ├── screen3.jpg
│       └── screen4.jpg
├── src/
│   ├── components/
│   │   ├── Navbar.vue           (Sticky nav with status indicator)
│   │   ├── Hero.vue             (Hero section with CTAs)
│   │   ├── IPadShowcase.vue     (Animated iPad with scroll loop)
│   │   ├── ProvenSection.vue    (Stats and case results)
│   │   ├── StatCard.vue         (Reusable stat card)
│   │   ├── Gallery.vue          (Auto-switching gallery)
│   │   ├── GalleryTile.vue      (Individual gallery item)
│   │   ├── ServicesProcess.vue  (Services and workflow)
│   │   ├── StackGuarantees.vue  (Tech stack and promises)
│   │   ├── Footer.vue           (Footer with links)
│   │   └── ContactModal.vue     (Contact form modal)
│   ├── App.vue
│   ├── main.js
│   └── style.css
├── index.html
├── package.json
├── vite.config.js
├── tailwind.config.js
└── postcss.config.js
```

## 🎨 Customization Guide

### 1. Replace Placeholder Images

Drop your real project screenshots into `public/screens/`:

- **screen1.jpg** through **screen4.jpg** - These are used in the hero iPad showcase and gallery tiles
- Recommended size: 1200×800px or higher
- Format: JPG, PNG, or WebP

### 2. Update CTA Links

**In `src/components/ContactModal.vue`** (line ~79):

```javascript
// Replace with your actual email
window.location.href = `mailto:YOUR_EMAIL@example.com?subject=${subject}&body=${body}`
```

**In `src/components/Navbar.vue` and `Hero.vue`**:

The "Hire Me" and "Book a 15-min Call" buttons emit an `open-contact` event that opens the modal. You can alternatively link directly to Calendly/Cal.com:

```vue
<!-- Replace button @click with href -->
<a href="https://calendly.com/your-link" target="_blank">
  Book a 15-min Call
</a>
```

### 3. Update Gallery Projects

**In `src/components/Gallery.vue`** (line ~30):

```javascript
const projects = [
  {
    title: 'Your Project Name',
    url: 'https://your-live-site.com',  // ← Change this
    images: [
      '/screens/your-screenshot1.jpg',   // ← Add your images
      '/screens/your-screenshot2.jpg',
      '/screens/your-screenshot3.jpg'
    ]
  },
  // ... add more projects
]
```

### 4. Update Avatar/Status Circle

**In `src/components/Navbar.vue`** (line ~38):

Replace the placeholder gradient circle with your actual avatar image:

```vue
<!-- Replace the div with: -->
<img 
  src="/your-avatar.jpg" 
  alt="Profile" 
  class="w-full h-full object-cover"
/>
```

### 5. Brand Colors

**In `tailwind.config.js`** (line ~10):

```javascript
colors: {
  brand: {
    purple: '#5c3cff',        // ← Change to your brand color
    'purple-dark': '#4a2edb',
    'purple-light': '#7859ff',
  }
}
```

### 6. Contact Information

**In `src/components/Footer.vue`** (line ~33):

```javascript
// Update email and phone
<a href="mailto:YOUR_EMAIL@example.com">
<a href="tel:+YOUR_PHONE">
```

### 7. Social Links

**In `src/components/Footer.vue`** (line ~50):

```javascript
const socials = [
  {
    name: 'Twitter',
    url: 'https://twitter.com/YOUR_HANDLE',  // ← Update
    icon: '...'
  },
  // ... update GitHub, LinkedIn
]
```

### 8. SEO Meta Tags

**In `index.html`** (line ~7):

```html
<meta name="description" content="Your custom description" />
<meta property="og:title" content="Your Name - Portfolio" />
<!-- Update other meta tags -->
```

## ✨ Features

### Animations

- **iPad Slide-in**: Entrance animation on hero load
- **iPad Scroll Loop**: Continuous vertical scroll simulation
- **Gallery Auto-swap**: Each tile cycles through 3 screenshots
- **Status Ring**: Pulsing green availability indicator
- **Prefers-reduced-motion**: All animations respect user preferences

### Responsive Design

- **Mobile-first**: Stacks to single column, hamburger menu
- **Tablet**: 2-column layouts
- **Desktop**: Full 3-column grids, sticky navbar

### Accessibility

- Semantic HTML5
- ARIA labels on interactive elements
- Keyboard navigation support
- Focus indicators on all interactive elements
- Alt text on all images
- Color contrast meets WCAG AA

### Performance

- Vite for lightning-fast HMR
- Tailwind JIT for minimal CSS
- No heavy animation libraries
- Optimized transitions
- Lazy-loaded components ready (add `defineAsyncComponent` if needed)

## 🛠 Tech Stack

- **Vue 3** - Composition API
- **Vite** - Build tool and dev server
- **Tailwind CSS** - Utility-first styling
- **PostCSS** - CSS processing
- **SVG** - Placeholder images and icons

## 📝 Notes

- **No Backend Required**: Contact form uses `mailto:` links
- **Static Hosting**: Deploy to Netlify, Vercel, GitHub Pages, or any static host
- **TypeScript Ready**: Rename `.vue` to add `<script setup lang="ts">` if needed
- **No External Dependencies**: Beyond Vue and Tailwind

## 🌐 Deployment

### Netlify

```bash
npm run build
# Drag `dist` folder to Netlify
```

### Vercel

```bash
npm run build
vercel --prod
```

### GitHub Pages

```bash
npm run build
# Copy dist contents to gh-pages branch
```

## 📄 License

MIT - feel free to use this template for your portfolio!

---

**Need help?** Open an issue or reach out via the contact form.

