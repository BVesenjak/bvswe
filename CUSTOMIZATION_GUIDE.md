# Quick Customization Guide

> **TL;DR**: Search for these exact strings in your editor and replace them with your actual content.

## 🎯 5-Minute Setup

### 1. Replace Images (Required)

**Location**: `public/screens/`

Replace these 4 placeholder files with your real screenshots:
- `screen1.jpg` - Dashboard/Home page
- `screen2.jpg` - Product/Feature page  
- `screen3.jpg` - Checkout/Conversion page
- `screen4.jpg` - Analytics/Backend view

**Recommended specs**: 1200×800px, JPG or PNG

---

### 2. Update Email (Required)

**File**: `src/components/ContactModal.vue`  
**Line**: ~79

**Find**:
```javascript
window.location.href = `mailto:hello@example.com?subject=${subject}&body=${body}`
```

**Replace** `hello@example.com` with your email.

---

### 3. Update Gallery Projects (Required)

**File**: `src/components/Gallery.vue`  
**Line**: ~30

**Find**:
```javascript
const projects = [
  {
    title: 'eCommerce Platform',
    url: 'https://example.com',
    images: ['/screens/screen1.jpg', ...]
  },
```

**Replace** with your real projects:
```javascript
const projects = [
  {
    title: 'Your Project Name',
    url: 'https://your-live-site.com',
    images: [
      '/screens/your-project-home.jpg',
      '/screens/your-project-about.jpg',
      '/screens/your-project-contact.jpg'
    ]
  },
  // Add 3-6 projects total
]
```

---

### 4. Update Footer Contact (Required)

**File**: `src/components/Footer.vue`  
**Line**: ~33-38

**Find**:
```html
<a href="mailto:hello@example.com">hello@example.com</a>
<a href="tel:+1234567890">+1 (234) 567-890</a>
```

**Replace** with your contact info.

---

### 5. Update Social Links (Required)

**File**: `src/components/Footer.vue`  
**Line**: ~50-65

**Find**:
```javascript
const socials = [
  { name: 'Twitter', url: 'https://twitter.com', ... },
  { name: 'GitHub', url: 'https://github.com', ... },
  { name: 'LinkedIn', url: 'https://linkedin.com', ... }
]
```

**Replace** URLs with your profiles.

---

## 🎨 Optional Customization

### Change Brand Color

**File**: `tailwind.config.js`  
**Line**: ~10

**Find**:
```javascript
purple: '#5c3cff',
```

**Replace** with your brand color (e.g., `'#FF6B35'`).

---

### Add Your Avatar

**File**: `src/components/Navbar.vue`  
**Line**: ~38-44

**Find**:
```vue
<div class="w-full h-full bg-gradient-to-br from-brand-purple to-brand-purple-light">
  P
</div>
```

**Replace** with:
```vue
<img src="/your-avatar.jpg" alt="Your Name" class="w-full h-full object-cover" />
```

Don't forget to add `your-avatar.jpg` to the `public/` folder!

---

### Update SEO Meta Tags

**File**: `index.html`  
**Line**: ~7-11

**Find**:
```html
<meta name="description" content="Full-stack developer specializing..." />
<title>Portfolio - Software & eCommerce Developer</title>
```

**Replace** with your title and description.

---

### Change CTA Button Text

**File**: `src/components/Hero.vue`  
**Line**: ~26 and ~35

**Find**:
```html
<button>Hire Me</button>
<button>Book a 15-min Call</button>
```

**Replace** with your preferred CTAs.

---

### Link to Calendar (Optional)

**File**: `src/components/Hero.vue` or `Navbar.vue`

**Find**:
```vue
<button @click="$emit('open-contact')">Book a 15-min Call</button>
```

**Replace** with direct Calendly/Cal.com link:
```vue
<a href="https://calendly.com/your-link" target="_blank" class="...">
  Book a 15-min Call
</a>
```

---

## 🔍 Find & Replace Reference

Use your editor's "Find in Files" feature:

| Find This | Replace With | Location |
|-----------|-------------|----------|
| `hello@example.com` | Your email | ContactModal.vue, Footer.vue |
| `https://example.com` | Real URLs | Gallery.vue (6 instances) |
| `#5c3cff` | Your brand color | tailwind.config.js |
| `Portfolio` (in navbar) | Your name/brand | Navbar.vue, Footer.vue |
| `+1 (234) 567-890` | Your phone | Footer.vue |

---

## ✅ Pre-Launch Checklist

- [ ] Replaced all 4 screenshot placeholders
- [ ] Updated contact email (2 locations)
- [ ] Added real project URLs in Gallery
- [ ] Updated social links (Twitter, GitHub, LinkedIn)
- [ ] Changed brand colors (optional)
- [ ] Added real avatar image (optional)
- [ ] Updated page title and meta description
- [ ] Tested mobile responsiveness
- [ ] Verified all links work
- [ ] Ran `npm run build` successfully

---

## 🚀 Deploy

```bash
npm run build
```

Then upload the `dist/` folder to:
- **Netlify**: Drag & drop at netlify.com/drop
- **Vercel**: `npx vercel --prod`
- **GitHub Pages**: Push `dist/` to `gh-pages` branch

---

**That's it!** Your portfolio is ready to go live. 🎉

