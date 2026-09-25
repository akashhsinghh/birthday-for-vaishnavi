# 💝 Birthday Surprise Website

A premium, interactive digital birthday journey built with React, TypeScript, Tailwind CSS, and Framer Motion. Personalize every detail and deploy to share with someone special.

---

## 📋 Quick Start

### 1. Install & Run

```bash
npm install
npm run dev
```

The app opens at `http://localhost:5173` — hot reload enabled.

### 2. Personalize Everything

**All personal content lives in ONE file:**

```
src/config/birthday.ts
```

Open it and replace placeholders like `[Her Name]`, `[Add location]`, etc. Every screen pulls from this config — no need to dig through React components.

### 3. Add Photos

Place photos in `/public/images/`:

```
public/images/
├── memory-1.jpg
├── memory-2.jpg
├── gallery-1.jpg
├── gallery-2.jpg
└── ... (add as many as you like)
```

Update `src/config/birthday.ts` to reference them:

```typescript
memories: [
  {
    image: '/images/memory-1.jpg',
    // ...
  }
]
```

If a photo is missing, the app shows a graceful placeholder — no errors.

### 4. Add Music

Place songs in `/public/music/`:

```
public/music/
├── song-1.mp3
├── song-2.mp3
└── song-3.mp3
```

Update the playlist in `src/config/birthday.ts`:

```typescript
playlist: [
  { id: 's1', title: 'Song Name', artist: 'Artist', src: '/music/song-1.mp3' },
  { id: 's2', title: '...', artist: '...', src: '/music/song-2.mp3' },
]
```

**Important:** Only use audio files you have the right to distribute. The app expects MP3s.

### 5. Build & Deploy

#### Vercel (Recommended — 2 minutes)

```bash
npm run build
npm install -g vercel
vercel
```

Follow the prompts. Your site is live.

#### Netlify

Drag `/dist` folder to netlify.com/drop, or:

```bash
npm run build
```

Connect your GitHub repo to Netlify for automatic deploys.

#### GitHub Pages

```bash
npm run build
# Push dist/ folder to your gh-pages branch
```

#### Self-Hosted

```bash
npm run build
# Deploy /dist folder to any static host
```

---

## 🎨 Customization Guide

### Edit the Love Letter

In `src/config/birthday.ts`, find `loveLetter`:

```typescript
loveLetter: `This is your letter. Use \n\n for paragraph breaks.
You can make it as long or short as you like.`
```

### Edit Reasons I Love You

```typescript
reasonsILoveYou: [
  { id: 'r1', text: 'Your smile', emoji: '😊' },
  // Add more...
]
```

### Edit Quiz Questions

```typescript
quiz: [
  {
    id: 'q1',
    question: 'Where did we first meet?',
    options: ['Real answer', 'Fake 1', 'Fake 2', 'Fake 3'],
    correctIndex: 0, // Index of the correct answer
  }
]
```

### Edit Final Messages

```typescript
finalTitle: 'Happy Birthday, My Love',
finalMessageOne: 'Thank you for being...',
finalMessageTwo: 'Forever grateful for you.',
finalEasterEggMessage: 'Secret message when tapping heart 5 times.',
```

### Edit Balloon Wishes

```typescript
balloonWishes: [
  { id: 'b1', message: "You're my favorite person." },
  // Add more...
]
```

---

## 🎬 Journey Stages

The website follows this flow automatically:

1. **Welcome** — Beautiful intro
2. **Intro** — Personalized message + days together
3. **Balloons** — Interactive balloon-popping game (7 wishes)
4. **Cake** — Light candles + blow them out celebration
5. **Reveal** — "Happy Birthday" cinematic reveal
6. **Memories** — Timeline of photos & moments
7. **Reasons** — Flip through reasons you love them
8. **Letter** — Handwritten-style love letter (envelope opens)
9. **Playlist** — Full music player with queue
10. **Gallery** — Masonry photo grid (long-press for hidden notes)
11. **Quiz** — "How well do you know us?" game
12. **Final** — Cinematic ending + confetti

Each stage unlocks only after the previous one completes. Users can't skip ahead.

---

## 🎵 Music Player Details

- **Plays**: MP3 files from `/public/music/`
- **Controls**: Play/pause, skip, volume, seek
- **Persistent**: Music keeps playing as you navigate
- **Smart**: If browser blocks autoplay, tap to play
- **Graceful**: Missing files don't break the experience

The player floats at the bottom-right with a tiny now-playing label.

---

## 📸 Photo Assets

### Memory Photos
- Path: `/public/images/memory-{1..6}.jpg`
- Size: Recommended 1200px wide (any aspect ratio)
- Format: JPG, PNG, WebP
- Quality: High (the site looks premium)

### Gallery Photos
- Path: `/public/images/gallery-{1..9}.jpg`
- Size: Recommended 600px to 800px wide
- Format: JPG, PNG, WebP

The gallery uses masonry layout — varied aspect ratios look great.

### Optional Hidden Notes
In the gallery, you can add secret messages to photos:

```typescript
{
  id: 'g3',
  src: '/images/gallery-3.jpg',
  caption: 'That afternoon',
  hiddenNote: "You didn't know I took this. I still smile when I see it."
}
```

Users discover the note by long-pressing the photo.

---

## 🔧 Advanced Customization

### Change Colors

Edit `/src/index.css` — the theme is defined at the top in `@theme`:

```css
@theme {
  --color-rose-500: #d06f8d;
  --color-ivory: #fdf6ee;
  /* ... more colors */
}
```

### Add More Sections

Each section is a React component in `/src/sections/`. To add a custom stage:

1. Create `/src/sections/MyStage.tsx`
2. Export a component that accepts `{ onComplete: () => void }`
3. Add to `STAGES` in `/src/data/stages.ts`
4. Import and add to the stageMap in `/src/App.tsx`

### Sound Effects

Optional sound effects (click, pop, chime) are in `/public/sounds/`. If files are missing, everything still works silently.

To add your own:

```
public/sounds/
├── click.mp3
├── pop.mp3
├── chime.mp3
├── whoosh.mp3
└── celebrate.mp3
```

---

## ♿ Accessibility

The site includes:

- Semantic HTML & ARIA labels
- Keyboard navigation
- Focus indicators
- High contrast text
- Respects `prefers-reduced-motion`
- Screen reader support

All interactive elements have proper labels.

---

## 📱 Mobile First

Optimized for:

- 360px, 375px, 390px, 412px, 430px (common mobile widths)
- Tablets & desktops
- Portrait & landscape
- Safe area insets (notches, etc.)
- Touch-friendly buttons

No horizontal scroll. Everything adapts smoothly.

---

## 🚀 Performance

- Lazy-loaded images
- Optimized animations (GPU accelerated)
- Code-split sections
- Minimal dependencies
- ~60fps on modern phones

Build size: ~150KB gzipped (including all assets).

---

## 🌐 Browser Support

- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile Safari 14+

No IE support (it's 2024 🎉).

---

## 🔒 Privacy

- **No backend.** Everything runs locally.
- **No tracking.** No analytics, no third-party scripts.
- **No data collection.** Your personal content stays on your device.
- **Open source.** You can audit every line of code.

---

## 📦 Project Structure

```
birthday-surprise/
├── src/
│   ├── components/       # Reusable UI (Button, ProgressBar, etc.)
│   ├── sections/         # The 12 journey stages
│   ├── config/           # birthday.ts — all personal content
│   ├── data/             # Structure metadata
│   ├── hooks/            # React hooks (journey, audio, etc.)
│   ├── animations/       # Framer Motion variants
│   ├── utils/            # Helpers (format, sound, haptics)
│   ├── types/            # TypeScript types
│   ├── App.tsx           # Main router
│   ├── main.tsx          # Entry point
│   └── index.css         # Design tokens & base styles
├── public/
│   ├── images/           # Photos (add yours)
│   ├── music/            # Songs (add yours)
│   ├── sounds/           # Optional sound effects
│   ├── icons/            # App icon (auto-generated)
│   └── manifest.json     # PWA manifest
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts
└── .gitignore
```

---

## 🐛 Troubleshooting

### "Image not loading"

→ Check the path in `src/config/birthday.ts` matches the file in `/public/images/`

### "Music won't play"

→ Ensure MP3 file is in `/public/music/` and the path in config is correct. Check browser console for errors.

### "Animations stutter"

→ Update your browser. Disable other tabs. The animations are GPU-accelerated.

### "How do I add my own easter egg?"

→ Open `/src/components/SecretHeart.tsx` and modify. You have full control.

---

## 📝 Pro Tips

- **Test on your phone** while developing (`npm run dev`, then visit on mobile)
- **Proofread the love letter** — it's the emotional heart
- **Choose high-quality photos** — they deserve to look beautiful
- **Pick songs that matter** — our playlist screen shows them front & center
- **Make quiz questions personal** — inside jokes work great
- **Deploy early** — test the live version before sharing

---

## 🎁 What You Get

✨ Fully working website (not a template)  
✨ All 12 interactive stages  
✨ Beautiful animations & micro-interactions  
✨ Mobile-first responsive design  
✨ Sound effects & haptics  
✨ Progress tracking & localStorage  
✨ Music player with persistent playback  
✨ Photo gallery with hidden notes  
✨ Easter eggs (secret heart, long-press reveals)  
✨ PWA support (add to home screen)  
✨ One-file personalization  
✨ Production-ready code  

---

## 💬 Questions?

- Stuck? Check `/src/config/birthday.ts` — 90% of customizations happen there
- Want to modify a section? Each component is well-commented
- Need a feature? All infrastructure is there — extend as needed

---

**Made with ❤️ for someone special.**

Deploy and share the link. The experience is fully personalized. Enjoy! 🎉
