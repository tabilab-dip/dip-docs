.. _author-spec-tutorial:

Author Specification Tutorial
=============================

This one is a simpler one, here we provide you a template and you just fill that in and put in "./dip_specs/author_specs.json"

.. code-block:: json
    :linenos:

        {
        
        "tr": {
            "project_name": "Morfolojik Analiz",

            "task_description": "Morfolojik analiz bir cümledeki kelimeleri morfemlerine ayırma işlemidir.",
            
            "usage_info": "Her bir cümleyi ayrı satıra yazınız. Cümle sonu işaretleri (., ! vb.) cümlenin son kelimesinden boşlukla ayrılmalıdır. \n\nÖrneğin:\n \"Şekerleri yedim .\"\n\"Eve gittim .\"",

        },
        "en": {
            "project_name": "Morphological Analysis and Disambiguation",

            "task_description": "Morphological Analysis is the process of finding the correct morphemes of a word and it generates set of possible morphological parsings for a sentence. Morphological Disambiguation chooses the most likely Morphological parse from this set",
            
            "usage_info": "Write each sentence in a newline. End-of-sentence markers should be seperated from the previous token with white spaces. \n\nExample:\n \"Şekerleri yedim .\"\n\"Eve gittim .\"",
        },


        "contact_info": "your_contact_info@mail.com",
        "paper_names": ["Morphological Parser, Morphological Disambiguator and Web Corpus",],
        "paper_handles": ["https://doi.org/10.1007/978-3-540-85287-2_40",],
        "paper_authors": ["Haşim Sak", "Tunga Güngör", "Murat Saraçlar"],
        "program_authors": ["Haşim Sak"],
        "program_links": ["https://github.com/tabilab-dip/morphological_parser_sak",],
        "example_sentences": [  "şekerleri yedim .\neve geldim .", "Bugun okula otobüsle gittim ."],
        
    }

* You can use \n, \t, \" etc. characters to format the output. 
* It needs to be in json format.
* One example is at `here <https://github.com/tabilab-dip/morphological_parser_sak/blob/main/dip_specs/author_specs.json>`_
