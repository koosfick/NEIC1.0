# NEIC1.0 🧬

## Description

**NEIC1.0** (NLR-Effector Interaction Classification 1.0) can be used to predict novel NLR-effector interactions in all pathosystems, based on predicted binding energy- and affinity values.

#### Using **NEIC1.0**? Remember to cite us:
If you use **NEIC1.0** and publish your work, we would be grateful if you could cite our work using the following:
- Fick, A., Fick, J.L.M., Swart, V., & van den Berg, N. (2024). What NLR you recognizing? Predicted binding affinities- and energies may be used to identify novel NLR-effector interactions, _bioRxiv_ (doi: https://doi.org/10.1101/2024.07.26.605369)


## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Credits](#credits)


## Installation

**NEIC1.0** was created using [MATLAB](https://www.mathworks.com) and relies on MATLAB Runtime for execution. 

**Follow these steps to install **NEIC1.0**:**

1. **_Download NEIC1.0 Installer:_** Obtain the correct **NEIC1.0** installer file for your operating system from the GitHub repository.
    - For installation on a platform using macOS as an operating system, download either the NEIC_Installer_MacOS_Apple_Silicon.zip or the NEIC_Installer_MacOS_Intel.zip file depending on your Mac’s CPU architecture. 
    - For installation on a platform using Linux Ubuntu as an operating system, download the NEIC_Installer_Ubuntu.zip file. 
    - For installation on a platform using Windows as an operating system, download the NEIC_Installer_Windows.exe.zip file.
2. **_Extract Contents:_** Unzip the downloaded file to reveal its contents.
     - **_NOTE:_** For macOS users, open a Terminal window and execute the following command where */path/to/downloaded/NEIC1.0/file* is the path to where the **NEIC1.0** **_extracted_** installer file has been saved to:
         - ```xattr -d com.apple.quarantine /path/to/downloaded/NEIC1.0/file```
3. **_Run Installer:_** Execute the installer file as an administrator on your computer and follow the instructions.
4. **_Automatic MATLAB Runtime:_** During installation, MATLAB Runtime will be automatically downloaded and installed—no separate MATLAB license is needed.
   - **_NOTE:_** It is not required nor recommended that you download MATLAB Runtime yourself, the **NEIC1.0** installation package will download and install the correct version of MATLAB Runtime. 

## Usage

1. **_Prepare sequences for protein complex prediction:_**
    - Identify NLR- and effector domains using InterPro. This can be done using the [InterPro online web tool](https://www.ebi.ac.uk/interpro/search/sequence/) OR using a locally installed version.
    - Remove signal domains from effector sequences, and CC/TIR and NB domains from NLR sequences. 
        - **_NOTE:_** Only use NLR LRR domain-encoding sequences.

2. **_Predict NLR-effector structures using AlphaFold2-Multimer:_**
    - Template mode should be set to "PDB100".
    - Pair mode should be set to "Unpaired".
    - Model type should be set to "alphafold_multimer-v3".

3. **_Identify predicted complexes with acceptable accuracy:_**
    - Calculate AlphaFold confidence scores for top-ranked structures using the formula: 0.2(pTM) + 0.8(ipTM).
    - Predicted complexes with AF confidence scores ≥ 0.42 may be used for further analysis.

4. **_Predicting Binding energy- and affinity values:_**
    - Predict Binding energy- and affinity values using the [Area-Affinity web tool](https://affinity.cuhk.edu.cn).
    - Values should be predicted using both the "Protein-protein", and "Antibody-antigen protein" options.
    - Download results (output in .txt format).
    - Combine results from "Protein-protein" and "Antibody-antigen protein" predictions. This should be done by copying- and pasting values from the "Antibody-antigen protein".txt file (without header) directly below "Protein-protein" values.

5. **_Prepare **NEIC1.0** input Excel file:_**
    - Copy combined Binding energy- and affinity values (without header), and paste the values into the "Data_Transformation.xlsx" file provided. This file orders data, with the output being in the correct format.
    - Transformed data will be in the second row (coloured in blue), which can be pasted (using the "Paste special > Values" option) into a new Excel spreadsheet. This allows for binding energy- and affinity values from multiple NLR-effector complexes to be analysed by **NEIC1.0**.
    - The first row in the new Excel spreadsheet should contain an alphabetic header, which can be found in the first row of the "Data_Transformation.xlsx" file.
    - Once the spreadsheet contains all data to be analysed, "Find and replace" all "#VALUE!" with "-1".
    - Save the spreadsheet in .xlsx format.

6. **_Classify NLR-effector interactions using **NEIC1.0**:_**
    - Import the .xlsx file prepared in step 5.
    - Results will be displayed, with an interaction probability value given in the format "Forced vs Interacting". 

## Credits

A huge thank you to [MATLAB](https://www.mathworks.com) for their incredible software!


