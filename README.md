# Deploy Next.js to Deno

This is a Next.js template which can be deployed to [Deno](https://deno.com).

## Deploying to Deno

To deploy to Deno Deploy, it is recommended to build the Next.js application
with "standalone" output. Once the standalone application is built, you can
deploy your application to Deno Deploy by linking your GitHub repository or
using the CLI.

### Link GitHub repository

The most convenient way to deploy your Next.js application to Deno Deploy is to
link your GitHub repository to Deno Deploy. This way, your application will be
automatically deployed on every commit you push to your repository. To link your
GitHub repository, follow these steps:

1. Fork this template (you need write permissions to the repository to link it
   to Deno Deploy).
2. Go to https://dash.deno.com/new_project
3. If it's the first time you're using Deno Deploy, you will be asked to sign up
   with your GitHub account.
4. Search for the repository in the dropdown menu. Deno Deploy will
   automatically detect that you are using Next.js and prepare the necessary
   build configuration.
5. Click "Deploy project". Deno Deploy will commit to the repository and run for
   the first time a deploy.yml action that will build and deploy the application
   on every push to the main branch. After that, you can customize the action
   freely by editing the `.github/workflows/deploy.yml` file in your repository.

### `deployctl` CLI

1. Install `deployctl`:

```bash
deno install -gArf jsr:@deno/deployctl
```

2. Copy the statics into the standalone output directory:

```bash
cp -r public .next/standalone/public
cp -r .next/static .next/standalone/.next/static
# Deno needs the explicit .cjs extension to interpret the file as CommonJS
mv .next/standalone/server.js .next/standalone/server.cjs
```

3. Deploy

```bash
deployctl deploy --include=.next/standalone .next/standalone/server.cjs
```

For more information, see our
[deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying#self-hosting).

## Learn More

To learn more about Next.js and Deno Deploy, take a look at the following
resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js
  features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.
- [Deno Deploy](https://docs.deno.com/deploy/manual/) - Deno Deploy
  documentation.

You can check out
[the Next.js GitHub repository](https://github.com/vercel/next.js) - your
feedback and contributions are welcome!
