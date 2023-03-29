https://bookish-disco-5997zvo.pages.github.io/docs/en/intro/

## License

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

❯ vercel login
Vercel CLI 28.18.2
? Log in to Vercel saml
? Enter your Team slug: clickhouse
> Success! SAML Single Sign-On authentication complete for dan@roscigno.com
Congratulations! You are now logged in. In order to deploy something, run `vercel`.
💡  Connect your Git Repositories to deploy every branch push automatically (https://vercel.link/git).
❯ vercel link
Vercel CLI 28.18.2
? Set up “/work/Docs/doc-pr-preview-test”? [Y/n] y
? Which scope should contain your project? ClickHouse
? Link to existing project? [y/N] n
? What’s your project’s name? doc-pr-preview-test
? In which directory is your code located? ./
Local settings detected in vercel.json:
Auto-detected Project Settings (Docusaurus 2):
- Build Command: docusaurus build
- Development Command: docusaurus start --port $PORT
- Install Command: `yarn install`, `pnpm install`, or `npm install`
- Output Directory: build
? Want to modify these settings? [y/N] n
✅  Linked to clickhouse/doc-pr-preview-test (created .vercel and added it to .gitignore)


## GitHub repo secrets

### VERCEL_ORG_ID
Get this from the .vercel/project.json after running `vercel link`

### VERCEL_PROJECT_ID
Get this from the .vercel/project.json after running `vercel link`

### VERCEL_TOKEN NOTE: I renamed this to VERCEL_TOKEN_FOR_PREVIEWS and edited the workflow also
Create this secret in Vercel, and add it to GitHub secrets.

