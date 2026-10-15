# Document Utilities

A collection of standalone HTML applications for preparing printable forms, creating document copies with signatures, and working with PDF files. Each application provides its own interface and can be opened independently in a browser, with no application installation, build process, or backend service required.

## Applications at a glance

| Application | Purpose | Input | Output |
| --- | --- | --- | --- |
| [LIC NEFT Mandate Form](lic_neft_form_studio.html) | Print a structured bank mandate form for policy payment details. | Details entered by hand after printing. | Printed form or PDF through the browser print dialog. |
| [Printable Xerox Document & Signature Studio](printable_xerox_signature_studio.html) | Prepare an A4 document image with photocopy effects and an optional signature block. | A document image and a drawn or uploaded signature. | Printed A4 sheet, browser-generated PDF, or PNG image. |
| [LocalPDF Studio](localpdf_studio_client_side_pdf_toolkit.html) | Merge, split, compress, organize, convert, watermark, and sign PDFs. | PDF files or supported images, depending on the selected tool. | PDF, JPG, PNG, or ZIP downloads. |

## Getting started

1. Clone or download this repository.
2. Open the desired `.html` file in a modern browser with JavaScript enabled.
3. Follow the workflow described below for that application.

The LIC form is self-contained. The two studio applications load libraries, styles, icons, and fonts from external services, so an internet connection is needed to load those resources reliably.

If local-file browser restrictions interfere with loading resources, serve the repository over localhost. With Python 3 installed, run this command from the repository directory:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Then open [http://127.0.0.1:8000/](http://127.0.0.1:8000/) and select an application. Stop the server with `Ctrl+C` when finished.

## LIC NEFT Mandate Form

**File:** [lic_neft_form_studio.html](lic_neft_form_studio.html)

A print-focused HTML rendition of an LIC National Electronic Funds Transfer mandate form, headed for the Divisional Office Hyderabad. It provides a structured paper layout for recording policyholder and bank details associated with receiving policy payments through NEFT.

### Features

- A4 portrait layout with dedicated print styles and a **Print Form** button.
- Six policy-number rows, arranged in two columns with individual character boxes.
- Fields for the policyholder or claimant name, bank name, branch address, account type, account number, and IFS code.
- Mobile number, email address, and SMS/email preference sections.
- Aadhaar and PAN sections with self-attested photocopy notes.
- An enclosure checklist for a cancelled cheque or relevant bank passbook copy.
- Space for the policyholder's signature and date, followed by the form's explanatory notes.

### How to use

1. Open the HTML file and review the form layout.
2. Select **Print Form** to open the browser print dialog.
3. Choose A4 portrait paper, inspect the preview, and disable browser headers and footers if they appear.
4. Print a blank copy to complete by hand, or choose **Save as PDF** when that option is available in your browser.

### Scope

The form uses static text, lines, and boxes; it does not provide editable input fields, validation, saved records, or online submission. Its heading and wording are fixed in the HTML source. The layout reproduces a form with a January 2018 imprint and should not be treated as confirmation of current submission requirements.

## Printable Xerox Document & Signature Studio

**File:** [printable_xerox_signature_studio.html](printable_xerox_signature_studio.html)

An interactive workspace for turning a document or identity-card image into a photocopy-style A4 sheet. Image adjustments, physical sizing controls, and a signature panel let users prepare a document copy and review its arrangement before printing or downloading it.

### Features

- **Document import:** Upload or replace a document image using the file picker or drag-and-drop area. A built-in PAN-card-style example provides an initial preview.
- **Photocopy presets:** Choose Laser Xerox, High-Contrast B&W, Soft Grayscale Copy, or Dark Heavy Toner.
- **Image adjustments:** Tune background whitening, contrast, brightness, grayscale intensity, and toner grain. Optional controls trim dark outer edges and add a card border.
- **Signature creation:** Draw with a mouse or touch input, or upload a signature image with adjustable white-background removal. Drawing controls include ink colors, pen thickness, and a clear-pad action.
- **Signature presentation:** Show or hide the signature block, select an attestation header and caption, include an editable date, and adjust signature size and spacing. The signature block can also be dragged on the preview.
- **Physical page layout:** Choose document-width presets of 8.6 cm, 11.2 cm, or 14 cm, or adjust the width manually. Set the top margin, choose left/center/right alignment, and rotate the document in 90-degree steps.
- **Live preview:** Inspect the arrangement on an A4 portrait sheet with zoom controls.
- **Print and export:** Print the sheet with interface controls hidden, or download the composed page as a PNG image.

### How to use

1. Open the studio and select **Upload / Replace ID Image**, or drop an image into the document source area.
2. Choose a photocopy preset and refine the image controls until the text and photograph are clear.
3. Open the signature tab to draw or upload a signature, then set the caption, attestation text, and date as needed.
4. Open the layout tab to set the document's printed size, alignment, rotation, and top margin.
5. Review the A4 preview, then select **Print Document (A4)** or **Download A4 Image**.

### Output and printing details

The image download is named `Printable-Xerox-Document-A4.png` and uses a 1654 × 2339 pixel canvas, approximately 200 DPI at A4 size. The application accepts image files directly; convert PDF pages to images first if needed. For physical sizing, select A4 portrait and 100%/actual-size printing, and review the browser's margins and preview before printing. A PDF copy can be produced through the browser's **Save as PDF** option.

The initial document and signature are built-in examples. Replace them and review the caption and date before exporting a personal document.

## LocalPDF Studio

**File:** [localpdf_studio_client_side_pdf_toolkit.html](localpdf_studio_client_side_pdf_toolkit.html)

A browser-based PDF workspace with eight tools covering common document preparation tasks. Files are read and processed in the browser, with visual page previews, tool-specific settings, and downloadable results. The dashboard groups tools by organization, optimization, conversion, and editing tasks.

### Available tools

| Tool | Capabilities | Output |
| --- | --- | --- |
| **Merge PDF** | Combine multiple PDFs; reorder documents with arrow controls, sort by filename, and remove files from the queue. | One combined PDF. |
| **Split & Extract PDF** | Select pages visually, enter ranges such as `1-3, 5, 7-9`, or split every page. Selected pages can be combined into one PDF or exported separately. | Extracted PDF or a ZIP of separate page PDFs. |
| **Compress PDF** | Choose extreme, balanced, or high visual quality presets; adjust JPEG quality and rendering resolution; optionally convert pages to grayscale. A separate structure-stream mode rewrites the PDF while retaining vector text. | A rewritten PDF; size reduction depends on the source and settings. |
| **Organize & Rotate Pages** | Reorder, reverse, rotate, duplicate, or delete pages using a visual page manager. | A PDF containing the revised page sequence. |
| **JPG / PNG to PDF** | Combine JPEG, PNG, or WebP images into a PDF; choose A4, US Letter, or image-sized pages, orientation, and margins. | One PDF with an image on each page. |
| **PDF to JPG / PNG** | Render selected pages as JPG or PNG with configurable resolution and JPEG quality. | A single image for one page, or a ZIP for multiple pages, with individual image downloads also available. |
| **Watermark & Page Numbers** | Add text watermarks with color, size, opacity, rotation, and placement controls; add page numbers in several positions and formats. | A PDF with the selected stamps and numbering. |
| **Sign & Edit Metadata** | Draw a signature or use the built-in signature preset, choose a target page and placement, and edit document title, author, and subject. | A PDF with an embedded signature image and updated metadata. |

### Workspace features

- Drag-and-drop file loading and file-picker support.
- Page thumbnails and visual selection controls for applicable tools.
- Built-in sample files for exploring tools before loading personal documents.
- Light and dark interface themes.
- Processing progress feedback and a result screen with download and settings actions.
- PDF workflow chaining: send a generated PDF directly to compression, watermarking, organization, or PDF-to-image conversion.

### How to use

1. Select a tool from the dashboard.
2. Drop the required files into the workspace, use the file picker, or load a sample file.
3. Review the thumbnails and configure the tool's page selection, layout, or output settings.
4. Run the tool. The application initiates a download when processing completes and also provides a download button on the result screen.
5. Adjust the settings and run again if needed, or continue with a PDF result in one of the supported follow-on tools.

### Processing considerations

- Visual compression presets render each page to a JPEG image and rebuild the PDF. This flattens page content, so selectable text, vector detail, links, and interactive form behavior are not preserved by that compression path. The structure-stream mode retains vector text but does not guarantee a smaller file.
- Signatures are embedded images placed on a page. The signing tool does not create a certificate-based digital signature.
- Text watermarks and metadata controls do not provide redaction or removal of underlying document content.
- Large documents and high-resolution image exports require more browser memory and processing time. Smaller batches or lower rendering resolutions can help when resources are limited.

## Architecture and dependencies

All three applications keep their markup and styles in a single HTML file. The studio applications also contain their application JavaScript inline. There is no package manifest, build pipeline, backend API, or database in this repository.

| Application | Dependencies loaded by the HTML |
| --- | --- |
| LIC NEFT Mandate Form | Inline CSS and SVG, system fonts, and the browser print API; no external scripts or stylesheets. |
| Printable Xerox Document & Signature Studio | Tailwind CSS CDN, Font Awesome 6.5.1, Google Fonts, and browser Canvas/File APIs. |
| LocalPDF Studio | Tailwind CSS CDN, Font Awesome 6.5.1, Google Fonts, pdf-lib 1.17.1, PDF.js 3.11.174 and its worker, JSZip 3.10.1, and browser Canvas/File APIs. |

## Local processing and network access

The current source processes selected documents and images in browser memory and does not implement document uploads to a backend. Network requests are still made to load third-party resources for the two studio applications, including the PDF.js worker when needed. Local document processing therefore does not imply that the applications are fully self-contained or guaranteed to work offline.

The applications do not implement persistent project storage. Download the results you need before closing or refreshing the page. For a reliably offline deployment, the external dependencies would need to be bundled locally and their references updated.

## Repository layout

```text
docs_utils/
├── Readme.md
├── lic_neft_form_studio.html
├── printable_xerox_signature_studio.html
└── localpdf_studio_client_side_pdf_toolkit.html
```

To customize an application, edit its HTML file directly and reload it in the browser. After changes to page geometry or print styles, inspect both the on-screen layout and the browser print preview.
