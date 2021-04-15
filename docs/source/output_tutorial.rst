.. _output-tutorial:

Output Format Tutorial
=======================

This section describes what outputs your system can produce. 


Your system should produce a JSON from its endpoint. If you followed the :ref:`form schema tutorial <form-schema-tutorial>` : here, nli.run_algorithm function returns a python dictionary and json.dumps(.) function turns it into a JSON string. Depending on your language/framework there are similar methods, pick the one that's most suitable for your.


How does that python dictionary look like:
------------------------------------------------

The output is assumed to be in the following format:

.. code-block:: json
    :linenos:

    {
        "text": "Text output of the system",
        "brat_standoff": "If you use annotated output (e.g. in dependency parsers etc.), and the developer decides to return in standoff format",
        "brat_conll": "If we use annotated output but developer returns conll format"
    }

* Regardless of you use annotated output, you can give textual output together with it by providing value to the text field. You can use \t, \n characters for nicely indented outputs. For now we don't have html outputs.
* If you are using annotated output filling in only one of "brat_standoff" or "brat_conll" is enough.
* Now I need to explain what are those:
    * **brat_conll**: This is the conll formatted string. If you provide this our system converts it into the standoff format.
    * **brat_standoff**: This is the standoff format, required by annotator called brat. In times, your conll string can have special misc fields filled in, for these times, your are expected to provide the standoff formatted output.
    * To see how these work check out the below sections.


Example CONLL output:
------------------------
Below, I show you in python code, so you also understand the data-type is string:

.. code-block:: python
    :linenos:

    conll = """# newdoc
    # newpar
    # sent_id = 1
    # text = bu örnek bir cümledir.
    1   bu  bu  PRON    Demons  Case=Nom|Number=Sing|Person=3|PronType=Dem  2   det _   det
    2   örnek   örnek   NOUN    Noun    Case=Nom|Number=Sing|Person=3   4   nsubj   _   _
    3   bir bir NUM ANum    NumType=Card    4   det _   _
    4-5 cümledir    _   _   _   _   _   _   _   _
    4   cüm cüm NOUN    Noun    Case=Nom|Number=Sing|Person=3   0   root    _   _
    5   ledir   i   AUX Zero    Aspect=Perf|Mood=Gen|Number=Sing|Person=3|Tense=Pres    4   cop _   cop
    6   .   .   PUNCT   Punc    _   4   punct   _   _
    """


How can you test your CONLL output
------------------------------------
You can use the file `conllXtostandoff.py <https://github.com/tabilab-dip/backend-proxy/blob/main/backend_proxy/misc/conllXtostandoff.py>`_ to parse your example conll output. Example usage is given at the bottom of the file. Once you get the standoff output you can test check if it produces a valid annotation by using the `live brat tool <http://brat.nlplab.org/embed.html>`_. At the bottom of that page, you can see the "live embedding" part. Here you can paste your output to the right text area and leave the left text area blank.


How can you get your own brat_standoff format
------------------------------------------------
You can use the file `conllXtostandoff.py <https://github.com/tabilab-dip/backend-proxy/blob/main/backend_proxy/misc/conllXtostandoff.py>`_ to parse your outputs in your own way. For that, you better take a look at `brat embedding examples <http://brat.nlplab.org/embed.html>`_ and get a valid output for your case.
