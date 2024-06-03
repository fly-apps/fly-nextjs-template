![Next.js + Fly.io logos](public/nextjs-flyio2.png)

# Next.js Template for Fly.io
This is a [Next.js](https://nextjs.org/) template that's configured for easy deployment on Fly.io. It's bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app), and includes the following:

- Config for `standalone` builds (this keeps your Docker image as small as possible)
- Github Action workflow for auto-deploys when `main` branch is updated
- Github Action workflow for spinning up [review apps](https://fly.io/docs/blueprints/review-apps-guide/) each time a new PR is made

The template also includes the default options offered by [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app):

- TypeScript
- Tailwind
- App Router
- ESLint


## Getting Started Locally

To use this template, run the following command:

```bash
npx create-next-app@latest --example https://github.com/fly-apps/fly-nextjs-template <your-app-name>
```

To run the app locally, start the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Auto-deploy and review apps

To take advantage of the Github Actions included in this template, generate a Fly.io auth token using [flyctl](https://fly.io/docs/hands-on/install-flyctl/), and then set it as a repository secret on your repo. This is most easily done through the [GitHub CLI](https://github.com/cli/cli?tab=readme-ov-file#installation), but it's also possible to set secrets from the [web UI](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions?tool=webui#creating-secrets-for-a-repository).


```bash
# set the repository secret in GitHub
fly auth token | gh secret set FLY_API_TOKEN
```

## Deploy to Fly.io

First, launch your app to Fly.io by running the following command:

```bash
fly launch --name $YOUR_APP_NAME
```

Replace `$YOUR_APP_NAME` with whatever name you'd like. This command will generate a Dockerfile and a `fly.toml` for you. 

Lastly, you can make your first deploy in one of two ways:

1. Run `fly deploy`
2. If you've added your `FLY_API_TOKEN` as a repository secret in Github, you can `git push origin main`, and the auto-deploy Github action will deploy it for you.