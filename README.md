# Deploy Next.js to Deno

This is a Next.js template which can be deployed to [Deno](https://deno.com).

## Deploying to Deno

To deploy to Deno Deploy, it is recommended to build the Next.js application with "standalone" output. Once the standalone application is built, you can deploy your application to Deno Deploy by connecting your GitHub repository or using the CLI:

1. Install `deployctl`:
```bash
deno install -gArf jsr:@deno/deployctl
```
2. Move the statics not copied into the standalone output directory:
```bash
cp -r public .next/standalone/public
# cp -r .next/static .next/standalone/.next/static
# Deno needs the explicit .cjs extension to interpret the file as CommonJS
mv .next/standalone/server.js .next/standalone/server.cjs
```
3. Deploy
```bash
deployctl deploy --include=.next/standalone .next/standalone/server.cjs
```

For more information, see our [deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying#self-hosting).

## Learn More

To learn more about Next.js and Deno Deploy, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.
- [Deno Deploy](https://docs.deno.com/deploy/manual/) - Deno Deploy documentation.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!
