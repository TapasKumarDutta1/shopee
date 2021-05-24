# Shopee
# Best submission
Trained models efficientnet-b0,b1,b2,b3 on the entire data with stochastic weight averaging and weighted loss. Trained efficientnet-b0 with group-KFold on labels with stratification on the count of each label. Used KNN with cosine distance to find the nearest neighbor for the embeddings:
- taking the 1st 1280 embeddings(b0,b1,b2,b3) and taking the mean 
- embeddings for b0,b1,b2,b3
- average of the 5-fold embeddings 
Final prediction is the union of 1st,3rd with the intersection of predictions from b0,b1 and b2,b3. Used TFIDF for text.
# Best single model
# Best text model
# Best text using bert
# Thing tried but didn't work
- Tried using [EAST](https://github.com/kurapan/EAST) for ocr. It gave unsatisfactory results so used the mask extracted from it and concatenated with the original image along the channels for extracting embeddings. For testing using the same procedure gave "Notebook Exceeded Allowed Compute". So created a new model by joining east model with my model such that the input image to model will be the concatenation of mask with the original data and input to east is original data. It gave satisfactory results but took too much time so could not use KFold with it.
- Tried to use distilbert,XLMRobert,bert for text data but score did not improve than using TFIDF.
- Implemented a simple neural network to classify is the results of the KNN were correct or not. Trained it with focal loss, binary-crossentropy on the out of fold five closest embeddings and the cosine distance from original data and the current image embedding and cosine distance but could not improve score.
- Tried to implement an xgboost on the same data. It took too much time to train(exceeded 2 hours).
- Trained the efficientnet-b0 with dynamic arcmargin, weighted loss, gem pooling best was using weighted loss with globalaveragepooling. 
# References
- https://www.kaggle.com/c/cdiscount-image-classification-challenge/discussion/45863
- https://www.kaggle.com/c/cdiscount-image-classification-challenge/discussion/45733

