# Nest-asyncio

## Description

Patch asyncio to allow nested event loops

## README

|Build| |Status| |PyPiVersion| |License| |Downloads|

Introduction
------------

By design asyncio `does not allow <https://github.com/python/cpython/issues/66435>`_
its event loop to be nested. This presents a practical problem:
When in an environment where the event loop is
already running it's impossible to run tasks and wait
for the result. Trying to do so will give the error
"``RuntimeError: This event loop is already running``".

The issue pops up in various environments, such as web servers,
GUI applications and in Jupyter notebooks.

This module patches asyncio to allow nested use of ``asyncio.run`` and
``loop.run_until_complete``.

Installation
------------

.. code-block::

    pip3 install nest_asyncio

Python 3.5 or higher is required.

Usage
-----

.. code-block:: python

    import nest_asyncio
    nest_asyncio.apply()

Optionally the specific loop that needs patching can be given
as argument to ``apply``, otherwise the current event loop is used.
An event loop can be patched whether it is already running
or not. Only event loops from asyncio can be patched;
Loops from other projects, such as uvloop or quamash,
generally can't be patched.


.. |Build| image:: https://github.com/erdewit/nest_asyncio/actions/workflows/test.yml/badge.svg?branche=master
   :alt: Build
   :target: https://github.com/erdewit/nest_asyncio/actions

.. |PyPiVersion| image:: https://img.shields.io/pypi/v/nest_asyncio.svg
   :alt: PyPi
   :target: https://pypi.python.org/pypi/nest_asyncio

.. |Status| image:: https://img.shields.io/badge/status-stable-green.svg
   :alt:

.. |License| image:: https://img.shields.io/badge/license-BSD-blue.svg
   :alt:

.. |Downloads| image:: https://static.pepy.tech/badge/nest-asyncio/month
   :alt: Number of downloads
   :target: https://pepy.tech/project/nest-asyncio