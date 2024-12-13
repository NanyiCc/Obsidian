# Basic Information

This paper is about a neural network algorithm for semi-supervised node label learning from unbalanced data. The key points are:

- The paper proposes a new algorithm called COSNet for semi-supervised node label learning in graphs where the node labels are highly unbalanced (e.g. many more negatives than positives).
- COSNet is based on a parametric family of [[Hopfield networks]]. It learns the neuron activation values and thresholds in a supervised way to account for label imbalance.
- The network dynamics are restricted to only the unlabeled nodes, which allows COSNet to scale efficiently.
- A regularization method is introduced to prevent COSNet from trivial solutions on extremely unbalanced data.
- COSNet is applied to gene function prediction, where there is a severe class imbalance problem. It is shown to outperform other methods like label propagation, Gaussian random fields, and SVMs on this task.
- The algorithm converges efficiently to a local minimum of an energy function that is close to the global minimum. This makes it more scalable than methods that require the global minimum.
- COSNet balances precision and recall better than other methods on unbalanced gene function prediction benchmarks.

# Method

- COSNet is based on a parametric Hopfield network with binary neuron states. The parameters are:
    - W - Symmetric weight matrix representing connections between neurons
    - γ - Vector of neuron activation thresholds
    - α - Parameter determining neuron activation values (sinα and -cosα)

- COSNet separates neuron labels (+1 or -1) from activation values. This allows tuning the influence of positive vs negative neurons to handle label imbalance.

- It operates in two main steps:
	1. Learn optimal α and γ parameters:
	    - Project known labeled nodes into 2D points based on their connections.
	    - Learn a line separating positive and negative points.
	    - Line slope = α, intercept = -γ/cosα.
	    - Find α,γ that maximize F-score of point separation.
	2. Perform network dynamics:
	    - Fix labeled node states based on known labels.
	    - Run Hopfield dynamics on unlabeled nodes using learned α,γ.
	    - Equilibrium state induces labeling of unlabeled nodes.

- Restricting dynamics to unlabeled nodes makes COSNet efficient and scalable.
- A regularization method is added to prevent trivial solutions on highly imbalanced data.
- COSNet reaches a local minimum of an energy function that is typically very close to the global minimum.
- It balances precision and recall better than other methods on unbalanced tasks like gene function prediction.