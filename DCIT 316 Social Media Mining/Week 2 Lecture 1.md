# Eager vs Lazy Learning
**Eager Learning** is a learning method in which the system tries to construct an input-independent target function during training
**Lazy Learning**  waits till the last minute before classifying the data

A **decision tree** is a flowchart-like tree structure 
- Each internal node denotes a test on an attribute
- Each branch represents an outcome of the test
- Each leaf node holds a class label
- It learns to partition based on the attribute value. Partitions are done *recursively*
- Is robust to outliers, and is able to model non-linear decision boundaries
- Demo using IRIS dataset
-  Can be used in
	- Medicine
	- Spam filtering
	- Fraud detection

**KNN**
	- Handwriting detection
	- Recommender systems
	- Image recognition

**Unsupervised learning** - Read on *Topic Modelling* , *User segmentation* , *Distance Measures*, *K-Means Clustering*
- *Distance Measures* - Determines the similarity between data points. Common measures include Euclidean distance, Manhattan distance, cosine similarity
- *K-means* - Groups data into 'k' clusters. Uses distance measures to assign each data point to the cluster whose center / centroid is nearest
- *Sentiment Analysis* = Transforms text data into vectors using techniques like TF-IDF or word embeddings 