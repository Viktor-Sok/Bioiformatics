# Summary of the QSAR model (more information in NN_Torch.ipynb notebook above)

## Objectives
Predicting pXC50 value which is associated with the SLC6A4 gene.
## Descriptors (features of the machine learning model) used 
Morrgan fingerprints generated from SMILES by RDKit tool
## Tools used
RDKit, Scikit-Learn, TensorFlow, Keras
## Model description
Feed Forward NN with 2 hidden layer and dropout regularization to prevent from overfitting
## References 
1. Dataset from the website: https://solr.ideaconsult.net/search/excape/, "Active" search option was chosen and Gene Symbol was set to SLC6A4.
2. Ideas and methods used are inspired by Cheminformania blog: https://www.cheminformania.com/, especially, the series of articles by Esbenbjerrum was of a great help.
