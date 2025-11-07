**Forced Alignment using Montreal Forced Aligner (MFA) **

This document explains the methods and results of a Forced Alignment project using the Montreal Forced Aligner (MFA). The project aimed to automatically create accurate time markers for words and individual sounds in speech audio.

**1. Environment Setup**

To ensure stability and manage dependencies, MFA was installed in a separate Conda environment called mfa. 
 
` #Create Environment conda create -n mfa python=3.9   
 #Activate Environment  conda activate mfa   
 #Install MFA  pip install montreal-forced-aligner`  

**2. Dataset Organization**

All audio and transcript files were sourced and organized to meet MFA's strict naming requirements. Each audio file (.wav) and its matching transcript (.txt) must have the same base name.

Content | Example File Names | Location  
--- | --- | ---  
Audio | F2BJRLP1.wav | /wav folder  
Transcript | F2BJRLP1.txt | /transcripts folder  

**3. Alignment Execution**

A. Models Used

The alignment used the pre-trained US English models:  
- Acoustic Model (AM): `english_us_arpa ` 
- Pronunciation Dictionary: `english_us_arpa` (Uses ARPABET phonetic representation.)

B. Execution Command

The alignment was executed by directing MFA to the organized input folders and specifying the output location:  

`mfa align transcripts/ wav/ english_us_arpa english_us_arpa output`

C. Output

The process generated accurate time-aligned labels in TextGrid file format, which were saved in the output folder. 

**4. Analysis and Key Observations**

Visual checks of the resulting TextGrid files in Praat confirmed the following quality points:  

- Handling Pauses: The system correctly identified brief silences between words (for example, between "march" and "it") and labeled them as <eps>. This demonstrates that the aligner can clearly differentiate between spoken words and non-speech gaps.  
- Boundary Precision: For most of the main spoken words (is, expected, to, be, named, in, march), the alignment showed high accuracy. The phonetic boundaries matched perfectly where the acoustic sounds changed, ensuring the output is in sync with the audio details.
