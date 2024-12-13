**研究学习的个人笔记**

---

Model structure:
--

![[Model Structure.excalidraw]]


---

模型训练时可能可以使用到的methods：
--
1. Multimodal fusion: This method combines protein structure and textual information into a single representation that can be fed into a machine learning model. This can be done using techniques such as concatenation, average fusion, or multimodal transformers.
2. Attention mechanisms: Attention mechanisms can be used to focus on specific parts of the protein structure and text that are relevant to each other. This helps the model to selectively attend to the most important parts of the input data.
3. Graph neural networks (GNNs): GNNs can be used to represent protein structures as graphs, allowing the model to learn the relationships between different parts of the protein. This can be combined with textual information to enable the model to understand the connections between the protein structure and the text.
4. Multitask learning: This approach involves training a single model on multiple tasks simultaneously. For example, a model can be trained on both protein structure prediction and text classification tasks. This can help the model learn shared representations between the two modalities.
5. Transfer learning: This method involves pre-training a model on a large dataset and fine-tuning it on a smaller dataset that includes both protein structure and text. The pre-trained model can learn general features that are useful for understanding the relationships between protein structure and text.
6.  Generative models: Generative models, such as Generative Adversarial Networks (GANs) or Variational Autoencoders (VAEs), can be used to learn a shared representation between protein structure and text. These models can generate new data that combines features from both modalities.
7. Clustering: Clustering algorithms, such as k-means or hierarchical clustering, can be used to group similar protein structures and text together. This can help identify patterns and relationships between the two modalities.
8. Contrastive Learning: In Contrastive Learning, the model is trained to maximize the similarity between positive examples and minimize the similarity between negative examples. Positive examples are typically pairs of data that are similar or related in some way, such as two images of the same object, while negative examples are pairs of data that are dissimilar or unrelated, such as two images of different objects.

---

下游任务可能可以涉及的蛋白质性质：
--
1. molecular functions, biological processes and subcellular locations

---

下游任务：
--
1. The first task is bidirectional language modeling of protein sequences. 
2. The second task is Gene Ontology (GO) annotation prediction, which captures diverse protein functions 
3. 蛋白质功能注释（from SiamDiff)
4. 蛋白质-蛋白质相互作用预测 (from SiamDiff)
5. 突变效应预测 (from SiamDiff)
6. 残基结构贡献 (from SiamDiff)
7. 蛋白质结构排序 (from SiamDiff)

---

蛋白质的图表述
--
一维序列：SMILES式，通常使用1D-CNN和注意力机制来进行编码
二维图：能描述分子的几何连通性
三维几何图：分子结构内部实体之间的空间关系可以通过它们的三维坐标在三维空间中表示，网络中的节点和边的特征通常由特定的知识给出。