# Input Data {#inputdata}

ADViSELipidomics allows the user to import files concerning different types of data:
* **LipidSearch** or **LIQUID.** ADViSELipidomics deals with the data files containing information on chromatographic peak area or peak intensity per lipid, obtained as output from external software for identifying and quantifying lipids (i.e., ADViSELipidomics currently supports the output formats from LipidSearch or LIQUID). Moreover, it requires the Target File with details on samples (such as treatments or biological replicates), the Internal Reference File with bounds for the filtering step in the following modules. ADViSELipidomics shows a quality plot based on the sum of chromatographic peak area per sample (or replicate). In the case of LipidSearch output associated with internal lipid standards, ADViSELipidomics also requires all the Calibration Files for the construction of the calibration curves.
* **Metabolomics Workbench.** ADViSELipidomics can download in real-time suitable selected lipidomic experiments from the online repository;
* **Excel.** The user can upload two Excel files: the data matrix and the Target File;
* **SummarizedExperiment.** The user can upload a SummarizedExperiment R object (SE), with several types of information (data matrix, information on lipids, information on samples, metadata if available).

Hence, as can be seen, ADViSELipidomics requires different files that may change between the different types of data. To sum up, here is a list with all the required files for each data type:


* **LipidSearch with Internal Standard lipid:** 
  * Target file (.xlsx)
  * Internal Reference file (.xlxs)
  * Data files coming from LipidSearch related to your samples (.txt)
  * Calibration File for deuterated (.xlsx)
  * Calibration File for nonlabeled (.xlsx)
  * Concentration files coming from LipidSearch related to the internal standard (.txt)
* **LipidSearch without Internal Standard lipid:** 
  * Target file (.xlsx)
  * Internal Reference file (.xlxs)
  * Data files coming from LipidSearch related to your samples (.txt)
* **LIQUID** 
  * Target file (.xlsx)
  * Internal Reference file (.xlxs)
  * Output coming from LIQUID related to your samples(.tsv)
* **User’s Excel File** 
  * Target file (.xlsx)
  * Data Matrix File (.xlsx)
* **SummarizedExperiment** 
  * SummarizedExperiment object (.rds)

For **Metabolomics Workbench** you don't need to import anything, just choose the  Metabolomics Workbench ID study.

Before running ADViSELipidomics make sure that you have all the required files and that they are compiled properly. Apart from the output files from LipidSearch and LIQUID, ADViSELipidomics requires that the Excel files have a given structure with some mandatory columns. Here we provide a guide to the creation of these Excel files. 



## Data files (LipidSearch or LIQUID) {#sec21}

The output of LipidSearch and LIQUID are some text files containing information on chromatographic peak area or peak intensity per lipid. If your data come from **LipidSearch** you should have a deuterated file and a non-labeled file for each sample (or replicate). The extension of these files should be .txt. If your data come from **LIQUID** you can have a positive and a negative file, with a .tsv extension. In any case, put your data file in a folder and rename each file with your sample id in a proper way. 

**Example:**  
Your sample is called "AF-1CM" and you have two technical replicates. Then, depending on the output software, the name of the data files should be:

* for LipidSearch: "AF-1C-M_deuterated_1.txt", "AF-1C-M_nonlabeled_1.txt" and "AF-1C-M_deuterated_2.txt" and "AF-1C-M_nonlabeled_2.txt"
* for LIQUID: "AF-1C-M_positive_1.tsv", "AF-1C-M_negative_1.tsv" and "AF-1C-M_positive_2.tsv", "AF-1C-M_negative_2.tsv"

The last two characters (e.g. "_1") refer to the technical replicate. If you don't have technical replicates just remove these two last characters (so for example in the case of LipidSearch you should have "AF-1C-M_deuterated.txt" and "AF-1C-M_nonlabeled.txt").



<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle-exclamation.svg" width="15" height="15"> **NOTE**  
In the choice of your sample name, it's better to avoid special characters and **DO NOT use underscores (_)**. This character is used by ADViSELipidomics to split the file name into three parts: the sample name, the type of file (deuterated/nonlabeled or positive/negative), and the technical replicate as shown in the following picture:

<img src="https://user-images.githubusercontent.com/78078351/160425060-4c576fe4-f328-4024-88dc-838af935cf1f.png" width="100%" />


For example, a bad name could be "Blood_bag_deuterated_1.txt", while a good name is "Blood-bag_deuterated_1.txt".


## Target File (LipidSearch, LIQUID, and User’s Excel File) {#sec22}
The Target File is an Excel file that contains all the information about your samples. It is the most important file since it is used for LipidSearch import, LIQUID import, and User’s Excel File import. This file requires some mandatory columns that have to be filled with some criteria:


* **SampleID (LipidSearch, LIQUID, and User’s Excel)** this column contains the ID of each sample. To prevent errors, the best way to write the IDs is: "samplename_1" where in "samplename" you can write your sample name and "_1" represents the identification for the technical replicate. If your experiment doesn't have technical replicates, you can simply write "samplename". A good SampleID could be "AF-1C_1" if technical replicates are present, or "AF-1C" if not. A bad name could be "AF_1C_1" (with another underscore).
*	**File_name (LipidSearch, LIQUID)** this column contains the name of the data files coming from LipidSearch or LIQUID. In both cases, for each sample there are two different files. In LipidSearch you have a "deuterated" and a "nonlabeled" file, while in LIQUID you have a "positive" and a "negative" file. Depending on your data type, write both file names in the corresponding cell separated by a **semicolon ";"** without any space.
* **Norm_factor (LipidSearch, LIQUID - optional)** If you need to normalize your data by a normalization factor, you can add this column and write a number (be careful with decimal points) for each sample. If it's not present, data won’t be normalized.

In the picture below there is a Target File example where the mandatory columns are enlightened in yellow and the optional column in green. You can fill the Target File with any other informative column, just try to avoid special characters like \\^$?\*/|+()[]{} and whitespace. You can use - or _ instead of whitespace. 


<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle-exclamation.svg" width="15" height="15"> **NOTE**  
If your Target File doesn't contain at least one informative column about the samples (e.g. Product, Model_type, etc.), you can't perform any exploratory or statistical analysis. 


<img src="https://user-images.githubusercontent.com/78078351/160630507-503a7b95-ce60-407b-bdf6-f3ae428f428b.png" width="100%" />



The example target file can be downloaded from here:

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/download.svg" width="20" height="20"> [Targetfile_Lipidomics.xlsx](https://github.com/ShinyFabio/ADViSELipidomics/files/8325363/Targetfile_Lipidomics_new.xlsx)


##  Internal Reference File (LipidSearch, LIQUID) {#sec23}
In LipidSearch and LIQUID option, ADViSELipidomics requires also another Excel file here called Internal Reference File which contains the list of the Internal Standard lipids defined per class and adduct, upper/lower bounds for the number of carbon atoms, upper/lower bounds for the number of double bonds, nominal standard concentration, and upper/lower bounds for the concentration linearity in the calibration curves. This file has many mandatory columns that depend both on the external software (LipidSearch, LIQUID) and the presence of internal standards (only for LipidSearch).

* **LipidSearch** 
  - **Class** lipid class of interest according to the nomenclature of LipidSearch (e.g. *DG* )
  - **Ion** the ion of interest written according to the nomenclature of LipidSearch(e.g. *M-H* )
  - **MinRt** minimum retention time of the class (numeric)
  - **MaxRt** maximum retention time of the class (numeric)
  - **InternalStandardLipidIon** name of each internal lipid standard according to the nomenclature of LipidSearch (e.g. *Cer(d18:1_17:0)-H* )
  - **MinLinearity** minimum value for the range of linearity in the calibration curves. (numeric) ONLY IF YOU USE INTERNAL STANDARD
  - **MaxLinearity** maximum value for the range of linearity in the calibration curves. (numeric) ONLY IF YOU USE INTERNAL STANDARD
  - **NominalStdConcentration** concentration of of each internal lipid standard initially spiked into the sample (numeric) ONLY IF YOU USE INTERNAL STANDARD

The picture below shows an Internal Reference File example in the case of LipidSearch and the presence of Internal Standards. In yellow are the mandatory columns, and in green the columns needed only in the presence of Internal Standards. The "Unit_measure" column is not used but can be useful to check that each standard concentration has the same unit measure. If you have different units measure, convert them to the same.


<img src="https://user-images.githubusercontent.com/78078351/160590351-652867af-a00f-434b-b0e2-67aa767c06c3.png" width="100%" />


The Internal Reference File example for the LipidSearch with Internal Standards option can be downloaded from here:

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/download.svg" width="20" height="20"> [Internal_Reference_file_LipidSearch_withIS.xlsx](https://github.com/ShinyFabio/ADViSELipidomics/files/8370364/Internal_Reference_file_LipidSearch_withIS.xlsx)



* **LIQUID**
  - **Class** lipid class of interest according to the nomenclature of LIQUID (e.g. *DG* )
  - **Adduct** the ion of interested written according to the nomenclature of LIQUID (e.g. *[M-H]+* )
  - **MinRt** minimum retention time of the class (numeric)
  - **MaxRt** maximum retention time of the class (numeric)

The picture below shows an Internal Reference File example in the case of LIQUID. In yellow are the mandatory columns.

<img src="https://user-images.githubusercontent.com/78078351/159518027-cb2a3eea-923f-49b7-8633-0502d0935032.png" width="100%" />


The Internal Reference File example for the LIQUID option can be downloaded from here:

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/download.svg" width="20" height="20"> [Internal_Reference_file_LIQUID.xlsx](https://github.com/ShinyFabio/ADViSELipidomics/files/8363693/Internal_Reference_file_LIQUID.xlsx)


## Calibration Files (LipidSearch with Internal Standards) {#sec24}
In the case of LipidSearch, if you have Internal Standard, you can choose to use them or not. In this case, you need to upload also some Calibration Files which are two Excel Files and the data files coming from LipidSearch (here called concentration files). The concentration files are the same .txt files described in Section \@ref(sec21). Please, refer to that Section if you need more information about how to rename the files. Be sure that all the concentration files are inside a folder and they aren't mixed with the data files of Section \@ref(sec21). 
Next, ADViSELipidomics, requires two Calibration Excel files, one for the Nonlabeled and the other for the Deuterated. They share the same structure:

* **Concentration (ng/mL)** the concentration of the standard (numeric)
* **Class** the lipid classes of interest separated by a comma **,** (e.g. *PG,PS,PI,PE,SM,PC,TG,DG* )
* **Name** the name of the data files coming from LipidSearch. They have to match perfectly with the file names. If you have technical replicates, separate them by a **semicolon ";"** without any space. (for example in the deuterated: *ISMix_5ugmL_deuterated_1.txt;ISMix_5ugmL_deuterated_2.txt;ISMix_5ugmL_deuterated_3.txt*)

The picture below shows an example of a Calibration Excel file for the deuterated. 

<img src="https://user-images.githubusercontent.com/78078351/161043392-9f9f3038-95eb-4e30-a465-1780fa6220d5.png" width="100%" />


An example for the Calibration Deuterated and Calibration Nonlabeled Excel files can be downloaded here:


<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/download.svg" width="20" height="20"> [Calibration_Deuterated.xlsx](https://github.com/ShinyFabio/ADViSELipidomics/files/8363641/Calibration_Deuterated.xlsx)

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/download.svg" width="20" height="20"> [Calibration_NonLabeled.xlsx](https://github.com/ShinyFabio/ADViSELipidomics/files/8326075/Calibration_NonLabeled.xlsx)


## User’s Excel File {#sec25}

If you already have a  matrix file containing the abundance for each lipid, you need just two Excel files: a Target File and a Data Matrix File. Here the Target File has only one mandatory column, the SampleID. The Data Matrix (.xlsx file) must have the list of the lipids in the first column, which must be called *"Lipids"*, and then the samples (or replicates) in the following columns, with the column names that is the same of the *SampleID* from the Target File. It is not necessary that the matrix is full (i.e. without missing values) since after uploaded, it is possible to filter and impute NAs. The picture below shows an example of a Data Matrix Excel file.

<img src="https://user-images.githubusercontent.com/78078351/160581333-cd7bf4ec-53ec-4c12-9bcc-d007d2dfbbe1.png" width="100%" />


<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle-exclamation.svg" width="15" height="15"> **NOTE** 
The column names in the data matrix must follow the same SampleID rules described in Section \@ref(sec22).

An example for the Data Matrix can be download from here:

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/download.svg" width="20" height="20"> [Excel_Data_Matrix.xlsx](https://github.com/ShinyFabio/ADViSELipidomics/files/8370052/Excel_Data_Matrix.xlsx)


## SummarizedExperiment {#sec26}

ADViSELipidomics allows the user to load a SummarizedExperiment (SE) object, saved as a .rds file, already prepared or previously downloaded after running ADViSELipidomics. Since the required SE object has a complex structure, we do not recommend the user to upload a SE object that wasn't downloaded from ADViSELipidomics. The idea behind this option was that the user can save the SE object after the preprocessing steps and performs the exploratory and statistical analysis in another moment.


## Metabolomics Workbench {#sec27}

In the case of Metabolomics Workbench, you don't need to import anything, because ADViSELipidomics downloads a selected Metabolomics Workbench experiment and converts it into an SE object.
