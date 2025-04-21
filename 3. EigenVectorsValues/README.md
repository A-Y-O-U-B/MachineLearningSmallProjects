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
      

