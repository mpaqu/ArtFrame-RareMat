Titles in Art Cataloging
=====================================================
ArtFrame, 2017-10-06, updated 2018-02-05

____________________________________________________________________________________________________________________________
NOTE: the following represents the direction taken by the ArtFrame group in the ontology development process and may not represent the final model. This pattern document was used internally to define a direction and is shared with the intention of contextualizing a pattern found within the ontology; terms specified below may not fully align to the ontology as published.
Bibliotek-o properties and classes may get replaced with BIBFRAME terms or defined within the ArtFrame/RareMat ontology.
_____________________________________________________________________________________________________________________________

Table of Contents
> - [Sources](#sources)
> - [Background](#background)
> - [Recommendations for Moving Forward](#recommendations)
> - [Relevant ArtFrame Use Case](#useCase)
> - [Titles in MARC](#MARC)
> - [Titles in BIBFRAME](#BIBFRAME)
> - [Titles in bibliotek-o](#bibliotek-o)
> - [Recommended Classes](#classes)
> - [Recommended Properties](#properties)
> - [Recommended Names Individuals](#individuals)
> - [Diagrams](#diagrams)
> - [RDF Samples](#rdf)


<a name="sources">Sources</a>
--------

> - **bibliotek-o Titles Pattern** [*https://wiki.duraspace.org/display/LD4P/bibliotek-o?preview=/79795231/83237331/bibliotek-o_pattern_titles_201612.pdf*](https://wiki.duraspace.org/display/LD4P/bibliotek-o?preview=/79795231/83237331/bibliotek-o_pattern_titles_201612.pdf)
> - **Performed Music Ontology--Titles in BIBFRAME** [*https://wiki.duraspace.org/display/LD4P/Performed+Music+Ontology?preview=/79795208/83236905/Titles%20in%20BIBFRAME.docx*](https://wiki.duraspace.org/display/LD4P/Performed+Music+Ontology?preview=/79795208/83236905/Titles%20in%20BIBFRAME.docx)
> - **BIBFRAME 2.0 Titles Specifications** [*https://www.loc.gov/bibframe/docs/pdf/bf2-draftspectitles-10-29-2015.pdf*](https://www.loc.gov/bibframe/docs/pdf/bf2-draftspectitles-10-29-2015.pdf)

<a name="background">Background</a>
--------

bibliotek-o, the BIBFRAME extension created by LD4L-Labs and the LD4P Ontology Group, takes a slightly different approach to recording titles than BIBFRAME itself. For example, bibliotek-o distinguishes between title sources and title origins, allows for indicating transcribed versus supplied titles, the ordering of subtitles, and the creation of sort titles by providing the possibility to separate initial articles from the title proper. This document discusses if the bibliotek-o title model covers the use cases identified by the ArtFrame team and the ArtFrame Extension Group related to naming art objects and identifies areas not covered that need to be addressed in the ArtFrame extension.

<a name="recommendations">Recommendation for Moving Forward with ArtFrame</a>
--------

After testing the bibliotek-o title model, the ArtFrame group agreed that it can generally be applied to art objects. The group also investigated specific art cataloging standards (such as CCO, CDWA and DCRM(G)) for other requirements unique to art objects. In particular, the group discussed title types listed in CCO Chapter 1, p. 49-50 ([*http://cco.vrafoundation.org/downloads/PartTwo_1-ObjectNaming.pdf*](http://cco.vrafoundation.org/downloads/PartTwo_1-ObjectNaming.pdf)) as well as CDWA ([*http://www.getty.edu/research/publications/electronic_publications/cdwa/4titles.html*](http://www.getty.edu/research/publications/electronic_publications/cdwa/4titles.html)). Most of these title types (e.g. creator’s title or repository title) are very relevant concepts, but can be expressed in other ways in a linked data environment. Two remaining title types were identified that need to be formally expressed in the ArtFrame ontology: exhibition title and translated title.

> - **Recommendations:**
Exhibition title will be addressed in the Exhibition Event Model. Translated title will be accomodated in the ArtFrame ontology as a named individual to be used with bib:origin. While ex:translated differs from most of the other named individuals in this category, including it follows precedent set by bib:supplied and bib:transcribed.

> - **Title Origin**

Title origins (the place from which a title originates, i.e. container, margin, spine) are less clearly defined for objects different from regular print books. Established owl:NamedIndividuals in bibliotek-o, such as bib:supplied and bib:transcribed should be applied where appropriate, along with the newly proposed ex:translated. No additional art specific named individuals will be defined within the ArtFrame namespace. DCRM(G) 1B2 states: Always make a note on the source of the title proper. The examples given are: Title from lower margin; Title from ink note on book of mount; title from item, etc. This list could potentially be endless. For the sake of consistency, this type of information will be recorded as a title origin using rdf:value.

<a name="useCase">Relevant ArtFrame Use Case</a>
--------
![Title Use Case](/modeling_recommendations/modeling_diagrams/art_titles_1.PNG)

Examples: Les Demoiselles d'Avignon (The Young Ladies of Avignon, and originally titled The Brothel of Avignon) (Wikipedia); Swimming, by Thomas Eakins (formerly The Swimming Hole) (title change based on research)

<a name="MARC">Titles in MARC</a>
--------
In a MARC bibliographic record, many types of titles are recorded in the 20x-24x area [*http://www.loc.gov/marc/bibliographic/bd20x24x.html*](http://www.loc.gov/marc/bibliographic/bd20x24x.html). The instance title is tagged as a 245. A work title is recorded in a 240 or 130. If neither one of these are present, then the 245 can be interpreted as the title of the work as well as the instance title. The 245 allows for sub-fielding of non-sorting characters and subtitles. Variant titles are recorded in a 246, where indicators can be used to show the type or source of the variant tiles. Related titles can occur in the 6xx $t, 7xx $t, 730 or 740.

<a name="BIBFRAME">Titles in BIBFRAME</a>
--------
The classes and properties that are available to express in BIBFRAME are summarized here:
![BIBFRAME Title Model](/modeling_recommendations/modeling_diagrams/art_titles_2.PNG)

[*http://id.loc.gov/ontologies/bibframe-category.html*](http://id.loc.gov/ontologies/bibframe-category.html) accessed on July 31, 2017.
Other properties that can be used in conjunction with title information are bf:source, bf:date, bf:qualifier, and bf:note.
Subclasses of bf:VariantTitle: KeyTitle, AbbreviatedTitle, ParallelTitle, CollectiveTitle

<a name="bibliotek-o">Titles in bibliotek-o</a>
--------
![bibliotek-o title properties](/modeling_recommendations/modeling_diagrams/art_titles_3_bibliotek-o.PNG
)

![bibliotek-o title classes](/modeling_recommendations/modeling_diagrams/art_titles_4_bibliotek-o.PNG)

Named individuals to be used with bib:Origin: binder, caption, container, cover, margin, spine, supplied, transcribed 

<a name="classes">Recommended Classes</a>
--------

**bf:Title**
> - **Label**: Title entity
> - **IRI:** http://id.loc.gov/ontologies/bibframe/Title
> - **Definition:** Title information relating to a resource: work title, preferred title, instance title, transcribed title, translated title, variant form of title, etc.

**bf:Note**
> - **Label**: Note
> - **IRI:** http://id.loc.gov/ontologies/bibframe/Note
> - **Definition:** Information, usually in textual form, on attributes of a resource or some aspect of a resource.

**bf:Source**
> - **Label**: Source
> - **IRI:** http://id.loc.gov/ontologies/bibframe/Source
> - **Definition:** Information, usually in textual form, on attributes of a resource or some aspect of a resource.

**bf:Status**
> - **Label**: Status
> - **IRI:** http://id.loc.gov/ontologies/bibframe/Status
> - **Definition:** Designation of the validity or position of something, e.g., whether something is incorrect or available.

**bib:MainTitleElement**
> - **Label**: Main title element
> - **IRI:** http://bibliotek-o.org/1.1/ontology/MainTitleElement
> - **Definition:** The main part of a title.
> - **Subclass of:** http://bibliotek-o.org/1.1/ontology/TitleElement

**bib:NonSortElement**
> - **Label**: Main title element
> - **IRI:** http://bibliotek-o.org/1.1/ontology/NonSortElement
> - **Definition:** The initial segment of a title that is removed for sorting.
> - **Subclass of:** http://bibliotek-o.org/1.1/ontology/TitleElement

**bib:Origin**
> - **Label**: Origin
> - **IRI:** http://bibliotek-o.org/1.1/ontology/Origin
> - **Definition:** The place from which a resource (e.g., a title) originates, such as spine, cover, container, etc.

**bib:PartNameElement**
> - **Label**: Part name element
> - **IRI:** http://bibliotek-o.org/1.1/ontology/PartNameElement
> - **Definition:** The part of a title that specifies the name of a part of the resource.
> - **Subclass of:** http://bibliotek-o.org/1.1/ontology/TitleElement

**bib:PartNumberElement**
> - **Label**: Part number element
> - **IRI:** http://bibliotek-o.org/1.1/ontology/PartNumberElement
> - **Definition:** The part of a title that specifies the number of a part of the resource.
> - **Subclass of:** http://bibliotek-o.org/1.1/ontology/TitleElement

**bib:SubTitleElement**
> - **Label**: Subtitle element
> - **IRI:** http://bibliotek-o.org/1.1/ontology/SubtitleElement
> - **Definition:** The subtitle of a title.
> - **Subclass of:** http://bibliotek-o.org/1.1/ontology/TitleElement

<a name="properties">Recommended Properties</a>
--------

**bf:title** (Object property)
> - **Label:** Title resource
> - **IRI:** http://id.loc.gov/ontologies/bibframe/title
> - **Definition:** Name given to a resource.
> - **Comment:** Used with Work, Instance or Item.
> - **Range:** http://id.loc.gov/ontologies/bibframe/Title

**bib:isTitleOf** (Object property)
> - **Label:** is title of
> - **IRI:** http://bibliotek-o.org/1.1/ontology/isTitleOf
> - **Definition:** Resource of which this title is the title.
> - **Skope note:** Expected value Work, Instance or Item.
> - **Domain:** http://id.loc.gov/ontologies/bibframe/Title
> - **Inverse:** http://id.loc.gov/ontologies/bibframe/title

**bf:note** (Object property)
> - **Label:** Note
> - **IRI:** http://id.loc.gov/ontologies/bibframe/note
> - **Definition:** General textual information relating to a resource, such as Information about a specific copy of a resource or information about a particular attribute of a resource.
> - **Comment:** Used with Unspecified.
> - **Range:** http://id.loc.gov/ontologies/bibframe/Note

**bf:status** (Object property)
> - **Label:** Status
> - **IRI:** http://id.loc.gov/ontologies/bibframe/status
> - **Definition:** Designation of the validity or position of something, such as indication that the classification number is canceled or invalid, circulation availability of an item, indication of whether the identifier is canceled or invalid.
> - **Comment:** Used with Unspecified.
> - **Range:** http://id.loc.gov/ontologies/bibframe/Status

**bib:hasActivity** (Object property)
> - **Label:** has activity
> - **IRI:** http://bibliotek-o.org/1.1/ontology/hasActivity
> - **Definition:** Relates this resource to an activity or contribution by a single agent that affects or alters its existence or state.
> - **Range:** http://bibliotek-o.org/1.1/ontology/Activity
> - **Inverse of:** http://bibliotek-o.org/1.1/ontology/isActivityOf

**bib:isActivityOf** (Object property)
> - **Label:** is activity of
> - **IRI:** http://bibliotek-o.org/1.1/ontology/isActivityOf
> - **Definition:** Relates an activity to the affected resource.
> - **Domain:** http://bibliotek-o.org/1.1/ontology/Activity
> - **Inverse of:** http://bibliotek-o.org/1.1/ontology/hasActivity

**bib:hasOrigin** (Object property)
> - **Label:** has origin
> - **IRI:** http://bibliotek-o.org/1.1/ontology/hasOrigin
> - **Definition:** Specifies the physical location from which this resource (e.g., a title) originates, such as spine, cover, container, etc.
> - **Scope note:** Distinct from http://bibliotek-o.org/1.1/ontology/hasSource, which specifies an external organization or scheme from which the resource was obtained.

**bib:hasSource** (Object property)
> - **Label:** has Source
> - **IRI:** http://bibliotek-o.org/1.1/ontology/hasSource
> - **Definition:** Relates this resource to the source from which it was derived.
> - **Scope note:** Has general applicability to many types of sources and resources.
> - **Inverse of:** http://bibliotek-o.org/1.1/ontology/isSourceOf

**bib:isSourceOf** (Object property)
> - **Label:** is source of
> - **IRI:** http://bibliotek-o.org/1.1/ontology/isSourceOf
> - **Definition:** Relates this resource to a resource of which it is the source.
> - **Scope note:** Has general applicability to many types of sources and resources.
> - **Inverse of:** http://bibliotek-o.org/1.1/ontology/hasSource

**bib:hasPreferredTitle** (Object property)
> - **Label:** has preferred title
> - **IRI:** http://bibliotek-o.org/1.1/ontology/hasPreferredTitle
> - **Definition:** Specifies the preferred title of this resource.
> - **Scope note:** A resource may have multiple directly linked titles, among which this is the preferred title.
> - **Subproperty of: http://id.loc.gov/ontologies/bibframe/title
> - **Range:** http://id.loc.gov/ontologies/bibframe/Title
> - **Inverse of:** http://bibliotek-o.org/1.1/ontology/isPreferredTitleOf

**bib:isPreferredTitleOf** (Object property)
> - **Label:** is preferred title of
> - **IRI:** http://bibliotek-o.org/1.1/ontology/isPreferredTitleOf
> - **Definition:** Specifies the resource for which this is the preferred title.
> - **Scope note:** A resource may have multiple directly linked titles, among which this is the preferred title.
> - **Subproperty of: http://bibliotek-o.org/1.1/ontology/isTitleOf
> - **Domain:** http://id.loc.gov/ontologies/bibframe/Title
> - **Inverse of:** http://bibliotek-o.org/1.1/ontology/hasPreferredTitle

**dcterms:hasPart**
> - **Label:** Has Part
> - **IRI:** http://purl.org/dc/terms/hasPart
> - **Comment:** A related resource that is included either physically or logically in the described
resource.

**vivo:rank**
> - **Label:** rank
> - **IRI:** http://vivoweb.org/ontology/core#rank
> - **Comment:** An integer indicating the position of an entity in a list.

<a name="individuals">Recommended Named Individuals</a>
--------

**bib:invalid**
> - **Label:** invalid
> - **IRI:** http://bibliotek-o.org/1.1/ontology/invalid
> - **Definition:** Applies to an identifier or other resource that is invalid.
> - **Belongs to:** http://id.loc.gov/ontologies/bibframe/Status

> - *Note: Note: All available title origin named individuals defined in bibliotek-o may be used if applicable, e.g.:*

**bib:caption**
> - **Label:** caption
> - **IRI:** http://bibliotek-o.org/1.1/ontology/caption
> - **Definition:** Applies to a resource (e.g., a title) given at the beginning of the first page of the text.
> - **Belongs to:** http://bibliotek-o.org/1.1/ontology/Origin

**bib:supplied**
> - **Label:** supplied
> - **IRI:** http://bibliotek-o.org/1.1/ontology/supplied
> - **Definition:** Supplied value, not directly transcribed from the resource itself.
> - **Belongs to:** http://bibliotek-o.org/1.1/ontology/Origin

**bib:transcribed**
> - **Label:** supplied
> - **IRI:** http://bibliotek-o.org/1.1/ontology/transcribed
> - **Definition:** Value transcribed directly from the resource.
> - **Belongs to:** http://bibliotek-o.org/1.1/ontology/Origin

**ex:translated**
> - **Label:** translated
> - **IRI:** TBD
> - **Definition:** Value translated from another language, not transcribed from the resource itself.
> - **Belongs to:** http://bibliotek-o.org/1.1/ontology/Origin

<a name="diagrams">Diagrams</a>
--------

Transcribed title

![TranscribedTitle](/modeling_recommendations/modeling_diagrams/TranscribedTitle.jpg)

Creator's title

![CreatorsTitle_2](/modeling_recommendations/modeling_diagrams/CreatorsTitle_2.jpg)

Translated title

![translatedTitle](/modeling_recommendations/modeling_diagrams/translatedTitle.jpg)

<a name="rdf">RDF Samples</a>
--------
**Title transcribed from resource**

```
:instance1 a bf:Instance ;
 bf:isInstanceOf :w1 ;
 bib:hasPreferredTitle :t1 .

:t1 a bf:Title ;
 bib:isPreferredTitleOf :instance1 ;
 rdf:value "Burial of Famine Victim,  
 Hengyang, China" ;
 bib:hasOrigin :transcribed ; origin1 ;
 dcterms:hasPart :mainTitleElement1 .

:mainTitleElement1 a bib:MainTitleElement ;
 rdf:value “Burial of Famine Victim,
 Hengyang, China” ;
 dcterms:isPartOf :t2 .

bib:transcribed a owl:NamedIndividual, bib:Origin ;
 rdfs:label "transcribed" .

:origin1 a bib:Origin ;
rdf:value “verso” .

```
**Supplied, transcribed, incorrect title**

```
:w1 a bf:Work ;
 bib:hasPreferredTitle :t1 ;
 bf:hasInstance :instance1, :instance2 .

:t1 a bf:Title ;
 bib:isPreferredTitleOf :w1 ;
 rdf:value "Barracks near Segezha
 Station"@en ;
 dcterms:hasPart :mainTitleElement1 .
 
:mainTitleElement1 a bib:MainTitleElement ;
 rdf:value "Barracks near Segezha
 Station"@en ;
 dcterms:isPartOf :t1.

:instance1 a bf:Instance ;
 bf:isInstanceOf :w1 ;
 bib:hasPreferredTitle :t2 ;
 bf:genreForm :negatives (photographs) ;
 bf:title :t2 .
 
:t2 a bf:Title ;
 bib:isPreferredTitleOf :instance1 ;
 rdf:value "Barracks near Segezha
 Station"@en ;
 bib:origin bib:supplied ;
 bib:hasSource :source1 ;
  bf:note :note1 .
 dcterms:hasPart :mainTitleElement2 .
 
 :mainTitleElement2 a bib:MainTitleElement ;
 rdf:value "Barracks near Segezha
 Station"@en ;
 dcterms:isPartOf :t2 .

 :note1 a bf:Note ;
 rdf:value "Title devised by Library staff."

:source1 a bf:Source ;
rdf:value "http://prokudin-gorsky.org/?lang=en"^^xsd:anyURI .
 
:instance2 a bf:Instance ;
 bib:hasPreferredTitle :t3 ;
 bf:title :t4 ;
 bf:genreForm :photographic prints ;
 bf:isInstanceOf :w1 .

:t3 a bf:Title ;
 bib:isPreferedTitleOf :instance2 ;
 rdf:value "Barracks near Segezha
 Station"@en ;
 bib:origin bib:supplied ;
 bib:hasSource :source1 ;
 bf:note :note1 ;
 dcterms:hasPart :mainTitleElement3 .

:mainTitleElement3 a bib:MainTitleElement ;
 rdf:value "Barracks near Segezha
 Station"@en ;
 dcterms:isPartOf :t3 .

:t4 a bf:Title ;
 bib:isTitleOf :instance2 ;
 rdf:value "Baraki dli︠a︡ voennopi︠e︡nnykh u st.
 Segezh (Prisoner of war barracks near the
 Segezh Station)" ;
 dcterms:hasPart :mainTitleElement4 ;
 bib:origin bib:transcribed, bib:caption ;
 bf:status bib:invalid ;
 bf:note :note2 .
 
 :note2 a bf:Note ;
 rdfs:label "Incorrect caption in album" .

bib:supplied a owl:NamedIndividual , bib:Origin ;
 rdfs:label "supplied" .

bib:transcribed a owl:NamedIndividual , bib:Origin ;
 rdfs:label "transcribed" .

**Example for title change**

:w1 a bf:Work ;
 bib:hasActivity :c1 ;
 bib:hasPreferredTitle :title1 ;
 bf:title :title2, :title3, :title4 .

:c1 a bib:ArtistActivity ;
 bib:hasAgent <http://id.loc.gov/rwo/agents/n80061185> .

:title1 a bf:Title ;
 rdf:value "Swimming" ;
 bib:isPreferredTitleOf :w1 ;
 dcterms:hasPart :MainTitleElement1 ; 
 bf:note :note1 ;
 bib:hasSource <http://worldcat.org/entity/work/id/36654331> , 
<http://id.loc.gov/rwo/agents/n80061185> .

:MainTitleElement1 a bib:MainTitleElement ;
 dcterms:isPartOf :title1 ;
 rdfs:label "Swimming" .

:note1 a bf:Note ;
 rdf:value "Correspondence with Sam Duncan, Asst. Museum Librarian,
 Amon Carter Museum, 4/11/96 (based on new research, "Swimming" has
 been determined to be Eakins' original title and the title under which
 it was first exhibited; wall labels, catalog listings, etc. have been
 changed from "The Swimming hole" to "Swimming" to reflect this new research.)" .

:title2 a bf:Title ;
 bf:isTitleOf :w1 ;
  rdf:value "Swimming hole" ;
 dcterms:hasPart :MainTitleElement2 ;
 bib:hasSource :source2 .

:source2 a bf:Source ;
 bib:isSourceOf :title2 ;
 rdf:value "Britannica Micro., 1995:
 v. 4, p. 315 (Eakins, Thomas; treading water
 next to his setter dog Harry and watching a
 group of students swimming in "The 
 Swimming Hole.")" .

:MainTitleElement2 a bib:MainTitleElement ;
 dcterms:isPartOf :title2 ;
 rdf:value "Swimming hole" .

:title3 a bf:Title ;
 bf:isTitleOf :w1 ;
 rdf:value "Old swimming hole" ;
 dcterms:hasPart :MainTitleElement3 ;
 bib:hasSource <http://worldcat.org/entity/work/id/36654331> .

:MainTitleElement3 a bib:MainTitleElement ;
 dcterms:isPartOf :title3 ;
 rdf:value "Old swimming hole" .

:title4 a bf:Title ;
 bf:isTitleOf :w1 ;
 rdf:value "Swimmers" ;
 dcterms:hasPart :MainTitleElement4 ;
 bib:hasSource <http://worldcat.org/entity/work/id/36654331> .

:MainTitleElement4 a bib:MainTitleElement ;
 dcterms:isPartOf :title4 ;
 rdfs:label "Swimmers" .

```
**Work in multiple languages**
```
:w1 a bf:Work ;
 bib:hasActivity :c1 ;
 bib:hasPreferredTitle :title1 ;
 bf:title :title2, :title3, :title4 .

:c1 a bib:ArtistActivity ;
 bib:hasAgent <http://id.loc.gov/rwo/agents/n78086005> .

:title1 a bf:Title;
 bib:isPreferredTitleOf :w1 ;
 rdf:value "Les Demoiselles d'Avignon"@fr ;
 dcterms:hasPart :mainTitleElement1, :nonSort1 ;
 bib:hasSource <http://id.loc.gov/rwo/agents/n79021281> .

:mainTitleElement1 a bib:MainTitleElement ;
 dcterms:isPartOf :title1 ;
 rdf:value "Demoiselles d'Avignon"@fr .

:nonSort1 a bib:NonSortElement ;
 dcterms:isPartOf :title1 ;
 rdf:value "Les"@fr .

:title2 a bf:Title ;
 bf:isTitleOf :w1 ;
 rdf:value "Young ladies of Avignon"@en ;
 dcterms:hasPart :mainTitleElement2 ;
 bib:hasSource :source1 .

:mainTitleElement2 a bib:MainTitleElement ;
 dcterms:isPartOf :title2 ;
 rdf:value "Young ladies of Avignon"@en .

:source1 a bf:Work ,
 bf:title :title5 .

:title5 a bf:Title ;
 rdf:value "Index to reproductions of    
 European art" .

:title3 a bf:Title ;
 bf:isTitleOf :w1 ;
 rdf:value "Avignon brothel"@en ;
 dcterms:hasPart :mainTitleElement3 ;
 bib:hasSource <http://worldcat.org/entity/work/id/56688045> .

:mainTitleElement3 a bib:MainTitleElement ;
 dcterms:isPartOf :title3 ;
 rdf:value "Avignon brothel"@en .

:title4 a bf:Title ;
 bf:isTitleOf :w1 ;
 rdf:value "Le Bordel"@fr ;
 dcterms:hasPart :mainTitleElement4, :nonSort2 ;
 bib:hasSource <http://worldcat.org/entity/work/id/3901310255> .

:mainTitleElement4 a bib:MainTitleElement ;
 dcterms:isPartOf :title4 ;
 rdf:value "Bordel"@fr .

:nonSort4 a bib:NonSortElement ;
 dcterms:isPartOf :title4 ;
 rdf:value "Le"@fr .
 
```
**Example of title, subtitle and a variant title**

```
:w1 a bf:Work ;
 bib:hasPreferredTitle :title1 ;
 bf:title :title2 ;
 bf:hasInstance :instance1 .

:title1 a bf:Title ;
 bib:isPreferredTitleOf :w1 ;
 rdf:value "I [love] Venice"@en ;
 dcterms:hasPart :mainTitleElement1 .

:mainTitleElement1 a bib:MainTitleElement ;
 dcterms:isPartOf :title1 ;
 rdf:value "I [love] Venice"@en .


:title2 a bfTitle ;
 bf:isTitleOf :w1 ;
 rdf:value "I heart Venice"@en ;
 dcterms:hasPart :mainTitleElement2 .

:mainTitleElement2 a bib:MainTitleElement ;
 dcterms:isPartOf :title2 ;
 rdf:value "I heart Venice"@en .
  :instance1 a bf:Instance
 bf:isInstanceOf :w1 ;
 bib:hasPreferredTitle :title3 ;
 bf:title :title4 .
 
:title3 a bf:Title ;
 bib:isPreferredTitleOf :instance1 ;
 rdf:value "I [love] Venice : portable pocket ashtray"@en ;
 dcterms:hasPart :mainTitleElement3, :subtitle1 ;
 bf:note :note1 .

:mainTitleElement3 a bib:MainTitleElement ;
 dcterms:isPartOf :title3 ;
 rdf:value "I [love] Venice"@en .

:subtitle1 a bib:SubTitleElement ;
 dcterms:isPartOf :title3 ;
 rdf:value "portable pocket ashtray"@en .

:title4 a bf:Title ;
 bf:isTitleOf :instance1 ;
 rdf:value "I heart Venice : portable pocket ashtray"@en ;
 dcterms:hasPart :mainTitleElement4, :subtitle2 .

:mainTitleElement4 a bib:MainTitleElement ;
 dcterms:isPartOf :title2 ;
 rdf:value "I heart Venice"@en .

:subtitle2 a bib:SubTitleElement ;
 dcterms:isPartOf :title2 ;
 rdfs:value "portable pocket ashtray"@en .

:note1 a bf:Note ;
 rdf:value “In title, the word "love" is   
 represented by a heart symbol.” .
 
 ```
 **Example of multiple subtitles**
 
 ```
 :instance1 a bf:Instance
 bf:isInstanceOf :w1 ;
 bib:hasPreferredTitle :title1 .

:title1 a bf:Title ;
 bib:isPreferredTitleOf :instance1 ;
 rdf:value "New York City : Newspaper Row 
 on an Election Night : Announcing the Returns ;
 dcterms:hasPart :mainTitleElement1, :subtitle1, :subtitle2 ;
 bib:origin :transcribed .

:mainTitleElement1 a bib:MainTitleElement ;
 dcterms:isPartOf :title1 ;
 rdf:value "New York City"@en ;
 vivo:rank 1 .

:subtitle1 a bib:SubtitleElement ;
 rdfs:label “Newspaper Row on an Election Night”@en ;
 vivo:rank 2 .    
 
:subtitle2 a bib:SubtitleElement ;
 rdfs:label “Announcing the Returns”@en ;
 vivo:rank 3 .
