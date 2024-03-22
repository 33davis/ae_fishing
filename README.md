# Bioinformatic optimization for capture of rare sequences in marine metagenomic data #
 ## subgoals include : 
  ## (1) understanding how relative parameter important in post-processing ancient metgenomic analyses 
  ## (2) how to utilze post-processing tools for samples to see when more targeted deep sequencing is needed 
  ## (3) compare relative outputs of current tools for shotgun metagenomic data
  ## (4) increase the identification and validation of rare marine species in sediment records with sedaDNA
  
### Intial goals of project 
1. identify current bioninformatic standards and methods
2. create synthetic test data
   - created database of 20 COI partial sequenences for Nototheniideae and Sphenisciformes from NCBI
   - I chose COI sequenences based on availability, as well as hoping to utilize new MARES COI barcode database pipeline that was recently published.
    2a. MARES pipeline: for intial testing the precompiled database from [https://osf.io/8rdqk/] was used, which was downloaded 20.02.2024.
    2b. after proof of concept testing with Armbrecht pipeline, the MARES custom database pipeline will be used to construct a custom COI databse [33davis/MARES_database_pipeline]
    2c. create a combined MARES + PR2v5 database to simulate a complex eukaryotic database to map published data against
    2d. understand utility and proof of concept using this database
3. create "fishing" dataset combining empirical and synthetic data
   - utilizing gargammel to simulate sedaDNA fragments
   - for COI sequence "syntheic" sequences, utilize the bioconda::gargammel-slim package to create random fragemetns and simulate damage on partial gene sequences (no gaps)
   - test nuclear and mitochondiral published genomes if available utilizing gargammel
   - these different datasets will then be run through target pipelines by themselves, and then also merged with published dataset to quantify and compare ability to be "fished" back out. This will help provide reference if simulated ancient Nototheniideae and Sphenisciformes sequences can be identified with current pipeline and settings, espeically in complex metagenomic samples
   - will also highlight the importance of database choice 
4. test data with Linda pipeline (Armbrecht et al., 2020) [https://onlinelibrary.wiley.com/doi/10.1111/1755-0998.13162]
   #### it is noted that MALT/ HOPS has not had an updated with NCBI since 2022. Most likely it will not be updated in the future. 
     - beginning with U1538 site data
     - initially testing of pipeline will follow published methods and parameters
     - intiall U1538 testing site data will vary only in which database it was run with
     - will begin with U1538 sample data, that is already been collapsed + adapterremoval + intial FastQC/MultiQC qaulity control
       (6a) create conda environment for testing data [link to code] available here
       (6b) databases were merged with code [add link to code]
       (6c) malt-build with [add link to code] for MARES preload database, and merged MARES + PR2 v5 database
       (6d) run Komplexity - bbtools/dedupe - MALT - blast2RMA [add link to code] 
           - one run with only U1538 samples + MARES only database
           - one run with U1538 samples + MARESPR2 v5 database
       (6e) Visualize and quanitify runs in MEGAN v. against built databases // previously published data. 
5. test Holi revised pipeline (Pedersen et al., 2016) [https://github.com/miwipe/metaDMG-core-holi]
6. test nf-core/eager v.2.5.0 pipeline (Fellows Yates et al., 2021) [https://github.com/nf-core/eager]
7. test aMeta pipeline (Pochon et al., 2023) [https://github.com/NBISweden/aMeta]
8. test euka pipline (Vogel et al., 2023) [https://doi.org/10.1111/2041-210X.14214]
9. utilize benchmarking statistics to compare outputs
