# VS Code Workspaces

> [!WARNING]
> I no longer use this repository.
> I still use a version of the `work` function, but all details now live in my [dotfiles](https://github.com/Rylan12/dotfiles).

This repository contains my VS Code workspaces that I want to make sure are backed up.

I use this repo along with the `work` shell function described below to easily open VS Code workspaces. For example, to open my [`homebrew` workspace](homebrew.code-workspace), I run:

```console
$ work homebrew
```

## Setup

Clone this repository into `~/Development` (or whatever directory is preferred; just make sure to update the function below):

```console
$ mkdir -p ~/Development

$ gh repo clone Rylan12/vscode-workspaces ~/Development/vscode-workspaces
```

Defined this shell function (changing `WORKSPACE_DIR` as needed):

```sh
work() {
    WORKSPACE_DIR=~/Development/vscode-workspaces/
    [[ $# -eq 0 ]] && cd $WORKSPACE_DIR && return

    WORKSPACE_FILE="$WORKSPACE_DIR/$1.code-workspace"
    [[ ! -f "$WORKSPACE_FILE" ]] && echo "$1 workspace not found!" && return 1

    open "$WORKSPACE_FILE"
}
```

## Open a Workspace

Run:

```console
$ work $WORKSPACE
```

## Save a New Workspace

When saving a VS Code workspace file, save it to `~/Development/vscode-workspaces` as `$NAME.code-workspace` where `$NAME` is the name you'd like to use when running the `work` shell function.
