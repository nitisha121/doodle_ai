## Tensorflow without a PhD ([link](https://codelabs.developers.google.com/codelabs/cloud-tensorflow-mnist/#2))

- __tensor:__ like a matrix but with arbitrary #dims.
- activation function takes in some linear function like __L_n = weights*inputs + biases__

##### Softmax activation function: e^L_n / ||e^L||
- exponential function is steeply increasing -> will increase differences between the elements of the vector and quickly produce large values.
- when you normalise the vector largest element will be normalised to a value close to 1 while all the other elements will end up divided by a large value and normalised to something close to 0
- resulting vector clearly shows which was its largest element, the "max", but retains the original relative order of its values, hence the "soft"
- keep as activation fcn on last layer, works best for classifying


- __epoch__: 50,000 training images -> feed 100 into training loop at once for 500 iterations
- mini batch vs. stochastic: mini batch: multiple inputs per iteration, larger matrices --> faster to optimize on GPU, faster convergence, stochastic: 1 input per iteration


- __Broadcasting:__ trick used in Python and numpy -> extends how normal operations work on matrices with incompatible dimensions. _"Broadcasting add":_  "if you are adding two matrices but you cannot because their dimensions are not compatible, try to replicate the small one as much as needed to make it work

##### One layer neural network:
Y = softmax(X*W + b)

Y: predictions [100,10]
softmax: activation function applied line by line  
X: Images [100, 784 (100 28px*28px images)]
W: Weights [784, 10]
b: Biases [10] broadcast on all lines

#### Gradient Descent

##### Cross entropy
- The neural network produces predictions, now measure how good they are with something like euclidian distance from true value. Try cross-entropy: Negate [ sum of actual probabilities (one hot encoding) * log(computed probabilities) ]
- Training NN == adjusting W and B to minimize cross entropy loss function


We get a __gradient__ through computing the partial derivatives of cross entropy w.r.t. the weights and biases. (tf will compute for us)

Gradient descent follows the path of steepest descent - updating W and B by a fraction of the gradient - until we converge to local min.

__Learning rate:__ The magnitude of the fraction of the gradient that you move down by.

Training loop:
Training digits and labels => loss function => gradient (partial derivatives) => steepest descent => update weights and biases => repeat with next mini-batch of training images and labels


Tensorflow's deferred execution model: static graph for sequence of computation.

- For final layers: using sigmoid (steep on zero, steep on 1) vs. softmax is the same for binary classifying, but for multi-classification (use softmax - probabilities add to 1)
- For intermediate layers, ReLU (rectified learning unit) [tf.nn.relu vs tf.nn.sigmoid] is a good activation fcn for intermediate layers

##### Optimizer

In high dim spaces, there are 'saddle points' where they aren't local minima but gradient is zero. tf optimizers will safely overlook these.
Usually tf.train.AdamOptimizer > tf.train.GradientDescentOptimiser.

- If you see NaNs in your output, add tf.nn.softmax_cross_entropy_with_logits to your code.
- adjust learning rate with fractions: lr = 0.0001 + tf.train.exponential_decay(0.003, step, 2000, 1/math.e)


When you notice __overfitting__ use a regularization technique called __dropout__: drop random neurons at each iteration of the training loop, choose a probability for a neuron to be kept (b/w 50-75%). Overfitting can be caused by bad network / not enough data / too many neurons.
