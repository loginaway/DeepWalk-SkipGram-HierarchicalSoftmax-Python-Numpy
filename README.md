# DeepWalk-SkipGram-HierarchicalSoftmax

An implementation of DeepWalk and SkipGram models. 

Hierarchical Softmax is implemented through building a binary tree (See file: BinaryTree.py). 



## Dependencies
The packages used in this implementation is **pymysql, numpy and dgl**.  
Please install the dependencies by running `pip3 install -r requirements.txt`.

## Skip-Gram

The DeepWalk model uses Skip-Gram from Word2Vec as its kernal algorithm. Therefore, the implementation of Skip-Gram is vital to our work. Here we give a customized version of Skip-Gram that is specifically designed for walks (node-index sequences) instead of word sequences. 

The most formidable task is the implementation of Hierarchical Softmax, which is intended to reduce the overall computational complexity for calculating P(u_i|Phi(v_i)) from O(|V|) to O(log|V|), by conducting the calculation under a binary tree.

## DeepWalk

DeepWalk shows how to combine Random Walk on a graph with Skip-Gram algorithm. Each walk generated by Random Walk is a sequence of indexes of nodes in the graph, and it is put into Skip-Gram model to be used for calculation, where Phi and Psi is updated in this process by Stochastic Gradient Descent (SGD).

## Graph Representation

In our implementation, the graph is implemented through a python package dgl. It is imported as follows.

```python
from dgl import DGLGraph
```

And then use a series of operations to make an object G (DGLGraph object), which is then passed to DeepWalk for further computing.

By far we've only implemented a method to build graph from text file. For details, see Graphtools.py. 

'p2p-Gnutella08.txt' is the data set we use during our testing.

## How to start

You may code as follows.

```python
from DeepWalk import DeepWalk
from Graphtools import Graphtools

gtools=Graphtools()
G=gtools.fromText('p2p-Gnutella08.txt')
deepwalk=DeepWalk(G,3, 30, 3, 10)

deepwalk(unit_iter=100, multiProcess=1, showLoss=True)
deepwalk.save()
```

## References
\[1\] Bryan Perozzi, Rami AI-Rfou, Steven, Skiena, DeepWalk- Online Learning of Social Representations, 2014.

## About me

Hi there, I am currently an undergraduate at Fudan University, majoring in Data Science. If you have any question, please file an issue or contact me by 

loginaway@gmail.com
