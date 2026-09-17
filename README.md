# fanlinke.github.io

Personal homepage of **Linke Fan**, built with the
[academic-homepage](https://github.com/luost26/academic-homepage) Jekyll template
(MIT licensed, see `LICENSE`) and deployed with GitHub Pages.

## What is in here

| Path | What it is |
| --- | --- |
| `index.html` | Home page: profile card, about, education / experience / awards, news, selected publications, selected projects |
| `publications.html` | Full publication list (grouped by year) |
| `projects.html` | Project list, rendered from `_data/projects.yml` |
| `experience.html` | Education, research, internships, social practice, campus activities, skills, honors |
| `_data/profile.yml` | Name, positions, email, links, bio, education, experience, awards |
| `_data/projects.yml` | All project entries (including the empty `repo` field) |
| `_data/navigation.yml` | Navbar items |
| `_data/display.yml` | Which home-page sections are shown, footer text |
| `_data/authors.yml` | Author formatting for publication lists (bold = you) |
| `_publications/2026/` | One Markdown file per paper |
| `_news/` | One Markdown file per news item |
| `assets/files/CV_Linke_Fan.pdf` | The CV linked from the home page |
| `assets/images/badges/tju.svg` | Placeholder university badge — replace it with the official logo if you like |

## Things that are intentionally left open

1. **Project repository links.** Every entry in `_data/projects.yml` has `repo: ""`.
   Put the GitHub URL there when a repository becomes public and the `[Code]` link
   appears automatically on both the home page and `/projects`.
2. **Portrait photo.** To show a photo on the home page, drop an image into
   `assets/images/photos/` and add a `portrait_url:` line to `_data/profile.yml`.
3. **Google Scholar / LinkedIn / ORCID.** There are commented-out lines in
   `_data/profile.yml`; uncomment and fill them in to add the icons.
4. **Chinese name.** If you want the Chinese name next to "Linke Fan" everywhere,
   fill in `secondary_name:` in `_data/profile.yml`.

## Preview locally

```bash
gem install --user-install bundler
bundle install
bundle exec jekyll serve
```

Then open <http://127.0.0.1:4000>.

If you prefer not to install Ruby, you can simply push to GitHub and let GitHub Pages
build the site for you (see below).

## Deploy to GitHub Pages

The repository has to be named `fanlinke.github.io` for the site to live at
<https://fanlinke.github.io>.

```bash
# from this directory
git remote add origin git@github.com:fanlinke/fanlinke.github.io.git
git push -u origin main
```

Then, on GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
branch `main`, folder `/ (root)`, and save. The site is published a minute or two later.

## Attribution

Template: [luost26/academic-homepage](https://github.com/luost26/academic-homepage) (MIT).
The link in the page footer is kept as the template author asks.

## Troubleshooting

### `git push` hangs or `dial tcp ... i/o timeout` to github.com

On this machine `github.com` resolves to `20.205.243.166`, which is unreachable from the
local network, while other GitHub edge IPs (e.g. `140.82.112.3`) answer fine. If pushes
start failing with a timeout, run the small CONNECT proxy in the workspace
(`work/ghproxy.py`) and point git at it:

```bash
python3 /Users/fanlinke/Documents/Codex/2026-09-17/h-t-t/work/ghproxy.py &
HTTPS_PROXY=http://127.0.0.1:9999 git -C /Users/fanlinke/Documents/Codex/2026-09-17/h-t-t/outputs/fanlinke.github.io push
```

The same env var makes `gh` work (`HTTPS_PROXY=http://127.0.0.1:9999 gh auth status`).
This is a workaround for the network, not something the site needs.
