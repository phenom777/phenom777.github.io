# 🌐 Dr. Arka Ghosh — Personal Research Website

> A single-file, zero-dependency personal academic website with warm academic design.  
> Live at: `https://YOUR-USERNAME.github.io` after deployment.

---

## 📁 What's in this repository

```
index.html    ← The entire website (HTML + CSS + JS + data, all in one file)
README.md     ← This guide
```

That's it. One file runs the whole site.

---

## 🚀 Deploying on GitHub Pages (free hosting)

### Step 1 — Create a GitHub account
Sign up at **https://github.com/join** if you don't have one.  
Choose a professional username (e.g. `arkaghosh`) — it becomes part of your URL.

### Step 2 — Create a special repository
1. Click **+** (top right) → **New repository**
2. Name it exactly: `YOUR-USERNAME.github.io`  
   *(e.g. `arkaghosh.github.io`)*
3. Set visibility to **Public**
4. Click **Create repository**

### Step 3 — Upload files
1. In your new repo, click **Add file → Upload files**
2. Drag and drop **`index.html`** and **`README.md`**
3. Click **Commit changes**

### Step 4 — Enable GitHub Pages
1. Go to your repo → **Settings** tab
2. Left sidebar → **Pages**
3. Under *Build and deployment*, set:
   - Source: **Deploy from a branch**
   - Branch: **main** / folder: **/ (root)**
4. Click **Save**

### Step 5 — Your site is live 🎉
Wait ~2 minutes, then visit:
```
https://YOUR-USERNAME.github.io
```

---

## ✏️ How to update content

**Everything you edit lives inside `index.html`**, in the `const SITE_DATA = { ... }` block near the bottom of the file (around line 400+).

Open the file in any text editor (Notepad, VS Code, etc.) and find that section. The structure is self-explanatory — each section is a clearly labelled JavaScript object.

---

### ➕ Add a new journal publication

Find `journalPubs: [` and add a new entry at the **top** of the array (newest first):

```javascript
{
  id: "J11",
  authors: ["Arka Ghosh", "Co-Author Name"],
  title: "Your Paper Title Here",
  journal: "Journal Name",
  year: 2026,
  volume: "XX",
  pages: "XXX–XXX",
  doi: "10.xxxx/xxxxxx",
  jcrQuartile: "Q1",       // "Q1" or "Q2"
  jcrD1: true,             // remove this line if not D1
  impactFactor: 8.5,
  status: "published"
},
```

---

### ➕ Add a new conference paper

Find `conferencePubs: [` and add at the top:

```javascript
{
  id: "C12",
  authors: ["Arka Ghosh", "Co-Author"],
  title: "Paper Title Here",
  venue: "Conference Name (ACRONYM), Publisher",
  year: 2026,
  doi: "10.xxxx/xxxxxx",
  presentation: "Oral",    // or "Poster" — remove line if not applicable
  coreRank: "A",           // "A*", "A", "B" — remove if not CORE ranked
  status: "accepted"       // "published" | "accepted" | "in press"
},
```

---

### ➕ Add a preprint or under-review paper

Find `preprintPubs: [` and add:

```javascript
{
  id: "PP5",
  authors: ["Arka Ghosh", "Co-Author"],
  title: "Paper Title Here",
  journal: "Target Journal Name",
  status: "under-review"   // "under-review" | "minor-revision"
},
```

---

### ➕ Add a new research project

Find `projects: [` and add a new entry:

```javascript
{
  id: "projectid",
  acronym: "ACRONYM",
  fullName: "Full Project Name Here",
  funding: "Horizon Europe",
  budget: "€X.XM",
  period: "2026 – 2029",
  role: "Principal Investigator",
  abstract: "Description of the project and your contributions...",
  topics: ["Topic 1", "Topic 2", "Topic 3", "Topic 4"],
  color: "#7C3AED",           // accent colour — any hex code
  website: "https://project-website.eu/",   // or "#" if none
  linkedPublications: ["J7", "C6"]          // IDs from your pub arrays
},
```

---

### ➕ Add a new PhD student

Find `phdStudents: [` and add:

```javascript
{
  id: "student2",
  name: "Student Full Name",
  photo: "student2.jpg",       // upload photo to GitHub repo root; or "" for emoji placeholder
  thesisTopic: "Thesis Title Here",
  startYear: 2024,
  expectedCompletion: 2027,
  fundingAgency: "Funding Source / Project Name",
  institution: "DeustoTech, University of Deusto, Bilbao, Spain",
  abstract: "Brief description of the thesis research...",
  linkedPublications: ["J1", "C3"]
},
```

---

### 🔢 Update citation metrics

Find the `personal:` block at the top of `SITE_DATA` and update:

```javascript
hIndex: 15,           // update when it changes
totalCitations: 700,  // update periodically
```

---

### 📸 Add your headshot photo

1. Name your photo file `headshot.jpg` (recommended: 400×533px, under 300KB)
2. Upload it to your GitHub repository (same folder as `index.html`)
3. In `SITE_DATA`, find `personal:` and set:
   ```javascript
   headshot: "headshot.jpg",
   ```
4. Commit — the photo appears automatically

For student photos, same process: upload `studentname.jpg`, then set `photo: "studentname.jpg"` in the student entry.

---

## 🔄 Updating the live website

### Via GitHub browser (easiest, no tools needed)

1. Go to your repository on GitHub
2. Click on `index.html`
3. Click the **pencil icon ✏️** (Edit this file)
4. Make your changes in the editor
5. Scroll down → **Commit changes** → **Commit directly to main** → **Commit changes**
6. Site updates automatically in ~1 minute

### Via Git command line

```bash
# Make your edits to index.html locally, then:
git add index.html
git commit -m "Added publication J11 — IEEE Trans. ITS 2026"
git push
```

---

## 🎨 Customising the design

All visual styling is inside the `<style>` block at the top of `index.html`.

| What to change | Where to find it |
|---|---|
| Colour palette | `:root { ... }` CSS variables at the very top |
| Font choices | `@import` line + `--font-display`, `--font-body` variables |
| Section spacing | `--section-gap` variable |
| Nav height | `.nav-inner { height: 64px }` |
| Hero layout | `.hero-grid` CSS rule |

The colour variables you'll most likely want to personalise:

```css
--teal:   #0D9488;   /* primary accent — nav underlines, badges, buttons */
--navy:   #1E3A5F;   /* headings and name */
--amber:  #F59E0B;   /* year markers, stat numbers */
--cream:  #FEFBF6;   /* page background */
```

---

## 🗂 Section reference

| Section | Where in SITE_DATA |
|---|---|
| Hero (name, bio, metrics) | `personal` |
| Work Experience | `experience` |
| Education | `education` |
| Research Interests | `interests` |
| Skill bars | `skills` |
| Journal Reviewer list | `service.journals` |
| Conference TPC list | `service.conferences` |
| Publications | `journalPubs`, `conferencePubs`, `preprintPubs` |
| Projects | `projects` |
| PhD Students | `phdStudents` |
| Contact details | `personal` (email, phone, googleScholar, orcid) |

---

## 🌐 Custom domain (optional)

To use your own domain (e.g. `arkaghosh.com`):

1. Buy a domain from any registrar (Namecheap, Google Domains, Porkbun, etc.)
2. In your GitHub repo → **Settings → Pages → Custom domain**
3. Enter your domain (e.g. `arkaghosh.com`) and click Save
4. In your domain registrar's DNS settings, add these records:

```
Type    Name    Value
A       @       185.199.108.153
A       @       185.199.109.153
A       @       185.199.110.153
A       @       185.199.111.153
CNAME   www     YOUR-USERNAME.github.io
```

5. Wait up to 24 hours for DNS to propagate. GitHub adds HTTPS automatically.

---

## 📋 Launch checklist

- [ ] Update `googleScholar` URL in `personal` with your real Google Scholar link
- [ ] Upload `headshot.jpg` and update `headshot: "headshot.jpg"` in `personal`
- [ ] Verify h-index and citation count are current
- [ ] Check all DOI links are correct
- [ ] Test on mobile (resize browser or use phone)
- [ ] Confirm GitHub Pages is enabled and site loads at your URL

---

## 🛠 Technical notes

- **No build tools, no frameworks, no dependencies** — pure HTML5, CSS3, and vanilla JavaScript
- **Single file architecture** — everything embedded; works offline once loaded (except Google Fonts)
- **Google Fonts** (`Playfair Display`, `DM Sans`, `DM Mono`) load from CDN — renders with system fonts if offline
- **Scroll animations** use `IntersectionObserver` — gracefully skipped in older browsers
- **Fully responsive** — tested down to 320px viewport width
- **Accessible** — semantic HTML5, ARIA labels, keyboard navigation

---

*Built for Dr. Arka Ghosh · DeustoTech, University of Deusto, Bilbao, Spain*  
*ORCID: 0000-0002-9479-2250*
