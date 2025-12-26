# pnpm security

- To prevent supply chain attacks on `npm` packages, we enforce that only `pnpm` can be used as a package manager.
- `pnpm` will not run lifecycle scripts (like `preinstall`) by default. This is commonly exploited by malware.
- `pnpm-workspace` rule: packages must be > 7 days old to be installed.
- This is not foolproof! But package exploits due to npm account hacks will generally be patched or rescinded by npm within that time period.

- You must have `.npmrc`, `pnpm-workspace`, and `package.json` with these specific keys in order to enforce the rules against usage of npm.

```json
{
"scripts": {
    //...
    "preinstall": "npx --yes only-allow pnpm",
    "preupdate": "npx --yes only-allow pnpm",
},
"engines": {
    "npm": "please-use-pnpm",
    "pnpm": ">=10.24.0"
},
"packageManager": "pnpm@10.24.0+sha512.01ff8ae71b4419903b65c60fb2dc9d34cf8bb6e06d03bde112ef38f7a34d6904c424ba66bea5cdcf12890230bf39f9580473140ed9c946fef328b6e5238a345a"
}
```