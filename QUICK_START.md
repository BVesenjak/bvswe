# 🚀 Quick Start Guide

## Get Running in 2 Minutes

### Step 1: Install Dependencies
```bash
npm install
```

### Step 2: Start Development Server
```bash
npm run dev
```

### Step 3: Open in Browser
```
http://localhost:5173
```

**You should now see your portfolio running!** ✨

---

## 📝 What You'll See

### Hero Section (Purple Background)
- Large headline: "Software, eCommerce & Automation that ships revenue."
- Two CTA buttons (opens contact modal)
- Animated iPad showcase on the right with auto-scrolling demo

### Proven Section (White Background)
- 4 stat cards with case-like results
- Anonymized company descriptions

### Live Gallery (White Background)
- 6 project tiles
- Each tile auto-swaps through 3 screenshots
- Hover shows project title and "Open site →"

### Services & Process (Gray Background)
- Left: "What I Do" list
- Right: "How I Work" timeline

### Tech Stack & Guarantees (White Background)
- 8 tech logos/badges
- 4 guarantee cards

### Footer (Gray Background)
- Contact info
- Social links
- Navigation sitemap

---

## 🎯 Next Steps

### 1. Replace Placeholder Images
Navigate to `public/screens/` and replace these 4 files with your real screenshots:
- `screen1.jpg` → Your project screenshot 1
- `screen2.jpg` → Your project screenshot 2
- `screen3.jpg` → Your project screenshot 3
- `screen4.jpg` → Your project screenshot 4

### 2. Update Your Email
Open `src/components/ContactModal.vue` and search for:
```
hello@example.com
```
Replace with your actual email address.

### 3. Add Your Projects
Open `src/components/Gallery.vue` and update the `projects` array with your real project URLs and images.

### 4. Customize Colors (Optional)
Open `tailwind.config.js` and change:
```javascript
purple: '#5c3cff'  // ← Your brand color
```

---

## 🛠️ Available Commands

```bash
# Development server (with hot reload)
npm run dev

# Build for production
npm run build

# Preview production build locally
npm run preview
```

---

## 📚 Documentation

- **Full Setup**: See `README.md`
- **Customization**: See `CUSTOMIZATION_GUIDE.md`
- **Project Details**: See `PROJECT_SUMMARY.md`
- **File Tree**: See `FILE_TREE.txt`

---

## 🎨 Design Features

### Animations (All Respect prefers-reduced-motion)
- ✅ iPad slides in from left on hero load
- ✅ iPad screen content scrolls continuously
- ✅ Gallery images auto-swap 3 times then freeze
- ✅ Green status ring pulses in navbar
- ✅ Smooth hover effects throughout

### Responsive Design
- ✅ Mobile: Hamburger menu, stacked layouts
- ✅ Tablet: 2-column grids
- ✅ Desktop: 3-column grids, side-by-side hero

### Accessibility
- ✅ Keyboard navigation support
- ✅ ARIA labels on interactive elements
- ✅ Focus indicators
- ✅ Semantic HTML
- ✅ Alt text on images

---

## 🐛 Common Issues

### Port Already in Use
```bash
# Kill process on port 5173
# Windows:
netstat -ano | findstr :5173
taskkill /PID <PID> /F

# Mac/Linux:
lsof -ti:5173 | xargs kill
```

### Images Not Loading
- Ensure files are in `public/screens/`
- Check file names match exactly (case-sensitive)
- Restart dev server after adding images

### Tailwind Classes Not Working
```bash
# Restart dev server
Ctrl+C
npm run dev
```

---

## 🚀 Ready to Deploy?

### Netlify (Easiest)
1. Run `npm run build`
2. Go to https://netlify.com/drop
3. Drag the `dist/` folder
4. Done! 🎉

### Vercel
```bash
npm run build
npx vercel --prod
```

### GitHub Pages
```bash
npm run build
cd dist
git init
git add -A
git commit -m 'deploy'
git push -f git@github.com:username/repo.git main:gh-pages
```

---

## 💡 Tips

1. **Test Animations**: Open dev tools → Network → Throttle to "Slow 3G" to see animations better
2. **Mobile Testing**: Use Chrome DevTools responsive mode (Ctrl+Shift+M)
3. **Performance**: Run Lighthouse audit (Chrome DevTools → Lighthouse)
4. **Accessibility**: Test with keyboard only (no mouse)

---

## 📧 Need Help?

Check these resources:
1. `README.md` - Comprehensive guide
2. `CUSTOMIZATION_GUIDE.md` - Quick find & replace guide
3. `PROJECT_SUMMARY.md` - Complete project details

---

**Happy coding!** 🎉

