# Eigendecomposition of a Matrix
In this project we will talk about Eigendecomposition of a Matrix, we will start with a brief definitions and Eigendecomposition's relationship to Machine Learning then we will dive into the Calculation of Eigendecomposition and we will do it two ways. First using numpy then we will do it manually to compare each of these ways and note the results.

2) Eigendecomposition of a Matrix:

   1. Definitions:
      1. Matrix Manipulation:
         - Matrix manipulation involves performing operations such as addition, multiplication, transposition, and inversion on matrices. These are essential in 
           representing and transforming data in machine learning.
           
      2. Eigenvalues and Eigenvectors:
         - For a square matrix 𝐴, an eigenvector 𝑣 and its corresponding eigenvalue 𝜆 satisfy:
                                             𝐴𝑣 = 𝜆𝑣
           This means that multiplying matrix 𝐴 by vector 𝑣 only stretches (or shrinks) 𝑣 by a factor 𝜆, without changing its direction.
         - Normally when we multiply a matrix by a vector, the vector changes. It gets rotated, flipped or stretched. But somtimes there are special vectors that 
           only get stretched or shrunk without changing direction. So these special vectors are called eigenvectors and the amount they get stretched or shrunk is 
           called their eigenvalue.
           
   2. Relationship to Machine Learning:
      - Matrix operations and Eigendecomposition(eigenvalues and eigenvectors) are core mathematical tools in many machine learning techniques, especially in 
        dimensionality reduction, data transformation, and optimization. We will talk briefly about some of these techniques.
          1. Principal Component Analysis (PCA):
             - PCA is one of the most common uses of eigenvalues and eigenvectors. It transforms the original features into a set of orthogonal components 
               (principal components) where these components are derived from the eigenvectors of the covariance matrix of the dataset. The eigenvalues indicate 
               the amount of variance captured by each principal component.
          2. Singular Value Decomposition (SVD):
             - SVD is a powerful matrix factorization technique used to decompose any 𝑚×𝑛 matrix 𝐴 into three matrices:
                                              A = 𝑈Σ𝑉^𝑇
               Where:
               - 𝑈: left singular vectors (orthogonal)
               - Σ: diagonal matrix of singular values (square roots of eigenvalues)
               - 𝑉^𝑇: right singular vectors (orthogonal)
          3. Spectral Clustering:
             - This method uses the eigenvectors of a similarity matrix (like a graph Laplacian) to reduce dimensionality before applying clustering algorithms 
               such as k-means.
          4. Latent Semantic Analysis (LSA):
             - In Natural Language Processing (NLP), LSA uses Singular Value Decomposition (SVD), which involves eigenvalues, to identify patterns in relationships 
               between terms and documents.
          5. Linear Discriminant Analysis (LDA):
             - LDA is a supervised method that finds the linear combination of features that best separates classes. It uses eigenvectors of the scatter matrices 
               to perform the projection.
      
   3. Why it is important:
      - Understand how a matrix transforms space, Reduce computational complexity and Capture the most informative structure of the data. In machine learning, this 
        leads to better generalization, interpretability and efficiency.

   4. Calculation of Eigendecomposition via numpy.linalg.eig():
      - The numpy.linalg.eig() function is used to compute the eigenvalues and right eigenvectors of a square matrix.
      - This function helps you solve the eigenvalue equation:
                                                 𝐴𝑣 = 𝜆𝑣
        Where:
          𝐴 is a square matrix (the input),
          𝑣 is an eigenvector,
          𝜆 is the corresponding eigenvalue.
      - Parameters:
        - A : (..., M, M) array_like
          A square matrix. Can be 2D or batched.
      - Returns:
        - w : (…, M) ndarray
          The eigenvalues of matrix A.
        - v : (…, M, M) ndarray
          The eigenvectors of matrix A. Each column v[:, i] is the eigenvector corresponding to w[i].
      
      - Calculation:
        - NumPy is solving the eigenvalue equation:
                                                 𝐴𝑣 = 𝜆𝑣
          This can be rearranged to:
                                                (𝐴−𝜆I)⋅𝑣=0
          This equation has non-trivial solutions (non-zero vectors 𝑣) only if:
                                               det(𝐴−𝜆I)=0
          This is called the characteristic equation. Solving it gives you the eigenvalues 𝜆. Once those are found, the corresponding eigenvectors 𝑣 can also be 
          determined.
          
      - NumPy Internally Calls LAPACK(Linear Algebra Package):      ...(1)
        - NumPy doesn’t implement this from scratch. Instead, it uses LAPACK, a powerful library written in Fortran that is used in high-performance scientific 
          computing.
        - For real-valued matrices, NumPy calls LAPACK’s dgeev function.
        - For complex-valued matrices, it uses zgeev.
       
      - BLAS(Basic Linear Algebra Subprograms) for Speed            ...(2)
         - LAPACK itself is built on top of BLAS, which are super-optimized for doing fast matrix operations.
           
      - Because of ...(1) and ..(2):
        - np.linalg.eig() is very fast, even for large matrices
        - It is also numerically stable — meaning it's resistant to floating-point errors
       
   5. Comparison of Manual Eigendecomposition Calculation and Numpy's eig():
      - If here we are talking about time, then ofcourse NumPy is much faster then any manual implementation.
      - But the real and challenging question here is,
        Do manually computed eigenvalues/vectors differ from NumPy’s eig()?!! the answer for this question can be consider in to way as follows,
        1. In theory:
          - No, the mathematical results should be the same.Eigenvalues and eigenvectors are unique mathematical solutions to the equation:
                                                      𝐴𝑣 = 𝜆𝑣
            So whether you solve it by hand (manually) or with NumPy, you are solving the same problem.
        2. But in practice:
          - Yes, minor differences can occur due to:
            1. Numerical Precision:
               - Manual calculations (by hand or in simple code) often use rounded values, where NumPy uses floating-point arithmetic with high precision 
                 (typically float64).
            2. Eigenvector Scaling:
               - Eigenvectors are not unique in magnitude. If 𝑣 is an eigenvector, then so is 2𝑣, or 𝑣, or any non-zero multiple.
               - So your manual result might give:
                                                 𝑣 = [1, 2]  while NumPy gives  𝑣 = [0.477, 0.894]
                 Both are valid.
               - !!! NumPy often returns unit vectors (length = 1).
            3. Order of Results:
               - NumPy's eig() function does not guarantees that the calculated eigenvalues and eigrnvectors are returned in a specific order. So,
                 NumPy may return:
                                                 𝜆1 = 5  and  𝜆2 = 2
                 The manual implementation might list:
                                                 𝜆1 = 2  and  𝜆2 = 5
               - And that’s totally fine, order doesn't matter unless you're matching pairs.
              
         
          
