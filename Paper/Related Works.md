LLM:
目前的大语言模型在大量未标记数据上进行预训练的LLM显示出了非凡的效果，并且在zero-和few-shot泛化能力令人震惊，目前最成功的大语言模型当属GPT-4，它能很好的几乎所有领域文本内容。同时，在开源领域，LLAMA，Alpaca, Vincuna等大语言模型也都在文本内容生成任务上展现出了优异的性能。在对LLM进行微调后，其在各个领域（比如哪些哪些领域）的表现已经展露头角，其在蛋白和医学领域的表现也令人期待。



PLM:
语言模型是一种表示学习技术，它从大规模的数据中学习数据内部蕴含的特征。PLMs被设计用于挖掘大规模蛋白质序列语料库中数据的内在联系，希望从这些氨基酸序列中学习蛋白质的表示。由于这一语料库数据庞大且人工标注困难，通过借鉴NLP任务上的经验，自监督学习方法在这一领域应用广泛，并且在结构、功能预测等下游任务中取得了令人印象深刻的性能。Transformer的使用使得PLMs拥有通过中间注意力图隐式捕捉到数据内部特征的能力。


自监督预训练方法已经广泛的应用与PLM的训练，并且使得这些模型能够基于蛋白质seq和stru信息，在各种下游任务中都取得了令人印象深刻的性能。然而，这些模型对于蛋白质的预测主要来自于对于蛋白质自身结构和序列的学习，对于已经经过研究的蛋白质，没有很好的从现有的论文数据中提取信息。于现有的工作相比，我们的方法让模型同时拥有蛋白质和论文信息，从而更好的捕获蛋白质特征并实现多轮对话能力。