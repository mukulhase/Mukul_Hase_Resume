# Mukul_Hase_Resume

LaTeX source for my resume. The source syncs with Overleaf, and a GitHub Action
compiles `main.tex` on every push to `main` and publishes the resulting PDF to
the `gh-pages` branch, which GitHub Pages serves at a stable URL:

<https://mukulhase.com/Mukul_Hase_Resume/main.pdf>

That link is used in several places, including [mukulhase.com](https://mukulhase.com).
The built PDF is not committed — it is a build artifact and is gitignored.

## Building locally

Compile with LuaLaTeX, matching CI:

```sh
latexmk -lualatex main.tex
```

Without a local TeX install:

```sh
podman run --rm -v "$PWD:/data:Z" -w /data docker.io/texlive/texlive:latest \
  latexmk -lualatex -interaction=nonstopmode main.tex
```

The document should stay on one page. `\pdfgentounicode=1` keeps the output text
extractable so applicant tracking systems can parse it — worth re-checking if the
preamble changes.

## Template

Based on [sb2nov/resume](https://github.com/sb2nov/resume), MIT licensed; see
`LICENSE.txt` for the retained attribution.
