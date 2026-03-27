# Newsletter

A regularly published newsletter covering **AI** and **Stock-Economic** topics, hosted on GitHub Pages.

**Live site:** https://pkyosx.github.io/newsletter/

## Writing a New Newsletter

1. Create a new file in `_posts/` with the naming format:
   ```
   YYYY-MM-DD-short-title.md
   ```
   Example: `2026-04-01-ai-trends-q2.md`

2. Copy the frontmatter template from `POST_TEMPLATE.md` or use:
   ```yaml
   ---
   layout: post
   title: "Your Newsletter Title"
   date: 2026-04-01
   categories: [AI]
   tags: [trends, quarterly]
   author: Author Name
   ---
   ```

3. Write your content in Markdown below the frontmatter.

4. Commit and push to `main`:
   ```bash
   git add _posts/2026-04-01-ai-trends-q2.md
   git commit -m "Add AI trends Q2 newsletter"
   git push origin main
   ```

5. GitHub Actions will automatically build and deploy the site within a few minutes.

## Categories

Use one or both of these categories in your frontmatter:

| Category | Description |
|----------|-------------|
| `AI` | Artificial intelligence, LLMs, ML developments |
| `Stock-Economic` | Market trends, economic analysis, investments |

## Local Development

```bash
bundle install
bundle exec jekyll serve
```

Then visit `http://localhost:4000/newsletter/`

## Project Structure

```
├── _config.yml          # Jekyll configuration
├── _posts/              # Newsletter posts (Markdown)
├── .github/workflows/   # CI/CD auto-deploy pipeline
├── index.md             # Homepage listing all newsletters
├── POST_TEMPLATE.md     # Template for new posts
├── Gemfile              # Ruby dependencies
└── README.md            # This file
```
