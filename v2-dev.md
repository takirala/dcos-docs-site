# V2 Content Dev

## To get started on `review` branch
1. `git fetch`
2. `git checkout review`
3. `git reset --hard origin/review` - don't try to merge, just reset to latest (very large fileset change)
4. Delete the `build-ngindox` and `build-swagger` folders
5. `make build-api` - builds them again with updated info
6. `npm run dev` - runs a full build, go to `localhost:3000`

Option 1 - work directly on review, making commits (this is fine)
Option 2 - check out a new branch from here and then merge it in 

## Metalsmith File Structure
- each folder MUST have an index.md, and each index.md must have a front matter at the top
- `navigationTitle` - shows in the sidebar
- `title` - shows in content cards and at top of content page
- `excerpt` - shows in content cards and at top of content page
- `menuWeight` - use positive integers to arbitrarily set the order, if a tie, sorts alphanumeric

## Build content locally
1. `npm run dev` is the way to get the full build if you want to check functionality or view at top level
2. `RPP=1.14/day-1/**` - RPP is a render path pattern, builds the subset and turns on webpack --watch to rebuild on file changes (still have to refresh the browser). The initial `pages` dir does not need to be listed, and note the `/**` to capture all the subfolders. Go to `localhost:3000/1.14/day-1/` to view.

## Build work on hosted site

1. `git push origin review` - this will be picked up by Jenkins and trigger a build, takes about 15 mins
2. Visit the updated site at https://docs-review.mesosphere.com
