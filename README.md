# Portparser
This repository has all the files used in the paper "[Towards Portparser -- a highly accurate parsing system for Brazilian Portuguese following the Universal Dependencies framework](https://aclanthology.org/2024.propor-1.41.pdf)", including the proposed model that can be used to parser Portuguese texts.

# The Proposed Model
One of the main contributions of this paper is the proposed model to annotate Portuguese texts using UDPipe 2.

This model is available here and it is composed by the contents of the directory [Portparser_model](https://github.com/LuceleneL/Portparser/tree/main/Portparser_model).
To use this model with UDPipe 2 you need to:
- install UDPipe 2 in your machine - see the requirements and instructions at [UDPipe 2 page](https://ufal.mff.cuni.cz/udpipe/2);
- copy the directory `Portparser_model` to the same location of your UDPipe 2 code file (`udpipe2.py`);
- run UDPipe 2 over your CoNLL-U file (UDPipe 2 does not perform tokenization) with the command:
    - `python udpipe2.py Portparser_model --predict --predict_input your.conllu --predict_output your_predicted.conllu`

# Paper Summary
This paper presents a parsing model -- whose corresponding system is named Portparser -- for Brazilian Portuguese, which outperforms current systems for this language.
Following the Universal Dependencies (UD) framework, we build our model by using a manually annotated corpus ([Porttinari-base](https://sites.google.com/icmc.usp.br/poetisa/porttinari)) for training.
We test different parsing methods and explore parameter settings in order to propose a highly accurate model, encompassing not only the dependency annotation, but also the Part of Speech tagging and the identification of lemmas and the related morphological features.
Our experiments show that our best model achieves around 99\% accuracy for Part of Speech tagging, lemma, and morphological features, with around 95\% for dependency annotation, surpassing known systems for Portuguese by up to 7\% accuracy.
Furthermore, we conduct an error analysis of the proposed model to show the current limitations and challenges for future works.

## File Structure
The files are stored in the following directories:
- `Portparser_model` - the model proposed in the paper to be used with UDPipe 2;
- `datasets` - a directory holding all datasets used in the paper (`.conllu`), plus the generated word embeddings necessary for the BERTimbau experiments (`.npz files`), and the name of files inside this directory follow this naming structure:
    - `hXXXX_Y_ZZZZ.conllu` stands for the CoNLL-U file used for
        - a model with `XXXX` sentences (`8418`, `6314`, `4209`, or `2104`),
        - the random model numbered `Y` (`0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, or `9`), and
        - corresponding to the set `ZZZZ` (`train`, `dev`, or `test`).
        For instance the file `h8418_3_test.conllu` correspond to a model taken from the corpus with 8,418 sentences, it is the random version 3, and it is the test set of the experiments.
    - `hXXXX_Y_ZZZZ.npz` is the word embeddings for bert-base-portuguese-cased (BERTimbau) * corresponding to the `.conllu` file with the same name. Note that the embeddings are only needed for the `8418` versions of the `train` and `dev` sets.

\* In the paper, the text mentions bert-large-portuguese-cased, but it should state bert-base-portuguese-cased.

# Acknowledgments
This work was carried out at the Center for Artificial Intelligence of the University of São Paulo (C4AI - [http://c4ai.inova.usp.br/](http://c4ai.inova.usp.br/)), with support by the São Paulo Research Foundation (FAPESP grant #2019/07665-4) and by the IBM Corporation. The project was also supported by the Ministry of Science, Technology and Innovation, with resources of Law N. 8.248, of October 23, 1991, within the scope of PPI-SOFTEX, coordinated by Softex and published as Residence in TIC 13, DOU 01245.010222/2022-44.

