## Bridging the Gap between Different Programming Paradigms in Coverage-based Fault Localization

Welcome to the homepage of our Internetware'22 paper "Bridging the Gap between Different Programming Paradigms in Coverage-based Fault Localization"! This paper have been extended to JCST titled "Coverage-based Fault Localization in Haskell".

In this website, we first release the HaFLa benchmark, which contains both real faults and seeded faults collected from popular open-source projects. Then, we give the complete experimental results in our paper, which are not fully shown in the paper due to space limit.

### HaFLa

To our knowledge, there is no fault localization benchmark in Haskell. Therefore, we manually build the first benchmark for Haskell called HaFLa, including real faults and seeded faults. The projects include [Pandoc](https://github.com/jgm/pandoc), [Hadolint](https://github.com/hadolint/hadolint), and [Duckling](https://github.com/facebook/duckling) after careful selection.

#### Real Faults

The detailed information of the collected real faults is shown [here](HaFLa/Faults_Information_for_HaFLa_RealFaults.pdf). The table includes the fault ID, the relevant issue, the relevant commits(s), SLOC, \#tests, and \#failing tests.

To encourage more research on this direction, we present the detailed information of each real fault from two aspects.

On one hand, we release the tarballs for real faults. Specifically, for each fault, its tarball is a complete version which contains the corresponding fault and in the version, at least one test will fail after running the test suite. The tarballs are put [here](https://drive.google.com/file/d/1ch7Ah5TEMGmHjZwl3aY53dKsm-pFidOO/view?usp=sharing).

One the other hand, we present some collected data that is necessary for fault localization [here](https://drive.google.com/file/d/1vBCDVK9ANKxqeUm5fQ6nYxtpijRFv3Hg/view?usp=sharing).

* ```testlist``` contains all test contents in this version, where one test occupies one line and the tests are numbered from 0.
* ```testresult``` contains the the running results of each test in this version, where the first number represents the test's unique number and the second number indicates the testing results (0 for passed, 1 for failed).
* ```expbox``` contains the information of expressions. For each expression (row), we present its unique number, the file that contains it, its starting row, its starting column, its ending row, and its ending column.
* ```toplevelbox``` contains the information of functions. For each function (row), we present its unique number, its name, the file that contains it, its starting row, its starting column, its ending row, and its ending column.
* ```detailedexpbox``` contains the mapping relations between expressions and functions. For each expression (row), we present its unique number, the file that contains it, its starting row, its starting column, its ending row, its ending column, and the function's unique number that contains it.
* ```covmeta``` contains the description of each program element. For each element (row), we present the file that contains it, its starting/ending row/column, and its type (e.g., expression, function). Here, the line number of each element is its unique number, which is also used in ```expbox```, ```toplevelbox```, ```detailedexpbox```, ```covinfo``` and ```suspicious_value```.
* ```covinfo``` contains the coverage information of each test. For each test (row), we record the times that each program element is covered in ascending order of their unique numbers.
* ```suspicious_value``` contains the suspiciousness scores of each program element. For each program element (row), we present its unique number, Ochiai score, DStar score, and Tarantula score, where -1 means non-existing.

#### Seeded Faults

As the quantity of seeded faults is large, we do not present their tarballs here. On the contrary, we release the mutants and their corresponding mutated files [here](https://drive.google.com/file/d/1ZAaZLhAi953UqIiNzE2zqfd2mOs1KZ-9/view?usp=sharing). Specifically, we group the mutants according to their corresponding file names. The HEAD that we perform the mutation is ```d5c13dd``` for Pandoc and ```e4e0354``` for Hadolint, and users could replace the original files with mutated files to obtain the faulty versions.

At the same time, similar to real faults, we present some collected data that is necessary for fault localization [here](https://drive.google.com/file/d/1uUEk5YB3j8XFN7TWxHCycqP22F64tc9W/view?usp=sharing). The contents of each file are consistent with real faults.

#### Orcale

The faulty function(s) of each real/seeded fault are shown [here](HaFLa/oracle). For each fault, we give the unique number(s) of all faulty function(s).

### Experimental Results

In our paper, due to space limit, we do not show all results. Therefore, we give the complete results in this website.

#### Real Faults

In our paper, we present the ranking position of each approach on each real fault by using the Ochiai formula. Here, the complete results by using Ochiai, DStar, and Tarantula are [here](Results/Result_on_Real_Faults.pdf).

#### Seeded Faults

Due to the large quantity of seeded faults, in our paper, we only present some statistics (i.e., Top-N metrics) on them. In our paper, we also present the results by only using the Ochiai formula. Here, we release the complete results of [FCBA](Results/FCBA_seeded), [PBA](Results/PBA_seeded), [PBA\_TB](Results/PBA_TB_seeded), and [Learning](Results/Learning_seeded). Specifically, the first column represents the mutated file, the second column represents the mutant' id within the mutated file, and the remaining column(s) represent the ranking position(s). Here, for the first three approaches, we report the results by using Ochiai, DStar, and Tarantula, respectively.

