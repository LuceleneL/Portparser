This repository has all the files used in the paper "Towards Portparser -- a highly accurate parsing system for Brazilian Portuguese following the Universal Dependencies framework".

These files in the following directories:
- Portparser_model - the model proposed in the paper to be used with UDPipe 2;
- datasets - a directory holding all datasets used in the paper (.conllu), plus the generated word embeddings necessary for the BERTimbau experiments (.npz files), and the name of files inside this directory follow this naming structure:
    - hXXXX_Y_ZZZZ.conllu stands for the CoNLL-U file used for
        - a model with XXXX sentences ("8418", "6314", "4209", or "2104"),
        - the random model numbered Y ("0", "1", "2", "3", "4", "5", "6", "7", "8", or "9"), and
        - corresponding to the set ZZZZ ("train", "dev", or "test").
        For instance the file "h8418_3_test.conllu" correspond to a model taken from the corpus with 8,418 sentences, it is the random version 3, and it is the test set of the experiments.
    - hXXXX_Y_ZZZZ.npz is the word embeddings for bert-large-portuguese-cased (BERTimbau) corresponding to the .conllu file with the same name. Note that the embeddings are only needed for the "8418" versions of the train and dev sets.

