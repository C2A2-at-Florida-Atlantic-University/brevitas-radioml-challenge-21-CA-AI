# ITU-ML5G-PS-007: Lightning-Fast Modulation Classification with Hardware-Efficient Neural Networks
The repository contains python source code (FAU_CA_AI_SOURCE.py) for training and testing 

1) a baseline model -- The baseline model weights checkpoint are saved in the FAU_CA_AI_baseline.pth file
2) the proposed optimized model (FAU_CA_AI_final_model.pth) --  whose inference cost is the one to be considered for evaluation for the ITU-ML5G-PS-007 competition
for modulation classification using the RadioML 2018.01A dataset provided by DeepSig.

# Instructions for reproduction

We introduce a neural network optimization technique based on multi-linear principal component analysis (MPCA) [1],[2] to reduce the width and depth of the initial overparameterized baseline model, while maintaining its classification accuracy. MPCA works on the activation map of each layer of the baseline model. Given that the activation maps strictly depend on the input data, a seed was set for the PyTorch Random Sampler (without affecting the imposed numpy seed and guaranatee a fair train-test split). The seed allows the sampler to randomly select always the same data, so that the activation maps generated by the baseline model will stay the same and, consequently, the optimization will result in the same compressed/optimized neural network model. In this way, the code is reproducible and it will always return the same optimized model. 

The new model checkpoints were saved in the FAU_CA_AI_final_model.pth file. The inference cost is calculated by the sandbox at 4.3. The parts of the python code required to train both models are commented. 

If you would like just to run the code that loads the models and computes the inference cost in the sandbox, it is only required to change the path to the dataset (i.e., variable dataset_path in line 24 of FAU_CA_AI_SOURCE.py). The code will print the accuracy obtained by the proposed optimized model i.e., 57.19%. If you wish to get the test accuracy of the baseline model you will need to uncomment lines 217-271 in FAU_CA_AI_SOURCE.py.

If you wish to re-train the baseline model from scratch, you will need to uncomment lines 176-207. 

If you wish to re-train the proposed optimized model from scratch, you will need to uncomment lines 428-454.

# FAU CA-AI Team (web: https://ca-ai.fau.edu)
Giulia Muscara, Visiting M.S. student, Sapienza University of Rome, Rome, Italy |
E-mail: gmuscara2021@fau.edu

Dariush Hassan, Undergraduate student researcher, Florida Atlantic University, Boca Raton, FL |
E-mail: dhassan2019@fau.edu

Dr. George Sklivanitis, Research Assistant Professor & I-SENSE Fellow, Florida Atlantic University, Boca Raton, FL |
E-mail: gsklivanitis@fau.edu

# References
[1] H. Lu, K. N. Plataniotis and A. N. Venetsanopoulos, "MPCA: Multilinear Principal Component Analysis of Tensor Objects," in IEEE Transactions on Neural Networks, vol. 19, no. 1, pp. 18-39, Jan. 2008, doi: 10.1109/TNN.2007.901277.

[2] N. D. Sidiropoulos, L. De Lathauwer, X. Fu, K. Huang, E. E. Papalexakis and C. Faloutsos, "Tensor Decomposition for Signal Processing and Machine Learning," in IEEE Transactions on Signal Processing, vol. 65, no. 13, pp. 3551-3582, 1 July1, 2017, doi: 10.1109/TSP.2017.2690524.
