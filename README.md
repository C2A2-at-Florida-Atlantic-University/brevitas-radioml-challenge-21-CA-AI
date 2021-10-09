# ITU-ML5G-PS-007: Lightning-Fast Modulation Classification with Hardware-Efficient Neural Networks
The repository contains python source code (FAU_CA_AI_SOURCE.py) for training and testing 

1) a baseline model -- The baseline model weights checkpoint are saved in the FAU_CA_AI_baseline.pth file
2) the proposed optimized model (FAU_CA_AI_final_model.pth) --  whose inference cost is the one to be considered for evaluation for the ITU-ML5G-PS-007 competition
for modulation classification using the RadioML 2018.01A dataset provided by DeepSig.

# Instructions for reproduction

We introduce a neural network optimization technique based on multi-linear principal component analysis (MPCA) to reduce the width and depth of the initial overparameterized baseline model, while maintaining its classification accuracy. MPCA works on the activation map of each layer of the baseline model. Given that the activation maps strictly depend on the input data, a seed was set for the pytorch Random Sampler (without affecting the imposed numpy seed and guaranatee a fair train-test split). The seed allows the sampler to randomly select always the same data, so that the activation maps generated by the baseline model will stay the same and, consequently, the optimization will result in the same compressed/optimized neural network model. In this way, the code is reproducible and it will always return the same optimized model. 

The new model checkpoints were saved in the FAU_CA_AI_final_model.pth file. The inference cost is calculated by the sandbox at 4.3. The parts of the python code required to train both models are commented. 

If you would like just to run the code that loads the models and computes the inference cost in the sandbox, it is only required to change the path to the data set in the variable dataset_path. The code will print the accuracy obtained by the proposed optimized model 57.19%. 

If you wish to retrain the proposed optimized model from scratch, you will need to uncomment lines 428-454, and the name of the FAU_CA_AI_final_model.pth checkpoint file should be changed so that you will not overwrite the one that we provided. 

# FAU CA-AI Team https://ca-ai.fau.edu 
Giulia Muscara, Visiting M.S. students, LaSapienza University, Rome, Italy |
E-mail: gmuscara2021@fau.edu

Dariush Hassan, Undergraduate student researcher, Florida Atlantic University, Boca Raton, FL |
E-mail: dhassan2019@fau.edu

Dr. George Sklivanitis, Research Assistant Professor & I-SENSE Fellow, Florida Atlantic University, Boca Raton, FL |
E-mail: gsklivanitis@fau.edu
