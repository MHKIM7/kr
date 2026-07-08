# GIScience & Spatial Bigdata Lab — Website

Source code for the website of the **GIScience & Spatial Bigdata Lab**,
Department of Geography, Kyungpook National University.

🌐 **Live site**: <https://knu-giscience.github.io/>

Built with [Jekyll](https://jekyllrb.com/) using a customized version of the
[al-folio](https://github.com/alshedivat/al-folio) theme.
Hosted on GitHub Pages, automatically rebuilt by GitHub Actions on every
push to `main`.

---

## For students: editing the site

You **don't need to clone this repo or use Git**. Use Pages CMS:

1. Go to <https://app.pagescms.org/>
2. Sign in with your GitHub account
3. Pick `knu-giscience/knu-giscience.github.io`
4. Edit Members, Projects, Publications via web forms

📘 Detailed Korean guide: [STUDENT_GUIDE.md](./STUDENT_GUIDE.md)

If you don't yet have edit access, send your GitHub username to Prof. Lee.

---

## Repository structure

```
_pages/        Top-level pages (about, members, projects, publications, contact)
_projects/     Research project pages
_bibliography/papers.bib   Publications in BibTeX
_data/members.yml          Lab member profiles
_data/socials.yml          ORCID/Scholar/email shown on homepage
_data/venues.yml           Optional badges for journals on the publications page
assets/img/    Images: profile photo, member photos (members/), projects (projects/)
.pages.yml     Pages CMS configuration (defines the editing forms)
.github/workflows/deploy.yml   Build & deploy pipeline
```

---

## Local development (advanced)

If you want to preview changes locally before pushing:

```bash
# Requires Ruby 3.x and Bundler
cd ~/Projects/knugis-homepage
bundle install
bundle exec jekyll serve --livereload
# open http://127.0.0.1:4000
```

---

## License

Theme code is under MIT (see al-folio upstream).
Content (text, photos, publication metadata) is © GIScience & Spatial
Bigdata Lab, Kyungpook National University.
