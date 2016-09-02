***********
Cargo Watch
***********

Simple shell script to watch a Rust project on Unix like systems.
*(Only tested on Linux so far)*.


Why?
====

Unlike the existing utility on cargo, this script is very small and easy to extend,
it has the ability to run many commands, clears the terminal each time and alerts on failure.

Since the script is small, its not a big undertaking to maintain.


Details
=======

- Monitors ``src/`` recursively.
- Can run from the projects root or any subdirectory.
- All proceeding arguments are forwarded to cargo.
- If no arguments are provided, then cargo will run ``build`` and ``test``.
- For more advanced usage,
  multiple commands can be passed using a quoted argument newlines,
  *(blank lines are ignored)*.
- Resets the terminal on each execution,
  to keep messages isolated and reduce scrolling.
- Errors raise an alert in the terminal on failure.


Examples
========

Build when a file changes.

.. code-block:: bash

   cargo-watch build

Run tests and print their output.

.. code-block:: bash

   cargo-watch test -- --nocapture


Run multiple commands, using quoted newlines:

.. code-block:: bash

   cargo-watch "
   clean
   build
   test
   run
   "



Dependencies
============

- ``inotifywait`` from ``inotify-tools`` package.
- ``tput`` from from ``ncurses`` package
  *(included by default on most systems)*.

