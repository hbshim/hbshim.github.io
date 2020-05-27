    :Author: Hyungbo Shim

.. contents::

1 Emacs
-------

1.1 Abbrevs mode
~~~~~~~~~~~~~~~~

- `https://www.emacswiki.org/emacs/AbbrevMode <https://www.emacswiki.org/emacs/AbbrevMode>`_

- ``abbrev-mode`` start the (minor) mode

- ``C-x a l`` (``add-mode-abbrev``) Define abbrev for current mode.

- ``C-x a i l`` (``inverse-add-mode-abbrev``) define a word in the buffer as a mode-specific abbrev

- ``list-abbrevs`` Display a list of defined abbrevs

- ``edit-abbrevs`` edit abbrevs. This is the best way to add or remove abbrevs. The number in the middle column is the number of times you've used (expanded) the abbrev. To remove a abbrev, just delete the line. To add a abbrev, just add a line. When done, to load and or save, call any of:

  - ``C-c C-c`` (``edit-abbrevs-redefine``) Redefine abbrevs according to current buffer contents.

  - ``C-x C-s`` (``abbrev-edit-save-buffer``) Redefine and save to abbrev file.

1.1.1 options
^^^^^^^^^^^^^

- ``abbrev-file-name`` The abbrevs is saved in a file at a path specified by this variable (default: ``\~/.emacs.d/abbrev_defs``)

- ``save-abbrevs``

1.2 ``(ansi-)term`` mode
~~~~~~~~~~~~~~~~~~~~~~~~

- ``C-c C-j`` (``term-line-mode``) switch to line mode (acts like an editor).

- ``C-c C-k`` (``term-char-mode``) switch to char mode (acts like a usual terminal).

- ``C-c C-c`` (``term-interrupt-subjob``) send a literal ``C-c`` to the sub-shell

- ``C-c <char>`` is equivalent to ``C-x <char>`` in normal Emacs modes, e.g. ``C-c o`` invokes the global binding of ``C-x o`` which is normally \`~other-window~'

- ``C-c C-q`` (``term-pager-toggle``) toggle the page-at-a-time feature. When enabled, the mode-line displays the word \`~page~' and each time Term receives more than a screenful of output, it pauses and displays \`~\*\*MORE\*\*~' in the mode-line where ``<SPC>`` displays the next screenful of output and ``?`` displays the other options -- the interface is similar to the ``more`` program.

1.3 Bookmarks
~~~~~~~~~~~~~

- ``C-x r m`` (``bookmark-set``) Set the bookmark for the visited file, at point

- ``C-x r l`` (``list-bookmarks``) list all bookmarks

- ``C-x r b`` (``bookmark-jump``) then type a bookmark name. You can type ``\*`` for wildcard

- ``bookmark-save`` save all the current bookmark values in the default bookmark file ``\~/.emacs.d/bookmarks``. Can be modified by setting the variable ``bookmark-default-file``

- when in the bookmark file:

  - ``d`` mark the current item for remove

  - ``x`` remove all marked ones

  - ``r`` rename current item's title

  - ``s`` save the change

1.4 helm
~~~~~~~~

- ``RET`` executes the default action upon exiting the Helm session

- ``C-j`` executes the default action but without exiting the Helm session

- ``TAB`` displays a list of actions available

- ``C-@`` mark/unmark a candidate

- ``M-U`` unmark all visible marked candidates at once

1.5 ``\*buffers*``
~~~~~~~~~~~~~~~~~~

- ``C-x C-b`` helm-buffers

- ``M-SPC`` or ``C-SPC`` mark

- ``C-x >`` and ``C-x <`` horizontal scroll

- ``C-x C-s``  save buffer without leaving Helm

- ``C-x s`` save all unsaved buffers

- ``C-c d`` delete buffer without leaving Helm

- ``M-D`` delete marked buffers and leave Helm

- ``C-x k`` is meant to kill buffers but cannot kill multiple buffers selected by ``C-SPC`` with ``RET``.

1.6 ``\*kill-buffer*``
~~~~~~~~~~~~~~~~~~~~~~

- This seems only useful when killing the currently opened buffer

- ``C-x k`` open kill-buffer

1.7 Case conversion A <-> a
~~~~~~~~~~~~~~~~~~~~~~~~~~~

- ``M-l/M-u`` (``downcase-word/upcase-word``) convert following word to lower/upper case.

- ``M-c`` (``capitalize-word``) capitalize the following word.

- ``C-x C-l/C-x C-u`` (``downcase-region/upcase-region``) convert region to lower/upper case

1.8 Deleting and killing
~~~~~~~~~~~~~~~~~~~~~~~~

1.8.1 Deleting by character
^^^^^^^^^^^^^^^^^^^^^^^^^^^

- ``<Del>~/~C-d`` Delete the character before/after point

- ``M-d~/~M-<Del>`` Kill forward/back to the end/beginning of the next/previous word

- ``C-k~/~M-k`` Kill to the end of the line/sentence

- ``C-o`` Insert a blank line after the cursor

- ``C-S-<DEL>`` (``kill-whole-line``) Kill a whole line

- ``C-u 50`` or ``M-5 0 <moving_command>`` repeat the moving command by 50 times. The tutorial says ``C-u`` is better \`because it works on any terminal'. \`50' is called a "prefix argument". Exception: ``C-u 8 C-v~/~C-u 8 M-v`` Instead of scrolling 8 pages up/down, it scrolls the current screen by 8 lines up/down.

- ``mouse-3`` (right click) set the mark at point then select up to and move point to where you click

- ``'shifted cursor motion keys'`` Set the mark at point if the mark is inactive, then move point.

- ``C-w`` Kill the selected region

- ``C-x <TAB>`` Indent the selected region

- ``M-$`` Check the spelling of words

- ``C-/``, ``C-_``, ``C-x u`` **undo**. On some text terminals, typing ``C-/`` actually sends ``C-_`` to Emacs.

- ``C-g`` changes the \`direction'. So, after undoing ``C-/`` n-times, doing ``C-g C-/`` and repeating ``C-/`` (n-1)-times will do **redo** all.

- the auto saved file's name for "``hello.c``" is "``#hello.c#``". To recover auto-saved editing, run ``M-x recover-this-file <RET>``

1.9 Dired
~~~~~~~~~

- ``C-x d`` invoke Dired, ``C-x 5 d`` (``dired-other-frame``)

- ``g`` re-read all directories (retains all marks)

1.9.1 directories
^^^^^^^^^^^^^^^^^

- ``+`` (``dired-create-directory``) create a directory

- ``C-M-n`` (``dired-next-subdir``) go to next subdirectory header line regardless of level

- ``C-M-p`` (``dired-prev-subdir``) go to previous subdirectory header line regardless of level

- ``C-M-u`` (``dired-tree-up``) go up to the parent directory's header line

- ``C-M-d`` (``dired-tree-down``)

- ``^`` (``dired-up-directory``) go to parent directory

- ``<`` (``dired-prev-dirline``) move up to the previous directory-file line

- ``>`` (``dired-next-dirline``) move down to the next directory-file line

- ``a`` (``dired-find-alternate-file``) visit file or directory on current line via

1.9.2 flags
^^^^^^^^^^^

- ``d`` (``dired-flag-file-deletion``) flag 'D' the file for deletion

- ``u`` (``dired-unmark``) remove the deletion flag

1.9.3 files
^^^^^^^^^^^

- ``x`` (``dired-do-flagged-delete``) delete files flagged for deletion

- to create a new file in the directory, just use ``C-x C-f`` as usual

- ``f``, ``e``, ``<ret>`` (``dired-find-file``) visit the file

- ``v`` (``dired-view-file``) view the file with view mode (visit without change)

- ``a`` (``dired-find-alternate-file``) visit file or directory on current line via \`find-alternate-file'

- ``C NEW <RET>`` (``dired-do-copy``) copy; ``NEW`` is the directory to copy into ir the new name

- ``D`` (``dired-do-delete``) delete the specified or marked files

- ``x`` (``dired-do-flagged-delete``) delete all flagged files

- ``S NEW <RET>`` (``dired-do-symlink``) make symbolic links; this is line 'ln -s'

- ``M MODESPEC <RET>`` (``dired-do-chmod``) change the mode

1.9.4 marks
^^^^^^^^^^^

- ``m`` mark with '\*'

- ``u`` (``dired-unmark``) remove any mark

- ``U`` (``dired-unmark-all-marks``) remove all marks from all files in the buffer

- ``M-}`` (``dired-next-marked-file``) move down to the next marked file

- ``M-{`` (``dired-prev-marked-file``) move up to the previous marked file

- ``C-_`` (``dired-undo``) undo changes in the Dired buffer

1.9.5 shell command
^^^^^^^^^^^^^^^^^^^

- ``M-x !`` ('``dired-do-shell-command``') reads a shell command string in the minibuffer, and runs that shell command on one or more files

1.10 File
~~~~~~~~~

- save: ``C-x C-s``

- save as: ``C-x C-w``

1.11 Find/replace
~~~~~~~~~~~~~~~~~

- incremental search: ``C-s`` (forward), ``C-r`` (backward)

- find all occurrence: ``M-s o`` (``occur``)

1.12 font
~~~~~~~~~

- M-x customize-face<RET>default<RET>

- ``C-x C-+`` (``(text-scale-adjust INC)``) / ``C-x C--`` (``(text-scale-adjust -INC)``) to increase/decrease the size.

- ``C-x C-0`` reset to the default font size

1.13 frames
~~~~~~~~~~~

- ``C-x 5 2`` (``make-frame-command``) create a new frame

- ``C-x 5 0`` (``delete-frame``) delete the selected frame

- ``C-x 5 1`` delete all frames except the selected one

- ``C-x 5 o`` cycle and select other frames

1.14 help and info
~~~~~~~~~~~~~~~~~~

- ``C-h i`` (``info``) run Info, the GNU documentation browser

- ``C-h b`` (``describe-bindings``) display all active key bindings

- ``C-h c KEY`` (``describe-key-briefly``) display the name of the command that ``KEY`` is bound to

- ``C-h k KEY`` (``describe-key``) display the name and documentation of the command that ``KEY`` runs

- to open separate buffer for ``info``, do ``M-2 M-x info``, ``M-3 M-x info``, etc.

- ``C-h`` help apropos

- ``C-h c <command>`` displays a very brief description of the command. Eg. ``C-h c C-p``.

- ``C-h k <command>`` displays the documentation of the function along with its name.

- ``C-h f <function_name>`` describe a function. Eg. ``C-h f previous-line<RET>``.

- ``C-h a <keyword>`` or ``M-x <keyword>`` (command apropos) list all the commands whose names contain that keyword. Eg. ``C-h a file<RET>`` displays a list of all ``M-x`` commands with "file" in their names with character-command.

1.14.1 Browsing inside info
^^^^^^^^^^^^^^^^^^^^^^^^^^^

- ``L`` (``Info-history``), ``l`` (``Info-history-back``), ``r`` (``Info-history-forward``)

- ``^`` (``Info-up``)

1.15 ispell (flyspell)
~~~~~~~~~~~~~~~~~~~~~~

- ``M-$`` Check and correct spelling of the word at point (ispell-word). If the region is active, do it for all words in the region instead.

  - ``i`` Insert this word in your private dictionary file so that it will be considered correct from now on, even in future sessions.

1.16 Menubar ``F10``
~~~~~~~~~~~~~~~~~~~~

1.17 Moving around
~~~~~~~~~~~~~~~~~~

1.17.1 by characters/lines
^^^^^^^^^^^^^^^^^^^^^^^^^^

- ``C-b~/~C-f`` move back/forward by one character

- ``C-p~/~C-n`` move up/down by one line

1.17.2 by words
^^^^^^^^^^^^^^^

- ``M-b~/~M-f`` move back/forward by one word

1.17.3 horizontally
^^^^^^^^^^^^^^^^^^^

- ``C-a~/~C-e`` move to the beginning/end of the line

- ``M-m`` (``back-to-indentation``) Jump to first non-whitespace character of the line

1.17.4 by sentence
^^^^^^^^^^^^^^^^^^

- ``M-a~/~M-e`` move to the beginning/end of the sentence

1.17.5 by paragraph
^^^^^^^^^^^^^^^^^^^

- ``M-{`` (``backward-paragraph``) Move back to previous paragraph beginning

- ``M-}`` (``forward-paragraph``) Move forward to next paragraph end.

1.17.6 by matching parentheses
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- ``C-M-f`` (``forward-sexp``)

- ``C-M-b`` (``backward-sexp``)

1.17.7 by buffer
^^^^^^^^^^^^^^^^

- ``M-<`` ``M->`` move to the beginning/end of the buffer

1.17.8 by page
^^^^^^^^^^^^^^

- ``C-v`` ``M-v`` page down/up by one page

- ``C-M-v`` scroll the other window

- ``C-l`` Clear screen and redisplay all the text, moving the text around the cursor to the center of the screen

1.17.9 back to previous position
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- ``C-<SPC>`` Set the mark at point

- ``C-x C-x`` Set the mark at point, activate, then move back to the original point

1.17.10 GO TO
^^^^^^^^^^^^^

- ``M-g g`` go to the line

1.18 Outline minor mode
~~~~~~~~~~~~~~~~~~~~~~~

- A *heading line* together with all following *body lines* is called an **entry**.

  - ``outline-hide-entry`` and ``outline-show-entry`` only applies to the body.

  - The **body** as in ``outline-hide-body`` refers to all body lines in the buffer.

  - **All** as in ``outline-show-all`` literally means all of the lines in the buffer.

- A heading line together with all of its deeper entries is called a **subtree**.

- Immediate (one level down) subheadings of the current heading is called **children**.

- All of deeper subheadings under the current heading are called **branches**.

- *Bodies* of the current heading and *bodies* of its subheadings are collectively called **leaves**.

- Everything except the top N levels of heading lines and their bodies are called **sublevels**

- Everything except the heading or body with heading lines leading up to the top level are called **other**

1.18.1 Motion commands
^^^^^^^^^^^^^^^^^^^^^^

- ``C-c @ C-n`` (``outline-next-visible-heading``)     move point to the next     visible heading line

- ``C-c @ C-p`` (``outline-previous-visible-heading``) move point to the previous visible heading line

- ``C-c @ C-f`` (``outline-forward-same-level``)  move point to the next     visible heading line of the same level

- ``C-c @ C-b`` (``outline-backward-same-level``) move point to the previous visible heading line of the same level

- ``C-c @ C-u`` (``outline-up-heading``) move point up to a lower-level visible heading line

1.18.2 Visibility commands
^^^^^^^^^^^^^^^^^^^^^^^^^^

- ``C-c @ C-a`` (``outline-show-all``) expand all (bufferwise)

- ``C-c @ C-q`` (``outline-hide-sublevels``) collapse all (bufferwise) sublevels

- ``C-c @ C-d`` (``outline-hide-subtree``) hide everything under the current heading except the heading itself

- ``C-c @ C-s`` (``outline-show-subtree``) show everything under the current heading (body, subheadings and their bodies)

- ``C-c @ C-l`` (``outline-hide-leaves``) hide the body of the current heading line and bodies of its subheadings

- ``C-c @ C-k`` (``outline-show-branches``) show all subheadings, at all levels, of the current line

1.19 Reference sites
~~~~~~~~~~~~~~~~~~~~

`http://pragmaticemacs.com/emacs/org-mode-basics-structuring-your-notes/ <http://pragmaticemacs.com/emacs/org-mode-basics-structuring-your-notes/>`_

1.20 Region/Mark
~~~~~~~~~~~~~~~~

- ``C-<SPC>`` (``set-mark-command``) Set the mark at point, and activate it.

- ``C-x C-x`` (``exchange-point-and-mark``) Set the mark at point, and activate it; then move point where the mark used to be.

1.21 Registers
~~~~~~~~~~~~~~

- ``M-x view-register RET r`` display a description of what register ``r`` contains

- Saving Positions

  - ``C-x r SPC r`` (``point-to-register``) record the position of point and the current buffer in register ``r``

  - ``C-x r j r`` (``jump-to-register``) jump to the position and buffer saved in register ``r``

- Saving text

  - ``C-x r s r`` (``copy-to-register``) copy region into register ``r``

  - ``C-x r i r`` (``insert-register``) insert text from register ``r``

  - ``M-x append-to-register RET r`` append region to text in register ``r``

  - ``C-x r +`` (``increment-register``) if the register ``r`` contains a text, append region to text in register ``r``. If the register contains a number, increase it by 1

  - ``M-x prepend-to-register RET r`` prepend region to text in register ``r``

- Saving numbers

  - ``C-u number C-x r n r`` (``number-to-register``) store ``number`` into register ``r``

  - ``C-u number C-x r + r`` if the register ``r`` contains a number, increse that number by ``number``

1.22 Select
~~~~~~~~~~~

- ``C-x h`` (``mark-whoe-buffer``) put point at beginning and mark at end of buffer (select all)

1.23 Sessions
~~~~~~~~~~~~~

- See info > (emacs)Top > Saving Emacs Sessions for detail

- if the variable ``desktop-save-mode`` is ``t``,

  - Emacs looks, when it started, for a saved desktop in the current directory or in the location specified by ``desktop-path`` if specified by command ``desktop-change-dir``

  - Emacs, by default, auto-saves the desktop whenever any of it changes. ``desktop-auto-save-timeout`` determines how frequently Emacs checks for modifications

- ``M-x desktop-save`` Manually save the desktop

- ``M-x desktop-clear`` empty the Emacs desktop by killing all buffers and clears the global variables listed in ``desktop-clear-preserve-buffers-regexp``

- if Emacs crashes, the lock stays on the dektop file and Emacs will ask next time whether use the locked desktop file or not. the variable ``desktop-load-locked-desktop`` valued ``nil`` will load the locked desktop file without asking

1.24 Symbol
~~~~~~~~~~~

- ``C-q C-<KEY>`` Enter ``^<KEY>`` symbol, eg. ``^A`` for ``CTRL-A`` key combination

1.25 Timestamp
~~~~~~~~~~~~~~

- ``C-u M-! date`` insert timestamp

1.26 windows
~~~~~~~~~~~~

- ``C-x o`` (``other-window``) Select another window.

- ``C-M-v`` (``scroll-other-window``) Scroll the next window.

- ``C-x 0`` (``delete-window``) Delete the selected window.

- ``C-x 1`` (``delete-other-windows``) Delete all windows in the selected frame except the selected window.

- ``C-x 4 0`` (``kill-buffer-and-window``) Delete the selected window and kill the buffer that was showing in it. The last character in this key sequence is a zero.

- ``C-x ^`` (``enlarge-window``) Make selected window taller.

- ``C-x }`` (``enlarge-window-horizontally``) Make selected window wider.

- ``C-x {``  (``shrink-window-horizontally``) Make selected window narrower.

- ``C-x -`` (``shrink-window-if-larger-than-buffer``) Shrink this window if its buffer doesn't need so many lines.

- ``C-x +`` (``balance-windows``) Make all windows the same height.

1.26.1 transpose windows
^^^^^^^^^^^^^^^^^^^^^^^^

- `https:ff//www.emacswiki.org/emacs/TransposeWindows <https:ff//www.emacswiki.org/emacs/TransposeWindows>`_

- top and bottom windows open and want to switch their positions: ``C-x 0 C-x 4 b``

- buttom window active and moving it to the top window: ``C-x 0 C-x 2 C-x b RET``

1.27 YASnippet
~~~~~~~~~~~~~~

- ``C-c C-n`` (``yas-new-snippet``) Creates a new buffer with a template for making a new snippet. The buffer is in snippet-mode (see below). When you are done editing the new snippet, use ``C-c C-c`` to save it.

1.27.1 variables
^^^^^^^^^^^^^^^^

- ``yas-global-mode`` Non-nil if Yas-Global mode is enabled

- ``yas-snippet-dirs`` list of top-level snippet directories

2 AucTeX
--------

.. table::

    +---------------------------------------+----------------------------------------------------------------------+
    | option                                | description                                                          |
    +=======================================+======================================================================+
    | ``preview-auto-reveal``               | Cause previews to open automatically when entered.                   |
    +---------------------------------------+----------------------------------------------------------------------+
    | ``helm-bibtex-library-path``          | A directory or list of directories in which PDFs are stored.         |
    +---------------------------------------+----------------------------------------------------------------------+
    | ``helm-candidate-number-limit``       | Global limit for number of candidates displayed.                     |
    +---------------------------------------+----------------------------------------------------------------------+
    | ``helm-ff-candidate-number-limit``    | The ‘helm-candidate-number-limit’ for ‘helm-find-files’ and friends. |
    +---------------------------------------+----------------------------------------------------------------------+
    | ``helm-occur-candidate-number-limit`` | Value of ‘helm-candidate-number-limit’ for helm-occur.               |
    +---------------------------------------+----------------------------------------------------------------------+
    | \                                     | \                                                                    |
    +---------------------------------------+----------------------------------------------------------------------+

3 emacsclient
-------------

.. code:: shell

    emacsclient -e '(with-current-buffer "Downloads" (dired-previous-line 3))'

4 Magit
-------

.. table::
