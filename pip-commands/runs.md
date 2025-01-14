---
tags: ["#python", "#developer-tools", "#code-sample", "#programming-tutorial", "#example-code", "|", "#subprocess-enhancement", "#command-execution", "#python-utility"]
---

# Runs

## Description

🏃 Run a block of text as a subprocess 🏃

## README

🏃 runs: a better subprocess 🏃
---------------------------------------------------------------------

``runs`` has improved versions of ``call()``, ``check_call()``, ``check_output()``,
and ``run()`` from Python's ``subprocess`` module that handle multiple commands and
blocks of text, fix some defects, and add some features.

.. code-block:: python

    import runs

    runs('''
        ls
        df -k  # or perhaps -h?
        echo 'Done and done'
    ''')

---

``subprocess`` is essential but:

* You can only run one command at a time

* Commands to subprocess must be either a sequence of strings or a string,
  depending on whether ``shell=True`` or not

* Results are returned by default as bytes and not strings

---

The ``runs`` functions let you run a block of text as a sequence of subprocess
calls.

``runs`` provides call-compatible replacements for the functions
``subprocess.call()``, ``subprocess.check_call()``, ``subprocess.check_output()``,
and ``subprocess.run()``

Each replacement function takes a block of text, which is split into individual
command lines, or a list of commands, and returns a list of values, one for
each command. A block of text can contain line continuations, and comments,
which are ignored.

The replacement functions also add optional logging, error handling,
and lazy evaluation, and use UTF-8 encoding by default.

The module ``runs`` is callable - ``runs()`` is a synonym for ``runs.run()``.

EXAMPLES:

.. code-block:: python

    # ``runs()`` or ``runs.run()`` writes to stdout and stderr just as if you'd run
    # the commands from the terminal

    import runs

    runs('echo "hello, world!"')  # prints hello, world!

    # runs.check_output() returns a list, one string result for each command

    results = check_output('''
        echo  line   one  # Here's line one.
        echo   'line "  two  "'  # and two!
    ''')
    assert results == ['line one', 'line "  two  "']

    # Line continuations work too, either single or double
    runs('''
        ls -cail

        # One command that takes many lines.
        g++ -DDEBUG  -O0 -g -std=c++17 -pthread -I ./include -lm -lstdc++ \
          -Wall -Wextra -Wno-strict-aliasing -Wpedantic \\
          -MMD -MP -MF -c src/tests.cpp -o build/./src/tests.cpp.o

        echo DONE
     ''')

NOTES:

Exactly like ``subprocess``, ``runs`` differs from the shell in a few ways, so
you can't just paste your shell scripts in:

* Redirection doesn't work.

.. code-block:: python

    result = runs.check_output('echo foo > bar.txt')
    assert result == ['foo > bar.txt\n']

* Pipes don't work.

.. code-block:: python

    result = runs.check_output('echo foo | wc')
    assert result == ['foo | wc \n']

* Environment variables are not expanded in command lines

.. code-block:: python

    result = runs.check_output('echo $FOO', env={'FOO': 'bah!'})
    assert result == ['$FOO\n']

Environment variables are exported to the subprocess, absolutely,
but no environment variable expension happens on command lines.

API
===

``runs()``
~~~~~~~~~~

.. code-block:: python

  runs(
       commands,
       *args,
       iterate=False,
       encoding='utf8',
       on_exception=None,
       echo=False,
       **kwargs,
  )

(`runs.py, 186-200 <https://github.com/rec/runs/blob/master/runs.py#L186-L200>`_)

Call ``subprocess.run()`` on each command.
Return a list of ``subprocess.CompletedProcess`` instances.
See the help for ``subprocess.run()`` for more information.

Arguments:
  commands:
    A string, which gets split into lines on line endings, or a list of
    strings.

  args:
    Positional arguments to ``subprocess.run()`` (but prefer keyword
    arguments!)

  on_exception:
    If ``on_exception`` is ``False``, the default, exceptions from
    ``subprocess.run()`` are raised as usual.

    If ``on_exception`` is True, they are ignored.

    If ``on_exception`` is a callable, the line that caused the exception is
    passed to it.

    If ``on_exception`` is a string, the line causing the exception
    is printed, prefixed with that string.

  echo:
    If ``echo`` is ``False``, the default, then commands are silently executed.
    If ``echo`` is ``True``, commands are printed prefixed with ``$``
    If ``echo`` is a string, commands are printed prefixed with that string
    If ``echo`` is callable, then each command is passed to it.

  iterate:
    If ``iterate`` is ``False``, the default, then a list of results is
    returned.

    Otherwise an iterator of results which is returned, allowing for lazy
    evaluation.

  encoding:
    Like the argument to ``subprocess.run()``, except the default  is
    ``'utf8'``

  kwargs:
    Named arguments passed on to ``subprocess.run()``

``runs.call()``
~~~~~~~~~~~~~~~

.. code-block:: python

  runs.call(
       commands,
       *args,
       iterate=False,
       encoding='utf8',
       on_exception=None,
       echo=False,
       **kwargs,
  )

(`runs.py, 186-200 <https://github.com/rec/runs/blob/master/runs.py#L186-L200>`_)

Call ``subprocess.call()`` on each command.
Return a list of integer returncodes, one for each command executed.
See the help for ``subprocess.call()`` for more information.

Arguments:
  commands:
    A string, which gets split into lines on line endings, or a list of
    strings.

  args:
    Positional arguments to ``subprocess.call()`` (but prefer keyword
    arguments!)

  on_exception:
    If ``on_exception`` is ``False``, the default, exceptions from
    ``subprocess.call()`` are raised as usual.

    If ``on_exception`` is True, they are ignored.

    If ``on_exception`` is a callable, the line that caused the exception is
    passed to it.

    If ``on_exception`` is a string, the line causing the exception
    is printed, prefixed with that string.

  echo:
    If ``echo`` is ``False``, the default, then commands are silently executed.
    If ``echo`` is ``True``, commands are printed prefixed with ``$``
    If ``echo`` is a string, commands are printed prefixed with that string
    If ``echo`` is callable, then each command is passed to it.

  iterate:
    If ``iterate`` is ``False``, the default, then a list of results is
    returned.

    Otherwise an iterator of results which is returned, allowing for lazy
    evaluation.

  encoding:
    Like the argument to ``subprocess.call()``, except the default is
    ``'utf8'``

  kwargs:
    Named arguments passed on to ``subprocess.call()``

``runs.check_call()``
~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python

  runs.check_call(
       commands,
       *args,
       iterate=False,
       encoding='utf8',
       on_exception=None,
       echo=False,
       **kwargs,
  )

(`runs.py, 186-200 <https://github.com/rec/runs/blob/master/runs.py#L186-L200>`_)

Call ``subprocess.check_call()`` on each command.
If any command has a non-zero returncode, raise ``subprocess.CallProcessError``.

See the help for ``subprocess.check_call()`` for more information.

Arguments:
  commands:
    A string, which gets split into lines on line endings, or a list of
    strings.

  args:
    Positional arguments to ``subprocess.check_call()`` (but prefer keyword
    arguments!)

  on_exception:
    If ``on_exception`` is ``False``, the default, exceptions from
    ``subprocess.check_call()`` are raised as usual.

    If ``on_exception`` is True, they are ignored.

    If ``on_exception`` is a callable, the line that caused the exception is
    passed to it.

    If ``on_exception`` is a string, the line causing the exception
    is printed, prefixed with that string.

  echo:
    If ``echo`` is ``False``, the default, then commands are silently executed.
    If ``echo`` is ``True``, commands are printed prefixed with ``$``
    If ``echo`` is a string, commands are printed prefixed with that string
    If ``echo`` is callable, then each command is passed to it.

  iterate:
    If ``iterate`` is ``False``, the default, then a list of results is
    returned.

    Otherwise an iterator of results which is returned, allowing for lazy
    evaluation.

  encoding:
    Like the argument to ``subprocess.check_call()``, except the default  is
    ``'utf8'``

  kwargs:
    Named arguments passed on to ``subprocess.check_call()``

``runs.check_output()``
~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python

  runs.check_output(
       commands,
       *args,
       iterate=False,
       encoding='utf8',
       on_exception=None,
       echo=False,
       **kwargs,
  )

(`runs.py, 186-200 <https://github.com/rec/runs/blob/master/runs.py#L186-L200>`_)

Call ``subprocess.check_output()`` on each command.
If a command has a non-zero exit code, raise a ``subprocess.CallProcessError``.
Otherwise, return the results as a list of strings, one for each command.
See the help for ``subprocess.check_output()`` for more information.

Arguments:
  commands:
    A string, which gets split into lines on line endings, or a list of
    strings.

  args:
    Positional arguments to ``subprocess.check_output()`` (but prefer keyword
    arguments!)

  on_exception:
    If ``on_exception`` is ``False``, the default, exceptions from
    ``subprocess.check_output()`` are raised as usual.

    If ``on_exception`` is True, they are ignored.

    If ``on_exception`` is a callable, the line that caused the exception is
    passed to it.

    If ``on_exception`` is a string, the line causing the exception
    is printed, prefixed with that string.

  echo:
    If ``echo`` is ``False``, the default, then commands are silently executed.
    If ``echo`` is ``True``, commands are printed prefixed with ``$``
    If ``echo`` is a string, commands are printed prefixed with that string
    If ``echo`` is callable, then each command is passed to it.

  iterate:
    If ``iterate`` is ``False``, the default, then a list of results is
    returned.

    Otherwise an iterator of results which is returned, allowing for lazy
    evaluation.

  encoding:
    Like the argument to ``subprocess.check_output()``, except the default is
    ``'utf8'``

  kwargs:
    Named arguments passed on to ``subprocess.check_output()``

(automatically generated by `doks <https://github.com/rec/doks/>`_ on 2020-12-16T13:48:26.579866)
