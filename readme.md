# `shad`

Homework for the [SHAD program](https://shad.yandex.ru), written in [Typst](https://typst.app).

Every `*.typ` file under `src/` is a standalone document compiled to its own PDF.

## Development

[Nix](https://nixos.org/) is the only prerequisite.

### Common commands

```bash
nix develop --ignore-env             # Enter development shell.
nix build                            # Compile all documents into ./result/.
nix flake check                      # Same as `nix build`, via flake checks.
nix run .#format                     # Format the codebase (fix mode).
nix run .#lint                       # Lint the codebase (check mode, same as CI).
typst watch src/math/hw2.typ hw2.pdf # Live preview while editing (in dev shell).
```

The `format` and `lint` apps bundle typstyle, typos, yamllint, nixfmt, statix, prettier, markdownlint-cli2 and gitleaks;
see their definitions in `flake.nix`. All tools are also available individually inside the dev shell.

CI runs `nix run .#lint` plus `nix build`; see `.github/workflows/workflow.yml`.
