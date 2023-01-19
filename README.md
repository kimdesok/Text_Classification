[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/selfcontrol7/Korean_Voice_Phishing_Detection/HEAD)

# AI-based Voice Phishing Detection in Korean Texts
Several machine learning and deep learning methods were developed to classify texts in Korean involved with voice phishing [1][2].
This repository is organized as below:
- **Attention** : contains source codes for investigating mostly an attention-based detection model and comparing its performance to other models such as CNN-BiSLTM, BiLSTM, LSTM, and CNN models 
- **Data_Collection_Preprocessing** : contains source codes for preprocessing raw data and create the datasets 
- **KoBERT** : contains source codes for implementing a KoBERT detection model
- **ML_DL_models** : contains  source codes for implementing a shadow ML and DL models

## Classification of Voice Phishing Texts vs. Normal Phone Conversation Texts
### A. Attention-based CNN-BiLSTM model
This model has been implemented in a script named 'Att-Based CNN-BiLSTM for Detecting Korean Vishing.ipynb' available at https://github.com/selfcontrol7/Korean_Voice_Phishing_Detection/tree/main/Attention (the original repository created by the first author[1][2])

Several minor things to mind before a fully blown execution of the script: <br>
1)Two text input files are required (that are NOT provided at the repo: One contains non vishing tokens and the orther contains vishing tokens.  <br>
For this step, outfile_space_20230117.npz needs to be loaded and is available at https://github.com/kimdesok/Korean_Voice_Phishing_Detection/tree/main/Attention. <br>
2) To evaluate the performance of a trained model, the model needs to be (re)compiled just before 'model.evaluate()' command.

> model = load_model(model_path, custom_objects=create_custom_objects()) <br>
> **model.compile(loss = "categorical_crossentropy", optimizer = Adam(learning_rate=learning_rate, decay=learning_decay), metrics = ['accuracy'])** <br>
> model.evaluate(X_test, y_test) <br>

3) pip install textblob, pydot, and graphviz (See the updated 'requirement.txt')

The figures below show the loss, accuracy, and the classification report.

<img src=https://user-images.githubusercontent.com/64822593/213070074-4acfba7b-6ad6-4428-aefa-708c3422f0c5.png width="600" height="480">
<img src=https://user-images.githubusercontent.com/64822593/213069089-a971596c-01fb-4749-910c-1daec9c14c99.png width="600" height="480">
<img src=https://user-images.githubusercontent.com/64822593/213071179-4e845c8d-541c-4913-80d9-8130317c4592.png width="600" height="300">

To compare the performance of the attention based model to other models such as CNN-BiLSTM, CNN, BiLSTM, and LSTM.
By training and testing the rest of the methods, a performance comparison table could be prepared:

![image](https://user-images.githubusercontent.com/64822593/213107883-1da2fbb5-443d-49b1-ba3f-604735677eb6.png)

The proposed attention based CNN-BiLSTM model and CNN-BiLSTM resulted in the same accuracy but the former converged a lot faster, about three times.
At the moment, it is not quite sure that this is a known fact.  CNN-BiLSTM seems to fluctuate a quite bit at the beginning of training in terms of accuracy and loss but eventually converged after about 25 epochs.

Later on CNN, BiLSTM, and LSTM....

## References
[1] M. K. M. Boussougou, S. Jin, D. Chang, and D.-J. Park, “Korean Voice Phishing Text Classification Performance Analysis Using Machine Learning Techniques,” Proceedings of the Korea Information Processing Society Conference, pp. 297–299, Nov. 2021.<br>
[2] M. K. M. Boussougou and D.-J. Park, “Exploiting Korean Language Model to Improve Korean Voice Phishing Detection,” KIPS Transactions on Software and Data Engineering, vol. 11, no. 10, pp. 437–446, Oct. 2022. <br>
