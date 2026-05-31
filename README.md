# Personal Portfolio Website

[![GitHub](https://img.shields.io/badge/repo-aparey%2Fportfolio-blue)](https://github.com/aparey/portfolio)

A simple, responsive personal portfolio you can host for free. No build tools, frameworks, or backend required—just HTML, CSS from [W3.CSS](https://www.w3schools.com/w3css/), and a few CDN links for fonts and icons.

**Repository:** [github.com/aparey/portfolio](https://github.com/aparey/portfolio)

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

### Use this as your own site (recommended)

1. **Fork the repository** on GitHub: open [aparey/portfolio](https://github.com/aparey/portfolio) and click **Fork**, or run:

   ```bash
   gh repo fork aparey/portfolio --clone
   cd portfolio
   ```

2. **Clone your fork** (if you did not use `gh repo fork --clone`):

   ```bash
   git clone https://github.com/YOUR_USERNAME/portfolio.git
   cd portfolio
   ```

3. **Add your assets** (see [Assets](#assets)) — profile photo and resume PDF in the project root.

4. **Customize content** — follow the [Customization guide](#customization-guide).

5. **Preview locally**

   - **Easiest:** double-click `index.html` to open it in your browser.
   - **Recommended:** use a local server so links behave like on a real site:

     ```bash
     python3 -m http.server 8000
     ```

     Then open [http://localhost:8000](http://localhost:8000).

6. **Commit and push** to your fork, then [deploy](#deploy-your-site).

### Clone the original repo directly

If you only want a local copy without forking yet:

```bash
git clone https://github.com/aparey/portfolio.git
cd portfolio
```

You can also download a ZIP from the repo’s **Code → Download ZIP** button.

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

| File | What to change | Example |
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

The live repo currently ships HTML only. Photo and resume are **not** committed yet—add yours locally, then push:

```bash
git add your-photo.jpg your-resume.pdf
git commit -m "Add profile photo and resume"
git push
```

Example filenames in the template (replace with yours):

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

### GitHub Pages (this repo)

1. Push your customized code to GitHub (your fork or `aparey/portfolio`).
2. In the repository, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Choose branch **`main`**, folder **`/ (root)`**, then **Save**.
5. After a minute or two, the site is live at:

   **`https://YOUR_USERNAME.github.io/portfolio/`**

   For example, after enabling Pages on a fork owned by `jane`:

   `https://jane.github.io/portfolio/`

   If the repository is renamed to `YOUR_USERNAME.github.io`, the site is served at `https://YOUR_USERNAME.github.io/` with no `/portfolio` path.

### Netlify / Vercel / Cloudflare Pages

1. Sign up and **Import** the GitHub repo [aparey/portfolio](https://github.com/aparey/portfolio) (or your fork).
2. Build command: leave empty. Publish directory: `/` (root).
3. Deploy.

### Other options

- University or employer web space
- Amazon S3 + CloudFront
- Any web host’s `public_html` folder

After deploying, open your live URL and click through Home, Projects, About, and Contact to confirm links and assets load.

## Updating your site after changes

```bash
cd portfolio
# edit index.html, projects.html, or add assets
git add .
git commit -m "Update portfolio content"
git push
```

GitHub Pages redeploys automatically when you push to the branch configured in Pages settings.

## Checklist before you go live

- [ ] Replaced all personal text (name, bio, skills, contact)
- [ ] Updated photo paths and files exist in the repo
- [ ] Resume PDF linked and downloads correctly
- [ ] Social links point to your profiles
- [ ] Projects page lists your real work with correct URLs
- [ ] Tested on phone or narrow browser window (mobile nav)
- [ ] Removed or replaced any content you do not want public
- [ ] Enabled GitHub Pages (or another host) and verified the live URL

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Broken images | Check filename and path match exactly (case-sensitive on many hosts) |
| Sidebar overlaps content on mobile | Normal below 600px width; mobile top bar should appear |
| Projects link goes nowhere | Use `./projects.html` from `index.html` and `index.html` from `projects.html` |
| Resume download 404 | Put the PDF in the repo root, commit, push, and match the `href` filename |
| Pages shows 404 | Confirm Pages uses branch `main` and root `/`; wait a few minutes after first enable |

## License

Use this template freely for your own portfolio. If you fork or share it, a credit or link back is appreciated but not required.

## Credits

Layout inspired by [W3.CSS Portfolio Template](https://www.w3schools.com/w3css/tryw3css_templates_dark_portfolio.htm). Built with W3.CSS, Google Fonts, and Font Awesome.

Maintained by [@aparey](https://github.com/aparey).
