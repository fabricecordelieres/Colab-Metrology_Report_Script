# **Colab-Metrology_Report_Script / Metrology Notebook <a href="https://colab.research.google.com/github/fabricecordelieres/Colab-Metrology_Report_Script/blob/main/Colab-Metrology_Report_Script.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>**



---
_This scripts takes as an input a Google Drive folder in which tempora metrological data from several microscopes have been stored and builds XLSX and PPTX reports from the data.
Data should have been exported using the Fiji/ImageJ MetroloJ plugin, along side the power measurements that have been properly formatted. The following section gives information about what data structure is expected._


## **Data organization**

### Metrology folder:
---
> # *__Root_metrology_Folder__*

>> <ins>*__Microscope 1 (subfolder)__*</ins>

>>> *__Power_file__* (mandatory, see below for a full description)

>>> *__YYMMDD__* (subfolder, date at which measurement was done: should match dates in the power_file)

>>>> __pdf__ (optionnal subfolder, stores the pdf extracted by the MetroloJ plugin)

>>>> __table__ (mandatory subfolder, stores tables extracted by the MetroloJ plugin)

>>> *__YYMMDD__* (subfolder, date at which measurement was done: should match dates in the power_file)

>>>> __pdf__ (optionnal subfolder, stores the pdf extracted by the MetroloJ plugin)

>>>> __table__ (mandatory subfolder, stores tables extracted by the MetroloJ plugin)

>> <ins>*__Microscope 2 (subfolder)__*</ins>

>>> *__Power_file__* (mandatory, see below for a full description)

>>> *__YYMMDD__* (subfolder, date at which measurement was done: should match dates in the power_file)

>>>> __pdf__ (optionnal subfolder, stores the pdf extracted by the MetroloJ plugin)

>>>> __table__ (mandatory subfolder, stores tables extracted by the MetroloJ plugin)

>>> *__YYMMDD__* (subfolder, date at which measurement was done: should match dates in the power_file)

>>>> __pdf__ (optionnal subfolder, stores the pdf extracted by the MetroloJ plugin)

>>>> __table__ (mandatory subfolder, stores tables extracted by the MetroloJ plugin)
---


### Powers file:

The powers file contains all measured powers as tabulation separated values.

*__The filename should be puissance.csv.__*

There is only one puissance.csv file per microscope folder, stored at its root.

The file is assumed to contain the following columns:
* *__date__*: should be formatted as YYMMDD, not forgetting the leading zeros
* *__source__*: name of the light source (LED, laser etc)
* *__obj__*: objective that was used for measurements
* *__Channel_405__*: illumination setting used for measuring the 405 channel
* *__Channel_488__*: illumination setting used for measuring the 488 channel
* *__Channel_561__*: illumination setting used for measuring the 561 channel
* *__Channel_633__*: illumination setting used for measuring the 633 channel
* *__405__*: power measured using the Channel 405 illumination setting (in mW)
* *__488__*: power measured using the Channel 488 illumination setting (in mW)
* *__561__*: power measured using the Channel 561 illumination setting (in mW)
* *__633__*: power measured using the Channel 633 illumination setting (in mW)

Data are stored, one date per line

*__ex:__*

---

date	source	obj	Channel_405	Channel_488	Channel_561	Channel_633	405	488	561	633

201201	LED	10x	0	Eye-GFP_50pct	0	0	0.000	18.800	0.000	0.000

201218	LED	10x	Eye-DAPI_50pct	Eye-GFP_50pct	Eye-TRITC_50pct	Fluo - CY5 quad quad	51.300	17.300	16.470	11.170

210127	LED	10x	Eye-DAPI_50pct	Eye-GFP_50pct	Eye-TRITC_50pct	Fluo - CY5 quad quad	43.5	15.12	14.96	9.17

---

## **How to run this script**

1. Upload this script to Google Colab using the dedicated button
2. Once in Google Colab, first go to File/Save a copy to my Google Drive
3. Have all you data ready on the Google Drive
4. Run all the steps: Run/Run all
   - Step 1 only is interactive: it will require that acces is given by the Google Drive to the script. Simply follow the procedure explained at Step 1.1
   - The metrology root folder should be defined: follow the procedure explained at Step 1.2
   - All subsequent steps are run without any interaction with the user
5. At the end of the script, two files are generated in the metrology root folder:
   - An XLSX file containing all the data pulled into a single, multitabs file
   - A PPTX file containing graphs for all microscopes/dates/measurements

