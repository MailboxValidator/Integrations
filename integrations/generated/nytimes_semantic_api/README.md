# @datafire/nytimes_semantic_api
The Semantic API complements the Articles API. With the Semantic API, you get access to the long list of people, places, organizations and other locations, entities and descriptors that make up the controlled vocabulary used as metadata by The New York Times (sometimes referred to as Times Tags and used for Times Topics pages).

The Semantic API uses concepts which are, by definition, terms in The New York Times controlled vocabulary. Like the way facets are used in the Articles API, concepts are a good way to uncover articles of interest in The New York Times archive, and at the same time, limit the scope and number of those articles. The Semantic API maps to external semantic data resources, in a fashion consistent with the idea of linked data. The Semantic API also provides combination and relationship information to other, similar concepts in The New York Times controlled vocabulary.


## Operation: name.concept_type.specific_concept.json.get


### Input Schema
```json
{
  "type": "object",
  "properties": {
    "concept-type": {
      "type": "string",
      "description": "The type of the concept, used for Constructing a Semantic API Request by Concept Type and Specific Concept Name. The parameter is defined as a name-value pair, as in \"concept_type=[nytd_geo|nytd_per|nytd_org|nytd_des]\".\n",
      "enum": [
        "nytd_geo",
        "nytd_per",
        "nytd_org",
        "nytd_des"
      ]
    },
    "specific-concept": {
      "type": "string",
      "description": "The name of the concept, used for Constructing a Semantic API Request by Concept Type and Specific Concept Name. The parameter is defined in the URI path, as the element immediately preceding \".json\" like with \"Baseball.json\".\n"
    },
    "fields": {
      "type": "string",
      "description": "\"all\" or comma-separated list of specific optional fields: pages, ticker_symbol, links, taxonomy, combinations, geocodes, article_list, scope_notes, search_api_query\n\nOptional fields are returned in result_set. They are briefly explained here:\n\npages: A list of topic pages associated with a specific concept.\nticker_symbol: If this concept is a publicly traded company, this field contains the ticker symbol.\nlinks: A list of links from this concept to external data resources.\ntaxonomy: For descriptor concepts, this field returns a list of taxonomic relations to other concepts.\ncombinations: For descriptor concepts, this field returns a list of the specific meanings tis concept takes on when combined with other concepts.\ngeocodes: For geographic concepts, the full GIS record from geonames.\narticle_list: A list of up to 10 articles associated with this concept.\nscope_notes: Scope notes contains clarifications and meaning definitions that explicate the relationship between the concept and an article.\nsearch_api_query: Returns the request one would need to submit to the Article Search API to obtain a list of articles annotated with this concept.\n",
      "enum": [
        "all",
        "pages",
        "ticker_symbol",
        "links",
        "taxonomy",
        "combinations",
        "geocodes",
        "article_list",
        "scope_notes",
        "search_api_query"
      ]
    },
    "query": {
      "type": "string",
      "description": "Precedes the search term string. Used in a Search Query. Except for &lt;specific_concept_name&gt;, Search Query will take the required parameters listed above (&lt;concept_type&gt;, &lt;concept_uri&gt;, &lt;article_uri&gt;) as an optional_parameter in addition to the query=&lt;query_term&gt;."
    }
  },
  "additionalProperties": false,
  "required": [
    "concept-type",
    "specific-concept",
    "query"
  ]
}
```
### Output Schema
```json
{
  "properties": {
    "copyright": {
      "type": "string"
    },
    "num_results": {
      "type": "integer"
    },
    "results": {
      "items": {
        "$ref": "#/definitions/Concept"
      },
      "type": "array"
    },
    "status": {
      "type": "string"
    }
  },
  "type": "object"
}
```
## Operation: search.json.get


### Input Schema
```json
{
  "type": "object",
  "properties": {
    "query": {
      "type": "string",
      "description": "Precedes the search term string. Used in a Search Query. Except for &lt;specific_concept_name&gt;, Search Query will take the required parameters listed above (&lt;concept_type&gt;, &lt;concept_uri&gt;, &lt;article_uri&gt;) as an optional_parameter in addition to the query=&lt;query_term&gt;."
    },
    "offset": {
      "type": "integer",
      "description": "Integer value for the index count from the first concept to the last concept, sorted alphabetically. Used in a Search Query. A Search Query will return up to 10 concepts in its results."
    },
    "fields": {
      "type": "string",
      "description": "\"all\" or comma-separated list of specific optional fields: pages, ticker_symbol, links, taxonomy, combinations, geocodes, article_list, scope_notes, search_api_query\n\nOptional fields are returned in result_set. They are briefly explained here:\n\npages: A list of topic pages associated with a specific concept.\nticker_symbol: If this concept is a publicly traded company, this field contains the ticker symbol.\nlinks: A list of links from this concept to external data resources.\ntaxonomy: For descriptor concepts, this field returns a list of taxonomic relations to other concepts.\ncombinations: For descriptor concepts, this field returns a list of the specific meanings tis concept takes on when combined with other concepts.\ngeocodes: For geographic concepts, the full GIS record from geonames.\narticle_list: A list of up to 10 articles associated with this concept.\nscope_notes: Scope notes contains clarifications and meaning definitions that explicate the relationship between the concept and an article.\nsearch_api_query: Returns the request one would need to submit to the Article Search API to obtain a list of articles annotated with this concept.\n",
      "enum": [
        "all",
        "pages",
        "ticker_symbol",
        "links",
        "taxonomy",
        "combinations",
        "geocodes",
        "article_list",
        "scope_notes",
        "search_api_query"
      ]
    }
  },
  "additionalProperties": false,
  "required": [
    "query"
  ]
}
```
### Output Schema
```json
{
  "properties": {
    "copyright": {
      "type": "string"
    },
    "num_results": {
      "type": "integer"
    },
    "results": {
      "items": {
        "$ref": "#/definitions/ConceptRelation"
      },
      "type": "array"
    },
    "status": {
      "type": "string"
    }
  },
  "type": "object"
}
```