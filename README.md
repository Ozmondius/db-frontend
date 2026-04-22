# Lion Guild ELDB Frontend

Guild database interface for Eternal Lands - searchable tables for harvestables, secrets, creatures, and routes.

**Live Demo:** (Will be hosted on GitHub Pages)

## Features

- 🌾 **Harvestable Locations** - Plants, herbs, and resources by map
- 🌀 **Secret Passages** - Portals, hidden routes, and teleporters  
- ⚔️ **Creature Spawns** - Monster locations across all maps
- 📍 **Route Guide** - Multi-map transitions and pathfinding
- 🔍 **Search & Filter** - Find any map, item, or creature instantly
- ↕️ **Sortable Tables** - Click headers to sort by any field
- 📱 **Responsive Design** - Works on desktop, tablet, mobile

## Quick Start (For Guild Members)

1. Visit the forum link: https://lionguild.freeforums.net/
2. Click the **ELDB Database** link in the navigation
3. Search for what you need:
   - **Harvestables**: Find gathering spots for herbs/plants
   - **Secrets**: Locate hidden passages and portals
   - **Creatures**: See where monsters spawn
   - **Routes**: Plan multi-map travels efficiently

## For Developers - Setup on GitHub Pages

### Prerequisites
- GitHub account (free)
- Git command-line tool (optional, but easier)

### Option A: Using GitHub Web Interface (Easiest)

1. **Create GitHub Repository**
   - Go to https://github.com/new
   - Name: `eldb-frontend` (or whatever you like)
   - Make it **Public**
   - Click "Create repository"

2. **Upload Files**
   - Click "Add file" → "Upload files"
   - Drag-and-drop these HTML files from `Local/Guardbot/ELDB/`:
     - `index.html`
     - `harvestables.html`
     - `secrets.html`
     - `creatures.html`
     - `routes.html`
   - Click "Commit changes"

3. **Enable GitHub Pages**
   - Go to repository Settings
   - Scroll to "GitHub Pages"
   - Source: Select `main` branch
   - Click Save
   - Wait ~1 minute for deployment

4. **Your URL will be:**
   ```
   https://YOUR-GITHUB-USERNAME.github.io/eldb-frontend/index.html
   ```

### Option B: Using Git Command Line

```bash
# Clone the repository you created (substitute YOUR-USERNAME)
git clone https://github.com/YOUR-USERNAME/eldb-frontend.git
cd eldb-frontend

# Copy HTML files from Local/Guardbot/ELDB/
cp /path/to/Local/Guardbot/ELDB/*.html .

# Push to GitHub
git add .
git commit -m "Initial ELDB database frontend"
git push origin main
```

### Option C: Using GitHub Desktop (Graphical)

1. Download GitHub Desktop: https://desktop.github.com/
2. Create new repository with your GitHub account
3. Drag-and-drop HTML files into the folder
4. Commit and push via the GUI

## Updating the Database

When you run the ELDB scraper or make changes:

```bash
# Regenerate HTML files (on your local machine)
python Utilities/Export-ELDB-StaticHTML.py

# Push updates to GitHub
cd Local/Guardbot/ELDB
git add *.html
git commit -m "Update ELDB data - $(date)"
git push origin main
```

The website will auto-update within ~1 minute.

## Embedding in Freeforums Guild Forum

Once your GitHub Pages URL is ready, embed it in your forum:

1. Log in to https://lionguild.freeforums.net/
2. Go to **Admin Panel** → **Pages**
3. Create new page or edit existing one
4. Add this HTML where you want the database:

```html
<iframe 
    src="https://YOUR-USERNAME.github.io/eldb-frontend/index.html" 
    width="100%" 
    height="900" 
    frameborder="0"
    style="border: 1px solid #ccc; border-radius: 4px;">
</iframe>
```

Replace `YOUR-USERNAME` with your actual GitHub username.

## File Sizes

The generated files are:
- `index.html` - 9.4 KB (dashboard)
- `harvestables.html` - 597 KB (2,211 locations)
- `secrets.html` - 61 KB (138 secret routes)
- `creatures.html` - 333 KB (1,442 spawn records)
- `routes.html` - 41 KB (transition guide)

Total: ~1.1 MB - well within GitHub's free hosting limits.

## Data Source

Data generated from the ELDB (Eternal Lands Database) with custom aggregation:
- Harvestable locations from el-db.com
- Secret interactions curated by guild members
- Creature spawns from automated extraction
- Routes calculated from map transition data

Last updated: See footer on each page.

## Customization

To modify the look/feel, edit `Utilities/Export-ELDB-StaticHTML.py`:

- **Colors**: Change `LION_GOLD`, `LION_DARK`, `LION_ACCENT` constants
- **Title/Header**: Edit strings in each `generate_*()` function
- **Table columns**: Add/remove fields from SQL SELECT statements

Then regenerate:
```bash
python Utilities/Export-ELDB-StaticHTML.py
```

## Troubleshooting

**"Can't find the database"**
- Make sure `Local/Guardbot/ELDB/eldb.db` exists
- Run `Utilities/Build-ELDB-Database.py` first to create it

**"HTML won't upload to GitHub"**
- Check file is named correctly (no spaces, lowercase)
- GitHub Pages requires `index.html` for the root

**"Iframe not showing in forum"**
- Check freeforums allows iframes (some hosts block them)
- Try adding `allow="all"` attribute to iframe tag
- Test URL directly in browser first

**"Data is stale"**
- Regenerate with `Export-ELDB-StaticHTML.py`
- Push new files to GitHub
- Clear browser cache (Ctrl+Shift+Delete)
- Wait ~5 minutes for GitHub Pages to update

## Questions?

See `Main Scripts/Farm/Farm Docs/` or contact guild leadership for:
- ELDB data questions
- Feature requests
- Technical issues

---

**Lion Guild ELDB** - Keeping Eternal Lands organized since 2026.
