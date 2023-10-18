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

Biodiversity data now relies heavily on binomial nomenclature, a system adopted and popularized by Carl Linnaeus nearly 275 years ago.
Binomial nomenclature provides us some of the most enduring and universally accepted scientific identifiers: taxon names.

The Global Names Architecture (GNA/GN) initiative was conceived in 2007 [Ref], to provide tools and services to work with scientific names.
To achieve the goal three main categories of tools had been developed, aiming to *detect*, *parse* and *reconcile* scientific names.

This grant proposal is concentrated on perfecting names' detection in texts on
a very large scale.
Such advanced name-detection together with emerging AI technologies would allow creating unprecedented insight into biodiversity literature.

-------------------------------------------------------------------------------

The ability to *parse*, *detect*, and *reconcile* scientific names is crucial for scientific and governmental agencies, researchers, and policymakers when handling extensive biodiversity data.

*Parsing Service*: Parsing involves the dissection of a name into its semantic components, namely the name itself, authorship, and year, as well as the normalization of names for subsequent matching [Ref].

*Detection Service*: Detection encompasses the identification of scientific names within a variety of content types, including plain texts, PDFs, Word Processor documents, and images [Ref].

*Reconciliation/Resolution Service*: Reconciliation is the process of matching lexical variants of names, while resolution involves determining whether a name is accepted for a taxon or is categorized as a synonym [Ref].

The GNA tools and services for *parsing*, *detection* and *reconciliation* of scientific names were released from the get-go under Open Source licenses and continue to be completely free and open.

Global Names' parsing, detection, and reconciliation tools have now reached high levels of speed and quality, making them capable of operating on an extensive scale.
However, one critical area in need of substantial improvement is name detection.
Our collaboration with the Biodiversity Heritage Library (BHL) project serves as an excellent platform for advancing name detection using their extensive corpus of 60 million pages.
Once these algorithms are refined, our goal is to broaden their application to cover all available digitized and digital texts.

Based on our experience, we estimate that BHL users still miss approximately 25% of names due to various issues, including genus abbreviations, false positives, non-conventional capitalization, optical character recognition (OCR) errors, and other related challenges.
Many of these problems can be addressed using conventional methods, as well as by harnessing the rapidly advancing capabilities of Artificial Intelligence (AI).
The AI revolution offers methods and tools that were unimaginable just a decade ago.

We are seeking funding to further develop Global Names tools in the following areas:

1.1 Significantly Improving Scientific Name Detection

The Biodiversity Heritage Library is a global project that aggregates biodiversity literature.
The scientific name index within BHL enables researchers to quickly locate publications related to their taxonomic groups of interest.
This index encompasses an impressive 60 million pages of text, containing 12 million name-strings with 250 million occurrences.
It is generated using the BHLindex [Ref] application developed by GN.

Thanks to previous funding, we have managed to accelerate the creation of the BHL index by over 100-fold, reducing the processing time from 40 days on four high-end servers to just 12 hours on a laptop.
However, around 25% of scientific names could not be included in the name index.

The BHL corpus serves as an ideal testing ground for enhancing the name-finding process.
Users of BHL will also benefit from these improvements and will have the opportunity to provide feedback if anything is missing.
When these new tools are ready, they will enable us to apply these enhancements on a global scale and create a comprehensive Global Name Index.
It would also allow anybody to use GNfinder tool to extract scientific names nearly perfectly from documents.

We are planning to address the following issues in name detection:

1.1.1 Abbreviated Names Expansion.

About 20% of the names in the BHL are abbreviated, typically involving the truncation of the genus to 1-3 letters.
The challenge lies in reconciling and expanding these abbreviations accurately without introducing a significant number of false positives.
Our proposed solution involves developing algorithms that leverage statistical and natural language processing approaches to expand abbreviations with precision and reliability.
 
1.1.2 Dramatic Reduction of False Positives.

A notable number of generic names share identical spellings with common words, particularly in texts composed in Latin or Romance languages.
This creates both false positives, wherein names are incorrectly detected, and the removal of real names in the effort to diminish false positives.
We intend to develop heuristic and machine learning algorithms to substantially reduce false positives.
This will allow us to eliminate "ambiguous words filters", which in turn, will decrease false negatives.

1.1.3 Detection of Names Concealed by OCR Errors.

While OCR quality has seen considerable improvements, the prevalence of OCR errors remains high.
We estimate that roughly 15% of name occurrences in the BHL remain undiscovered by our name-detection tools due to these errors.
Previous attempts by uBio [Ref] project employing n-gram analysis identified 70 million name occurrences not found by BHLindex.
A significant portion of these are false positives.

Our strategy includes implementing the techniques established in section 1.1.2 to refine n-gram analysis results, effectively diminishing false positives.
We also intend to integrate n-gram or similar approaches into BHLindex.
This enhancement will enable us to overcome OCR errors and human inconsistencies
For instance, it will facilitate the identification of names that conform to currently outdated capitalization rules.

1.2 Detection of Vernacular Names

Existing detection algorithms do not encompass vernacular names, which are often more ambiguous than scientific names and thus generate a higher rate of false positives.
Leveraging the algorithms developed in 1.1.2, we will mitigate false positives within vernacular names occurrences, making it feasible to provide dependable indices of vernacular names.
This enhancement will improve accessibility for laymen and citizen scientists using services like the BHL.

1.3 A prototype of Global Name Index.

Enhancing names data with "taxonomic intelligence" can be highly advantageous, as information about a biological taxon can be accessible through multiple scientific names (currently accepted taxon name and synonyms).
We are in the process of developing a tool that exposes users to augmented name index.
Such index broadens their search from one name to all known nomenclatural synonyms of a taxon, provides known links to original description text, uncovers the original description of a name, identify books about a specific higher taxon, and categorize texts based on their taxonomic context [Ref].
We do hope, that introduction of specifically trained Large Language Models (LLM)will allow the tool to receive a massive usability gain.

Presently, this tool relies exclusively on data from BHL, but we aspire to expand it to encompass texts aggregated in HathiTrust [Ref], a massive repository of published literature.
This expansion would extend "taxonomic intelligence" searches to several million books. The improvements outlined in sections 1.1, 1.2, and 1.3 will provide a solid foundation for this ambitious project.

When this tool reaches proof-of-concept phase for BHL, we will plan to expand it to HathiTrust corpus.

2. Background and Prerequisites

In the latter part of the eighteenth century, naturalists embraced the Linnaean approach to nomenclature.
The advent of a unified and simplified nomenclatural system brought forth evident advantages.
Over the past 275 years, it has granted us an unparalleled ability to pinpoint species of interest with high precision.
Furthermore, it has equipped experts worldwide with a common "biodiversity language."

Nomenclatural rules underwent a series of alterations and standardization procedures, effectively "partitioning" nomenclature into four major codes:

* International Code of Zoological Nomenclature [Ref]
* International Code of Nomenclature for algae, fungi, and plants [Ref]
* International Code of Nomenclature for Cultivated Plants [Ref]
* International Code of Nomenclature of Prokaryotes [Ref]

All these Codes adhere to the fundamental principles of binomial nomenclature, albeit with some differences in the details.
Historical shifts in nomenclatural practices have presented certain additional challenges.
However, these distinctions are sufficiently minor to facilitate the development of generic rules for parsing, detecting, and resolving all names created in accordance with the Codes.

Another major nomenclatural code, The International Code of Virus Classification and Nomenclature [Ref] does not follow rules of binomial nomencature and is out of scope of this proposal.

It is conceivable that, in the future, binomial nomenclature may lose its preeminence, making room for alternative nomenclatural approaches, may be becoming a user-friendly nomenclatural system to underlying identifiers.
In such a scenario, the mapping of binomial names to a new system would be of paramount significance.
This transition would enable the continued utilization of the vast body of data and research accumulated over the past several centuries.
Much of this data is irreplaceable due to species extinctions and transformations in the habitats.

2.1 Global Names Architecture: History and Progress to Date

The concept of the Global Names Architecture (GNA) was conceived in 2007 through a collaborative effort between the Global Biodiversity Information Facility (GBIF) and the Encyclopedia of Life (EOL).
The fundamental idea behind GNA was to harness the names and related information found in expert sources to establish global connectivity within the realm of biodiversity data.
GNA was envisioned as a virtual layer designed to manage biodiversity data dispersed across the Internet, making it more of an infrastructure than a research project.

The inception of GNA involved an extensive international consultative process, with the active participation of over 100 taxonomists, biodiversity informaticians, managers, and users of biodiversity data. This consultative process took shape in the form of 13 Nomina meetings [Ref].

The domain of scientific names can be considered from three distinct perspectives: lexical, nomenclatural, and taxonomical.

1. Lexical View: This perspective encompasses approximately 100 million lexical variants of names.
There is no rigid standard for how a name should be rendered in a text. 
Sometimes scientific names are accompanied by authorship and year, while at other times, this information may be omitted.
Additionally, authors' names may be abbreviated, or be given for more than one part of a name.
Furthermore, names without authorship can exhibit differences, including distinct suffixes or alternate spelling variants for the genus.

2. Nomenclatural View: The nomenclatural perspective includes around 10 million nomenclatural acts, where a single act unites all the lexical variants of a name.
Each such act represents a factual registration of a name, the publication in which it was described, and the type specimen housed in a museum.
It's important to note that not all names have been properly registered.

3. Taxonomical View: This view comprises about 2.5-3 million records and consists of taxonomic hypotheses. These hypotheses may be widely accepted or reflect disagreements among taxonomists.
Nomenclatural events collectively form a scientific names "cloud" for each taxonomic opinion, with one of the names generally considered as the "currently accepted" term (referred to as "the Valid Name" in zoology and "the Correct Name" in Botany).
All other names in the cloud are classified as synonyms of various kind.
The name for a taxon is picked according to the rules of the corresponding Nomenclatural Code.

The GNA project endeavors to reconcile names on a lexical level.
Subsequently, it aims to resolve names to the taxonomical level if possible.
For resolution it uses taxonomic data-sources such as "Catalogue of Life [Ref]", AlgaeBase [Ref], Myriatrix [Ref] etc.

The initial implementation of GNA was supported by an ABI Innovation grant [Ref].
Additional contributions have been made by organizations such as GBIF, EOL, Kew Gardens, PESI, and others.
The primary objective of the ABI Innovation grant was to explore the feasibility of the GNA vision.
By the end of this funding period, our collaborative team successfully produced a suite of proof-of-concept, prototype, and production-level services.
Notably, these services include an online registry for zoological nomenclature known as ZooBank [Ref], a repository for nomenclatural events called GNUB [Ref], the name finding service GNRD [Ref], a name reconciliation and resolution service GN Resolver [Ref], the name index GNI [Ref], the taxonomic editor GNITE [Ref], and a citation repository named CiteBank [Ref].

The initial GNA services for names' parsing, detection, and reconciliation, although valuable, had notable limitations common to prototype projects.
They struggled to efficiently process substantial volumes of data, and their installation proved overly complex, thus constraining their practical use.

Resolution and reconciliation of scientific names operated at a rate of 50 names per second, which falls short of the requirements for large-scale assessments (for instance, verifying the BHL index would take five days).
Parsing scientific names also proved to be excessively slow, taking an entire day to process all the names in the Encyclopedia of Life.
Creating a scientific name index for the Biodiversity Heritage Library's 50 million pages required 40 days and the deployment of four high-end servers, with joined cost $60,000 at the time.
Considering the combined expenses of labor and hardware, such indexing could only be accomplished once, with no opportunity to rectify name detection errors in subsequent runs.

The second round of funding from ABI Development [Ref] via NSF enabled us to tackle these limitations.
Our objective was to identify an approach that not only improved the speed of our re-implemented programs but also made them easy to install, with a minimal memory footprint.
We aimed to ensure that individuals with expertise at the intersection of biology and informatics, even without formal computer science training, could maintain these programs.
To achieve this, we extensively explored various programming languages, including Java, Scala, Haskell, Elm, Go, Ruby, and Python.
This process led us to discover a nearly ideal language for our purposes: Go.
Go employs a minimalist design philosophy, making it highly approachable remarkably easy to learn, therefor suitable for academia, where students and postdocs come and go [Ref].
Moreover, it was purpose-built for modern, multi-CPU computers, enabling us to harness all available computing power for our tasks.
The compiled code in Go produces a stand-alone file ranging from 3 to 15 MB in size, making such files effortless to install.

For instance, while parsing 20 million names using our 'prototype' parser would take over 24 hours, Go-based GNparser accomplishes the same task in less than 5 minutes on a contemporary computer.
Name reconciliation rates improved from 50 names per second to 2000 names per second, and the detection of scientific names surged from 14 pages per second to 10,000 pages per second.
Consequently, the creation of a scientific names index for the Biodiversity Heritage Library was trimmed from 40 days to just 12 hours, and the hardware costs were reduced from $60,000 to $3,000.

Over the last 15 years, we've developed numerous applications and libraries in Go [Ref] and Ruby [Ref].
All our code is made available as open source under the MIT public license.
We actively maintain some Ruby applications, as they continue to be utilized in Ruby-based projects.
Many of these applications were first published between 2008 and 2011.
According to the RubyGems site [Ref], some of the most popular ones (such as damerau-levenshtein, biodiversity, gni, dwca-archive, taxamatch) have been downloaded 2.5 million times and have received 216 GitHub "stars" (a "star" is a way for GitHub users to express their appreciation for a project).
Our Go-based applications are more recent, having been first published between 2019 and 2021.
As there's no centralized repository like RubyGems for the Go language, we don't have statistics on the number of downloads.
These second-generation products have received 102 GitHub "stars" thus far.

The GNA applications ecosystem is build on 3 main projects: GNparser (name parsing), GNfinder (name detection), GNverifier (name reconciliation).
All 3 projects have a real-time code availability on GitHub. 
They are available as command line applications, web-applications, and provide have Application Programming Interface (API). GNverifier also implements popular Reconciliation Service API [Ref] used by OpenRefine [Ref]. Other higher level application use all three as Go libraries. 

GlobalNames is envisioned as an integral component of the biodiversity informatics infrastructure and is utilized by projects such as Biodiversity Heritage Library, Encyclopedia of Life, Arctos, TaxonWorks, DINA, iNaturalist, HathiTrust, BioStor, Global Biotic Interactions, and others.
It's a common scenario in academia for projects to have limited lifespans and eventually fade away due to insufficient funding.
In 2015, the Global Names projects outlined in this proposal obtained stable financial support from the Species File Group endowment, University of Illinois Champaign/Urbana), which provided essential equipment and a salary for one team member.
Nevertheless, to make a substantial leap in quality, we require additional resources.

In this proposal, we explore the development of innovative methods to significantly enhance the identification of scientific names within textual content. Our strategy involves a fusion of traditional techniques with machine learning and artificial intelligence approaches. Our ultimate objective is to attain scientific name detection of very high speed and quality, comparable to human accuracy in this domain.

3. Challenges and Implementation

3.1. Scope and Overall Goals

We consider that the main purpose of GNA tools is to accurately connect a name with data and metadata about a taxon.

We estimate that about 2.5 million species are currently accepted.
A "species taxon" is a circumscription of closely related organisms united by their morphology, behavior, procreation compatibility, similarities in DNA sequence, the area they occupied, the time period they live in.
For convenience researches assign a scientific name identifier to point to a particular taxon.

There are often many scientific names historically assigned to the same taxon.
They can be nomenclaturaly valid heterotypic or homotypic synonyms, names that were not validly published, etc.
The same scientific name can be written in different ways as well.
It can include authorship, year, annotations, contain abbreviations, different punctuation, misspellings.

We consider that 2.5 million described species [Ref] are connected to approximately 10 million unique nomenclatural events and combinations, each with its own scientific name. In turn these are expressed in as many as 100 million unique name-strings (See Fig X).

GNA scope is lexical, meaning that it should be able to work with any of the name-strings, reconcile them into names using name parser, and then resolve names to taxons.
It should also be able to find information about a taxon in published literature, in spite of a variety of name-strings used for a taxon in different circumstances.

Quite often taxon concepts change with time, with their circumscription expanding, shrinking, traversing. Global Names does not currently address names/taxons relationship with such resolution and granularity.

The global scale of the GN area of interest is a crucial challenge. GN should be able to deal with tens of millions of name-strings, thousands of data-sources, billions of pages.

To summarize, GN tools has to address three major challenges.
Discovery of name-strings in billions of digitized pages of texts.
Reconciliation of 100 million name-strings to 10 million lexical groups.
Resolution of 10 million lexical groups to 2.5 million taxonomic groups.

The scope of this grant proposal is a significant imporovement of name-strings
discovery.

3.2 Discovery of name-strings in texts
3.2.1. Current Status

Discovery of name-strings in texts allows to create a name-indices.
This, in turn, allows to connect taxons to the texts.

Current implementation of name-finding is written in Go language and is compiled for MS Windows, Mac OS X and Linux [Ref].
GNfinder can work with a large variety of documents, such as plain text, MS Word documents, MS Excel spreadsheets, PDFs, images in a variety formats.
After compilation, it is a 15 MB stand-alone binary, that is used without any additional external files or libraries.
The conversion of documents to plain text and verification of scientific names requires an internet connection.

Internally, GNfinder tokenizes a document into word-tokens, taking in account cases where a word is split between different lines or pages.
Then it traverses the tokens, it marks capitalized words as a possible start of a scientific name.
At such point it performs analysis of subsequent words, trying to find if a name exists at this location.
Two major algorithms are used for detection.
One is based on dictionary approach, where words are compared with known words from scientific names.
Another uses Naive Bayes algorithm, where putative name-strings are checked against pre-trained set of features, and are assigned a probability of being a scientific name.
Some words are ambiguous and can have common and biodiversity meaning.
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
For example, Sherborn's Index Animalium contains 33% of names that are unique for this source [Ref] and do not appear in any other data source in GNverifier.

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


























Advancements in computer science have empowered the automatic analysis of texts, enabling the extraction of pertinent data. The PLAZI project, for instance [Ref], has devised sophisticated algorithms to extract biological information by crafting templates for numerous biodiversity publications.

Nevertheless, many of the older texts aggregated in resources like BHL or HathyTrust lack consistent structure, making algorithms for scientific name detection to be better tools for mining biodiversity information.
Detected scientific names act as crucial pieces in the puzzle, facilitating the searching for additional details such as original nomenclatural descriptions, geographical locations, the identities of biologists, and essential illustrations.

The detection of scientific names within digitized texts presents several challenges:

1. The immense volume of digitized material.
2. The Optical Character Recognition (OCR) creates large number of mistakes.
3. The physical state of some pages is poor.
4. Many old names have fallen out of scientific circulation.
5. Resolving names with abbreviated genus is very error prone.
6. Significant amount of names consist of commonly used words.

We can consider the first challenge to be resolved, the speed of GNA tools surpasses now is more than enough to deal with any scale.
This proposal is geared toward addressing other 5 challenges.
The continual enhancement of OCR quality further aids in addressing these challenges.




The applications were developed with the support of two NSF grants and have progressed through two significant stages. 

The first stage, funded by ABI Innovation [Ref], created a proof of concept that demonstrated the feasibility of implementing global-scale scientific name parsing, detection, and reconciliation.
The resulting products, while somewhat sluggish, were already functional. 
Notably, projects like Arctos and the Biodiversity Heritage Library (BHL) based their reconciliation and name-finding processes on GNA.

The second stage, funded by ABI Development [Ref], focused on achieving production-level speed and quality for GNA tools.
As a result, it became possible to index names appearing on all 60 million pages of the Biodiversity Heritage Library (BHL) in just 12 hours on a laptop.
To further test the capabilities, we collaborated with the HathiTrust [Ref] consortium and applied name-finding algorithms to 6 billion pages of their corpus.
The HathiTrust's computer cluster managed to complete the task in 9 hours.
During this second stage, the GNA project also secured long-term funding from the Species File Group (SFG) [Ref] endowment, which provides resources for hardware and software maintenance, ensuring the longevity and high performance of GNA's online services.
