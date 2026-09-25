# ⚡ Setup in 5 Minutes

## Step 1: Unzip & Install

```bash
tar -xzf birthday-surprise.tar.gz
cd birthday-surprise
npm install
```

## Step 2: Customize

Open **`src/config/birthday.ts`** and replace these placeholders:

```
[Her Name]              → Her actual name
[Nickname]              → Your nickname for her
[Add location]          → Actual locations
[Add photos]            → Real photo paths
[Artist]                → Song artists
```

That's it for basic personalization. The site will work immediately.

## Step 3: Test Locally

```bash
npm run dev
```

Opens at `http://localhost:5173`. Test on mobile by visiting from your phone.

## Step 4: Deploy

**Vercel (recommended):**

```bash
npm install -g vercel
vercel
```

Follow the prompts. Your site is live in 2 minutes.

**Or use any host:** Just upload `/dist` folder after running `npm run build`.

---

## Optional: Add Real Photos & Music

### Photos
1. Add images to `/public/images/`
2. Update file references in `src/config/birthday.ts`
   
Example:
```typescript
image: '/images/my-photo.jpg',
```

### Music
1. Add MP3s to `/public/music/`
2. Update paths in `src/config/birthday.ts`

Example:
```typescript
{ title: 'Song Name', artist: 'Artist', src: '/music/my-song.mp3' }
```

The site works **with or without** real photos/music — placeholders will show if files are missing.

---

## 🎉 Done!

Copy the live link and send it. The experience is fully personalized.

For deeper customization, see **`README.md`**.
