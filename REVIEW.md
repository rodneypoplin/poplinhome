# REVIEW before first publish

All `[REVIEW — ...]` markers across the HTML files need a one-pass human check
before anything goes to a carrier reviewer.

## Placeholders to confirm

| File | Placeholder | Default used |
|---|---|---|
| `opt-in.html` | Full legal name | Rodney Poplin |
| `opt-in.html` | Cell phone (receiving) | +1 210 303 9300 |
| `opt-in.html` | Last updated | needs date at publish |
| `privacy.html` | Full legal name | Rodney Poplin |
| `privacy.html` | State of residence | Texas |
| `privacy.html` | Last updated | needs date at publish |
| `terms.html` | Full legal name | Rodney Poplin |
| `terms.html` | State of governing law | Texas |
| `terms.html` | Last updated | needs date at publish |
| `contact.html` | Full legal name | Rodney Poplin |
| `contact.html` | Best email | rodneypoplin@gmail.com |
| `contact.html` | Postal address | blank — add if needed |

## Quick search-and-replace

After confirming each value, this one-liner updates everything:

```bash
cd ~/poplinhome
# Confirm legal name
sed -i '' 's/Rodney Poplin \[REVIEW — confirm full legal name\]/Rodney Poplin/g' *.html
# Confirm state
sed -i '' 's/State of <strong>Texas<\/strong> \[REVIEW — confirm home state\]/State of <strong>Texas<\/strong>/g' *.html
sed -i '' 's/Texas<\/strong> \[REVIEW — confirm home state\]/Texas<\/strong>/g' *.html
# Confirm cell
sed -i '' 's/+1&nbsp;210&nbsp;303&nbsp;9300<\/strong> \[REVIEW — confirm cell\]/+1&nbsp;210&nbsp;303&nbsp;9300<\/strong>/g' *.html
# Confirm email
sed -i '' 's/rodneypoplin@gmail.com<\/a> \[REVIEW — confirm best email\]/rodneypoplin@gmail.com<\/a>/g' *.html
# Set today's date
TODAY=$(date '+%B %d, %Y')
sed -i '' "s/\[REVIEW — will be set at first publish\]/$TODAY/g" *.html
```

Then re-grep to make sure all markers are gone:

```bash
grep -l REVIEW *.html && echo "⚠️ still some REVIEW markers" || echo "✅ clean"
```

## After scrub

```bash
git add .
git commit -m "finalize placeholder values for publish"
git push
```

Cloudflare Pages auto-deploys on push.
