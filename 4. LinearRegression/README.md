Lets start with a brief introduction to Linear Regression and give some important definations then we will implement the Linear Regression two ways as usual, Sklearn version and form scratch version and we will compare each of them in terms of time and cost.

4) Linear Regression:

   1. Definitions:
      1. What is Linear Regression?
         - Linear regression is a fundamental supervised learning algorithm used to model the relationship between a dependent variable (target) and one or more 
           independent variables (features). It assumes that this relationship is linear. In another words, the target can be approximated by a straight line (in 
           higher dimensions, a hyperplane).
         - Simple linear regression models one feature:
                                                 𝑦 = w0 + w1𝑥
           Multiple linear regression models multiple features:
                                       𝑦 = w0 + w1𝑥1 + w2𝑥2 + ⋯ + wn𝑥n
   2. Setup:
      - Given:
        ➔ A training dataset of 𝑛 examples (instances).
      - Each example:
        ➔ Comes as a pair of input and output:
                                        (𝑥𝑖 ,𝑦𝑖)
        𝑥𝑖 : the input (like features or conditions)
        𝑦𝑖 : the output (the result we want to predict)
      - 𝑥𝑖 is a vector with d attributes:
        ➔ This means each input 𝑥𝑖 could have many features (not just one!).
      - 𝑦𝑖 ∈ R:
        ➔ Each output is a real number (not a category or class).
    3. Goal:
       - The goal is predicting a continous values by learning  the parameters 𝜃 (theta).
       - Training Phase:
         ➔ You use the inputs (𝑥1 , …,𝑥𝑛) and outputs (𝑦1 , …, 𝑦𝑛).
         ➔ You feed them into a Learning Algorithm.
         ➔ The algorithm learns and produces the parameters 𝜃 (theta).
         ➔ After training, your prediction function looks like:
                                    f(𝑥) = 𝜃 + 𝜃1𝑥1 + 𝜃2𝑥2 + ⋯ + 𝜃n𝑥n
            - where:
              - 𝜃 is the bias term (intercept).
              - 𝜃1, 𝜃2, …, 𝜃𝑛 are the weights for each feature.
       - Validation / Prediction Phase:
         ➔ Now you are given new unseen inputs:
                                     𝑥n+1, 𝑥n+2, …
         ➔ Use the learned parameters 𝜃 and your Prediction Machine to compute:
                                 𝑦^n+1, 𝑦^n+2, …
            - where:
              - 𝑦^ are the predicted outputs (using the trained model).
    4. Calculations:
       - Least Squares Method:
         ➔ The Least Squares method is used to find the best-fitting line by minimizing the total squared difference between the predicted values and the actual 
            target values.
            Mathematically, the cost function is:
                                                  J(w) = 1/(2m) * ∑(𝑦 - 𝑦^)^2
            Where:
              - 𝑚: number of training examples
              - 𝑦: predicted value
              - 𝑦: actual value
            This function is also called the Mean Squared Error (MSE) cost.
   
       #To solve a linear regression problem using the least squares method, there are two common approaches:

       1. Analytical Method ➔ Normal Equation:
          ➔ This method involves taking the derivative of the cost function (Mean Squared Error) and setting it equal to zero. Solving the resulting equation 
             yields the optimal weights directly:
                                                   𝜃 = ((XT) X)^−1 (XT)Y
             - It gives an exact solution.
             - Best for small to medium datasets.
             - Requires matrix inversion, which is computationally expensive for large or high-dimensional data.
       2. Iterative Method ➔ Gradient Descent:
          ➔ Instead of solving algebraically, gradient descent finds the minimum of the cost function by repeatedly updating the weights:
                                                    𝜃 := 𝜃 − α⋅∇J(𝜃)
             Where:
               - α is the learning rate.
               - ∇J(w) is the gradient (slope) of the cost function.
             This method:
               - Suitable for large datasets, where inversion is too slow or unstable.
               - Requires tuning and multiple iterations to converge.
          

          


​

           
           
            
           
         
​



















