# NBME / USMLE Exam Simulator

Upload an exam PDF and take it as a timed, NBME-style block. You get scoring, a review report and optional AI explanations.

It's a static site with no server and no build step, so it can be hosted free on GitHub Pages.

## Files (all in one folder, no subfolders)

| File | Purpose |
|---|---|
| `index.html` | Page layout |
| `style.css` | Styles (light + dark mode) |
| `app.js` | All logic: PDF parsing, exam, timer, scoring, AI |
| `sample_exam.pdf`, `sample_key.txt` | Used by the "Try the sample exam" button |
| `README.md` | This file |

## External dependencies (loaded from jsDelivr, pinned versions)

| Library | Version | Loaded |
|---|---|---|
| [pdf.js](https://github.com/mozilla/pdf.js) (`pdfjs-dist`, legacy build) | 6.3.289 | Always; it reads the PDFs |
| [Tesseract.js](https://github.com/naptha/tesseract.js) | 5.1.1 | Only if a PDF is a scan with no text |

To upgrade a library, change `PDFJS_VERSION` or `TESSERACT_URL` near the top of `app.js`. Users need internet access to `cdn.jsdelivr.net`.

## Put it online with GitHub Pages

1. **Create a repo.** On github.com, click **+** → **New repository**. Name it, e.g. `nbme-simulator`, choose **Public**, then click **Create repository**.
2. **Upload the files.** Click **uploading an existing file**. Drag in all 6 files and click **Commit changes**.
3. **Turn on Pages.** Go to **Settings** → **Pages** → **Deploy from a branch**. Choose branch `main` and folder `/ (root)`, then click **Save**.
4. **Wait 1–2 minutes.** Your site goes live at `https://YOUR-USERNAME.github.io/nbme-simulator/`.

To update the site, upload the changed file again. Pages redeploys in about a minute.

## Run it on your own computer

Double-clicking `index.html` won't work, because browsers block `app.js` on `file://` pages. Serve the folder instead:

```bash
python3 -m http.server 8000      # Windows: py -m http.server 8000
```

Then open http://localhost:8000.

## Notes

- **AI is optional and off by default.** With AI off, use an answer key or mark the correct answers yourself in the report.
- **With AI on**, the browser calls Anthropic or OpenAI directly using the user's own key. This site never receives keys or exam content.
- **AI-derived answers are labelled "AI"** and can be wrong.
- **Only upload material you have the right to use.**
