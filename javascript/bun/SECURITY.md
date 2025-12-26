# pnpm security

- To prevent supply chain attacks on `npm` packages, we enforce that only `bun` can be used as a package manager.
- `bun` will not run lifecycle scripts (like `preinstall`) by default. This is commonly exploited by malware.
- `bunfig.toml` rule: packages must be > 3 days old to be installed.
- This is not foolproof! But package exploits due to npm account hacks will generally be patched or rescinded by npm within that time period.

- You must have `.npmrc`, `bunfig.toml`, and `package.json` with these specific keys in order to enforce the rules against usage of npm.

```json
{
"scripts": {
    //...
    "preinstall": "npx --yes only-allow pnpm",
    "preupdate": "npx --yes only-allow pnpm",
},
"engines": {
    "npm": "please-use-bun",
    "bun": ">=1.3.5"
}
// bun is not supported in corepack yet, so this is not added. 
// "packageManager": "bun"
}
```