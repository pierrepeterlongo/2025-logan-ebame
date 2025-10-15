# Part C — Find alignments between Logan Search results and the query using BLAST

As presented in Part B, the Logan-Search interface enables to obtain a blast alignment between you query and the contigs or unitigs from **one** accession identifier. In case you want to perform a blast alignment between your query and **all** the contigs or unitigs from **all** or at least a subset of the accessions that were retrieved by Logan-Search, you can follow the steps below.

## Step 1: Clone the https://github.com/pierrepeterlongo/blast_logan_search_results repository

```bash
git clone https://github.com/pierrepeterlongo/blast_logan_search_results
```

## Step 2: Install the dependencies

Follow the instructions in the README.md file of the repository to install the dependencies.

Dependencies are: 
- blast
- biopython
- back_to_sequences

## Step 3: Get an accession list of interest
The README.md explains how to create an accession list of interest from Logan-Search results (either from the link provided in the Logan-Search email, or directly exporting a csv file from the Logan-Search interface).

## Step 4: Run the blast_logan_search_results.py script
Again everything is explained in the README.md file.
In the framework if this tutorial, we would have the following query file: `query.fasta`
```
>my_query
ATGATATTTTCAACTTTAGAGCATATATTACTTCATATATCCTTTTCGGTGGTTTCAATTGTAATTACAATTCAATTGATAACCTTGTTAGTCGATGAAATCATAGGACTATGTGATTCATCCGAAAAAGGGATGGTAGCGACTTTTTGCTGTATAACAGGATTATTAGTTACTCGTTGGATTTATTGGGGACATTTACCATTAAGTAATTTATATGAATCATTAATCTTTCTTTCATGGAGTTTCTCCATTATTTATATGGTTCCACTTTTTAAAAAATATAAAAACTATTTCAATGTAAACGTAATAACCGCGCCGAGTGTTAATTTTACCCAAGGTTTTGCTACTTCGGGTCTTTTAAATGAAATGAATCAATCCGAAATATTAGTACCCGCTCTTCAATCCCATTGGTTAATGATGCACGTAAGTATGATGGTATTGAGCTATGCAGCTCTTTTATGCGGATCATTATTATCACTAGCTCTTCTAGTCATTACATTTCGAAAATTCATAAGAATTCTTAGTCAAAGTAATAATTTAGTAAATGAGTCTTTTTCTTGGAGCGAGATTGAATACGTGAGAGAAAAAAAAAATATTTTACAAAAGACTTCTTTTCTTTCTTCTAGGAATTATTACAGGTTTCAATTGGTTCAACAATTGGATCTTTGGAGTTATCGTATTATTAGTCTAGGGTTTACCTTTTTAACCATAGGTATTCTTTCAGGCGCAGTATGGGCTAATGAAGCATGGGGATCCTATTGGAATTGGGATCCAAAGGAGACTTGGGCATTTATTACTTGGACCATATTTGCCATTTATTTACATACTAGAACAAATAAAAATTTTGAAAGCGTAAATTCCGCAATTGTAGCCTCGATAGGCTTTCTTATAATTTGGGTATGCTATTTTGGGGTTAATTTATTAGGAATAGGGTTGCATAGTTATGGTTTATTTCCTAATTGA
```

We would create the following accession list file: `accessions.txt` from the Logan-Search results `https://logan-search.org/api/download/kmviz-d1ad8763-b9e6-4813-9ea3-fe7039584d58`:
```bash
tail -n +2 kmviz-c21feaeb-4f33-4abc-b119-7db7bd47069b/query.tsv | awk '{print $1}' | tr -d "\"" > accessions.txt
```

Finally we would run the following command:
```bash
sh logan_blast.sh -a accessions.txt -q query.fa -l 10 
```




