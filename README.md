# Which Novel Do I Belong To?

Author: Kai Chen
Date:   October, 2020


## Introduction

The goal of the task is to build a deep learning model that classifies a given line as belonging to one of the following 12 novels.

0: alice_in_wonderland
1: dracula
2: dubliners
3: great_expectations
4: hard_times
5: huckleberry_finn
6: les_miserable
7: moby_dick
8: oliver_twist
9: peter_pan
10: talw_of_two_cities
11: tom_sawyer


## Methodology

The novel classification task is formulated as a classification problem. 
Given a sentence x, the object is to predict its label y.
To solve this problem, the sentences are transformed into pretrained text representations and then the text representations are fed to various deep learning architectures to classify the sentences into classes. 
The proposed solution is described as follows.

1. Create a character dictionary which contains the mapping of each character in xtrain_obfuscated.txt to an integer.

2. Transfer each sentence into a sequence of integers by using the character dictionary created in the first step.

3. All the sentences are padded with zeros to make all the sentences have the same length which is the maximum length of the sentences.

4. Download the pre-trained word embedding vectors of fastText and create a dictionary which contains the mapping of a character to a vector.

5. Create a matrix of one embedding for each character by enumerating all unique character in the character dictionary created in step 1 and locating the embedding weight vector from the loaded embedding from step 4.

6. Define a deep learning model. The input layer takes the sequence of integers (generated in step 2) as input.

7. The initial weights of the second layer are the values of the embedding matrix which is created in step 5.

8. The following layers of the deep learning model are composed of the combination of CNN and GRU layers.

9. 80% of the data in xtrain_obfuscated.txt and ytrain.txt is used to train the deep learning model. 20% of the data is considered as the validation set to compute the performance of the trained model.

10. Finally, all the data in xtrain_obfuscated.txt and ytrain.txt is used to train the deep learning model. 

11. The trained model is used to predict the class of the sentences in xtest_obfuscated.txt. 

12. Save the predictions to ytest.txt.

The details of the proposed solution are in the notebook, novel-classification.ipynb


a) your predictions (in the same format as ytrain.txt)

The predictions are in ytest.txt


b) Expected accuracy on the test set

Experiments show that the proposed deep learning model (CNN+GRU) achieves around 78% accuracy on the validation set. 
The validation set consists of 20% of the data randomly selected from xtrain_obfuscated.txt.
The rest 80% of the data is used as a training set to train the deep learning model.

Based on the assumption that the sentences of train and test sets belong to the same distribution and the results of the experiments, 
I would expect the proposed approach achieves similar accuracy (around 78%) on the test set.

Please note, due to the limited time available and the limited computation resources 
(the experiments were conducted on a Macbook pro 2015), 
I only trained the model with 60 epochs.
The learning curve shows that if I increase the number of epochs, the accuracy might be higher.


c) the source code for training and prediction (< 10MB)

The source code is in novel-classification.ipynb


d) a brief description of your method (optional)

A brief description of the solution is explained in the above section.




