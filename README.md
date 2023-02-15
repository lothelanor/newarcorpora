# Tools for the Newar Annotated Corpora (NewAC)
!!!DISCLAIMER: WORK IN PROGRESS!!!

This repository will soon contain all scripts and links to the Newar Annotated Corpora. When using any part of this repo, please cite the relevant accompanying paper(s), abstracts of which can be found below:

For Newar HTR:
O'Neill, Alexander. (2022). OCR model for Pracalit for Sanskrit and Newar MSS 16th to 19th C., Ground Truth (Version 1) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.6967421

O’Neill, A. J., & Hill, N. (2022). Text Recognition for Nepalese Manuscripts in Pracalit Script.
Journal of Open Humanities Data, 8: 26, pp. 1–6. DOI:https://doi.org/10.5334/johd.90 

For Newar Segmentation and POS tagging:
Meelen, Marieke & O'Neill, Alexander (forth) 

## Tools & Dependencies

This repo currently presents tools to preprocess, segment and POS tag Newar texts, focused on subsequent linguistic tasks (but useful for any downstream NLP tasks). It features rule-based segmentation and uses the Memory-Based Tagger for POS tagging:

- [Memory-Based Tagger](https://github.com/LanguageMachines/mbt/) (for POS tagging)
- [Natural Language Toolkit](https://www.nltk.org/) (for Parsing)

NOTE that for POS tagging, we also tested neural-network based approaches, but results are still worse for Classical Tibetan, which is why we keep using the MBT for now. Preliminary tests with improved word embeddings indicate accuracies for BiLSTM-RNN taggers are likely to improve as soon as better embeddings are implemented (see Meelen, Roux & Hill 2021).

## Preprocessing 

To preprocess Old Tibetan and/or Wylie transcriptions:

`python preprocessing.py <my_directory>`

## Segmentation 

To segment transliterated Newar:

`python segNewar.py <my_directory>`

## POS tagging

To run the script:

`python pos-directory.py <my_directory>`

## Parsing & SentenceIDs

After POS tagging, phrase structure can be added with the parsing script. To parse and add automatically add SentenceIDs:

`python tibparse.py <my_POS-taggedtext.txt>`

Just like the UPenn-style historical corpora, constituency-based parsed .psd files can be queried with [CorpusSearch](http://corpussearch.sourceforge.net/) or XQuery after conversion to .psdx with, for example, [Cesax](http://erwinkomen.ruhosting.nl/software/Cesax/).

## Querying POS-tagged files

POS-tagged files can be queried with the dedicated queryPOS.py script, which allows for queries for 1-5 POS sequences as well as wildcards (using \*).

`python queryPOS.py <my_folder>`

It produces an output folder with text files listing all exact matches as well as matches in context for each input file in the folder. Total number of hits per file and for the entire folder are also calculated.

## Available Corpora

The current version of the Newar Annotated Corpus will soon be shared through Zenodo.
