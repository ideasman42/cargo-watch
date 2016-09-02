***********
Cargo Watch
***********

Simple shell script to watch a Rust project on Unix like systems.
*(Only tested on Linux so far)*.

- Monitors ``src/`` recursively.
- All proceeding arguments are forwarded to cargo.
- Can run from the projects root or any subdirectory.
- Resets the terminal on each execution,
  to keep messages isolated and reduce scrolling.
- For more advanced usage,
  multiple commands can be passed using a quoted argument newlines,
  *(blank lines are ignored)*.


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
   clear
   build
   test
   run
   "


Dependencies
============

- ``inotifywait`` from ``inotify-tools`` package.
- ``tput`` from from ``ncurses`` package
  *(included by default on most systems)*.

