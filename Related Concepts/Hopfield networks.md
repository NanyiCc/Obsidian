A Hopfield network is a type of recurrent artificial neural network that is used as a content-addressable memory system. Some key properties of Hopfield networks:

- The network contains neurons with binary states (-1 or +1). 

- The connections between neurons are symmetric, described by a weight matrix W.

- Each neuron has a bias/threshold term. 

- The state of a neuron is updated based on the weighted input from connected neurons.

- The network has an energy function associated with each state. 

- The network dynamics are guaranteed to converge to a minimum of the energy function.

- This minimum represents a stored memory or pattern in the network.

- Hopfield networks are often used for optimization, content-addressable memory, and binary classification problems.

- They have the ability to recover a stored pattern from a corrupted or incomplete version.

- A key advantage is that they converge efficiently to a local minimum, unlike methods that require the global minimum.

- Their simple binary neuron model allows fairly easy hardware implementation.

So in summary, a Hopfield network has binary neuron states, symmetric connections, an energy function, and dynamics that converge to stored pattern memories corresponding to local minima of the energy landscape. This makes them useful for optimization and memory problems.