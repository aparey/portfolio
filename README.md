# Personal Portfolio Website

A simple, responsive personal portfolio you can host for free. No build tools, frameworks, or backend required—just HTML, CSS from [W3.CSS](https://www.w3schools.com/w3css/), and a few CDN links for fonts and icons.

## What you get

- **Home page** (`index.html`) — hero, about, skills, resume download, contact, social links
- **Projects page** (`projects.html`) — project cards with descriptions and links
- **Responsive layout** — sidebar navigation on desktop, top bar on mobile
- **Dark theme** — easy to tweak with W3.CSS color classes

## Requirements

- A text editor (VS Code, Cursor, Sublime, etc.)
- A modern web browser
- Optional: [Git](https://git-scm.com/) for version control and deployment

You do **not** need Node.js, Python, or any package manager.

## Quick start

1. **Get the files**

   ```bash
   git clone https://github.com/YOUR_USERNAME/portfolio.git
   cd portfolio
   ```

   Or download the repository as a ZIP and unzip it.

2. **Add your assets** (see [Assets](#assets))

   Place these in the project root (same folder as `index.html`):

   | File | Purpose |
   |------|---------|
   | Your profile photo | Sidebar avatar and hero image |
   | Your resume (PDF) | Download button on the home page |

3. **Customize content** — follow [Customization guide](#customization-guide) below.

4. **Preview locally**

   - **Easiest:** double-click `index.html` to open it in your browser.
   - **Recommended:** use a local server so links behave like on a real site:

     ```bash
     # Python 3
     python3 -m http.server 8000
     ```

     Then open [http://localhost:8000](http://localhost:8000).

5. **Publish** — see [Deploy your site](#deploy-your-site).

## Project structure

```
portfolio/
├── index.html      # Home, About, Contact
├── projects.html   # Project showcase
├── README.md
├── your-photo.jpg  # You add this (any name you use in HTML)
└── your-resume.pdf # You add this (any name you use in HTML)
```

External resources (loaded from the internet, no install):

- W3.CSS — layout and styling
- Google Fonts — Montserrat
- Font Awesome 4 — sidebar and footer icons

## Customization guide

Edit the HTML files in any text editor. Search for the example text and replace it with your own.

### 1. Page titles

| File | Line to change | Example |
|------|----------------|---------|
| `index.html` | `<title>` in `<head>` | `Your Name Portfolio` |
| `projects.html` | `<title>` in `<head>` | `Your Name — Projects` |

### 2. Profile photo

Update **both** files wherever you see the image `src`:

- Sidebar: `<img src="./YOUR_PHOTO.jpg" ...>` in `<nav class="w3-sidebar">`
- Home hero: `<img src="./YOUR_PHOTO.jpg" ...>` in the `#home` header

Use the same filename in both places, or use two different images if you prefer.

### 3. Home page (`index.html`)

| Section | What to edit |
|---------|----------------|
| **Hero** | Name in `<h1>`, tagline in `<p>` under the hero |
| **About** | Heading (`<h2>`), bio paragraph in `#about` |
| **Skills** | Items inside the `<ul>` under "My Skills" |
| **Resume** | `href` on the download link and the PDF filename |
| **Contact** | Location, phone, email in `#contact`; update `mailto:` on the send button |
| **Footer** | Social URLs (`href` on each `<a>`) and optional tagline |

### 4. Navigation links

Keep sidebar and mobile nav in sync on both pages:

- **On `index.html`:** Home → `#` or `#home`, About → `#about`, Projects → `./projects.html`, Contact → `#contact`
- **On `projects.html`:** Home → `index.html`, About → `index.html#about`, Projects → `#projects`, Contact → `index.html#contact`

### 5. Projects page (`projects.html`)

Each project is a block like this:

```html
<div class="w3-card-4 w3-margin w3-white">
  <div class="w3-container">
    <h3><b>Project Title</b></h3>
    <h5>Category or tech stack</h5>
  </div>
  <div class="w3-container">
    <p>Short description of what you built and why it matters.</p>
    <a href="https://github.com/you/repo" class="w3-button w3-black w3-margin-bottom">View Details</a>
  </div>
</div>
```

- **Add a project:** copy one full `w3-card-4` block and paste it above the comment `<!-- Add more projects as needed -->`.
- **Remove a project:** delete the entire `w3-card-4` block for that project.
- **Change the intro:** edit the `<h1>` and `<p>` in the `#projects` header.

### 6. Styling (optional)

Shared styles live in the `<style>` block at the top of each file:

- **Font:** change the Google Fonts link and the `font-family` in `<style>`.
- **Theme color:** `body` uses `class="w3-black"`. Try `w3-dark-grey`, `w3-grey`, or see [W3.CSS colors](https://www.w3schools.com/w3css/w3css_colors.asp).
- **Sidebar width:** adjust `.w3-sidebar { width: 120px; }` and `#main { margin-left: 120px; }` together.

## Assets

The template expects files in the **project root**. If you rename them, update every `src` and `href` in `index.html` and `projects.html`.

Example filenames from the original site (replace with yours):

- Photo: `CFD440A6-4F2E-4DFC-9C10-56B171C89BD2_1_201_a.jpeg`
- Resume: `Aditya_Parey_Resume_2025_DS1351.pdf`

**Tips:**

- Use a square or nearly square photo for the circular sidebar avatar.
- Keep the hero image reasonable size (e.g. under 500 KB) for faster loading.
- Use a clear PDF filename without spaces if possible (e.g. `Jane_Doe_Resume.pdf`).

## Contact form note

The form posts to `/action_page.php`, which is a W3Schools placeholder and **will not work** on static hosting. The site already uses a **mailto** link on the send button, which opens the visitor’s email client. For a real form backend, use a service such as [Formspree](https://formspree.io/), [Netlify Forms](https://docs.netlify.com/forms/setup/), or your own server.

## Deploy your site

Any host that serves static files works.

### GitHub Pages

1. Push this folder to a GitHub repository.
2. Go to **Settings → Pages**.
3. Source: **Deploy from branch**, branch `main` (or `master`), folder `/ (root)`.
4. Your site will be at `https://YOUR_USERNAME.github.io/REPO_NAME/`.

If the repo is named `YOUR_USERNAME.github.io`, the site is at `https://YOUR_USERNAME.github.io/`.

### Netlify / Vercel / Cloudflare Pages

1. Sign up and connect your GitHub repo (or drag-and-drop the folder on Netlify).
2. Build command: leave empty. Publish directory: `/` (root).
3. Deploy.

### Other options

- University or employer web space
- Amazon S3 + CloudFront
- Any web host’s `public_html` folder

After deploying, open your live URL and click through Home, Projects, About, and Contact to confirm links and assets load.

## Checklist before you go live

- [ ] Replaced all personal text (name, bio, skills, contact)
- [ ] Updated photo paths and files exist in the repo
- [ ] Resume PDF linked and downloads correctly
- [ ] Social links point to your profiles
- [ ] Projects page lists your real work with correct URLs
- [ ] Tested on phone or narrow browser window (mobile nav)
- [ ] Removed or replaced any content you do not want public

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Broken images | Check filename and path match exactly (case-sensitive on many hosts) |
| Sidebar overlaps content on mobile | Normal below 600px width; mobile top bar should appear |
| Projects link goes nowhere | Use `./projects.html` from `index.html` and `index.html` from `projects.html` |
| Resume download 404 | Put the PDF in the repo root and match the `href` filename |

## License

Use this template freely for your own portfolio. If you fork or share it, a credit or link back is appreciated but not required.

## Credits

Layout inspired by [W3.CSS Portfolio Template](https://www.w3schools.com/w3css/tryw3css_templates_dark_portfolio.htm). Built with W3.CSS, Google Fonts, and Font Awesome.
