
# 中文关键总结

使用了一种方法，对数据分类，增加边界样本集中的正样本，减少非边界样本集上的负样本。
# Basic Information

这篇论文主要研究了不平衡数据处理方法。主要内容如下:
1. 引言部分提出了不平衡数据分类的问题及其重要性。
2. 相关工作部分回顾了当前不平衡数据分类的主要方法,包括过采样和欠采样等数据级方法及其改进算法。
3. 方法部分提出了一种基于边界混合重采样的不平衡数据分类方法。该方法通过计算每个样本的k近邻异常度,划分边界样本集和非边界样本集。对边界少类样本采用改进的SMOTE算法过采样,对非边界多类样本采用基于距离的欠采样。
4. 实验部分在8个不同不平衡数据集上与其他方法进行对比,结果表明该方法可以有效提高少类样本的召回率、F1值、G-mean等指标。
5. 结论部分总结了该方法的效果及优点。

# Method

This paper propose an unbalanced data classification method based on boundary mixed resampling.

Here are the main steps:

1. Calculate the k-nearest neighbor outlier degree for each sample, and divide the samples into boundary sample set and non-boundary sample set using a preset threshold.
2. For the positive (minority) samples in the boundary sample set, use the improved SMOTE algorithm for over-sampling, while also adopting certain strategies to balance the numbers of positive and negative samples in the boundary sample set.
3. For the negative (majority) samples in the non-boundary sample set, use distance-based undersampling algorithm to remove some of the negative samples.
4. Integrate the above two steps to obtain a new balanced training sample set.

This approach considers the importance of boundary samples, reduces the interference of non-boundary negative samples on classification, and balances the numbers of positive and negative samples, thereby improving classification performance.

Therefore, boundary mixed resampling makes full use of the differences between boundary and non-boundary samples, and combines over-sampling and under-sampling to achieve better sampling results.

# Results 

Here are the main effects and advantages of the boundary mixed resampling method for imbalanced data classification:

1. Effectiveness - It can improve evaluation metrics like recall, F1 score, G-mean for positive samples, thus enhancing classification performance. Experiments showed significant improvements compared to other methods.

2. Advantages - It balances the numbers of positive and negative samples better, avoiding overfitting. It combines the importance of boundary samples and the role of non-boundary ones, making the sampling more reasonable. 

3. It handles class imbalance, overlapping distributions, and small disconnectedness effectively.

4. By distinguishing boundary and non-boundary samples, it retains more important information while removing redundant and irrelevant samples, improving classification.

5. It integrates both over-sampling and under-sampling, achieving the merits of both. Over-sampling retains positive class information while under-sampling removes redundant negatives.

6. It has low computational cost and time complexity, suitable for large-scale imbalanced data. 

7. It is decoupled from the classifier and has good versatility, can be combined with different models.

In summary, it balances the distributions more reasonably while ensuring performance. Thus it is an effective solution for imbalanced data classification.

