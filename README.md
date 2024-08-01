# EnvClassification Methodology

While the IRS creates NTEE codes (National Taxonomy of Exempt Entities) to classify nonprofit organizations, these codes are very inaccurate and not of significant practical use to researchers. Historically, it has been necessary to hire handcoders to manually sort through the entire desired dataset before performing any analysis. In order to automatically classify the organizations, this approach trained and compared 3 separate models to predict which organizations are focused on 'environmental' issues. The leading model used a bag-of-words approach combined with a 3-layer fully connected model with 750 neurons in each hidden layer. The model took as input the processed and vectorized text description of the organization name + activity description. This approach resulted in prediction success with 93% accuracy, 90% precision, and 89% recall. Two other networks were also considered. First, the same network was trained with NTEE codes also included as an input node. However, this only increased the accuracy by a 1-2%, and resulted in a less generalizable model when used on other years (outside of the training data) due to the importance the model placed on NTEE weights. Therefore, this model was not ultimately selected. A transfer learning approach using the BERT HuggingFace large model was also trained using Amazon Sagemaker. However, due to the relatively small training dataset size of only 30,000 cases we were unable to take advantage of the increased complexity of this tranformer architecture/ability to see more complex patterns. Therefore, the eventual accuracy (even after sufficient training epochs) was ultimately lower than the initial CNN approach (although this would likely be different if a larger training dataset was available). This methodology outlines a novel use for existing machine learning algorithms, and helps contribute to a more complete mapping of the nonprofit space in the United States.


# Supporting Visualizations

![image](https://github.com/user-attachments/assets/b5ca274d-bd91-4306-bfb6-3bbdb5b0358f)

Model training process. In order to avoid overfitting, the loss function was minimized while also monitoring accuracy on the testing dataset (not shown to the model in training).

![image](https://github.com/user-attachments/assets/0595017a-89cd-45c8-9500-f366bebe29e7)

Percentage correct, false positive, false negative, and uncertain as produced by the final model (and split out by NTEE code, the current attempt by the IRS to hand-classify organizations). Notice how classifications are largely correct for all categories.

![image](https://github.com/user-attachments/assets/ee8d0531-d48b-4faf-a0b2-446b429239e6)

Absolute number correct, false positive, false negative, and uncertain, with NTEE code as a factor.

![image](https://github.com/user-attachments/assets/b4be978b-33fc-4cd7-ac84-0e91e3377448)

Overall number correct vs. false positive/negative/uncertain, without NTEE code as a factor.

![image](https://github.com/user-attachments/assets/b5c872e4-d7f8-4029-a67b-81128099b578)

Precision-recall curve for the model (visualizing the tradeoff between not 'missing' any '1' values vs. not mistakenly including and 'false positives'). This curve was used to optimize the model for the purposes of the paper, which would prefer to falsely exclude rather than falsely include organizations.

![image](https://github.com/user-attachments/assets/58b57d28-64c0-44fd-a6c4-ecaed9fcbb06)

Results for the alternative model trained that uses NTEE code (the IRS hand-classification codes, which are in general very inaccurate) as an included input into the model. Notice that, while the accuracy did improve by a percentage point or two, the tradeoff is not worth it due to overfitting and lack of generalization to other years (where NTEE codes are coded differently).
