# Drug-Drug-Interactions
The reaction between two or more drugs (drug-drug interaction) or between a drug and a sepecific food (drug-food interaction) is called a
drug interaction. This phenomenon can have threatening side effects on body and it may also make your medication stop working, become less effective, or too strong. Therefore learning about drug interactions and avoiding them plays a critical role in everyone’s health
## Dataset
I will use the [ogbl-ddi](https://ogb.stanford.edu/docs/linkprop/#ogbl-ddi) dataset which is a homogeneous, unweighted, undirected graph, representing the drug-drug interaction network. Each node represents an FDA-approved or experimental drug. Edges represent interactions between drugs and can be interpreted as a phenomenon where the joint effect of taking the two drugs together is considerably different from the expected effect in which drugs act independently of each other.


| Number of Nodes | 4267 |
| ---------------- | ---------------- |
| Number of edges     | 1067911     |

![Image](/img/1.png)

## Task
The task is to predict drug-drug interactions given information on already knowndrug-drug interactions.

## Evaluation Metric
For evaluation, the model is supposed to rank true drug interactions higher thancnon-interacting drug pairs. The [hits@k](https://stackoverflow.com/questions/58796367/how-is-hitsk-calculated-and-what-does-it-mean-in-the-context-of-link-prediction) describes the fraction of true entities that appear in the first k entities of the sorted rank list
![Image](/img/2.jpg)

## Proposed Methods
### Node2Vec and MLP
node2vec is an algorithm for learning features and representations of a given graph. For any given graph it can learn representations of its nodes which can be used in several tasks. Such as node classification, link prediction and graph level classification. Node2Vec uses flexible, biased random walks that can trade off between local and global structures of a network. In this way it can generate features. Firstly I generate embeddings using Node2Vec. Then I train a MLP using extracted embeddings.

### GNN
I use GCN to extract features and then I use MLP with the following architecture. Refer to [CS224W](https://www.youtube.com/watch?v=RU9uTa_-ZOw&list=PLoROMvodv4rPLKxIpqhjhPgdQy7imNkDn&index=20) for more information on Graph Neural Networks. 
 
![Image](/img/3.jpg)


## Results
* Result of GNN
  ![Image](/img/gnn1.jpg "Train and Validation Hits Scores")
  
* Result of Node2Vec
  ![Image](/img/node2vec.jpg "Train and Validation Hits Scores")
