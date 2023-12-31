# about_scRNAseq_clustering
## Evaluating the limits of scRNAseq clustering 
Dimensionality reduction and clustering are closely intertwined in the analysis of single-cell data. Additionally, most clustering methods have concentrated on highly diverse datasets that encompass various cell types, such as PBMC. Nevertheless, there is limited information available regarding the assessment of performance of clustering in scRNAseq datasets characterized by subtle heterogeneity, such as cancer organoids.

## Benchmark datasets
Benchmarking datasets are essential to validate bioinformatics methodologies for analysing single-cell omics in oncology. Specifically we have built a dedicated dataset, ([*BE1*](https://www.singlecellomics.org/pages/tools/index#be1), [*GSE243665*](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE243665)), providing the basic material to build virtual tumor organoids. The dataset is made of 7 different lung cancer cell lines, eachone characterised by a different cancer driver genes:

-  PC9, 4492 sequenced cells (EGFR Del19, activating mutation, PMID: [*Simonetti et al. (2010)*](https://pubmed.ncbi.nlm.nih.gov/21167064/) 
-  A549, 6898 sequenced cells (KRAS p.G12S, growth and proliferation,  PMID: [*Yoon et al. (2010)*](https://pubmed.ncbi.nlm.nih.gov/20358631/) 
-  NCI-H596 (HTB178), 2965 sequenced cells (MET Del14 , enhanced protection from apoptosis and cellular migration PMID: [*Cerqua et al. (2022)*](https://pubmed.ncbi.nlm.nih.gov/35636967/) 
-  NCI-H1395 (CRL5868), 2673 sequenced cells (BRAF p.G469A, gain of function, resistant to all tested MEK +/− BRAF inhibitors, PMID: [*Negrao et al. (2020)*](https://pubmed.ncbi.nlm.nih.gov/32540409/)) 
-  DV90, 2998 sequenced cells (ERBB2 p.V842I, increases kinase activity, PMID: [*Boese et al. (2013)*](https://pubmed.ncbi.nlm.nih.gov/23220880/) 
-  HCC78, 2748 sequenced cells (SLC34A2-ROS1 Fusion, ROS1 inhibitors have antiproliferative effect PMID: [*Davies et al. (2012)*](https://pubmed.ncbi.nlm.nih.gov/22919003/) 
- CCL.185.IG, 6354 sequenced cells [*EML4-ALK Fusion-A549 Isogenic Cell*](https://www.atcc.org/products/ccl-185ig)

Furthermore, we also developed an [*R Shiny App*](http://aisc.hpc4ai.unito.it:3838/) allowing the creation of virtual organoids (VO) incorporating user-defined genetic heterogeneity. The output is a sparse matrix in 10XGenomics format, where the cell barcodes include the name of the cell line they belong, e.g. TCTGCCACATGTGCTA-1_A549. 

Starting from this the GSE243665 data we have built the following datasets:

- Set2: 1400 PC9, 1000 A549, **200 CCL185IG** cells
  - Set2d: 1400 PC9, 1000 A549, **1000 CCL185IG** cells
  - Set2c: 1400 PC9, 1000 A549, **500 CCL185IG** cells
  - Set2b: 1400 PC9, 1000 A549, **400 CCL185IG** cells
  - Set2a: 1400 PC9, 1000 A549, **300 CCL185IG** cells
  - Set2_1: 1400 PC9, 1000 A549, **150 CCL185IG** cells
  - Set2_2: 1400 PC9, 1000 A549, **100 CCL185IG** cells
  - Set2_3: 1400 PC9, 1000 A549, **50 CCL185IG** cells
    
  - Set2x1: 1400 PC9, **1500 A549**, 200 CCL185IG cells
  - Set2x2: 1400 PC9, **2000 A549**, 200 CCL185IG cells
  - Set2x3: 1400 PC9, **3000 A549**, 200 CCL185IG cells
  - Set2x4: 1400 PC9, **4000 A549**, 200 CCL185IG cells

  - Set2y1: **2800 PC9**, 1000 A549, 200 CCL185IG cells
  - Set2y2: **4492 PC9**, 1000 A549, 200 CCL185IG cells

  - Set2z1: 1400 PC9, 1000 A549, 200 CCL185IG, **1000** HCC78 cells
  - Set2z2: 1400 PC9, 1000 A549, 200 CCL185IG, **1500** HCC78 cells
  - Set2z3: 1400 PC9, 1000 A549, 200 CCL185IG, **2000** HCC78 cells
  - Set2z4: 1400 PC9, 1000 A549, 200 CCL185IG, **2500** HCC78 cells

- BE1-500: PC9 500, A549 500, CCL185IG 500, CRL5868 500, DV90 500, HCC78 500, HTB178 500 cells

## Testing clustering approaches on BE1-500

We employed the BE1-500 dataset to assess the effectiveness of various clustering tools in identifying distinct cancer subpopulations, i.e. cell lines expressing different driver genes. Our main focus was on evaluating each clustering tool's capability to distinguish the CCL185IG cell line from A549, given the complexity of BE1-500 experiment. Note: CCL185IG and A549 cell line are syngeneic, and the ALK fusion is exclusively expressed in the CCL185IG cell line.








