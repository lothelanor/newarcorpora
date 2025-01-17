# Tools for the Diachronic Annotated Corpus of Newar (DACON)
!!!DISCLAIMER: WORK IN PROGRESS!!!

This repository will soon contain all scripts and links to the Diachronic Annotated Corpus of Newar (DACON), deposited on [Zenodo](https://zenodo.org/records/12887386). When using any part of this repo, please cite the relevant accompanying paper(s):

For Newar HTR:
O'Neill, Alexander. (2022). OCR model for Pracalit for Sanskrit and Newar MSS 16th to 19th C., Ground Truth (Version 1) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.6967421

O’Neill, A. J., & Hill, N. (2022). Text Recognition for Nepalese Manuscripts in Pracalit Script.
Journal of Open Humanities Data, 8: 26, pp. 1–6. DOI:https://doi.org/10.5334/johd.90 

For Newar Segmentation and POS tagging:
O'Neill, Alexander and Meelen, Marieke (2024). The Diachronic Annotated Corpus of Newar
from Manuscript to Morphosyntax. in Cahier de Linguistique Asie Orientale: East Asian Languages and Linguistics. pp.

Detailed annotation manuals are available for each step in the workflow:

Meelen, M., & O'Neill, A. (2024). Classical Newar Annotation Manual: Part I: Preprocessing. Zenodo. https://doi.org/10.5281/zenodo.13117923

O'Neill, A., & Meelen, M. (2024). Classical Newar Annotation Manual: Part II: Segmentation and Part-of-Speech Tagging. Zenodo. https://doi.org/10.5281/zenodo.13117962

## Tools & Dependencies

This repo currently presents tools to preprocess, segment and POS tag Newar texts, focused on subsequent linguistic tasks (but useful for any downstream NLP tasks). It features rule-based segmentation and uses the Memory-Based Tagger for POS tagging:

- [Memory-Based Tagger](https://github.com/LanguageMachines/mbt/) (for POS tagging)
- [Natural Language Toolkit](https://www.nltk.org/) (for Parsing)

Note that the Memory-Based Tagger has undergone an update and can now be easily installed with brew:

```
brew install timbl
brew install mbtagger
```
Using this new version means a slightly different settings file is required. This new version is now the default in the Conf files, but for those using the older version of the MBT, the old Conf files can still be found in the `Old' folder.

## Getting Started 

The following instructions work in the Mac terminal if the right dependencies are installed, but could be tranferred to any linux system too:

Simply clone and cd to the repo:
```sh
git clone newarcorpora
cd newarcorpora
```

## Segmentation 

To segment transliterated Newar:

`python NewarSeg.py <my_directory>`

## POS tagging

POS tag a single plain text file and write to 'my-file_tagged.txt' with the [TiMBL / MBT](https://languagemachines.github.io/mbt/):
```sh
Mbt -t my-file.txt -s /conf/clasnew20k_15Nov23_train.txt.settings > 'my-file_tagged.txt'
```

## Parsing & SentenceIDs

After POS tagging, phrase structure can be added with the parsing script. To parse and add automatically add SentenceIDs, run the following script:

```
tba
```

Just like the UPenn-style historical corpora, constituency-based parsed .psd files can be queried with [CorpusSearch](http://corpussearch.sourceforge.net/) or XQuery after conversion to .psdx with, for example, [Cesax](http://erwinkomen.ruhosting.nl/software/Cesax/).

## Querying POS-tagged files

POS-tagged files can be queried with the dedicated queryPOS.py script, which allows for queries for 1-5 POS sequences as well as wildcards (using \*).

`python queryPOS.py <my_folder>`

It produces an output folder with text files listing all exact matches as well as matches in context for each input file in the folder. Total number of hits per file and for the entire folder are also calculated.

## Available Corpora

The current version of the Diachronic Annotated Corpus of Newar (DACON) can be found on [Zenodo](https://zenodo.org/records/12887386)
