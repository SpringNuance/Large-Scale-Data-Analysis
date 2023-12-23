This assignment is about various optimization algorithms for the problem of finding the optimal solutions x* of dimension $N \times 1$ in the equation of $Ax = b$, where A is a square matrix of dimension $N \times N$ and b is a vector of dimension $N \times 1$. In a small scale settings, this problem can be simply be solved with np.linalg.solve(A, b), or np.linalg.inv(A) @ b. However, if $N$ is very large (10000 or more), then inverting the matrix would be computationally expensive. Therefore, approximating the optimal solution $x*$ is the main optimization problem that we need to solve. 

This assignment features four such algorithms to find the optimal solution
1. Gradient Descent
2. Conjugate Gradient
3. FISTA (Fast Iterative Shrinkage-Thresholding Algorithm)
4. Coordinate Descent

Note that gradient descent, conjugate gradient and coordinate descent have access to the analytic gradient of the loss functions, while FISTA does not need it. This makes FISTA suitable for problems where gradients are intractable. 

The formula for the four algorithms
- Gradient descent

$$ x_{k+1}=x_k - \alpha_k \Delta f(x_k), \quad \alpha_k > 0$$


How to select the step size $\alpha_k$: 
1. Fixed: use rules based on $L$ and $\mu$ (trivial), where $L$ is the Lipschitz constant. For least squares, minimum $L$ is the maximum eigenvalue of $X^TX$
The gradient descent lower bound minimized by a gradient descent step with $\alpha_k = 1/L$
Read more at [this paper](https://www.cs.ubc.ca/~schmidtm/Courses/540-W18/L4.pdf) by UBC
2. Backtracking (computationally easy), 
3. exact line search (computationally may be hard). For the above ways of step size selection 2 and 3, we typically have global convergence at unspecified rate. 

The 'greedy" strategy of getting good decrease in the current search direction may lead to better practical convergence results. 

For the above way of step size selection, fixed step size selection focuses on convergence rate. 
