+++
author = "Andrew Smith"
title = "What is the Singular Value Decomposition?"
date = "2022-05-12"
description = "Introduction to the meaning of the SVD in terms of linear transformations."
tags = [
    "tutorial",
]

math = true
+++

In linear algebra, the singular value decomposition (SVD) is a factorization of a real or complex matrix. Let \\(M \in \R^{2\times 2} \\). There exists \\(U,S,V\\) such that

In simple terms, the SVD breaks a matrix down into it's fundamental components. Often, a matrix is easier to understand if we can decompose it into fundamental components. 

$$\displaystyle M = U\Sigma V^T.$$

_Shown here is the transformation diagram of a singular value decomposition. By the end of the article, you will understand what it means._

![rotation](/images/svd/6_svd.svg)

{{< notice warning >}} We are not going to describe any algorithms to determine the SVD. It would be a good exercise for you to do this for at least one example. You may find the algorithm [here](https://en.wikipedia.org/wiki/Singular_value_decomposition#Calculating_the_SVD:~:text=Calculating%20the%20SVD%5Bedit%5D). {{< /notice >}}

### Example
Let's examine the following matrix and the _meaning_ of the SVD, as opposed to _how_ to compute it. For the following matrix,
$$M=\begin{bmatrix}
1 & 2\newline
0 & 3
\end{bmatrix}$$
we determine that
$$\displaystyle M = U\Sigma V^T.$$
for
$$
U=
\begin{bmatrix}
0.58 & -0.81\newline
0.81 & 0.58
\end{bmatrix}
$$
$$\Sigma=\begin{bmatrix}
3.65 & 0\newline
0 & 0.82
\end{bmatrix}
$$
$$
V^T=\begin{bmatrix}
0.16 & 0.98\newline
-0.99 & 0.16
\end{bmatrix}.
$$

What does this mean? We know the left side and right side of the SVD are equal by matrix multiplication, but how can we confirm that the meaning of the left side and the meaning of the right side are equivalent? We start with the meaning of the left hand side, then we will show that the right hand side is equivalent.

Matrices are commonly interpreted as transformation operators. Suppose you have a vector in the 2-dimensional Cartesian plane. We can transform this vector by a matrix by multiplying the matrix by the vector.

_Example_
For example,suppose we have a column vector \\(v=\begin{bmatrix}
0 \newline
1 
\end{bmatrix}\\) and a transformation matrix \\(M=\begin{bmatrix}
1 & 2\newline
0 & 3
\end{bmatrix}\\). We apply the transformation matrix to the column vector by the following
$$
Mv=\begin{bmatrix}
1 & 2\newline
0 & 3
\end{bmatrix}
\begin{bmatrix}
0 \newline
1 
\end{bmatrix}
$$
and obtain the transformed vector
$$v'=\begin{bmatrix}
2 \newline
3 
\end{bmatrix}.$$
The following figure shows \\(v\\) in blue (before applying the transformation matrix) and \\(v'\\) in red (after applying the transformation matrix).

![test](/images/svd/0_svd.svg)

It is no coincidence that the result of the multiplication yields the second column vector in the transformation matrix. In fact, the identity basis transforms under a transformation matrix to be the basis in the transformed space. Thus, another way to conceptualize the transformation matrix is as the location of the identity basis vectors after transformation.

Indeed, an easy way to visualize and therefore understand the effect of a transformation matrix is to view the effect not only on the identity basis vectors, but a cloud of points surrounding the identity basis vectors (the unit circle).

Here we show a visualization of the example transformation matrix acting on the unit circle. We transform the unit circle, shown here,

![unit circle](/images/svd/1_svd.svg)

into a transformed unit circle using the transformation matrix, shown here.

![transformed unit circle](/images/svd/2_svd.svg)

It is worth noting that the 'transformed unit circle' is still a unit circle in the transformed space. The units in the space just look distorted compared to the original space. We will use these diagrams for visualizing transformations moving forward.

So far we have shown the interpretation of the left hand side of the singular value decomposition equation. The matrix we have called \\(M\\) applies a linear transformation to a coordinate system.

Now we want to show that the right hand side of the SVD equation performs the same transformation. Well, we have already shown that the right hand side multiplies to be the left hand side; therefore, we are done. However, let's look at the sequence of transformations done by \\(U,\Sigma
,V\\) to gain an intuitive understanding of what is going on.

Starting again from the identity basis \\(I\\), shown here,

![unit circle](/images/svd/1_svd.svg)

we first apply \\(V^T\\) to the identity basis

$$
IV^T=\begin{bmatrix}
1 & 0\newline
0 & 1
\end{bmatrix}
\begin{bmatrix}
0.16 & 0.98\newline
-0.99 & 0.16
\end{bmatrix}
$$
resulting in the transformation shown in the following figure.

![rotation](/images/svd/3_svd.svg)

Interesting! We observed no scaling effect from this transformation. This transformation only rotated the space.

Now, we apply \\(\Sigma\\) to this transformed space, that we can call \\(I'\\) we have just computed by the following matrix multiplication:


$$
I'\Sigma=I'
\Sigma=\begin{bmatrix}
3.65 & 0\newline
0 & 0.82
\end{bmatrix}.
$$

Thus, we performed the \\(V^T\\) transformation followed by the \\(\Sigma\\) transformation and obtained the transformation shown in the following figure.

![rotation](/images/svd/4_svd.svg)

Interesting! We observed no rotating effect from this transformation. This transformation only scaled the space.

Finally, we apply \\(\U\\) to this transformed space, that we can call \\(I''\\) we have just computed by the following matrix multiplication:


$$
I\'\'U=I\'\'\begin{bmatrix}
0.58 & -0.81\newline
0.81 & 0.58
\end{bmatrix}.
$$

Thus, we performed the \\(V^T\\) transformation followed by the \\(\Sigma\\) transformation followed by the \\(U\\) transformation and obtained the transformation shown in the following figure.

![rotation](/images/svd/5_svd.svg)

Interesting! We observed no scaling effect from this transformation. This transformation only rotated the space.

Wow! Visually, this space looks identical to the space after the linear transformation represented by \\(M\\). In fact, this is the purpose of the singular value decomposition. It was no coincidence that \\(V^T\\) rotated the space, \\(\Sigma\\) scaled the space, and \\(U\\) rotated the space. These facts are confirmed by rigorous mathematics. I will not prove any of these things here, but it is a nice exercise to do for yourself.

Here we show the transformation diagram for the SVD equation, omitting axes and normalizing scale.

![rotation](/images/svd/6_svd.svg)
