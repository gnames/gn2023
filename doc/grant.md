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
We do hope, that introduction of specifically trained Large Language Models (LLM) will allow the tool to receive a massive usability gain.

Presently, this tool relies exclusively on data from BHL, but we aspire to expand it to encompass texts aggregated in HathiTrust [Ref], a massive repository of published literature.
This expansion would extend "taxonomic intelligence" searches to several million books. The improvements outlined in sections 1.1, 1.2, and 1.3 will provide a solid foundation for this ambitious project.

