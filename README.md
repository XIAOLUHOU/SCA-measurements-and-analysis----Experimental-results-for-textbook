# SCA Measurements and Analysis
This repository contains the measurements and evaluations for Chapter 4 of the following book.

_Cryptography and Embedded Systems Security, Xiaolu Hou, Jakub Breier, ISBN: 978-3-031-62205-2, Springer Nature, 2024._

For any usage, please cite
```
@book{SCAbook2024,
  title={Cryptography and Embedded Systems Security},
  author={Hou, Xiaolu and Breier, Jakub},
  year={2024},
  publisher={Springer Nature}
}
```
The author's copy of the book can be found at the following link:
_https://xiaoluhou.github.io/Textbook.pdf_

The source codes are in Jupyter notebook files. As the name suggests, different files contain the analysis for different sections.

## SNR, TVLA and DPA
Section 4.2 focuses on SNR computations and TVLA. Section 4.3 illustrates differential power analysis.
Four datasets are used for those two sections.
Each of the datasets contains the power consumption measurements for one round of PRESENT encryption, surrounded by NOP operations.
- _fixed_dataset_1_ contains 5,000 traces with a fixed round key _FEDCBA0123456789_ and a fixed plaintext _ABCDEF1234567890_. 
- _fixed_datset_2_ contains 5,000 traces with a fixed round key _FEDCBA0123456789_ and a fixed plaintext _84216BA484216BA4_.
- _random_pt_dataset_ contains 5,000 traces with a fixed round key _FEDCBA0123456789_ and a random plaintext for each trace. The corresponding plaintext values are recorded in the file _plaintexts.txt_. For example, the plaintext corresponding to _trace_0.text_ is _eee53883c44a3899_, where the 0th nibble is _9_.
- _random_dataset_ contains 10,000 traces with a random round key and a random plaintext for each trace. The corresponding plaintext and round key values are recorded in the files _plaintexts.txt_ and _keys.txt_.

## SCA on masked PRESENT implementation
Section 4.5.2.3 presents Boolean masking for PRESENT as well as attacks on the implementation. Four datasets are used for the analysis. They are similar to the datasets for unprotected PRESENT implementations.
Each of the datasets contains the power consumption measurements for one round of masked PRESENT encryption, surrounded by NOP operations.
- _masked_fixed_dataset_A_ contains 100 traces with a fixed round key _FEDCBA0123456789_ and a fixed plaintext _ABCDEF1234567890_.
- _masked_fixed_dataset_B_ contains 100 traces with a fixed round key _FEDCBA0123456789_ and a fixed plaintext _84216BA484216BA4_.
- _masked_random_plaintext_dataset_ contains 20,000 traces with a fixed round key _FEDCBA0123456789_ and a random plaintext for each trace. The corresponding plaintext values are recorded in the file _plaintext.txt_
- _masked_random_dataset_ contains 10,000 traces with a random round key and a random plaintext for each trace. The corresponding plaintext and round key values are recorded in the files _plaintext.txt_ and _keys.txt_.

## SCA on RSA
Section 4.4.2 presents DPA attacks on RSA implementations.
Section 4.5.1.2 discusses countermeasures for SPA attacks on RSA implementations.
The datasets and analysis for those two parts of the book can be found in the directory _Section 4.4.2 and 4.5.1.2 SCA on RSA_

In this directory, there are four datasets. The following two datasets are mainly used for SPA attacks on RSA
- _traces_ contains measurements of unprotected RSA computations implemented using the square and multiply algorithm
- _traces_protected_ contains measurements of unprotected RSA computations implemented using the square and multiply always algorithm

The other two datasets are mostly used for DPA attacks on RSA
- _DPA_Mon_ contains 10,000 measurements of unprotected RSA computations implemented using the square and multiply algorithm and Mongomery's method was used for implementing modular multiplication. Each trace corresponds to one random input. The input values are recorded in the file _inputs.txt_.
- _DPA_Counter_ contains 10,000 measurements of RSA computation with Mongomery's method for implementing modular multiplication, protected by square and multiply always algorithm. Each trace corresponds to a random input. The input values are recorded in the file _inputs.txt_.

## Encoding-based countermeasure against SCA attacks
Section 4.5.1.1 analyzes encoding-based countermeasures against SCA attacks on PRESENT implementations. The analysis is mostly on one instruction - MOV.
- _MOV_SNR_traces_ contains 10,000 traces for the computation of the MOV instruction. Each trace corresponds to one random input between 0 and 15. The input values are recorded in the file _bytes.txt_. This dataset is mainly used for finding the POI for protection.
- _MOV_attack_traces_original_input_ contains 100,000 traces for the computation of the MOV instruction. Each trace corresponds to one random input between 0 and 15. The input values are recorded in the file _bytes.txt_. This dataset is used for performing attacks on unprotected implementation.
- _MOV_profile_traces_ contains 10,000 traces for the computation of the MOV instruction. Each trace corresponds to one random input between 0 and 255. The input values are recorded in the file _bytes_long_bit.txt_. This dataset is used for profiling the leakage at the POI in order to find the optimal code.
- _MOV_protected_traces_ contains six folders, each corresponding to protected implementation with one particular code. This dataset is used for profiling the leakages in order to perform attacks on protected implementations. In every folder,
  - there are 10,000 traces for the computation of the MOV instruction with encoded inputs;
  - each trace in the folder corresponds to one random encoded input;
  - the input values are recorded in the file _bytes_encoded.txt_.
- _MOV_attack_traces_encoded_ contains six folders, each corresponding to protected implementation with one particular code. This dataset is used for performing attacks on protected implementations. In every folder,
  - there are 100,000 traces for the computation of the MOV instruction with encoded inputs;
  - each trace in the folder corresponds to one random encoded input;
  - the input values are recorded in the file _bytes.txt_.
