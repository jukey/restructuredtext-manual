.. highlight:: rst

============================
reStructuredText with Sphinx
============================

This manual is heavily influenced and based on https://github.com/kiith-sa/RestructuredText-tutorial

---------------------------
Setting up Sphinx on Ubuntu
---------------------------

* Python is installed (Unless you're using a brutally lightweight distro. Probably not ideal for documentation production).
* Install Sphinx by typing the following commands to the terminal::
  
     sudo apt-get install python-pip
     sudo pip install sphinx


--------------------------
Creating the documentation
--------------------------

* Now, still in the terminal, create a directory for your documentation and move there.

  Win7/Linux::

     mkdir mydoc
     cd mydoc

* And finally generate a basic documentation template::

     sphinx-quickstart

* Quickstart will ask you some questions.
  The only questions that should interest you for now are:

  - *Project name:*
  - *Author name:*  
  - *Project version*

  You can skip the others by pressing Enter.
  This will set up default settings.

  You can change any of these options later (you will be changing at least the version as your project develops).
  
* This created a documentation source directory. 
  Important files in this directory:

  ===============  =======================================================================
  Directory        Contents
  ===============  =======================================================================
  ``conf.py``      Documentation configuration file.
  ``index.rst``    Documentation master file.
  ``Makefile``     Make file to generate documentation on Linux/Unix.
  ``make.bat``     Batch file to generate documentation on Windows.
  ===============  =======================================================================

* The master document, ``index.rst``, serves as a table of contents and
  welcome page for the documentation. 

  It contains a heading, table of contents, and a section called
  *Indices and Tables* with references for module index, search and so on.

  You probably won't need the *Indices and Tables* section for now, so I
  recommend to remove it. (This section is added with Python documentation
  in mind - getting module index and search to work for non-Python documentation
  would need some googling.)


  reStructuredText depends on indentation. For example,
  below, each entry in the table of contents has the same indentation.
  This is always **3 spaces**, no tabs. Less or more might work, or it might not.

  By default, the table of contents should look like this::

     Contents:

     .. toctree::
       :maxdepth: 2

  You can add documents to the table of contents like this::
     
     Contents:

     .. toctree::
       :maxdepth: 2

       tutorial

  ``tutorial`` refers to a document called ``tutorial.rst`` in the documentation directory.

  Example table of contents from a real project::

     Tutorials:
     
     .. toctree::
        :maxdepth: 2
     
        tutorials/getting_started
        tutorials/custom_types 
        tutorials/yaml_syntax 
     
     Articles:
     
     .. toctree::
        :maxdepth: 2
     
        articles/spec_differences

  Here we see documents in subdirectories of the documentation directory.


* Now create some content.

  Create a new reStructuredText file, for example ``example.rst``, in the documentation directory.
  Add it to table of contents (add ``example`` to ``toctree`` in ``index.rst``.)

  Open the file in any text editor (MS Word is not a text editor).
  When saving the file, **make sure** to use the UTF-8 encoding. 

  Use `source code of this tutorial <https://raw.github.com/kiith-sa/reStructuredText-tutorial/master/README.rst>`_ 
  as a reference.

  Use ``Ctrl-C`` and ``Ctrl-V`` . Do random stuff to try what does what.


  For example you can do `this <https://github.com/jukey/RestructuredText-tutorial/blob/master/Syntax.rst>`_


* Now generate the documentation.

  Linux::

     make html

  This will generate the documentation in HTML format. To find out what other formats 
  are available, use make with no arguments:

  Linux::

     make 

  Among others, there should be HTML, LaTeX, Windows HTML Help (chm), man, and so on.

  The generated documentation will be found in the ``_build`` directory, each format
  in its own subdirectory (e.g. ``_build/html`` for HTML).

---------------------
Example documentation
---------------------

* `Python documentation <http://docs.python.org/>`_
* `Zope documentation <http://docs.zope.org/zope2/index.html>`_
* `D:YAML documentation <http://dyaml.alwaysdata.net/static/html/doc_0.4/index.html>`_

-----
Links
-----

* `Sphinx <http://sphinx.pocoo.org>`_
* `Sphinx tutorial <http://sphinx.pocoo.org/tutorial.html>`_
* `reStructuredText Primer <http://sphinx.pocoo.org/rest.html#rst-primer>`_
* `Quick reStructuredText reference <http://docutils.sourceforge.net/docs/user/rst/quickref.html>`_ 
* `Sphinx documentation <http://sphinx.pocoo.org/contents.html>`_
* `rst2pdf (generates PDF from reStructuredText) <http://code.google.com/p/rst2pdf/>`_

