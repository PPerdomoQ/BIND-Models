# BIND-Models
This module describes the data elements in the KHTQ. It specifically covers the data element in the table _DCDE Laboratory measurement_. This module is based on the EJP RD CDE semantic model module for _Disease diagnosis_ group [CDE-semantic-model/disease diagnosis](https://github.com/ejp-rd-vp/CDE-semantic-model/blob/master/docs/disease_diagnosis.md).

<p align="center">
    <a href="/RNAseq_model_v2.png" target="_blank">
        <img src="/RNAseq_model_v2.png">
    </a>
</p>

### Example RDF (turtle)
```ttl
@prefix : <http://w3id.org/bind/data/v1/example-rdf/> .
@prefix obo: <http://purl.obolibrary.org/obo/> .
@prefix sio: <http://semanticscience.org/resource/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix prov: <http://www.w3.org/ns/prov#> .


:identifier_ a sio:SIO_000115 ;
    rdfs:label "Identifier"^^xsd:string ;
    sio:SIO_000020 :role_ ;
    sio:SIO_000300 "mouse_36242"^^xsd:string .

:mouse_ a sio:SIO_000486 ;
    rdfs:label "Mouse"^^xsd:string ;
    sio:SIO_000228 :role_ ;
    sio:SIO_000008 :expression_.
    
:role_ a obo:OBI_0000112, sio:SIO_000016 ;
    rdfs:label "Role: Specimen"^^xsd:string ;
    sio:SIO_000356 :rna_process_ .
    
:rna_process_ a obo:OBI_0001177, sio:SIO_000006 ;
    rdfs:label "Process: RNA-seq"^^xsd:string ;
    sio:SIO_000291 :rna_ ;
    sio:SIO_000229 :raw_ ;
    sio:SIO_000229 :normalized_ ;
    sio:SIO_000230 :cell_;
    prov:wasInformedBy :sampling_process_.

:cell_ a sio:SIO_010001; 
    rdfs:label "Cell"^^xsd:string ;
    obo:HSO_0000243 :anatomic_entity_.

:sampling_process_ a sio:SIO_001049;
    rdfs:label "Sampling Process"^^xsd:string .
    
:anatomic_entity_ a sio:SIO_001262;
    rdfs:label "Anatomical entity"^^xsd:string .
    
:rna_ a sio:SIO_010450, sio:SIO_000015;
    rdfs:label "RNA-transcript"^^xsd:string ;
    sio:SIO_010079 :gene_.
    
:gene_ a sio:SIO_010101;
    rdfs:label "RNA-gene"^^xsd:string .

:cell_id_ a sio:SIO_000115;
    rdfs:label "Cell-ID"^^xsd:string;
    sio:SIO_000020 :cell_ ;
    sio:SIO_000300 "cid_000001"^^xsd:string .
    
:raw_ a sio:SIO_000015, obo:NCIT_C184799;
    rdfs:label "Raw-Counts"^^xsd:string;
    sio:SIO_000628 :expression_;
    sio:SIO_000221 :integer_ ;
    sio:SIO_000300 "1262"^^xsd:string .

:normalized_ a sio:SIO_000015, obo:NCIT_C184799;
    rdfs:label "Normalized-Counts"^^xsd:string;
    sio:SIO_000628 :expression_;
    sio:SIO_000221 :float_ ;
    sio:SIO_000300 "0.16"^^xsd:string .
    
:float_ a sio:SIO_000074, obo:UO_0000192;
    rdfs:label "Float"^^xsd:string.

:integer_ a sio:SIO_000074, obo:UO_0000192;
    rdfs:label "Integer"^^xsd:string.
    
:expression_ a sio:SIO_000614, obo:NCIT_C103158; 
    rdfs:label "RNA expression"^^xsd:string.
```
