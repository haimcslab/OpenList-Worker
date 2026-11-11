# Instructions for agents working in OpenList-Worker

haimcslab's fork of OpenListTeam/OpenList-Worker (TypeScript, Hono + SolidJS), deployed as the Cloudflare Worker "openlist-worker" at openlist.haimcslab.com. Cloudflare Workers Builds deploys every merge to main, so a merged PR goes live.

## How work happens
- Work arrives as a GitHub issue. Do only what the issue asks.
- Make changes on a branch and open a pull request. Never push to main.
- The PR description says what changed, why, how you tested it, and anything a person must do by hand.
- Extend existing folders instead of creating parallel ones.
- Keep each PR small. If the issue needs a decision you cannot make from the repo, ask in the issue instead of guessing.

## Secrets
- Never print, echo, cat or commit secrets, tokens, keys, .env or config.json files. Refer to secrets by name only.
- List the secret names a person must set in the PR description.

## .github/workflows/
**Never create, edit or delete files here.** The builder's token cannot push workflow changes, so the push fails and the work is lost. Put proposed workflow YAML in the PR description and a person adds it.

## Rules for this fork
- Keep our local config in wrangler.jsonc: worker name "openlist-worker", D1 binding DB (database openlist, id d905961f-18d5-4cd0-9245-1b8c1fb65b91), DB_DRIVER=d1, DB_FORMAT=sql. When merging upstream, keep ours on these lines.
- Keep our English-only README.md when merging upstream.
- Prefer upstream behavior. Put fork-only changes in as few files as possible so upstream merges stay easy.
- This repo is public. Never commit anything lab-internal (IPs, hostnames, tokens).
- Build check before a PR: `pnpm install && pnpm run build` if the change touches src/ or api/.
