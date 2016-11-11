  * An image: ``.. image:: image.png``

  * Bullet lists::

       * this is
       * a list
       
         * with a nested list
         * and some subitems
       
       * and here the parent list continues

  * Numbered lists::
       
       1. This is a numbered list.
       2. It has two items too.
     
  * Can be automatically numbered::

       #. This is a numbered list.
       #. It has two items too.

  * Tables::
     
       ====== ============ =======
       No.    Availability Name
       ====== ============ =======
       1      N/A          Biros
       2      42           piskoty
       3      N/A          beton
       ====== ============ =======

  * Comments::
     
       .. my awesome comment

  * Citations (the citation itself must be at the end of file)::

       Here is a citation reference: [CIT2002]_.

       .. [CIT2002] This is the citation.

  For more stuff, see the `reStructuredText Primer <http://sphinx.pocoo.org/rest.html>`_ .

-------------------------------------------------------------
Some extra features interesting for programming documentation
-------------------------------------------------------------

Code blocks
~~~~~~~~~~~

  * A code block (note the empty line and **3 spaces** of indentation)::

       A code block::
         
          print "Hello World!"


^^^^^^^^^^^^^^^^^^^^^^^^
Source code highlighting
^^^^^^^^^^^^^^^^^^^^^^^^

The ``code-block`` directive can be used to highlight source code.
Just about any language is supported. E.g. ``c`` for C, ``cpp`` for C++,
``java`` for Java, also ``python``, ``ruby``, ``yaml``, ``xml``, etc, etc...

Example highighing D source code where we also use ``:linenos:`` to
get line numbers and ``:emphasize-lines:`` to emphasize lines 1, 2 and 4::

   .. code-block:: d
      :linenos:
      :emphasize-lines: 1,2,4
   
      import std.stdio;
      import yaml;
   
      void main()
      {
          //Read the input.
          Node root = Loader("input.yaml").load();
   
          //Display the data read.
          foreach(string word; root["Hello World"])
          {
              writeln(word);
          }
          writeln("The answer is ", root["Answer"].as!int);
   
          //Dump the loaded document to output.yaml.
          Dumper("output.yaml").dump(root);
      }

^^^^^^^^^^^^^^^^
Cross-file links
^^^^^^^^^^^^^^^^

Sections can be labelled by labels in format ``.. _LABELNAME:``, 
where LABELNAME is the name of your label (duh).

They can be referenced like this: ``:ref:`LABELNAME``` . 

Example::

   .. _the-awesome-section:

   This Section is Awesome
   -----------------------
   
   This text is awesomely recursive: :ref:`the-awesome-section`


This works even across different files.

This is better than plain links because it works even if files get renamed.
