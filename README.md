# Bangor University thesis and dissertation template
[![Open in Overleaf](https://img.shields.io/badge/Open_in_Overleaf-44A141?style=for-the-badge&logo=overleaf&logoColor=white)](https://www.overleaf.com/docs?snip_uri=https://github.com/Mearman/bangor-thesis-template/archive/refs/heads/main.zip)
[![Use this template](https://img.shields.io/badge/Use_this_template-FDB913?style=for-the-badge&logo=github&logoColor=231F20&labelColor=231F20)](https://github.com/Mearman/bangor-thesis-template/generate)
[![Download ZIP](https://img.shields.io/badge/Download_ZIP-ED0000?style=for-the-badge&logo=github&logoColor=FDB913&labelColor=231F20)](https://github.com/Mearman/bangor-thesis-template/archive/refs/heads/main.zip)

A LaTeX template for theses and dissertations at Bangor University. It compiles on Overleaf with no install step: the package modules it needs sit in `vendor/`. This README uses controlled English. It is written in British English.

## Start on Overleaf

1. Press the *Open in Overleaf* badge above. Overleaf creates a project from this template and compiles it with pdfLaTeX at once. This path needs no GitHub account.
2. If you want your own git repository, press the *Use this template* badge or the green button instead, then import your copy into Overleaf from *New Project* and *Import from GitHub*.

If you use git on your own machine, clone your copy instead and run `latexmk -pdf main.tex`.

## Write your document

Set your facts in `main.tex`: title, author, degree scheme, school, college, supervisors, and date. School and college are free text: use the names your school publishes today. Write your chapters under `content/chapters/` and your sources in `references.bib`.

Pick your degree option on the `\documentclass` line. Research degrees such as `phd`, `mphil`, and `mres` set the title page to say *thesis*. Taught options such as `msc`, `bsc`, and `beng` set it to say *dissertation*. The options `thesis` and `dissertation` override the wording directly.

The citation style is `citations=ieee` by default. Any biblatex style name works. Ask your supervisor which style your school requires, and set it on the `\documentclass` line.

The class checks the university format rules and fails the build when one is broken: the font family and size, the margins, the 1.5 line spacing, and the 600-word cap on the abstract. Set `strict=false` to turn each failure into a warning. Check your school's handbook for rules this template does not cover, such as word counts for taught work.

State how you used generative AI tools. Replace the bracketed guidance through the `\aistatement` command in `main.tex`, and check your school's current policy.

## Keep the vendored modules current

The file `vendor/VERSION` shows which package release your copy carries. A scheduled workflow in `.github/workflows/vendor-update.yml` keeps it current: it pulls the latest package release into `vendor/`, compiles your document against it, and lands the update directly when the result is green and the change stays inside `vendor/`. GitHub disables scheduled workflows after 60 days of repository inactivity, so push or star your repository now and then. If you work only inside Overleaf, download the newest release of this template and copy the files in `vendor/` over your copies.

Never edit the files in `vendor/`. They are snapshots of the package repository, [Mearman/bangor](https://github.com/Mearman/bangor). A fix belongs there: open an issue or a pull request in that repository.

## Contribute

Make changes in the package repository, not in `vendor/` here. Commit messages follow the conventional commit format. Set up the hooks once per clone:

```sh
git config core.hooksPath .githooks
```

## Licence

The modules in `vendor/` are released under the LaTeX Project Public License, version 1.3c or later. See `vendor/LICENSE` in the package repository. Derived in part from the `bangorcsthesis` class by Cameron Gray, Bangor University.

## Roadmap

Done:

- Worked example thesis with declarations, AI statement, abstract, tables, and bibliography.
- Vendored package modules with automatic vendor updates.
- CI that compiles the template and checks the compile time against the Overleaf free-tier budget.

Next:

- Welsh interface strings, once the package provides them.

At the CTAN switchover:

- This template stops vendoring and resolves against the installed package. The update workflow migrates your copy for you.
- A `-vendored` duplicate of this template keeps carrying the vendored copies, for people who want to tweak the module sources directly. Both variants stay available.
