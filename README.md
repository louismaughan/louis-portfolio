# Louis Maughan: football analytics portfolio

A personal portfolio built with [Quarto](https://quarto.org) and hosted free on GitHub Pages. It holds my projects, Power BI dashboards and blog.

## Structure

```
_quarto.yml            Site settings, navigation, theme
styles.scss            Colours and custom styles
index.qmd              Home page
about.qmd              About me and skills
contact.qmd            Contact details and CV link
projects/              One .qmd file per project (listed automatically)
blog/posts/            One folder per blog post (listed automatically)
.github/workflows/     Automatic publishing to GitHub Pages
requirements.txt       Python packages for your analysis
```

## One-time setup

1. **Install Quarto** from <https://quarto.org/docs/get-started/>.
2. **Install Python packages** (a virtual environment is recommended):
   ```bash
   python -m venv .venv
   source .venv/bin/activate        # Windows: .venv\Scripts\activate
   pip install -r requirements.txt
   ```
3. **Preview the site locally:**
   ```bash
   quarto preview
   ```
4. **Search and replace the placeholders.** Look for `YOUR-GITHUB-USERNAME`, `YOUR-REPO-NAME`, `YOUR-LINKEDIN-HANDLE` and `your.email@example.com`, mainly in `_quarto.yml` and `contact.qmd`. Text in *[square brackets and italics]* is a prompt for you to fill in.

## Deploy to GitHub Pages

1. Create a new repository on GitHub (for example `football-portfolio`) and push this folder to it on the `main` branch.
2. Do the first publish from your computer, which creates the `gh-pages` branch:
   ```bash
   quarto publish gh-pages
   ```
3. On GitHub, go to **Settings → Pages**, and set the source to **Deploy from a branch**, branch `gh-pages`, folder `/ (root)`.
4. Your site will be live at `https://YOUR-GITHUB-USERNAME.github.io/YOUR-REPO-NAME`.
5. After that, every push to `main` republishes the site automatically via `.github/workflows/publish.yml`.

**Important:** the workflow only runs Quarto, not Python. `freeze: auto` in `_quarto.yml` saves the results of your code when you render locally, so commit the `_freeze/` folder that Quarto creates alongside your changes. If you add a post with Python code, run `quarto render` locally first and commit the `_freeze/` folder.

To use your own domain later, add it under **Settings → Pages → Custom domain**.

## Adding a blog post

1. Create a new folder in `blog/posts/`, for example `blog/posts/my-first-xg-model/`.
2. Add an `index.qmd` (or a Jupyter notebook `index.ipynb`) with this at the top:
   ```yaml
   ---
   title: "Your post title"
   description: "One-sentence summary"
   date: "2026-11-20"
   categories: [xg, python]
   ---
   ```
3. Write your post, run `quarto preview` to check it, then commit and push.

## Adding a project

Copy `projects/recruitment-dashboard.qmd`, rename it, and replace the content. Each project should answer: the question, the data, the method, what you found, and what a club could do with it.

## Embedding Power BI dashboards

- **Publish to web** (if your Power BI account allows it): in the Power BI service, open your report, choose **File → Embed report → Publish to web (public)**, and paste the iframe into your project page using the `dashboard-embed` class from `styles.scss`. Anyone with the link can see this data, so only use open data.
- **If you can't publish to web:** add screenshots or a short screen recording, and link the `.pbix` file from your GitHub repo.

## Before you go live

- [ ] Replace every placeholder and delete template notes
- [ ] Add a `favicon.png` (or remove the `favicon` line in `_quarto.yml`)
- [ ] Add your CV as `assets/Louis-Maughan-CV.pdf` (or delete the CV section in `contact.qmd`)
- [ ] Replace the sample project with your first real one
- [ ] Check the site on your phone
