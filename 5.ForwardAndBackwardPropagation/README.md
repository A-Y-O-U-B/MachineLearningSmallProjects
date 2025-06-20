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
       Output Neuron: y* = θ5 + θ6.o11 + θ7.o12    ; where o11 and o12 is the the output of the activation function.
       This combination allows us to model complex non-linear functions by summing “bumps” from sigmoid outputs.
       - θ6"squeezes" → controls steepness.
       - 𝜃7"flips" → controls direction (positive/negative)
       Expectation Interpretation:
       We treat the output as:
                         y*i = E(yi ∣ xi;θ)
       And assume Gaussian noise:
                         P(yi ∣ xi;θ) = 1/(✓​2πσ ) x exp(-(y*i-yi)^2 / ​2σ)
       This leads naturally to Mean Squared Error (MSE) as the loss.
   
   1.3 Multiclass Classification using MLP + Softmax:
       Now we have multiple output classes say 3 classes.
       the structure will be:
       - Input → hidden layer (with sigmoid) → 3 output neurons (one per class)
       - Instead of sigmoid at the end, we use softmax to turn raw outputs into probabilities:
         Let 𝑢21,𝑢22,𝑢23 be the raw scores from output neurons.
                            y*i1 = e^𝑢21 / (e^𝑢21 + e^𝑢22 + e^𝑢23) and same for y*i2 and y*i3
         This guarantees:
         - All probabilities are positive
         - They sum to 1
         - No need for sigmoid


2. Backward Propagation (How MLP Learns)
   Backward propagation is how an MLP learns from its mistakes.
   After making a prediction, the network compares its output to the true value to measure how wrong it was (the error). Then, starting from the output layer, it     sends the error backward through the network to adjust the weights.
   Each weight is updated based on how much it contributed to the error — this is done using a rule called the chain rule. The network uses this information to       tweak the weights slightly, so next time the prediction gets a bit better.
   This process is repeated many times, helping the network gradually improve.










   
