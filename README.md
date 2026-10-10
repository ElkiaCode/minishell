# minishell

*A small Bash-like shell written in C, built as part of the 42 curriculum.*

minishell reads a command line, splits it into tokens, expands environment variables, then runs the commands: it handles pipes, redirections and heredocs, and has its own builtins.

## Features

- Interactive prompt with history (GNU Readline)
- Tokenizer and parser that handle single and double quotes
- Environment variable expansion (`$VAR`, `$?`)
- Pipes: `cmd1 | cmd2 | cmd3`
- Redirections: `<`, `>`, `>>` and heredoc `<<`
- Command lookup through `PATH`
- Signal handling (`Ctrl-C`, `Ctrl-D`, `Ctrl-\`) that behaves like Bash
- Builtins: `echo -n`, `cd`, `pwd`, `export`, `unset`, `env`, `exit`

## Build and run

Requires `cc`, `make` and the Readline headers (`libreadline-dev` on Debian/Ubuntu).

```bash
make
./minishell
```

```text
minishell$ echo "hello $USER" | tr a-z A-Z > out.txt
minishell$ cat << EOF | wc -l
> line one
> line two
> EOF
2
```

## Project layout

```text
srcs/
  main.c, tokenizer.c, parsing.c   input → tokens → command list
  exec/                            pipes, fork/exec, redirections, heredoc
  builtins/                        builtin commands
  signals/                         signal handlers
utils/                             string helpers, expander, PATH lookup
includes/minishell.h
```

## Authors

Team project by [ElkiaCode](https://github.com/ElkiaCode) and [LeoFalkins](https://github.com/LeoFalkins), 42 Nice.
