# PhagePromoter

Get promoters of phage genomes

PhagePromoter is a python script that predicts promoter sequences in phage genomes, using machine learning models. Two different datasets were used to developed two models: the ANN model was built using a dataset with 26 features and 2400 examples (800 positives and 1600 negatives) and the SVM model was created using a dataset with 19 features and 3200 examples (800 positives and 2400 negatives). Each example represents a sequence of 65 base pairs of a phage genome. The positive examples correspond to phage sequences already identified as promoters.

**Inputs:**

- genome format: fasta vs genbank (default);
- genome file: acepts both GenBank and FASTA formats;
- both strands: yes or no (default). Allows the search only in the direct strand or in both DNA strands;
- threshold: represents the probability of the test sequence being a promoter (a float between 0 and 1, default=0.50). For example, if threshold=0.90, the model will only return predicted sequences with more than 90% probability of being a promoter. The larger the genome, the higher the threshold should be.
- Family: The family of the testing phage - Podoviridae (default), Siphoviridae or Myoviridae;
- Host: The host of the phage. The training dataset include the following hosts: Bacillus, Escherichia coli (default), Salmonella, Pseudomonas, Yersinia, Klebsiella, Pectobacterium, Morganella, Cronobacter, Staphylococcus, Streptococcus, Streptomyces, Lactococcus. If the testing phage has a different host, select the option 'other'.
- Phage type: The type of the phage, according to its lifecycle: virulent or temperate;

**Advanced options:**

Model: the user can choose which model to run: the SVM model (default) or the ANN model. The SVM model uses more negative data, so it will return less promoters but with a higher probability of being real promoters. However, it can fail to detect some of the real promoters. On the other hand, the ANN model will predict more promoters, so it can identify more real promoters, but it is expected to predict more false negatives.

**Outputs:**

This tool outputs two files: a FASTA file and a table in HTML, with the locations, sequence, score and type (recognized by host or phage RNAP) of the predicted promoters. In addition, the tool will output a GenBank file with the predicted promoters as features.

**Requirements:**

- Biopython
- Sklearn
- Numpy
- Pandas
