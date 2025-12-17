# Educational Apps Gallery Management System - Setup Guide

## 📋 Table of Contents
1. [Overview](#overview)
2. [System Architecture](#system-architecture)
3. [Initial Setup](#initial-setup)
4. [File Structure](#file-structure)
5. [Admin Panel Usage](#admin-panel-usage)
6. [Managing Apps](#managing-apps)
7. [GitHub Setup](#github-setup)
8. [Custom Domain Configuration](#custom-domain-configuration)
9. [Backup & Recovery](#backup--recovery)
10. [Troubleshooting](#troubleshooting)

---

## 🎯 Overview

This system allows you to manage multiple educational app galleries through a web-based admin interface. All galleries are static HTML pages hosted on GitHub Pages, with app configurations stored in your browser's localStorage.

### Key Features
- ✅ Multiple categorized galleries (Games, Chemistry, Quiz, etc.)
- ✅ GUI-based app management (no code editing required)
- ✅ Enable/disable apps with toggle switches
- ✅ Obscured gallery URLs for privacy
- ✅ Password-protected admin panel
- ✅ Export/import configurations for backup

---

## 🏗️ System Architecture

### Storage Method
- **localStorage**: App configurations are stored in your browser's localStorage
- **Static Hosting**: All pages are static HTML/CSS/JS on GitHub Pages
- **No Backend**: No server-side processing required

### Gallery Structure
Each gallery has:
- A unique short URL (e.g., `/g/gm` for games)
- Its own set of apps (can be enabled/disabled)
- Shared styling and functionality

---

## 🚀 Initial Setup

### Step 1: Create Your GitHub Repository

1. Go to [GitHub](https://github.com) and sign in
2. Click **"New repository"** (green button)
3. Name it: `edu-apps-gallery` (or your preferred name)
4. Set to **Public** (required for GitHub Pages)
5. Initialize with a README
6. Click **"Create repository"**

### Step 2: Enable GitHub Pages

1. In your repository, go to **Settings** → **Pages**
2. Under "Source", select **Deploy from a branch**
3. Choose branch: **main** (or master)
4. Choose folder: **/ (root)**
5. Click **Save**
6. Wait 2-3 minutes for deployment
7. Your site will be available at: `https://yourusername.github.io/edu-apps-gallery/`

### Step 3: Upload Files to GitHub

You have two options:

#### Option A: Upload via GitHub Web Interface (Easier)

1. In your repository main page, click **"Add file"** → **"Upload files"**
2. Drag and drop all files maintaining folder structure:
   ```
   - admin.html
   - index.html
   - g/gm.html
   - g/ch.html
   - g/qz.html
   - assets/admin-style.css
   - assets/admin-script.js
   - assets/gallery-style.css
   - assets/gallery-script.js
   ```
3. Write a commit message: "Initial gallery setup"
4. Click **"Commit changes"**

#### Option B: Upload via Git (Advanced)

```bash
# Clone your repository
git clone https://github.com/yourusername/edu-apps-gallery.git
cd edu-apps-gallery

# Copy all files into the directory (maintaining structure)
# Then commit and push
git add .
git commit -m "Initial gallery setup"
git push origin main
```

### Step 4: Set Your Admin Password

1. Open `assets/admin-script.js` in GitHub
2. Find line 2: `const ADMIN_PASSWORD = "your-secure-password-here";`
3. Click the **pencil icon** to edit
4. Change to your desired password
5. Commit the change

**IMPORTANT**: This is client-side password protection (not ultra-secure, but prevents casual access)

---

## 📁 File Structure

```
your-repo/
├── index.html                    # Public landing page
├── admin.html                    # Admin management panel
├── g/                           # Gallery pages (obscured URLs)
│   ├── gm.html                  # Games gallery
│   ├── ch.html                  # Chemistry gallery
│   └── qz.html                  # Quiz gallery
├── assets/
│   ├── admin-style.css          # Admin panel styling
│   ├── admin-script.js          # Admin panel logic
│   ├── gallery-style.css        # Gallery page styling
│   └── gallery-script.js        # Gallery page logic
└── SETUP-GUIDE.md              # This guide
```

### URLs After Setup

- **Admin Panel**: `https://yourusername.github.io/edu-apps-gallery/admin.html`
- **Games Gallery**: `https://yourusername.github.io/edu-apps-gallery/g/gm.html`
- **Chemistry Gallery**: `https://yourusername.github.io/edu-apps-gallery/g/ch.html`
- **Quiz Gallery**: `https://yourusername.github.io/edu-apps-gallery/g/qz.html`

---

## 🎮 Admin Panel Usage

### Accessing the Admin Panel

1. Navigate to: `https://your-domain.com/admin.html`
2. Enter your password
3. Click **"Login"**

### Admin Panel Sections

#### 1. Gallery Tabs
- Click tabs to switch between galleries
- Each gallery shows its own apps
- Add new galleries using the "+" button

#### 2. App Management
- **Toggle Switch**: Enable/disable apps instantly
- **Edit Button**: Modify app details
- **Delete Button**: Remove apps permanently
- **Drag Handle**: Reorder apps (drag and drop)

#### 3. Add New App
- Click **"+ Add New App"** button
- Fill in the form:
  - **Title**: App name
  - **Description**: Brief description
  - **URL**: Full URL to the app
  - **Icon**: Lucide icon name (see [Lucide Icons](https://lucide.dev/icons/))
  - **Color**: Hex color code (e.g., #0061ff)
- Click **"Add App"**

#### 4. Export/Import

**Export Configuration**:
1. Click **"Export Config"** button
2. A JSON file downloads automatically
3. Save this file as backup

**Import Configuration**:
1. Click **"Import Config"** button
2. Select your JSON backup file
3. Confirm the import
4. All galleries and apps are restored

---

## 📝 Managing Apps

### Adding an App

1. Log into admin panel
2. Select the gallery (Games, Chemistry, Quiz)
3. Click **"+ Add New App"**
4. Fill in details:
   - **Title**: "Periodic Table Interactive"
   - **Description**: "Explore elements with 3D visualization"
   - **URL**: "https://yourusername.github.io/periodic-table/"
   - **Icon**: "atom" (choose from [Lucide Icons](https://lucide.dev/icons/))
   - **Color**: "#05cdfe"
5. Click **"Add App"**

### Editing an App

1. Find the app card
2. Click the **"Edit"** (pencil) button
3. Modify any field
4. Click **"Save Changes"**

### Enabling/Disabling an App

1. Find the app card
2. Click the **toggle switch** at the top right
3. Green = Enabled (shows in gallery)
4. Gray = Disabled (hidden from gallery)

### Reordering Apps

1. Click and hold the **grip icon** (⋮⋮) on an app card
2. Drag to desired position
3. Release to drop
4. Order is saved automatically

### Deleting an App

1. Find the app card
2. Click the **"Delete"** (trash) button
3. Confirm deletion
4. App is permanently removed

### Moving Apps Between Galleries

1. Note the app details (or export config first)
2. Delete from current gallery
3. Switch to target gallery
4. Add the app again

---

## 🔧 GitHub Setup

### Method 1: GitHub Web Interface (Recommended for Beginners)

#### Initial Upload
1. Go to your repository on GitHub
2. Click **"Add file"** → **"Create new file"**
3. For folders, type: `g/gm.html` (creates folder automatically)
4. Paste content, commit
5. Repeat for all files

#### Updating Files
1. Navigate to the file in GitHub
2. Click the **pencil icon** (Edit)
3. Make changes
4. Scroll down, write commit message
5. Click **"Commit changes"**

### Method 2: GitHub Desktop (User-Friendly)

1. Download [GitHub Desktop](https://desktop.github.com/)
2. Clone your repository
3. Edit files locally with any text editor
4. GitHub Desktop shows changes
5. Write commit message and click **"Commit"**
6. Click **"Push origin"** to upload

### Method 3: Git Command Line (Advanced)

```bash
# First time setup
git clone https://github.com/yourusername/edu-apps-gallery.git
cd edu-apps-gallery

# After making changes
git add .
git commit -m "Updated gallery apps"
git push origin main
```

---

## 🌐 Custom Domain Configuration

### Using Namecheap with GitHub Pages

#### Step 1: In Namecheap

1. Log into Namecheap
2. Go to **Domain List** → Select your domain
3. Click **"Manage"** → **"Advanced DNS"**
4. Add these records:

**For main domain (yourdomain.com):**
```
Type: A Record
Host: @
Value: 185.199.108.153
TTL: Automatic

Type: A Record
Host: @
Value: 185.199.109.153
TTL: Automatic

Type: A Record
Host: @
Value: 185.199.110.153
TTL: Automatic

Type: A Record
Host: @
Value: 185.199.111.153
TTL: Automatic
```

**For subdomain (apps.yourdomain.com):**
```
Type: CNAME Record
Host: apps
Value: yourusername.github.io
TTL: Automatic
```

#### Step 2: In GitHub

1. Go to repository **Settings** → **Pages**
2. Under "Custom domain", enter: `apps.yourdomain.com`
3. Click **"Save"**
4. Wait for DNS check (can take 24-48 hours)
5. Once verified, check **"Enforce HTTPS"**

#### Step 3: Create CNAME File

1. In your repository root, create file: `CNAME`
2. Content: Just one line with your domain:
   ```
   apps.yourdomain.com
   ```
3. Commit the file

### Your URLs After Custom Domain

- Admin: `https://apps.yourdomain.com/admin.html`
- Games: `https://apps.yourdomain.com/g/gm.html`
- Chemistry: `https://apps.yourdomain.com/g/ch.html`
- Quiz: `https://apps.yourdomain.com/g/qz.html`

---

## 💾 Backup & Recovery

### Regular Backup Routine

**Every Month** (or when you make significant changes):

1. Log into admin panel
2. Click **"Export Config"** button
3. Save the JSON file with date: `gallery-config-2025-12.json`
4. Store in a safe location (cloud storage, external drive)

### Restoring from Backup

1. Log into admin panel
2. Click **"Import Config"** button
3. Select your backup JSON file
4. Click **"Open"**
5. Confirm import
6. All galleries are restored

### Manual Backup (Advanced)

Your localStorage data is stored in your browser at:
- Key: `galleryApps`
- Value: JSON string of all apps

To manually backup:
1. Open browser DevTools (F12)
2. Go to **Console** tab
3. Type: `console.log(localStorage.getItem('galleryApps'))`
4. Copy the output and save to a text file

---

## 🔍 Troubleshooting

### Issue: Admin panel won't load

**Solution 1**: Check if files are uploaded correctly
- Go to your GitHub repository
- Verify `admin.html` exists in root folder
- Verify `assets/admin-script.js` exists

**Solution 2**: Clear browser cache
- Press `Ctrl + Shift + Delete` (Windows) or `Cmd + Shift + Delete` (Mac)
- Clear cached images and files
- Reload the page

**Solution 3**: Check GitHub Pages deployment
- Go to repository **Settings** → **Pages**
- Ensure "Your site is live" message appears
- Wait 2-3 minutes after any changes

### Issue: Password not working

**Solution**: Check password in code
1. Open `assets/admin-script.js` in GitHub
2. Verify line 2: `const ADMIN_PASSWORD = "your-password";`
3. Password is case-sensitive
4. No extra spaces before/after password

### Issue: Apps not showing in gallery

**Checklist**:
- [ ] Is the app enabled? (toggle should be green in admin panel)
- [ ] Is the gallery ID correct in `gallery-script.js`?
- [ ] Did you hard refresh the gallery page? (`Ctrl + F5`)
- [ ] Check browser console for errors (F12 → Console tab)

### Issue: Changes not appearing

**Solutions**:
1. **Hard refresh**: `Ctrl + F5` (Windows) or `Cmd + Shift + R` (Mac)
2. **Clear localStorage**: 
   - Open DevTools (F12)
   - Go to **Application** → **Local Storage**
   - Right-click → **Clear**
   - Reload page
3. **Check GitHub deployment**:
   - Changes can take 1-2 minutes to deploy
   - Go to **Actions** tab to see deployment status

### Issue: Gallery page is blank

**Solution**: Check gallery ID
1. Open the gallery HTML file (e.g., `g/gm.html`)
2. Look for: `<script>const GALLERY_ID = 'games';</script>`
3. Verify this matches the gallery name in admin panel

### Issue: Icons not displaying

**Solution**: Check Lucide CDN
1. Verify internet connection
2. Check if Lucide CDN is accessible
3. Valid icon names are at: [https://lucide.dev/icons/](https://lucide.dev/icons/)
4. Ensure icon name is lowercase with hyphens (e.g., `flask-round`, not `FlaskRound`)

### Issue: Custom domain not working

**Solutions**:
1. **DNS propagation**: Can take 24-48 hours
2. **Check DNS records**: Use [dnschecker.org](https://dnschecker.org)
3. **Verify CNAME file**: Must exist in repository root
4. **GitHub Pages setting**: Ensure custom domain is set in Settings → Pages

---

## 📚 Reference

### Lucide Icons
- Browse all icons: [https://lucide.dev/icons/](https://lucide.dev/icons/)
- Use the icon name in your app config (e.g., `beaker`, `atom`, `dna`)

### Color Codes
Some nice color combinations:
- Blue: `#0061ff`, `#0d6efd`, `#05cdfe`
- Green: `#06cdaf`, `#28a745`, `#20c997`
- Pink: `#e83e8c`, `#d63384`
- Purple: `#6f42c1`, `#6610f2`
- Orange: `#fd7e14`, `#ff6b6b`

### localStorage Keys
- `galleryApps`: All app configurations
- `galleryOrder_[gallery-id]`: App order for each gallery

---

## 🔄 Update Workflow

### Adding a New App to Your Collection

1. **Create/deploy your app** on GitHub Pages
2. **Note the URL**: `https://yourusername.github.io/new-app/`
3. **Open admin panel**: `https://your-domain.com/admin.html`
4. **Select gallery**: Choose Games, Chemistry, or Quiz
5. **Click "Add New App"**
6. **Fill in details**:
   - Title: Your app name
   - Description: Brief description
   - URL: Full URL to your app
   - Icon: Choose from Lucide icons
   - Color: Pick a color
7. **Click "Add App"**
8. **Done!** App appears in gallery instantly

### Removing an App

1. **Open admin panel**
2. **Find the app**
3. **Option 1 - Disable**: Toggle switch off (keeps app for later)
4. **Option 2 - Delete**: Click delete button (permanent removal)

### Monthly Maintenance

1. **Backup**: Export config JSON file
2. **Test**: Visit each gallery, ensure all apps work
3. **Update**: Disable any broken apps
4. **Clean up**: Delete apps you no longer use

---

## 🎓 Best Practices

### Security
- ✅ Use a strong admin password
- ✅ Export config backups regularly
- ✅ Don't share admin URL publicly
- ❌ Don't commit sensitive data to GitHub

### Organization
- ✅ Use clear, descriptive app titles
- ✅ Group similar apps in same gallery
- ✅ Use consistent icon styles per gallery
- ✅ Keep descriptions concise (1-2 sentences)

### Performance
- ✅ Optimize app URLs (use custom domains)
- ✅ Keep number of apps per gallery reasonable (8-12 max)
- ✅ Use appropriate image sizes in your apps
- ✅ Test on mobile devices

### Workflow
- ✅ Backup before major changes
- ✅ Test in one gallery before applying to all
- ✅ Keep a changelog of major updates
- ✅ Document custom modifications

---

## 📞 Quick Command Reference

### Export Config
```javascript
// In browser console (F12 → Console)
const data = localStorage.getItem('galleryApps');
console.log(data);
// Copy output and save
```

### Clear All Data
```javascript
// In browser console (F12 → Console)
localStorage.removeItem('galleryApps');
localStorage.clear();
// Reload page
```

### Check Current Config
```javascript
// In browser console (F12 → Console)
const apps = JSON.parse(localStorage.getItem('galleryApps') || '{}');
console.table(apps);
```

---

## 🎉 You're All Set!

Your gallery management system is now ready to use. Remember:

1. **Admin URL**: Bookmark it for easy access
2. **Backup regularly**: Export config monthly
3. **Test changes**: Always check galleries after updates
4. **Keep this guide**: Refer back when needed

Need help? Check the troubleshooting section or review the specific section for your issue.

Happy app managing! 🚀
