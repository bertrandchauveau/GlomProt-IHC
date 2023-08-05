# GlomProt-IHC
## Immunohistochemical analysis of interferon-related proteins by deep learning in kidney transplantation
###### Using keras/tensorflow

This repository contains the code developed to (i) train a convolutional neural network (CNN)-based workflow for the binary classification of immunohistochemical images as “Antibody-Mediated Rejection” (ABMR) or “Other diagnosis” and (ii) visualize the morphological patterns learned by the CNN using the Gradient-weighted Class Activation Mapping (Grad-CAM) approach (as displayed in the keras documentation, https://keras.io). It is part of an unpublished project about kidney transplantation currently under review at a scientific journal.

The codes are written in Python, commented and presented in a format compatible with a Google Colaboratory implementation (last checked April 15, 2022). For a detailed description of the overall workflow, please refer to the related manuscript (published in Scientific reports: Sci Rep. 2022 Nov 9;12(1):19094. doi: 10.1038/s41598-022-23078-z, https://www.nature.com/articles/s41598-022-23078-z).

To use these scripts, data must be prepared according to the Aachen protocol as described here: https://zenodo.org/record/3694994. Whole slide images (WSI) must be cropped in square tiles using the QuPath software (https://qupath.github.io/). Tiles must be numbered, sorted and named following these examples: 
- “WARS_S017_14_(49517.0,3779.0).jpg”
- “TYMP_S001_71_(16928.0,4281.0).jpg”
- “GBP1_S016_11_(9384.0,7881.0).jpg”

where WARS, TYMP and GBP1 are the name of the tested antibodies, S0XX is the patient ID, followed by the tile number (tiles must be numbered and sorted) and by the position in the whole slide image (optional for this project).

For each antibody, all corresponding tiles should be structured as follows (example for the TYMP antibody):

```
Tiles/
      ABMR/
           TYMP_S017_14_(49517.0,3779.0).jpg
           TYMP_S017_15_(50029.0,3779.0).jpg
           …
      Other/
           TYMP_S029_65_(5966.0,10946.0).jpg
           TYMP_S029_66_(6478.0,10946.0).jpg
           …
```         
The proposed scripts allow to train models based on the images of the TYMP antibody. Simply replacing TYMP by WARS or GBP1 enables training of these two others.

<p align="middle">
      <img src="https://user-images.githubusercontent.com/110421330/182601389-d2b460e1-db18-45a5-942f-04e782d90580.jpg" width=30% height=30%>
      <img src="https://user-images.githubusercontent.com/110421330/182601456-6b8fe474-d778-4cea-b567-69ceba1e33fa.jpg" width=30% height=30%>
</p>

An example of one tile with the TYMP antibody in an ABMR case, showing a strong staining of the microcirculation i.e. glomerular and peritubular capillaries (left). The corresponding heatmap is displayed, focusing on stained capillaries (right) for a correct classification as ABMR.
