# Hugo for developers

## Create new Hugo website

tl;dr;

1. `docker run --rm -ti --name hugo -v $(pwd)/src:/app jojomi/hugo hugo new site /app/website`

Or:

1. `docker run --rm -ti --name hugo -v $(pwd)/src:/app jojomi/hugo sh --login`
1. `cd /app`
1. `hugo new site website`

This will create a new Hugo website with default settings and no theme.

Now copy yout theme of choice to `./themes` and make a copy an of an example website from your theme `./themes/_theme_name_/exampleSite`.

## Serving Hugo website locally

1. `docker run --rm -ti --name hugo -v $(pwd)/src:/app -p 3003:3003 jojomi/hugo hugo serve --source /app/website --port 3003 --bind 0.0.0.0`

## Building static version locally

1. Login to a running container: `docker exec -ti hugo sh --login`
1. Building for staging, includes drafts, expired and content for future publication: `hugo --minify --buildDrafts --buildFuture --buildExpired`
1. Building minified production version: `hugo --minify --verbose`

Built version will land in `./public`