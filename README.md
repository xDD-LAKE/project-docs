# API Endpoints
1. **xDD API**: Text-based search of over 15.5M full-texts from multiple publishers spanning all disciplines
    - https://xdd.wisc.edu/api: Statistics and search across entire xDD corpus (equivalent to deprecated https://geodeepdive.org/api)
        - Full-text search and retrieval of text snippets: https://xdd.wisc.edu/api/snippets; automatic surfacing of mentioned drugs and grounded EMMAA statements available with option `&known_entities=drugs,emmaa`
        - Can filter by set with `&set=xdd-covid-19`
        - Example to scroll (25 per page) through all documents within the `xdd-covid-19` set with surfaced drug mentions and EMMAA statements: https://xdd.wisc.edu/api/articles?set=xdd-covid-19&full_results=true&known_entities=emmaa,drugs&per_page=25
    - https://xdd.wisc.edu/sets/: xDD document sets defined by full text searches and journal titles. Different transformations to documents within sets are available within sub-pages of the set. For example, documents within a set may be used to train a word embedding model, or the COSMOS extraction pipeline may be deployed to extract figures, tables, and equations for documents within a set
        - https://xdd.wisc.edu/sets/xdd-covid-19/: Lists information about the `xdd-covid-19` set of documents, and lists available products (transformations) derived from the set.
2. **COSMOS API**: Figure, table, equation retreival by [COSMOS document processing pipeline](https://github.com/UW-COSMOS/Cosmos) deployed over xDD set. Note that use of these routes to retrieve table and figure objects requires an API key.
    - Get started by reading the [COSMOS documentation](https://uw-cosmos.github.io/Cosmos/index.html) and understanding the back-end.
    - https://xdd.wisc.edu/sets/xdd-covid-19/cosmos/api/: Base documentation for COSMOS search interface, available for the `xdd-covid-19` set.
    - https://xdd.wisc.edu/sets/xdd-covid-19/cosmos/api/search: Documentation for searching the COSMOS extractions.
    - https://xdd.wisc.edu/set_visualizer/sets/xdd-covid-19: COSMOS search and discovery interface deployed over `xdd-covid-19` set.
3. **word2vec API**: Word embedding models (unigram, bigram, trigram) trained on xDD document set. 
    - https://xdd.wisc.edu/sets/xdd-covid-19/word2vec/api/: Documentation for the API to explore the word embedding model.
        - https://xdd.wisc.edu/sets/xdd-covid-19/word2vec/api/most_similar - Documentation for the "most_similar" function
        - https://xdd.wisc.edu/sets/xdd-covid-19/word2vec/api/most_similar?word=covid&n=50&model=trigram&lowered=true&cleaned=true - Example query: uni- bi- and tri-grams most similar to "covid" in the case-insensitive, ligature-cleaned model.
4. **doc2vec API**: Document embedding model trained on xDD document set.
    - https://xdd.wisc.edu/sets/xdd-covid-19/doc2vec/api/similar: Documentation for "similar" function to return syntactically similar documents - Example ?doi=10.1002/pbc.28600
5. **ASKE-ID API**: Generate unique IDs and lookup metadata and linking information for data and documents used in ASKE infrastructure.
    - https://xdd.wisc.edu/aske-id/id/: base URL for API route, used for lookup.
    - Registering a new ASKE-ID and submitting metadata requires an API key
6. **thing2vec API** (experimental): For a given table, use the COSMOS object ID to discover tables "nearby" in a embedding model.  
    - https://xdddev.chtc.io/sets/xdd-covid-19/thing2vec/api/: Documentation for the API to explore the table embedding model.
