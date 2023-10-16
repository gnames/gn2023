---
title: Global Names 2023
author: Dmitry Mozzherin
date: 2023-03-10
geometry: left=2cm,right=2cm,top=2cm,bottom=2cm
mainfont: DejaVuSerif.ttf
mainfontoptions:
- BoldFont=DejaVuSerif-Bold.ttf
- ItalicFont=DejaVuSerif-Italic.ttf
- BoldItalicFont=DejaVuSerif-BoldItalic.ttf
sansfont: DejaVuSans.ttf
monofont: DejaVuSansMono.ttf
output: pdf_document
---

1. Vision

Biodiversity data is now unthinkable without binomial nomenclature.
The nomenclature adopted almost 275 years ago by Carl Linnaeus provides one of the most long-lived and universally accepted identifiers in science.
*Parsing*, *detecting* and *resolving* scientific names are crucial functionalities for scientific and governmental agencies, researchers, policymakers, when they deal with large-scale biodiversity data.
Global Names Architecture (GNA) [Ref] initiative was created in part to provide such functionalities, and had been offering the corresponding services since 2011.
These GNA services and applications had been developed with the help of two NSF grants and went so far through two stages.
The first stage funded by ABI Innovation [Ref] created a proof of concept, showing that scientific names' parsing, detecting and resolving can be implemented on a global scale.
The resulting products had been rather slow but already usable.
For example, Arctos [Ref] and Biodiversity Heritage Library (BHL) [Ref] based their name finding/name reconciliation on GNA.
The second stage funded by ABI Development [Ref] concentrated on achieving production level in speed and quality of the GNA tools.
As a result, it became possible to index names appearing on all 60 million pages of Biodiversity Heritage Library (BHL) in only 12 hours on a laptop.
To further test the limits of new capabilities we cooperated with HathiTrust [Ref] consortium, and ran name-finding algorithms against 6 billion pages of their corpus.
We were able to finish the job in 9 hours.
During the second stage GNA project was also lucky to receive a long-term funding via the Species File Group (SFG) [Ref] endowment.
The SFG funding provides resources for hardware and software maintenance, ensuring longevity and high performance of the GNA online services.
However, we see ways to dramatically improve usefulness of the GNA tools, especially name discovery, and we solicit funding for these purposes.

According to our experience, we estimate that users of name-finding still miss about 25% of names due to abbreviation, false positives, non-conventional capitalization and other problems.
Many of these problems can be solved by traditional means, as well as by the fast-growing capabilities of the Artificial Intelligence approach.
The Artificial Intelligence (AI) revolution provides methods and tools unthinkable just 10 years ago.
This proposal aims to develop additional "conventional" algorithms as well as to seize the opportunity of this unprecedented AI progress to dramatically enhance GNA tools, especially in the area of the scientific names' detection in literature.

We propose further developments in the following areas:

1.1. Dramatically improve the quality of the scientific names' detection.

Biodiversity Heritage Library (BHL) uses BHLindex [Ref] to create their index of scientific names.
The index covers 60 million pages of text and consists of 12 million name-strings, 250 million of their occurrences.
Using previous round of funding we were able to speed up the BHL index creation process more than 100-fold -- from 40 days on 4 high-end servers to 7 hours on a laptop.
We discovered that about 25% of names, while detected, cannot be put into names index.
There is also about 50 million name occurrences that are not detected due to OCR errors.

1.1.1 Abbreviated names.

About 20% of names in BHL are abbreviated; their genus is shortened to 1-3 letters.
Such names cannot be easily reconciled and expanded to full genus and added
to the names' index, because it would create significant amount of false positives.
We want to develop algorithms which will use statistical and natural language processing approaches to expand abbreviations accurately and reliably.

1.1.2. Elimination of most false positives.

Quite significant number of generic names have the same spelling as 'normal' words, especially in text written in Latin, or Romanic languages.
On one side, it creates false positives, with falsely detected names.
On the another side, trying to reduce the number of false positives, real names are sometimes removed.
We plan to develop heuristic and machine learning algorithms to mostly eliminate false positives.
It will allow us to remove the heuristic "ambiguous words filters" and decrease the amount of false negatives.

1.1.3. Detection of names masked by OCR errors.

OCR quality improved quite significantly recently, however, the quantity of OCR errors is still very high.
By our estimations about 15% of names in BHL cannot be discovered by current algorithms as a result of these errors.
Previous attempts to discover such names using n-gram analysis found 70 million names occurrences, however large percentage of these names are false positives.
We plan to apply methods developed in section 1.1.2 to n-gram analysis results and near all such false positives.
We also want to incorporate n-gram or similar approaches to name-finding, and use it for newly added, or re-OCRed manuscripts.

1.3. Detection of vernacular names with high precision.
Detection algorithms currently do not include vernacular names because they are even more ambiguous than scientific names, which generates more false positives.
Using algorithms developed for 1.1.2., we will be able to remove false positives from vernacular names occurrences.
This will make it possible to have reliable indices of vernacular names and make services like BHL more accessible for laymen and citizen scientists.

1.4. Customizable GNverifier data import.

GNverifier tool compares an input of tentative scientific names with the data from hundreds of sources and uses multistage sophisticated algorithms to find suitable matches.
Using the last round of funding we made an installation of most GNA products  on a local computer very approachable.
However, installation and usage of GNverifier, a name reconciliation/resolution tool is more complex due to its large database containing names from more than 150 data-sources.
We would like to make it possible for users, who want to run GNverifier locally, to be able to install only data-sources they need (for example only fungal datasets).
We want to create a standard automatic repository of data from hundreds of data-sources which can be used for GNverifier as well as other purposes.
Such a repository will be an experimental hub for biodiversity data.

1.5. A prototype of Global Name Index.

Adding a "taxonomic intelligence" to names data is very beneficial.
An information about a biological taxon often can be accessed not by one, but by multiple scientific names.
We are developing a tool that allows to expand search from one name to all known nomenclatural synonyms of a taxon, find a name's original description, discover books about a particular higher taxon, classify texts by their taxonomic context.
Currently, this tool uses only data from BHL. We want to expand it to texts aggregated in HathiTrust a massive aggregator of published literature.
It would bring "taxonomic intelligence" search to several million books.
Improvements, described in 1.1, 1.2, 1.3. 1.4., will build a solid basis for such project.

2. Background and Prerequisites

In the second half of the eighteenth century, naturalists accepted the Linnaean approach to nomenclature.
The emergence of a single unified and simplified nomenclatural system has obvious benefits.
For the last 275 years it has given us an unprecedented ability to point with high precision to species of interest.
It also has given experts around the world a common “biodiversity language”.

Nomenclatural rules went through series of modifications and standardization procedures "partitioning" nomenclature into 4 major codes.

* International Code of Zoological Nomenclature [Ref]
* International Code of Nomenclature for algae, fungi, and plants [Ref]
* International Code of Nomenclature for Cultivated Plants [Ref]
* International Code of Nomenclature of Prokaryotes [Ref]

All of these Codes follow common rules of binomial nomenclature, albeit differ in details.
Historical changes to common nomenclatural practices create some additional challenges.
However, the differences are small enough to allow development of generic rules for parsing, detection and resolution of all names created according to the Codes.

Another major nomenclatural code, The International Code of Virus Classification and Nomenclature [Ref] does not follow rules of binomial nomencature and is out of scope of this proposal.

It is quite possible, that eventually binomial nomenclature will lose its dominance, and other approaches to nomenclature will replace it.
If it happens, mapping binomial names to new system will be of crucial importance.
It would allow to continue the usage of gigantic amount of data and research accumulated during the last several hundred of years.
Some of such data is impossible to repeat due to a large amount of extinctions and modifications in the living space of taxa.

Advents in computer science allow automatic analysis of texts with extraction of the data of interest.
TODO: PLAZI and other similar approaches.
However, most of the older texts aggregated in BHL or HathyTrust are not structured consistently and algorithms of scientific names detection are the best tool for biodiversity information mining.

Found scientific names may serve as pieces of a jigsaw puzzle, allowing to narrow the search for other information, such as original nomenclatural descriptions, geographical locations, names of biologists, important illustrations.

Scientific names detection in digitized texts has several challenges:

1. The quality of Optical Character Recognition (OCR).
2. The level of preservation of the physical pages.
3. Massive amount of the digitized material
4. Detection and resolution of historical names lost from scientific circulation
5. Detection and resolution of abbreviated names
6. Detection and resolution of ambivalent names

Challenges 1 and 2 are already partially addressed by Global Names algorithms.
Continuous advents in OCR quality also helps to address challenges 1 and 2.
Current speed of GNA tools is more than sufficient to solve the 3d challenge.
We want to address challenges 4-6 by this proposal.

3. Global Names Architecture: History and Progress to Date

3.1. Background. GNA was conceived [Ref] in 2007 by Global Biodiversity Information Facility (GBIF) and Encyclopedia Of Life (EOL).
The underlying idea was to use names and associated information in expert sources to interconnect globally accessible information.
GNA would become a virtual layer for managing biodiversity data distributed across the Internet [Ref].
This makes GNA an infrastructure, rather than a research project.

GNA's conception involved an international consultative process with over 100 taxonomists, biodiversity informaticians, managers, and users of
biodiversity data in the form of 13 Nomina meetings [Ref].

TODO: Talk about 2M, 10M. 100M,

The initial GNA implementation was supported through an ABI Innovation grant [Ref].
Additional contributions are made by GBIF, EOL, Kew Gardens, PESI, and others.
The purpose of the ABI innovation award was to investigate if the GNA vision was achievable.
At the end of funding our combined team has produced a suite of proof of concept, prototype, and production-level services.
Most notably -- an online registry for zoological nomenclature ZooBank [Ref], nomenclatural events repository GNUB [3], name finding service GNRD [Ref], name reconciliation and resolution service GN Resolver [Ref], name index GNI [Ref], taxonomic editor GNITE [Ref], and a citation repository CiteBank [Ref].
This ABI Development grant would bring funds to push name finding, indexing and reconciliation services to a level of stable globally accessible services for the needs of Big Data Biology.

These original GNA services for names' parsing, detection and reconciliation, while useful, had significant shortcomings typical for prototype projects.
They did not process well a large amount of data, their installation was too complex; as a result their usage was limiting.

Resolution and reconciliation of scientific names had rate of 50 names a second,
which is not adequate for a large scale evaluations (BHL index would take 5 days to verify).
Parsing of scientific names had been too slow as well, requiring 1 day to go through all names in Encyclopedia of Life.
Creation of a scientific name index for Biodiversity Heritage Library's 50 million pages took 40 days while it was performed on four high-end servers priced at the time at $60,000.
Taking in account the cost of work and hardware, such indexing was done only once, and no bugs in name detection could be fixed later by subsequent runs.

The second round of funding by ABI Development [Ref] from NSF, allowed to address these shortcomings and dramatically increase the performance for every major functionality. This effort also received an ongoing financial support from SFG group providing stability required for an infrastructure project like Global Names.

We needed to find an approach which would not only make reimplemented programs fast, but also easy to install, having small memory footprint and able to be maintained by people specialized on the border of biology and informatics, but without a formal computer science education.
To achieve that we scanned dynamically evolving landscape of computer languages, gaining detailed experience in Java, Scala, Haskell, Elm, Go, Ruby and Python.
This approach allowed us to find an almost perfect language for our purposes: Go.
Go uses minimalistic approach in design, making it very simple to learn, making it ideal for academia where students, postdocs come and go [Ref].
It is created from the ground up for modern computers with many CPUs, which allows redirection of all computing power to our tasks.
Go compiles our code into a stand-alone files of 3-15 MB size, which makes them trivial to install.

Parsing of 20 million names using our 'prototype' parser would take more than 24 hours. GNparser is able to achieve the same job in less than 5 minutes on a modern computer.
Name reconciliation rate was improved from 50 names/s to 2000 names/s.
Detection of scientific names increased from 14 pages/s to 10,000 pages/s.
As a result, the creation of a scientific names index for Biodiversity Heritage Library shrank from 40 days to 7 hours, and the cost of hardware from $60,000 to $3000.

We developed many applications and libraries in Go [Ref] and Ruby [Ref] languages during the last 15 years.
All our code is released as Open Source under MIT public license.
We continue to actively maintain Ruby applications, because they are still used in Ruby-based projects.
These applications were published first time around 2008-2011 years.
According to RubyGems site [Ref] most popular of them (damerau-levenshtein, biodiversity, gni, dwca-archive, taxamatch) had been downloaded 2.5 million times and received 216 GitHub "stars" (a "star" is a way for GitHub users to express a "like" of a project).
As a control, our
Applications written in Go are more recent and were published first between 2019-2021 years.
There is no central repository similar to RubyGems for Go language, so we do not know how many times Go projects had been downloaded.
These, second generation products, received 102 GitHub "stars" so far.

GlobalNames is envisioned as a part of biodiversity informatics infrastructure and is used by such projects as Biodiversity Heritage Library, Encyclopedia of Life, Arctos, TaxonWorks, DINA, iNaturalist, HathiTrust, BioStor, Global Biotic Interactions  and others.
So often projects developed in academia have a short life-span, and disappear due to a lack of funds.
In 2015 Global Names projects described in this proposal received a stable monetary support from the SFG endowment providing equipment and a salary for one person.
However, to make a leap in quality we would require additional resources.

In this proposal we want to address problems that are best suited for machine learning, artificial intelligence techniques. We plant to study the landscape of fast-evolving machine learning techniques and pick ones that are best for achieving our goal -- a very fast high quality scientific name detection, that rivals a human ability to do such a task.

4. Challenges and Implementation

4.1. Scope and Overall Goals

We consider that the main purpose of GN is to accurately connect a name with data and metadata about a taxon.

We estimate that about 2.5 million species are currently described.
A "species taxon" is a circumscription of closely related organisms united by their morphology, behavior, procreation compatibility, similarities in DNA sequence, the area they occupied, the time period they live in.
For convenience researches assign a scientific name identifier to point to a particular taxon.

There are often many scientific names historically assigned to the same taxon.
They can be nomenclaturaly valid heterotypic or homotypic synonyms, names that were not validly published, etc.
The same scientific name can be written in different ways as well.
It can include authorship, year, contain abbreviations, different punctuation, misspellings.

We consider that 2.5 described species [Ref] are connected to approximately 10 million unique nomenclatural events and combinations, each with its own scientific name. In turn these are expressed in as many as 100 million unique name-strings (See Fig X).

GNA scope is lexical, meaning that it should be able to work with any of the name-strings, reconcile them into names, and then resolve names to taxons.
It should also be able to find information about a taxon in published literature, in spite of a variety of name-strings used for a taxon in different circumstances.

Reconciliation, finding a lexical group of a name quite often can be solved by name parsing.
Parsing allows determining the semantic elements of a name.
These elements are normalized and can be matched to other names.
However, to find a lexical group for abbreviated names, or names that cannot be easily parsed, additional methods are required.

Resolution, or finding a taxon associated with a name, can be done by using a taxonomic database like the Catalogue of Life.
In addition, a name in a text allows finding rich information about its taxon.
For this purpose the challenge is detection of names in large volumes of text.

Quite often taxon concepts change with time, with their circumscription expanding, shrinking, traversing. Global Names does not currently address names/taxons relationship with such resolution and granularity.

The global scale of the GN area of interest is a crucial challenge. GN should be able to deal with tens of millions of name-strings, thousands of data-sources, billions of pages.

To summarize, GN has to address three major challenges.
Discovery of name-strings in billions of digitized pages of texts.
Reconciliation of 100 million name-strings to 10 million lexical groups.
Resolution of 10 million lexical groups to 2 million taxonomic groups.

4.2 Discovery of name-strings in texts
4.2.1. Current Status

Discovery of name-strings in texts allows to create a name-index.
This, in turn, allows to connect a specific taxon to the text.

Current implementation of name-finding is written in Go language and can be compiled for a variety platforms [Ref].
We provide it for MS Windows, Mac OS X and Linux.
It can work with a large variety of documents, such as plain text, MS Word documents, MS Excel spreadsheets, PDFs, images in a variety formats.
After compilation, it is a 15 MB stand-alone binary, that is used without any additional external files or libraries.
Document conversion and verification of scientific names requires an internet connection.

Internally, it tokenizes a document into words, taking in account cases where a word is split between different lines or pages.
Then it traverses the tokens, marking capitalized words as a possible start of a scientific name.
At such point it performs analysis of subsequent words, trying to find if a name exists at this location.
Two major algorithms are used for detection.
One is based on dictionary approach, where words are compared with known words from scientific names.
Another uses Naive Bayes algorithm, where putative name-strings are checked against pre-trained set of features, and are assigned a probability of being similar to a scientific name.
Some words are ambiguous and can have common and scientific meaning.
For example 'Cancer', 'America', 'Casus belli' can be a scientific name.
Ambiguous words are treated with caution.
Without understanding the context, such words often create false positive or false negative results.
Abbreviated names are also detected and saved in the results.
Names that do not follow recent nomenclatural conventions are often detected only partially.
For example, for names with capitalized specific epithet only genus part is registered.

It would also be beneficial to discover occurrences of vernacular names in texts.
However, the large amount of false positives makes such feature currently impractical.

The last, optional stage of name-detection, is a name verification. This step allows weeding out name-like strings.
However, abbreviated names currently cannot be disambiguated and reconciled, which makes them unavailable in name-indices.


4.2.2 Challenges

There are several challenges in name-finding.

1. The quality of OCR, unknown names

Mistakes in character recognition are currently wide-spread.
As a result we are missing significant amount of scientific names due to OCR errors.
Also, not all names used earlier are still in circulation.
For example, Sherborn's Index Animalium contains 24% of names that are unique for this source [Ref] and do not appear in any other data source in GNverifier.

2. Abbreviated names.

Abbreviated scientific names are very common in biological literature.
Most of the time such names are preceded by a spelled out genus name.
In practice, as we found out, we cannot rely on the closest detected genus name which starts from the same letter as abbreviated names.
OCR error, obscure position of genus name in the text, partial detection of unrelated species (only genus detected) can create huge amount of false positives.

3. Ambiguous names.

Many scientific names are also "normal" words in European languages.
For example, "Cafeteria", "Cancer", "Laura", "America", "La cucaracha" can be scientific names.
Latin, and languages derived from Latin generate especially large number of such 4false positives.

4. Special cases.

Quite often species epithets are capitalized. It can happen because they are derived from a name of a person, geographical entity or other similar reason. Nomenclatural recommendations about such capitalization are evolving with time.Capitalization of specific epithets is also common for horticultural and other not strictly scientific literature.
Sometimes large indices of names change the order of genus and species.
It is especially common for name indices in the end of a publication.
Due to OCR errors such lists might be the only chance to detect a name.

5. Vernacular names detection.

Scientific names are significantly more reliable identifiers to point to an information about a taxon.
However, vernacular names, such as "Eastern Towhee", "喜鹊", "Бурый медведь" also point to potentially valuable information, especially in data collected by citizen scientists.
Indexing vernacular names would also be important to make sources like Biodiversity Heritage Library more accessible to laymen.
Due to much higher amount of false positives than for scientific names we currently do not detect vernacular names.

Solving these challenges would create a system approaching by quality to a well-educated biologist, but a billion times faster than human.

4.2.3 Implementation

1. The quality of OCR.

Machine learning models can be trained to do named entity recognition (NER) in texts of poor quality.
Such approach would be able to detect names by using semantic context and pattern similarity for strings with significant amount of misspellings.
We will be investigating what tools can do it with most precision and performance.

Steady increase in OCR quality might significantly decrease the number of errors in digitized text and greatly diminish the problems such errors generate.

2. Abbreviated names
