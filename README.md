# Evaluation of structures of transmembrane proteins predicted by AlphaFold2

##Steps of evaluation

1. Download structures from EBI
   >wget -c -q 'https://ftp.ebi.ac.uk/pub/databases/alphafold/UP000005640_9606_HUMAN.tar'

2. untar it
   >tar -xvf UP000005640_9606_HUMAN.tar

3. run TMDET software on all structures (see 10.1093/bioinformatics/bth340 and 10.1093/bioinformatics/bti121)(available in https://tmdet.enzim.hu)
   >Results are stored in tmdet dir

4. run CCTOP software (with tmFilter option) on all sequences (see doi.org/10.1093/nar/gkv451) (available in https://cctop.enzim.ttk.mta.hu)
   >Results are stored in cctop dir

5. get topologies from each corresponding cctop and tmdet file if cctop predicts transmembrane protein (transmembrane="yes")
   >Results are stored in results.csv 

   >columns are 
   * id, 
   * number of tm helices predicted by cctop,
   * number of tm helices determined by tmdet,
   * number of matching tm helices,
   * reliability of cctop prediction,
   * topology predicted by cctop (alphabets mean tm helices, hyphens extramembrane resions),
   * topology determined by tmdet (alphabets mean tm helices, hyphens extramembrane resions),
  
6. count perfect matchings (all tm helices match in cctop and tmdet) and non matched topologies (one or more tm helices does not aligned in cctop and tmdet) in results.cs
   ### Perfect topologies
   | \# of tm helices | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 |
   |-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
   | \# of proteins | 716 | 165 | 43 | 281 | 30 | 119 | 740 | 39 | 25 | 56 | 31 | 157 | 12 | 16 | 1 | 2 | 7 |


   ### Non matching topologies
   | | \# tm helices in tmdet | 1 | 2 | 3 |4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |  13 | 14 | 15 | 16 | 17 | 18 | 19 |
   |-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
   | \# tm helices in cctop | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
   | | 1 | 796 | 99 | 623 | 140 | 43 | 16 | 18 | 4 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
   | | 2 | 164 | 72 | 46 | 63 | 27 | 8 | 5 | 4 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
   | | 3 | 38 | 21 | 27 | 3 | 45 | 10 | 9 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
   | | 4 | 21 | 5 | 8 | 15 | 8 | 47 | 19 | 12 | 7 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
   | | 5 | 16 | 0 | 2 | 4 | 12 | 1 | 16 | 8 | 2 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
   | | 6 | 7 | 0 | 1 | 3 | 16 | 13 | 18 | 23 | 26 | 7 | 3 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
   | | 7 | 10 | 0 | 1 | 0 | 4 | 7 | 41 | 11 | 70 | 14 | 2 | 6 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
   | | 8 | 1 | 0 | 0 | 1 | 0 | 1 | 6 | 15 | 16 | 14 | 15 | 4 | 2 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
   | | 9 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | 3 | 7 | 7 | 12 | 6 | 2 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
   | | 10 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 10 | 10 | 7 | 7 | 11 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
   | | 11 | 2 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 3 | 13 | 4 | 3 | 3 | 5 | 1 | 0 | 0 | 0 | 0 |
   | | 12 | 1 | 0 | 0 | 0 | 0 | 0 | 2 | 0 | 2 | 7 | 8 | 18 | 13 | 12 | 14 | 1 | 1 | 0 | 0 | 1 | 
   | | 13 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 4 | 4 | 1 | 2 | 1 | 0 | 0 | 0 | 0 | 
   | | 14 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 5 | 1 | 2 | 0 | 1 | 0 | 0 | 0 | 
   | | 15 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | 2 | 0 | 1 | 0 | 0 | 0 | 
   | | 16 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 1 | 
   | | 17 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 
   | | 18 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 
   | | 19 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |


