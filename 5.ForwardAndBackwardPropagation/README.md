# MLP(Multi-Layer Perceptron)
In this project we will talk about MLP and we will implement it from scratch for solving some problems (e.g., Linear Regression, Classification,..).

Lets start with:
What is an MLP (Multi-Layer Perceptron)?
- A Multi-Layer Perceptron (MLP) is a type of artificial neural network made up of layers of neurons, where each neuron performs a simple computation:
                                                    Neuron output=σ(w⋅x+b)
  where:
  - 𝑥 is the input vector.
  - w is the weight vector.
  - 𝑏 is a bias term.
  - 𝜎(⋅) is a non-linear activation function (e.g., sigmoid, tanh, ReLU,..)
    
MLP Structure:
An MLP consists of:
- Input layer: receives the input features 𝑥
- Hidden layer(s): intermediate layers where the network learns representations
- Output layer: gives the final prediction (e.g., classification probability or regression value)

Biological Analogy
Just like the brain is composed of neurons that process signals, an MLP is made of artificial neurons that process data. Each neuron connects to the next layer via weighted edges, and learning means adjusting these weights to reduce error.

Simple Case: Logistic Regression as 1-Neuron MLP(Logistic Regression ≡ MLP-1 Neuron)
- Logistic regression is equivalent to a 1-neuron MLP with a sigmoid activation:
                                                   y* = 1/(1+e^(-u))   where u = θx and y* is the pridected valiue
- This neuron outputs the probability that 𝑦𝑖 = 1 given input 𝑥𝑖 :
                                                   y*i = P(yi=1 ∣ xi;θ)
- It creates a linear decision boundary (a line/hyperplane) that separates classes.

MLP Generalizes This Idea
While 1 neuron can separate linearly separable data, multi-layer MLPs allow the network to:
- Learn non-linear patterns
- Combine multiple neurons to form complex decision boundariesModel both classification and regression tasks
And this is possible because of:
- Non-linear activations (e.g., sigmoid, tanh)
- Layered composition of neurons


1. Forward Propagation in MLP:
   Forward propagation is the process by which input data passes through the network to produce an output. It’s like pushing values forward from one layer to the      next, applying transformations at each step.
   We will look at three cases:
   - Binary classification (Logistic Regression as MLP)
   - Regression using MLP
   - Multiclass classification using MLP

   1.1 Binary Classification: Logistic Regression as 1-Neuron MLP
       In this case, we want to model:
                                    y*i = P(yi=1 ∣ xi;θ)
       We compute a linear combination of inputs:
                                          u = θx
       Apply the sigmoid activation:
                                     y* = 1/(1+e^(-u))
       For binary classification problem and from bernoulli:
                            P(yi ∣ xi;θ) = y*i^(yi) x (1 - y*i)^(1 - yi)
       Which means:
       - If yi=1 the probability becomes y*i
       - If yi=0 the probability becomes 1-y*i
       This formulation will later be used in cross-entropy loss.
   
   1.2 Regression with MLP:
       Here, the goal is to predict a continuous value. MLP uses a linear output neuron, but the hidden layer uses non-linear activations.
       Given a network Structure example:
       - Two inputs 𝑥𝑖
       - Hidden layer: two neurons with sigmoid activations
       - Output layer: one neuron with identity activation (i.e., linear)
   
​

   













   
