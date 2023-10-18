## 1. Vision

Binomial nomenclature is great, sci names identifiers are used for 275 years.

Global Names (GN) was created to deal with sci anmes.

Main GN goal is Global Names Index. To achieve it parsing, detecting, reconciliation tools were needed and were developed.

This grant is about perfecting name-finding, then the first version of Global Names Index.

Many need tools to handle scientific names, GN provides them.

Parsing, Detection and Reconciliation are current three major GN services.

GN is open source, supported by 2 NSF grants so far.

First grant funded proof-of-concept tools

Second grant funded creation of very fast tools, e.g. 6 bil pages, 9 hrs.

Now we're looking for money *to make name discovery way better*.
We hone algorithms for BHL first, than apply them globally.

Planned developments:

### 1.1 Name detection improvement

BHL is great testing ground, and it still has ~25% of names not in the index.

We perfect tools with BHL, than expand globally.
The following will be addressed:

#### 1.1.1 Abbreviated Names 

20% of names abbreviated, heuristic and AI methods will allow us to expand them.

#### 1.1.2 False positives.

Many genera are also normal words.

We need to find ways to eliminate false positives.

This will also allow to decrease false negatives.

#### 1.1.3 OCR errors

70 mil additional occurrences found by N-gram, but a lot of them are false positives.

We can eliminate fals positives with 1.1.2 algorithms.

Then we can add n-gram to GNfinder

### 1.2 Vernacular names

Vernacular names detection creates even more false positives than sci names.

Using 1.1.2 algorithms we can create a clear index of vernacular names.

It will make BHL more accessible to lay people and citizen scientists.

### 1.3 A prototype of Global Name Index

The ultimate goal is building a global index of names to publications.

BHLnames project is a prototype of Global Names Index.

It uses "taxonomic intelligence":

    taxons can be found by any name

    books can be searched by higher taxons

    texts can be categorized by taxonomy inside

    names point to original descriptions

We will expand it to HathiTrust, it will add taxonomic intelligence to 6 billion pages of their corpus. Then we can go further.

## 2. Background and Prerequisites

Binomial nomenclature got popularized in late 18th century, its IDs are good for biology.

Nomenclature has 4 main codes

The difference between codes is not that big, so a universal parser can be made.

Virus code does not follow binomial nomencature.

There are a few problems with scientific names that we try to address with Global Names:

    Scientific names do not have consistent string representation
    There is approximately 3 names per each taxon
    Homonyms make life more complex
    Some names dissapear with time from use, but still have information attached
    There is no comperhensive index of scientific names for published docs

If binomial nomenclature will be abandoned, it is important to map it to future system.

### 2.1 Global Names, History

Started in 2007 by GBIF and EOL, had several nomina meetings.

The Ultimate idea -- connect names to data about names (Global Names Index)
We are not there yet, but intermediate steps are also generally useful.

Names attach on 3 levels: lexical, nomenclatural, taxonomical

GN reconciles names on lexical level, tries to resolve on taxonomical level.

First grant -- proof of concept, functional but slow tools created

Second grant -- production, better quality and very fast tools created

GN created many tools in Ruby at first, and than in Go.

We support "legacy" Ruby projects too, because they are used in by others in Ruby.

Three major state of the art components are GNparser, GNfinder, GNverifier.

GN is an infrustructure project, now it has stable backing from SFG

Hoewer to make a new leap in quality we need this grant.

The main scope of this grant: improving name-finding.

## 3. Challenges and Implementation

There are 2.5 mil species currently accepted

There are more nomenclatural events, even more name-strings.

Inspite of lexical variations we should be able to find, and reconcile names.



Computers allow automatic analysis of texts, and PLAZI uses structures of text.

However older texts have no common structure, gnfinder can find names.

Challenges in name finding

    Huge volume
    OCR problems
    Physical state of pages
    Names get abandoned
    Abbreviated names
    Ambiguous names

1rst is solved, others need work.

