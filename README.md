## I. Project Goals and Tasks

This project aimed to predict CYP3A4 inhibition rates using molecular structure data represented as SMILES, supporting early-stage drug discovery and toxicity screening.

I was responsible for building and evaluating regression models based on molecular representations, including fingerprint-based machine learning models, pretrained chemical language models, and graph neural networks, and assessing performance using inhibition rate as the target variable.


## II. EDA Summary

The inhibition rate values ranged from 0 to 100 and showed a highly imbalanced distribution, with the majority of compounds exhibiting low to moderate inhibition and relatively few samples with high inhibition rates.

After incorporating external data from ChEMBL, the dataset size increased significantly, improving chemical diversity. However, high-inhibition compounds (above 70%) remained sparse, highlighting the need for data augmentation and specialised modelling strategies.


## III. Description of Approach

### Data Preparation

The molecular dataset was cleaned and standardised by validating SMILES strings, removing invalid or duplicate molecules, and aligning inhibition rate values across sources. External data from ChEMBL was integrated to increase data volume and chemical diversity.

To address data imbalance, particularly the scarcity of high-inhibition compounds, SMILES randomisation was applied to augment samples with inhibition rates above 70%.

### Modelling Approach

Multiple regression models were compared, including fingerprint-based machine learning models, gradient boosting methods, pretrained chemical language model embeddings (ChemBERTa), and graph neural networks (GIN).

All models were evaluated using MAE and RMSE with cross-validation, and the best-performing model was further tuned through hyperparameter optimisation before being used for final inhibition rate prediction.


## IV. Results – Inhibition Rate Prediction

Because the target variable was a continuous inhibition rate without extreme outliers, MAE and RMSE were used to evaluate model performance. Using baseline settings, fingerprint-based gradient boosting models achieved stable performance, while more complex models showed varying trade-offs between accuracy and computational cost.

Models based on molecular fingerprints with XGBoost and Gradient Boosting provided strong baseline results and were relatively efficient to train. Pretrained embedding-based models using ChemBERTa achieved comparable or slightly improved accuracy but required additional preprocessing and longer runtimes.

Graph neural network models (GIN) demonstrated potential in capturing molecular structure information, particularly for higher inhibition compounds, but required careful tuning and showed higher variance during training.

Hyperparameter tuning was applied to the best-performing models to optimise learning rates, regularisation strength, and model complexity. The final selected model achieved a local validation score of approximately 0.82 and a leaderboard score of around 0.77, and was used to generate inhibition rate predictions for unseen compounds.


## V. Conclusion

The preliminary results of the inhibition rate prediction models were promising, with reasonably low error values indicating that molecular structure information can be effectively used to estimate CYP3A4 inhibition.

However, the models showed limitations in consistently predicting high-inhibition compounds, largely due to data imbalance and the scarcity of such samples. While advanced models such as pretrained chemical language models and graph neural networks demonstrated potential, they did not fully resolve these issues on their own.

This suggests that relying solely on a single modelling approach is insufficient. Incorporating additional domain knowledge, targeted modelling strategies for high-risk compounds, or ensemble methods could lead to more robust and personalised predictions. Furthermore, a more balanced dataset or improved augmentation strategies would likely improve performance in future iterations.

