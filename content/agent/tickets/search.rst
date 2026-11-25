Search
======

Use this screen to search for tickets based on various criteria.
The ticket search screen is available in the *Search* menu item of the *Tickets* menu.

.. figure:: images/tickets-search.png
   :alt: Search Dialog

   Search Dialog

The dialog is divided into three parts: *Templates*, *Filters in use* and *Additional filters*.

If only one ticket matches, the :doc:`ticket-zoom` opens.
Otherwise the *Search Results* screen shows all matching tickets.

.. figure:: images/tickets-search-results.png
   :alt: Search Results Screen

   Search Results Screen


Templates
---------

Use this part of the dialog to save search criteria as a template for later use.

To create a new search template:

1. Click on the *Create New* button.
2. Enter a name for the search template.
3. Add some search criteria.
4. Click on the *Run search* button.

.. figure:: images/tickets-search-templates.png
   :alt: Search Templates Dialog

   Search Templates Dialog

To use a saved search template:

1. Select a template from the drop-down list.
2. Click on the *Run search* button.

To delete a saved search template:

.. warning::

   The template is deleted immediately without confirmation.

1. Select a template from the drop-down list.
2. Click on the *Delete* button.

To open the *Search Results* screen of a template directly, use the *Profile link* button.
It contains the permanent link of the search template.


Filters in Use
--------------

This part lists the filters that are used for the search.

To remove a filter, click on the *⊟* button next to the field.


Additional Filters
------------------

Use this part to add more filters and to select the output format of the results.

Add another attribute
   Select an extra attribute from the drop-down list to be used in the search.

Output
   Select the output format of the result.

To start the search, click on the *Run search* button.


Fulltext Search
---------------

The *Fulltext* filter searches the ticket title and the *From*, *To*, *Cc*, *Bcc*, *Subject* and *Body* fields of all articles.
The search is not case-sensitive.

OTOBO adds an asterisk ``*`` before and after each search word:
``print`` becomes ``*print*``.
The search word is therefore also found inside longer words, for example in *printer* and *blueprint*.

If you enter several words, OTOBO finds only tickets that contain all of the words:
``printer error`` becomes ``*printer* AND *error*``.

You can combine search words with the following operators:

.. list-table::
   :header-rows: 1
   :widths: 25 75

   * - Operator
     - Meaning
   * - ``AND``, ``&&``, ``+`` or a space
     - The ticket contains both words: ``printer AND error``.
   * - ``OR`` or ``||``
     - The ticket contains at least one of the words: ``printer OR scanner``.
   * - ``!``
     - The ticket does not contain the word: ``printer !error``.
   * - ``( )``
     - Groups words: ``(printer OR scanner) AND error``.
   * - ``" "``
     - Searches the words in quotation marks as one phrase: ``"printer error"``.


Search Index
~~~~~~~~~~~~

The fulltext search does not search the original article text, but a search index.
When OTOBO adds the subject and the body of an article to the search index, it changes the text in the following way:

- All words are converted to lower case.
- Punctuation and special characters are removed.
- Stop words are removed.
  Stop words are frequent words like *and*, *the* or *with* in English or *und*, *der* or *mit* in German.
- Words shorter than three characters or longer than 30 characters are removed.
- Each word is stored only once, at its first occurrence.
- Only the first 1000 remaining words of the subject and of the body are stored.

Single words are found reliably.
Phrase search, however, only works if the phrase is stored in the search index in exactly this form.

.. note::

   A phrase that contains stop words or short words is not found.
   For example, ``"call and connect via TeamViewer"`` is not found.
   The search index contains only *call connect via teamviewer*, because *and* is a stop word.

   To search for such a phrase, remove the stop words and short words from it: ``"call connect via TeamViewer"``.
   This only finds the phrase if none of its words already occurs earlier in the subject or body.
   If this is not reliable enough, search for the words without quotation marks: ``call connect TeamViewer``.

.. note::

   Your administrator can change the stop words, the word lengths and the number of stored words in the system configuration.
   The administrator can also configure OTOBO to store the original article text in the search index.
