# Histology-Analysis
The Histology Categorization Analysis Tool (HCAT) is an image analysis pipeline intended to provide preliminary discrimination between tissue, implant, and empty space present on histological images generated by an animal study on the effectiveness of a novel implant at adhering to skin. HCAT is a multi-step image analysis pipeline that primarily relies on K-means clustering to classify pixels. Because pixels corresponding to empty space and the implant have similar values in RGB space, K-means clustering with K=2 clusters is effective at separating pixels corresponding to tissue from those corresponding to empty space and the implant. Once a set of pixels have been categorized as tissue, they can be combined with the pixels corresponding to empty space by setting their RGB values to that of empty space. Applying K-means clustering with K = 2 clusters to this new image is effective at separating implant pixels from those corresponding to the now-combined empty space and tissue pixels. Median filtering is employed after each K-means clustering step to smooth the resulting classification while preserving local features. Once pixels corresponding to implant and tissue have been identified, anything left un-classified must correspond to empty space. The number of pixels in each category is then tabulated to allow for the estimation of metrics of interest: infill (how much available space is filled by tissue) and porosity (how much of the total area is not occupied by the implant). The final image is produced by recoloring the pixel categories so that implant is shown in black, tissue is shown in purple, and empty space is shown in white. 

The image used to benchmark pipeline performance is the top image, with the HCAT result below it:
![image](https://github.com/Jezen5Volk/Histology-Analysis/assets/138075884/e7c59c6a-e00f-469f-b082-a6d33d3143b2)
![image](https://github.com/Jezen5Volk/Histology-Analysis/assets/138075884/d796107b-1feb-45cf-9360-1ebdb5504297)

