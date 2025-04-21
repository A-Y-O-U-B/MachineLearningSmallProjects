# Eigendecomposition of a Matrix
In this project we will talk about Eigendecomposition of a Matrix, we will start with a brief definitions and Eigendecomposition's relationship to Machine Learning then we will dive into the Calculation of Eigendecomposition and we will do it two ways. First using numpy then we will do it manually to compare each of these ways and note the results.

2) Eigendecomposition of a Matrix:
   1. Definitions:
      - Matrix Manipulation:
         - Matrix manipulation involves performing operations such as addition, multiplication, transposition, and inversion on matrices. These are essential in 
           representing and transforming data in machine learning.
      - Eigenvalues and Eigenvectors:
         - For a square matrix 𝐴, an eigenvector 𝑣 and its corresponding eigenvalue 𝜆 satisfy:
                                             𝐴𝑣 = 𝜆𝑣
           This means that multiplying matrix 𝐴 by vector 𝑣 only stretches (or shrinks) 𝑣 by a factor 𝜆, without changing its direction.
         - Normally when we multiply a matrix by a vector, the vector changes. It gets rotated, flipped or stretched. But somtimes there are special vectors that only 
           get stretched or shrunk without changing direction. So these special vectors are called eigenvectors and the amount they get stretched or shrunk is called 
           their eigenvalue.


