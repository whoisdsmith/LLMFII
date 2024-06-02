# Windows-curses

## Description

Support for the standard curses module on Windows

## README

Adds support for the standard Python `curses` module on Windows. Based on
[these wheels](https://www.lfd.uci.edu/~gohlke/pythonlibs/#curses). Uses the
PDCurses curses implementation.

The wheels are built from [this GitHub
repository](https://github.com/zephyrproject-rtos/windows-curses).

PDCurses is compiled with wide character support, meaning `get_wch()` is
available. UTF-8 is forced as the encoding.

Starting from windows-curses 2.0, in the name of pragmatism, these wheels (but
not Gohlke's) include a hack to make resizing work for applications developed
against ncurses without Python code changes: Whenever `getch()`, `getkey()`, or
`get_wch()` return `KEY_RESIZE`, `resize_term(0, 0)` is called automatically.
This gives behavior similar to the automatic `SIGWINCH` handling in ncurses
(see PDCurses' `resize_term()` documentation). [This
commit](https://github.com/zephyrproject-rtos/windows-curses/commit/30ca08bfbcb7a332228ddcde026181b2009ea0a7)
implements the hack.

To add the same hack in Python code (which is harmless, and needed if you want
resizing to work with older windows-curses versions or with Gohlke's wheels),
call `curses.resize_term(0, 0)` after receiving `KEY_RESIZE`, and ignore any
`curses.error` exceptions. ncurses reliably fails and does nothing for
`resize_term(0, 0)`, so this is safe on *nix.

Please tell me if the `resize_term(0, 0)` hackery causes you any trouble.
