# Firefly Sitemap Generator

This project generates XML sitemaps for Firefly Social profiles using a shell script. The script fetches account handles from a remote API and creates per-provider sitemap files, as well as a main sitemap index.

## Features

- Fetches handles for multiple providers (Farcaster, Lens, Twitter)
- Generates chunked sitemap XML files for each provider
- Produces a main `index.xml` referencing all generated sitemaps
- Logs progress and errors to `build-sitemap.log`

## Prerequisites

- **jq** (for JSON parsing)
  - The script will attempt to auto-install `jq` if not found (supports Homebrew, apt, yum)
- **curl**
- Bash (tested on macOS and Linux)

## Usage

1. **Run the script:**
   ```sh
   ./build-sitemap.sh
   ```
   All logs will be written to `build-sitemap.log`.

## Output

- Generated sitemaps are saved in the `sitemap/` directory:
  - `farcaster-account-*.xml`, `lens-account-*.xml`, `twitter-account-*.xml`
  - `index.xml` (main sitemap index)
  - `static.xml` (static entries)

## Example Output Files

- `sitemap/index.xml`: Sitemap index referencing all generated sitemaps
- `sitemap/farcaster-account-1.xml`: Sitemap for Farcaster accounts (chunked)
- `sitemap/lens-account-1.xml`: Sitemap for Lens accounts (chunked)
- `sitemap/twitter-account-1.xml`: Sitemap for Twitter accounts (chunked)

## Customization

- To change the output directory, modify the `OUTPUT_DIR` variable in `build-sitemap.sh`.
- To adjust the number of links per sitemap file, change `MAX_LINKS_PER_FILE`.
- To add or remove providers, edit the `PROVIDERS` array.

## Troubleshooting

- If `jq` is not installed and cannot be auto-installed, install it manually from https://stedolan.github.io/jq/.

## License

MIT
