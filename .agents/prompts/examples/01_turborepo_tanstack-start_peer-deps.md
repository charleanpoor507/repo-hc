# Prompt: Turborepo + TanStack Start Peer-Dependencies

## Links
- README: `../README.md`
- Learning: `../learnings/01_turborepo_tanstack-start_peer-deps.md`

## Original Prompt
```text
Fix this please, turborepo, with tanstack start (router) apps:


<USER_REDACTED>@<HOST_REDACTED>:<PATH_REDACTED>$ pnpm install
Scope: all 4 workspace projects
 WARN  7 deprecated subdependencies found: @types/minimatch@6.0.0, glob@7.2.3, inflight@1.0.6, lodash.get@4.4.2, node-domexception@1.0.0, rimraf@3.0.2, whatwg-encoding@3.1.1
Packages: +100
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Downloading @rolldown/binding-linux-x64-musl@1.0.0-rc.9: 8.46 MB/8.46 MB, done
Downloading @rolldown/binding-linux-x64-gnu@1.0.0-rc.9: 8.51 MB/8.51 MB, done
Progress: resolved 856, reused 735, downloaded 14, added 20, done
 WARN  Issues with peer dependencies found
apps/backend
└─┬ nitro 3.0.260311-beta
  └─┬ unstorage 2.0.0-alpha.6
    ├── ✕ unmet peer chokidar@"^4 || ^5": found 3.6.0
    └── ✕ unmet peer lru-cache@^11.2.6: found 5.1.1

apps/frontend
└─┬ nitro 3.0.260311-beta
  └─┬ unstorage 2.0.0-alpha.6
    ├── ✕ unmet peer chokidar@"^4 || ^5": found 3.6.0
    └── ✕ unmet peer lru-cache@^11.2.6: found 5.1.1

Done in 11.6s
<USER_REDACTED>@<HOST_REDACTED>:<PATH_REDACTED>$
```
