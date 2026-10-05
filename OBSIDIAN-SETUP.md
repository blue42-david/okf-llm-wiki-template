# Obsidian setup

> **For humans.** Not part of the wiki and not instructions for an AI agent.
> An agent may use it only to walk a person through Obsidian setup when asked.

The vault is the repo root. Settings come from the repo (`.obsidian/`); the plugin itself, window layout and your login stay on each device. Sync runs only through git, with manual commits. `main` is the source of truth. `<owner>/<repo>` below is this wiki's GitHub repo.

## Desktop

1. Clone `<owner>/<repo>` (e.g. GitHub Desktop: *File → Clone repository*).
2. Obsidian: *Open folder as vault* → the cloned folder.
3. *Settings → Community plugins → Turn on → Browse* → **Git** (by Vinzent) → *Install* → *Enable*.
4. Run **Git: Pull**. On an auth error, run `git pull` once in a terminal in the repo to log in.

## Mobile (iOS and Android)

Follows the plugin's official mobile clone steps ([Getting Started](https://publish.obsidian.md/git-doc/Getting+Started)).

1. **Token**: github.com → *Settings → Credentials → Fine-grained personal access tokens*. Only this repo; *Contents* and *Commit statuses*: **Read and write** (*Metadata* read is added automatically). Copy it.
2. **New empty vault** named after the repo. iOS: **on the device, not iCloud**. Android: **app storage** (other apps can't read it). Don't customize it yet: the clone replaces its settings.
3. **Plugin**: install **Git** as on desktop → *Enable* → *Options*.
4. **Login** (stays on the phone): *Identity* → your GitHub username and the token.
5. **Clone**: command palette → **Git: Clone an existing remote repo** → `https://github.com/<owner>/<repo>.git` → *Vault Root* → `.obsidian` in remote: **YES** → confirm *Delete all your local config and plugins* (that's why the vault must be new) → depth **1**.
6. **Wait** until a popup asks you to *Restart Obsidian*. Don't leave the app before that. Then restart.
7. **Finish**: the clone removed the Git plugin's code, so reinstall **Git** (*Community plugins → Browse*) → *Enable*. Its settings come from the repo. In its *Options*, check *Identity* and set *Commit author* name and email. Use your GitHub noreply address from [github.com/settings/emails](https://github.com/settings/emails).
8. **Customize** the phone only now. The mobile toolbar is a per-vault setting stored in `.obsidian/app.json`, and vaults in app storage or on iOS can't be reached by a file manager, so set it by hand once. Then commit `app.json` so the next phone gets it; desktop ignores it.

## Daily workflow

1. Pull first (automatic on startup; else **Git: Pull**).
2. Edit.
3. **Source Control** view: stage files, write a message, *Commit*, *Push*. Avoid *Commit-and-sync*: it commits everything with a generic message.

## Reviewing a PR branch

**Git: Fetch** → **Git: Switch to remote branch** → `origin/<branch>`. The status-bar picker only lists local branches. Switch back to `main` before editing.

## Troubleshooting

| Problem | Fix |
|---|---|
| Red "Uninitialized" sync icon | Obsidian Sync, not git. *Core plugins → Sync* off. |
| Push rejected | Someone pushed first. Pull, then push. |
| Conflict on the phone | Copy your text out, *Git: Discard all changes*, pull, paste, commit. |
| Phone clone/pull hangs or crashes | Reclone with depth 1. Keep big binaries out of `raw/`. |
| Auth fails | Token expired. Make a new one, paste it in the plugin. |
| Desktop pull: "untracked files would be overwritten" in `.obsidian/` | Move those files out, pull again. |
| Empty folders left on the phone after a pull | The phone's git (isomorphic-git) deletes removed files but not their folders. Delete the empty folders in Obsidian's file explorer. Git doesn't track folders, so there's nothing to commit. |

## Sources

Labels match the app as of 2026-10-04 (plugin docs may lag behind). If something doesn't match, the plugin's docs are the reference:

- Obsidian Git docs: [Getting Started](https://publish.obsidian.md/git-doc/Getting+Started), [Authentication](https://publish.obsidian.md/git-doc/Authentication)
- Plugin repo, changelog and mobile limitations: [Vinzent03/obsidian-git](https://github.com/Vinzent03/obsidian-git)
- Empty folders: isomorphic-git's checkout only drops deleted folders from the index ([`rmdir-index`](https://github.com/isomorphic-git/isomorphic-git/blob/v1.42.4/src/commands/checkout.js)); v1.42.4 is the version the plugin uses ([package.json](https://github.com/Vinzent03/obsidian-git/blob/master/package.json)).
