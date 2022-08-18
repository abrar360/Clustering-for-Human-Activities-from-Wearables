# Clustering-for-Human-Activities-from-Wearables-by-Adopting-Nearest-Neighbors

Below are implementation details for "Clustering for Human Activities from Wearables by Adopting Nearest Neighbors" paper:

\noindent \textbf{Clustering and Fine-tuning the Cluster Assignments}
We train the pretext network for 100 epochs using the SGD optimizer with learning rate of $1e-3$, weight decay of $1e-4$, momentum of 0.9 and batch size of 256, and store the top-20 nearest neighbors of each window. 
The pre-trained weights are utilized to initialize the backbone of the clustering network. 
We set the number of output clusters to be equal to the number of ground truth classes for each dataset, solely for quantitative evaluation. 
Our clustering metrics require that the number of clusters match the number of ground truth classes. 
Additionally, previous baselines report results under this assumption \cite{abedin2020towards}. 

The clustering network is trained for 50 epochs using the Adam optimizer with learning rate $1e-4$, weight decay of $1e-4$, batch size of 64, entropy weight of 5 for the balanced datasets (UCI-HAR and MHealth), and a weight of 1 for all other datasets. 
The model with the lowest validation loss is then selected and fine-tuned for 100 epochs, as per the self-labeling protocol, using predictions with $\geq99\%$ confidence as pseudo-labels. 
For fine-tuning, the Adam optimizer with a learning rate of $1e-4$ and weight decay of $1e-4$ is used. 
Finally, the model is evaluated on the held out test set to obtain the reported results.

\noindent \textbf{Metrics}
We evaluate the accuracy of our trained clustering model on the test set using the following metrics: \emph{(i)} unsupervised clustering accuracy (ACC), which computes the prediction accuracy assuming the best possible mapping from cluster indices to labels, given the predictions.; and, \emph{(ii)} Normalized Mutual Information (NMI) score, which measures the degree of similarity or agreement between two labeling schemes, which in our case are the ground-truth labels and cluster assignments. 
These metrics are designed to be robust to permutations of cluster assignments, which is necessary because mappings from cluster indices to class labels can be arbitrary. Thus, we opt for these metrics for consistency to previous clustering baselines.
}

Code will be uploaded shortly after the release of the paper.
