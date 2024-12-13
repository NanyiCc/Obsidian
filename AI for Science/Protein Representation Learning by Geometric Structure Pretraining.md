# Basic Information:

- Title: Protein Representation Learning by Geometric Structure Pretraining (蛋白质几何结构预训练的表示学习)
- Authors: Zuobai Zhang, Minghao Xu, Arian Jamasb, Vijil Chenthamarakshan, Aurélie Lozano, Payel Das, Jian Tang
- Affiliation: Mila - Québec AI Institute, Université de Montréal, University of Cambridge, IBM Research, HEC Montréal, CIFAR AI Chair
- Keywords: protein representation learning, geometric structure pretraining, protein function prediction, protein structure prediction
- URLs: [Paper](https://arxiv.org/abs/2203.06125v5), [GitHub](https://github.com/DeepGraphLearning/GearNet)

# Brief introduction:

This paper proposes a method for learning effective protein representations by pretraining on the geometric structure of proteins. The authors develop a protein encoder called GearNet, which incorporates spatial information and performs relational message passing on protein residue graphs. They also introduce a geometric pretraining method based on contrastive learning and self-prediction tasks. Experimental results demonstrate that their approach outperforms existing sequence-based methods in protein function prediction and fold classification tasks, while using less pretraining data.

# Background:

Proteins play crucial roles in various biological tasks, and accurate protein function annotation methods are needed to bridge the gap between protein sequences and their functions. While sequence-based approaches have been effective, the structural information of proteins, which is known to determine their functions, has not been fully utilized. Existing structure-based protein encoders have limitations in capturing interactions between edges and have not explored pretraining methods using unlabeled 3D structures due to the scarcity of experimentally-determined protein structures. Recent advances in deep learning-based protein structure prediction methods have made it possible to efficiently predict structures for a large number of protein sequences. Motivated by this development, the authors propose GearNet, a protein encoder pretrained on a large number of protein structures. They introduce a contrastive learning framework with novel augmentation functions to discover biologically correlated protein substructures and perform self-prediction tasks. The authors aim to leverage the structural information of proteins to improve protein representation learning and achieve better performance in downstream tasks.

# Methods:

- a. Theoretical basis of the study:
    
    - The paper proposes the importance of learning effective protein representations for various tasks in biology, such as predicting protein function or structure.
    - Existing approaches pretrain protein language models on unlabeled amino acid sequences and then fine-tune them with labeled data.
    - The paper suggests exploring the power of pretraining on known protein structures.
    - The authors introduce a simple yet effective encoder called GearNet, which learns the geometric features of a protein by leveraging multiview contrastive learning and different self-prediction tasks.
- b. Technical route of the article (step by step):
    
    - The paper proposes a model called GearNet-Edge, which aims to learn representations encoding the spatial and chemical information of protein structures.
    - The model constructs a protein graph based on spatial features that are invariant under translations, rotations, and reflections in 3D space.
    - The graph consists of nodes representing the alpha carbon of each residue and edges representing different types of interactions between residues.
    - The model uses a relational graph convolutional neural network to learn graph representations, where a convolutional kernel matrix is shared within each edge type.
    - The model incorporates an edge message passing layer to model interactions between edges.
    - The layer constructs a relational graph among edges and uses angular information to determine the strength of their interaction.
    - The model achieves E(3)-invariance, meaning it is invariant to translation, rotation, and reflection.

# Results:

- a. Experimental settings in detail:
    
    - The experimental setup involves the use of the AlphaFold protein structure database for pretraining.
    - Two datasets are employed: 365K proteome-wide predictions and 440K Swiss-Prot predictions.
    - Four downstream tasks are evaluated: Enzyme Commission (EC) number prediction, Gene Ontology (GO) term prediction, fold classification, and reaction classification.
    - Dataset splits are used to ensure that the test set contains proteins with low sequence identity to the training set.
    
- Experimental results in detail:
    
    - The pretrained model demonstrates clear separation based on familial classification of proteins, indicating the effectiveness of the pretraining method.
    - The structure-based encoders outperform all baselines without pretraining on 7 out of 8 datasets.
    - GearNet and GearNet-Edge achieve competitive results on function prediction tasks (EC, GO, Reaction), and GearNet-Edge outperforms other baselines on EC, GO-BP, and GO-MF.
    - GearNet-Edge-IEConv achieves the best results on fold classification, indicating the importance of the IEConv layer in capturing structural information.
    - Pretraining with unlabeled structures significantly improves the performance of structure-based encoders.
    - The Multiview Contrast method achieves the best results on 7 out of 8 datasets and achieves state-of-the-art results on EC, GO-BP, GO-MF, Fold, and Reaction tasks.
    - The pretrained structure-based encoders perform on par with or even better than sequence-based encoders pretrained with much more data.
    - Their model is the only one that performs well on all four tasks, including fold classification, highlighting the potential of structure-based pretraining for learning protein representations.