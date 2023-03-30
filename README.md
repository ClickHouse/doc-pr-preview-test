
## License

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

## Configuration

### Work to be done in Vercel
None, nada, zilch.  This is configured from the commandline.

### Work to be done from your GitHub repository

Check out your repo and then:

1. Authenticate to Vercel
```bash
vercel login
```

You may be using SAML, or you may be using a different authentication method.  I am using SAML
```bash
Vercel CLI 28.18.2
? Log in to Vercel saml
```

Look at your Vercel URL, mine ends in `/clickhouse`, so that is my slug.
```bash
? Enter your Team slug: clickhouse
> Success! SAML Single Sign-On authentication complete for dan@roscigno.com
Congratulations! You are now logged in. In order to deploy something, run `vercel`.
💡  Connect your Git Repositories to deploy every branch push automatically (https://vercel.link/git).
```

2. Link this repo to Vercel

Note: I am not linking from the Vercel web UI, I am linking from the repo to Vercel.  Vercel will not actually know anything about the workflow other than the fact that it is Docusaurus 2.
```bash
vercel link
```

Answer some questions, when asked if you want to link to an existing project say no and then it will offer to create a new one. I accepted all of the defaults, as I wanted Vercel to build a configuration for me that will work with Docusaurus 2.  If you look at your Vercel overview you will see that it populated the proper yarn commands for Docusaurus.  In the next section we will modify the workflow.
```bash
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
```

3. Add a preview.yml workflow.  Get this from github.com/vercel/examples/ci-cd/preview.yml

[preview.yml](https://github.com/vercel/examples/blob/main/ci-cd/github-actions/.github/workflows/preview.yaml)

4. Modify the workflow, since we need to grab the reference docs from the ClickHouse repo.  These are the lines I added:

[mods to grab Reference Docs](https://github.com/ClickHouse/doc-pr-preview-test/blob/main/.github/workflows/preview.yml#L20-L25)

[mods to get PR number to write report to](https://github.com/ClickHouse/doc-pr-preview-test/blob/main/.github/workflows/preview.yml#L11-L14)

[mods to write report with URL to the PR](https://github.com/ClickHouse/doc-pr-preview-test/blob/main/.github/workflows/preview.yml#L30-L40)

## GitHub repo secrets

### VERCEL_ORG_ID
Get this from the .vercel/project.json after running `vercel link`

### VERCEL_PROJECT_ID
Get this from the .vercel/project.json after running `vercel link`

### VERCEL_TOKEN
NOTE: I renamed this to VERCEL_TOKEN_FOR_PREVIEWS and edited the workflow also
Create this secret in Vercel, and add it to GitHub secrets. It is modified three times in the [workflow](https://github.com/ClickHouse/doc-pr-preview-test/blob/main/.github/workflows/preview.yml#L15)

