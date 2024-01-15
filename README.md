This repository contains the measurements and evaluations for Chapter 4 of the following book


For any usage, please cite

The detailed analysis can be found in jupyter notebook files. As the name suggests, different files contain the analysis for different sections.

Section 4.2 focuses on SNR computations and TVLA. Section 4.3 illustrates differential power analysis.
Four datasets are used for Sections 4.2 and 4.3, each of them contains the power consumption measurements for one round of PRESENT encryption, surrounded by NOP operations
- fixed_dataset_1 contains 5000 traces with a fixed round key _FEDCBA0123456789_ and a fixed plaintext _ABCDEF1234567890_. 
- fixed_datset_2 contains 5000 traces with a fixed round key _FEDCBA0123456789_ and a fixed plaintext _84216BA484216BA4_.
- random_dataset contains 5000 traces with a fixed round key _FEDCBA0123456789_ and a random plaintext for each trace.
- random_pt_dataset contains 10000 traces with a random round key and a random plaintext for each trace.

