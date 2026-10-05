# Initialize LLM-Wiki in OKF

Read the LLM Wiki idea file at https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f and SPEC.md in this directory. Create the structure with files and directories based on the LLM Wiki idea file while following SPEC.md. Do not create or fill any other content.

If the repository this wiki lives in is private, save a copy of the LLM Wiki idea file as `llm-wiki.md` in the repository root, with its source URL at the top, so the wiki keeps it even if the gist changes. If the repository is or may become public, do not copy it, because the gist has no license; link it instead.

Write every markdown file without hard line wrapping: one line per paragraph, list item and footnote, because Obsidian's Live Preview shows line breaks exactly as written.

Link with relative markdown links, not `/`-absolute paths or `[[wikilinks]]`: Obsidian resolves `/` against the vault root, which is the repository, not the wiki folder. Link a folder through its `index.md`, because Obsidian can't open a link to a folder.

Organize the wiki by topic, not by page type: topic folders such as `wiki/security/` are created as sources arrive, each page's type goes in its `type` frontmatter, and cross-cutting facets go in `tags`.

Sources (do not check):
- https://github.com/GoogleCloudPlatform/open-knowledge-format/tree/main

## Obsidian setup (for humans, not part of the task above)

[OBSIDIAN-SETUP.md](OBSIDIAN-SETUP.md) explains how a person opens this wiki in Obsidian on desktop and mobile. It is not an instruction for the agent: do not act on it, change it or delete it while initializing. Use it only to walk the user through Obsidian setup when they ask.

## License (for humans, not part of the task above)

This template is MIT-licensed ([LICENSE](LICENSE)), except [SPEC.md](SPEC.md): it is the Open Knowledge Format specification from [GoogleCloudPlatform/open-knowledge-format](https://github.com/GoogleCloudPlatform/open-knowledge-format), licensed under the Apache License 2.0 ([LICENSES/Apache-2.0.txt](LICENSES/Apache-2.0.txt)) and included unmodified. The LLM Wiki idea by Andrej Karpathy is linked, not included, because it has no license.
