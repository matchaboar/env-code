# Python App

## Prerequisites

- If on linux, you must install prerequsite packages to the OS
that are needed to build python (google command for OS).
- Install mise.

```sh
# Installs uv to manage python packages.
# This is based on .mise.toml dependencies.
mise install
uv add sortedcontainers
```

## Running

`uv run ./package_name/main.py`

## Leetcode imports

- Standard library appears to be intact.
- Sortedcontainers is allowed, so you may install it local.

```py
from sortedcontainers import SortedList
from sortedcontainers import SortedDict
from sortedcontainers import SortedSet

ss = SortedSet('abracadabra')
# SortedSet(['a', 'b', 'c', 'd', 'r'])
ss.bisect_left('c')
# 2
```