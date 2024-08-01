# EnvClassification

This project overcame two problems:
1) Create code to scrape useful information from the data pool the IRS was storing data in
2) Develop a machine learning model to automatically classify 'environmental' organizations, in order to replace/facilitate the hand-coding process.







# Supporting Graphics

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
