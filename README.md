# Markdown → Google Doc (Colab)

A Colab notebook that converts a specific markdown meeting note into a well-formatted Google Doc using the Google Docs API.

## Features
- Converts H1 / H2 / H3 headings to Heading 1 / 2 / 3 in Google Docs.
- Converts markdown checkboxes (`- [ ]`) into actual Google Docs checkboxes.
- Preserves bullet hierarchy.
- Highlights assignee mentions like `@john_doe` with bold + color.
- Formats footer lines (Meeting recorded by, Duration) with distinct style.
- Handles basic horizontal-rule conversion.

## Setup / Pre-reqs
1. A Google account.
3. In Colab you'll sign-in with your Google account (OAuth) when prompted.

## Dependencies
- `google-api-python-client`
- `google-auth`
- `google-auth-oauthlib`
  
## How to run (in Colab)
1. Open Google Colab: https://colab.research.google.com/.
2. Create a new notebook and copy the notebook cells from the repository (or upload the `.ipynb` file).
3. Run the cells in order:
   - Install dependencies (first cell).
   - Authenticate: the notebook uses `google.colab.auth.authenticate_user()` and `google.auth.default(...)` (you will be prompted to allow access).
   - A new Google Doc will be created in your Drive and the notebook prints the document link.
4. If you don't want the created doc to be publicly shareable, remove/comment the permission creation step in the notebook.

## Notes & Limitations
- The parser is lightweight and tailored for the provided meeting-notes format.
- The code builds the doc by inserting a single marked text blob, then uses the Docs API `batchUpdate` requests to style ranges found by markers.

## Error handling
- The notebook prints helpful errors from the Google APIs.
- If you get `403` or `REQUEST_DENIED`, confirm the Docs API and Drive API are enabled for the Google Cloud project and that you signed in with the account you enabled them for.
