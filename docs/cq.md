## Competency Questions

Literal Reification can be sed for answering several questions related to literals' context.

In the following subsections, some of them are introduced together with their respective SPARQL queries. 

The prefixes that are used in all the SPARQL queries provided below are defined as follows:

    PREFIX literal: <http://www.essepuntato.it/2010/06/literalreification/>
    PREFIX dcterms: <http://purl.org/dc/terms/>

### CQ1

What is the literal value associated with a given entity, along with the creator of that reified literal?

    SELECT ?entity ?value ?creator WHERE {
        ?entity literal:hasLiteral ?lit .
        ?lit literal:hasLiteralValue ?value ;
            dcterms:creator ?creator .
    }

### CQ2

Which distinct reified literals share the exact same literal value?

    SELECT ?lit1 ?lit2 ?value WHERE {
        ?lit1 literal:hasSameLiteralValueAs ?lit2 ;
              literal:hasLiteralValue ?value .
        FILTER(?lit1 != ?lit2)
    }

### CQ3

Which entities are annotated with a literal that has a specific value?

    SELECT ?entity WHERE {
        ?entity literal:hasLiteral ?lit .
        ?lit literal:hasLiteralValue "Artificial Intelligence" .
    }
