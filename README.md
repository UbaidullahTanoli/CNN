# CNN

This project focuses on the predictive power of a CNN on Medical (Chest X-ray images) dataset to accurately classify an image as normal or not. This is part of a larger project which combines CNN and LLM to learn from images and the corresponding medical reports of the same patient to make highly accurate binary classification. This project serves as a baseline to compare CNN+LLM.

## Data

Indiana University Chest X-ray dataset was used in the project.
The dataset contains 7,470 pairs of images and reports and measures 14.19 GB. The reports were used as ground truth to compare the predictions of CNN.
IU X-ray (Demner-Fushman et al., 2016) can be accessed [here](https://www.kaggle.com/datasets/raddar/chest-xrays-indiana-university)

## CNN Model

The architecture of EfficientNet-B1 is used to process and convert the images into vector embeddings. EfficientNet-B1 is a Depp CNN pretrained on Medical dataset (ImageNet) and has ~6.5 Million trainable parameters. EfficientNet‑B1 component is fine‑tuned on the dataset I used, while the BioBERT model remains frozen. I've leveraged pre‑trained knowledge from both models but only updated the image branch and the fusion MLP during training. It's been proven that EfficientNet architecture gives slightly better accuracy per parameter. Refer to the research paper [here](https://arxiv.org/pdf/1905.11946)

## Parameters

| Parameters | Specification |
| --- | --- |
| Optimizer | Adam |
| Loss Function | Cross Entropy |
| Learning Rate | 0.003 |
| Number of Epochs | 40 |
| Train / Test data ratio | 80 : 20 |

## Results

| Epoch | Phase | Loss    | Accuracy | Precision | Recall  | F1-Score |
|-------|-------|---------|----------|-----------|---------|----------|
| 1     | Train | 0.6318  | 0.6470   | 0.6881    | 0.8164  | 0.7468   |
|       | Val   | 0.6103  | 0.6439   | 0.6443    | 0.9990  | 0.7834   |
| 2     | Train | 0.5908  | 0.6845   | 0.7190    | 0.8293  | 0.7702   |
|       | Val   | 0.5546  | 0.7182   | 0.7978    | 0.7539  | 0.7752   |
| 3     | Train | 0.5622  | 0.7113   | 0.7448    | 0.8325  | 0.7862   |
|       | Val   | 0.5569  | 0.6814   | 0.7051    | 0.8692  | 0.7786   |
| 4     | Train | 0.5440  | 0.7192   | 0.7572    | 0.8238  | 0.7891   |
|       | Val   | 0.5666  | 0.7175   | 0.7905    | 0.7643  | 0.7772   |
| 5     | Train | 0.5118  | 0.7472   | 0.7868    | 0.8277  | 0.8068   |
|       | Val   | 0.5716  | 0.6934   | 0.7809    | 0.7290  | 0.7540   |
| 6     | Train | 0.4815  | 0.7686   | 0.8008    | 0.8480  | 0.8237   |
|       | Val   | 0.5806  | 0.7162   | 0.7383    | 0.8671  | 0.7975   |
| 7     | Train | 0.4263  | 0.8073   | 0.8381    | 0.8648  | 0.8512   |
|       | Val   | 0.6141  | 0.7236   | 0.7624    | 0.8297  | 0.7946   |
| 8     | Train | 0.3681  | 0.8411   | 0.8670    | 0.8868  | 0.8768   |
|       | Val   | 0.5981  | 0.7269   | 0.7686    | 0.8245  | 0.7956   |
| 9     | Train | 0.2834  | 0.8788   | 0.9020    | 0.9086  | 0.9053   |
|       | Val   | 0.8349  | 0.6867   | 0.6947    | 0.9169  | 0.7905   |
| 10    | Train | 0.2259  | 0.9024   | 0.9205    | 0.9270  | 0.9237   |
|       | Val   | 0.8027  | 0.7035   | 0.7908    | 0.7342  | 0.7614   |
| 11    | Train | 0.1781  | 0.9313   | 0.9429    | 0.9498  | 0.9464   |
|       | Val   | 0.7950  | 0.6901   | 0.7887    | 0.7092  | 0.7469   |
| 12    | Train | 0.1529  | 0.9424   | 0.9563    | 0.9533  | 0.9548   |
|       | Val   | 0.8718  | 0.6934   | 0.7772    | 0.7352  | 0.7556   |
| 13    | Train | 0.1139  | 0.9595   | 0.9690    | 0.9674  | 0.9682   |
|       | Val   | 1.2281  | 0.6794   | 0.7636    | 0.7279  | 0.7453   |
| 14    | Train | 0.1202  | 0.9565   | 0.9646    | 0.9672  | 0.9659   |
|       | Val   | 0.9777  | 0.7041   | 0.7474    | 0.8172  | 0.7808   |
| 15    | Train | 0.0957  | 0.9625   | 0.9696    | 0.9716  | 0.9706   |
|       | Val   | 1.0847  | 0.6573   | 0.8076    | 0.6147  | 0.6981   |
| 16    | Train | 0.0942  | 0.9662   | 0.9715    | 0.9756  | 0.9735   |
|       | Val   | 1.1547  | 0.7082   | 0.7460    | 0.8297  | 0.7856   |
| 17    | Train | 0.0889  | 0.9667   | 0.9720    | 0.9758  | 0.9739   |
|       | Val   | 1.2092  | 0.6707   | 0.7524    | 0.7290  | 0.7405   |
| 18    | Train | 0.0753  | 0.9734   | 0.9782    | 0.9800  | 0.9791   |
|       | Val   | 1.0701  | 0.6921   | 0.7574    | 0.7684  | 0.7629   |
| 19    | Train | 0.0805  | 0.9700   | 0.9751    | 0.9779  | 0.9765   |
|       | Val   | 1.3888  | 0.6908   | 0.7458    | 0.7892  | 0.7669   |
| 20    | Train | 0.0696  | 0.9752   | 0.9798    | 0.9814  | 0.9806   |
|       | Val   | 1.3290  | 0.7028   | 0.7488    | 0.8110  | 0.7787   |
| 21    | Train | 0.0794  | 0.9692   | 0.9743    | 0.9774  | 0.9759   |
|       | Val   | 1.0472  | 0.7055   | 0.7517    | 0.8110  | 0.7802   |
| 22    | Train | 0.0662  | 0.9729   | 0.9780    | 0.9795  | 0.9787   |
|       | Val   | 1.1212  | 0.7008   | 0.7925    | 0.7259  | 0.7577   |
| 23    | Train | 0.0632  | 0.9782   | 0.9819    | 0.9840  | 0.9829   |
|       | Val   | 1.3890  | 0.6901   | 0.7847    | 0.7155  | 0.7485   |
| 24    | Train | 0.0625  | 0.9754   | 0.9793    | 0.9821  | 0.9807   |
|       | Val   | 1.1134  | 0.7008   | 0.7745    | 0.7560  | 0.7651   |
| 25    | Train | 0.0652  | 0.9769   | 0.9811    | 0.9827  | 0.9819   |
|       | Val   | 1.2692  | 0.7062   | 0.7615    | 0.7923  | 0.7766   |
| 26    | Train | 0.0650  | 0.9747   | 0.9788    | 0.9816  | 0.9802   |
|       | Val   | 1.2158  | 0.6941   | 0.7669    | 0.7549  | 0.7609   |
| 27    | Train | 0.0559  | 0.9787   | 0.9832    | 0.9835  | 0.9833   |
|       | Val   | 1.6451  | 0.6894   | 0.7338    | 0.8131  | 0.7714   |
| 28    | Train | 0.0538  | 0.9796   | 0.9835    | 0.9845  | 0.9840   |
|       | Val   | 1.3671  | 0.6827   | 0.7539    | 0.7539  | 0.7539   |
| 29    | Train | 0.0487  | 0.9826   | 0.9856    | 0.9871  | 0.9864   |
|       | Val   | 1.1919  | 0.6908   | 0.7411    | 0.7996  | 0.7692   |
| 30    | Train | 0.0560  | 0.9796   | 0.9830    | 0.9850  | 0.9840   |
|       | Val   | 1.1689  | 0.6921   | 0.7628    | 0.7580  | 0.7604   |
| 31    | Train | 0.0587  | 0.9771   | 0.9824    | 0.9816  | 0.9820   |
|       | Val   | 1.3553  | 0.6995   | 0.7397    | 0.8235  | 0.7794   |
| 32    | Train | 0.0477  | 0.9834   | 0.9871    | 0.9869  | 0.9870   |
|       | Val   | 1.5833  | 0.6901   | 0.6959    | 0.9221  | 0.7932   |
| 33    | Train | 0.0480  | 0.9843   | 0.9869    | 0.9884  | 0.9877   |
|       | Val   | 1.0839  | 0.6981   | 0.7535    | 0.7902  | 0.7714   |
| 34    | Train | 0.0402  | 0.9873   | 0.9898    | 0.9903  | 0.9900   |
|       | Val   | 1.4995  | 0.6928   | 0.7287    | 0.8339  | 0.7777   |
| 35    | Train | 0.0386  | 0.9859   | 0.9879    | 0.9900  | 0.9890   |
|       | Val   | 1.6914  | 0.6821   | 0.7711    | 0.7207  | 0.7450   |
| 36    | Train | 0.0522  | 0.9814   | 0.9850    | 0.9858  | 0.9854   |
|       | Val   | 1.1183  | 0.6914   | 0.7261    | 0.8370  | 0.7776   |
| 37    | Train | 0.0492  | 0.9834   | 0.9859    | 0.9882  | 0.9870   |
|       | Val   | 1.3838  | 0.6954   | 0.7619    | 0.7674  | 0.7646   |
| 38    | Train | 0.0421  | 0.9858   | 0.9885    | 0.9892  | 0.9888   |
|       | Val   | 1.4556  | 0.6934   | 0.7638    | 0.7591  | 0.7615   |
| 39    | Train | 0.0317  | 0.9901   | 0.9916    | 0.9929  | 0.9923   |
|       | Val   | 2.0211  | 0.6941   | 0.7189    | 0.8629  | 0.7843   |
| 40    | Train | 0.0474  | 0.9824   | 0.9851    | 0.9874  | 0.9862   |
|       | Val   | 1.5860  | 0.6827   | 0.7349    | 0.7944  | 0.7635   |

## Conclusion

