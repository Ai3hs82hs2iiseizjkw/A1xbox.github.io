# XZONE Xbox Shop 🎮

A full-stack Xbox product shop with Discord bot management and GitHub Pages website.

## Features

✅ **Website** (`index.html`)
- Sleek gaming aesthetic with neon lime green accents
- Product showcase with real-time inventory
- Mobile responsive (3 cols desktop, 2 tablet, 1 mobile)
- Admin panel with PIN protection (Default: `1234`)
- Discord webhook integration for notifications

✅ **Discord Bot** (`bot.js`)
- Slash commands for product management
- Supabase database (permanent, no expiration)
- Admin channel restriction
- Real-time inventory updates

## Setup

### 1. Supabase Database
1. Go to [supabase.com](https://supabase.com) → Create account
2. Create a new project
3. Go to **SQL Editor** → **New Query** → Run this:

```sql
CREATE TABLE products (
  id BIGSERIAL PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  price VARCHAR(100) NOT NULL,
  description TEXT,
  img TEXT,
  stock VARCHAR(20) DEFAULT 'in',
  category VARCHAR(50) NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);
```

4. Go to **Settings → API** → Copy:
   - **Project URL** → `SUPABASE_URL`
   - **anon public key** → `SUPABASE_KEY`

### 2. Discord Bot
1. Go to [discord.com/developers](https://discord.com/developers)
2. Click **New Application** → Name: "XZONE Bot"
3. Go to **Bot** → **Add Bot**
4. Copy **TOKEN** → `DISCORD_TOKEN`
5. Go to **OAuth2 → URL Generator**:
   - Scopes: `bot`
   - Permissions: `applications.commands`
   - Open the generated URL to invite bot to your server
6. Right-click your Discord channel → **Copy ID** → `ADMIN_CHANNEL_ID`

### 3. Environment Setup
```bash
# Copy template
cp .env.example .env

# Edit .env with your values
nano .env
```

Fill in:
```
DISCORD_TOKEN=your_bot_token
SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_key
ADMIN_CHANNEL_ID=your_channel_id
```

### 4. Install & Run
```bash
# Install dependencies
npm install

# Start bot
npm start

# Dev mode (auto-reload)
npm run dev
```

## Bot Commands

All commands work only in your admin channel:

- `/add name: price: desc: category: stock:` — Add product
- `/remove name:` — Remove product
- `/edit name: field: value:` — Edit product
- `/list` — Show all products
- `/soldout name:` — Mark out of stock
- `/restock name:` — Mark in stock
- `/clear` — Delete all products (confirmation required)

## Website

- **Live**: `https://Ai3hs82hs2iiseizjkw.github.io/A1xbox.github.io/`
- **Admin**: Press `Ctrl+Shift+A` on website → PIN: `1234`
- **Features**:
  - Add/edit/delete products
  - Change PIN
  - Save Discord webhook URL
  - Update social media links (Instagram/TikTok)

## Database Schema

```
products
├── id (PRIMARY KEY)
├── name (VARCHAR)
├── price (VARCHAR)
├── description (TEXT)
├── img (TEXT - image URL)
├── stock (VARCHAR - 'in' or 'out')
├── category (VARCHAR - 'series', 'xbox360', 'console')
└── created_at (TIMESTAMP)
```

## File Structure

```
A1xbox.github.io/
├── index.html          # Website (all-in-one HTML)
├── bot.js              # Discord bot
├── package.json        # Dependencies
├── .env                # Environment variables (keep secret!)
├── .env.example        # Template
└── README.md           # This file
```

## Shop Name

**Arabic:** احمد الكعبي  
**English:** Ahmad Al-Kaabi  
**Subtitle:** للاجهزة الالكترونية (Electronics)

## Design

- **Colors**: Black background, neon lime green (#39ff14), dark green accents
- **Fonts**: Bebas Neue (headings), Rajdhani (body)
- **Aesthetic**: Futuristic gaming streetwear
- **Effects**: Scanlines, grid texture, button glow, card hover animations

## Tech Stack

- **Frontend**: HTML5, CSS3, Vanilla JS (no frameworks)
- **Backend**: Discord.js v14, Node.js
- **Database**: Supabase (PostgreSQL)
- **Hosting**: GitHub Pages (website), any server (bot)

## Security Notes

⚠️ **Never commit `.env` file** — it contains sensitive tokens!
- Add to `.gitignore` (already included)
- Keep `DISCORD_TOKEN` and `SUPABASE_KEY` private
- Change default PIN to something secure

## Troubleshooting

**Bot not responding?**
- Check ADMIN_CHANNEL_ID is correct
- Ensure bot has "applications.commands" permission
- Run `/list` to test

**Website not updating?**
- Check Supabase connection in browser console
- Verify SUPABASE_URL and SUPABASE_KEY match

**Can't add products?**
- Ensure Supabase table exists
- Check bot is in admin channel

## License

Built with ❤️ for XZONE Xbox Shop
