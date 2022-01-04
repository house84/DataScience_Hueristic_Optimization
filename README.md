1 Introduction
In this project you will use Pandas and Numpy to implement a machine learning optimization
heuristic following the given specifications. Given a real-valued function of d variables, the
problem is to minimize the function (that is, nd values of the d variables that produce the
minimum value of the function).


2 The algorithm
Algorithm 1: The algorithm
initialize the population (of size n) uniformly randomly, obeying the bounds;

The heuristic employs a population of randomly-generated trial solutions (trial vectors)
and seeks to improve upon them iteratively, until a stopping condition is satised. A typical
stopping condition is based on a predetermined (high) number of iterations (such as 50 or
1000 or 100,000, depending on how large d is). At each iteration, we examine the vectors in
the population, conditionally replacing each with a newly created vector. A new vector is created 
from the current vector by using the best vector, the worst vector, and two random
numbers { each chosen uniformly randomly in (0, 1] { per problem variable. (Note that for d
dimensions, we have 2d such random parameters, each in (0, 1].) The creation of the new
vector xnew, given the current vector xcurrent, is described by the following equation (xnew,
xcurrent, xbest and xnew are each a d-component vector):

xnewi = xcurrenti + rt;i;1(xbestt;i 􀀀 jxcurrenti j) 􀀀 rt;i;2(xworstt;i 􀀀 jxcurrenti j)

where xi, i = 1 to d, represent the d variables to be optimized, rt;i;1 and rt;i;2 are each a
random number in (0.0, 1.0], t indicates the iteration number, xbestt and xworstt represent,
respectively, the best and the worst vector in the population at iteration t. When xnewi falls
outside its lower or upper bound (given in Table 1), it is clamped (clipped) at the appropriate
bound.


Note that the above equation represents the update logic for each of the n vectors in the
population in each iteration. Note the use of the iteration index t in the subscript to indicate
which values are determined once per iteration, and the use of the index i in the subscript to
denote which values are determined once per variable in each vector.
The goodness of a solution vector is determined by the objective function value (f value)
it produces; the lower the f-value, the better. The global minimum shown in Table 1 is only
for your information (so you know how far a given vector is from the optimal solution). The
algorithm updates the population-best and the population-worst vectors once every iteration.
Your program should be capable of handling any n and any d and any bounds (within
reasonable limits, of course); do not use hard coding. While reporting results, please use
n = 20, d = 5, and the numerical bounds shown in Table 1. 

This is a project designed to halp you acquire valuable skills in vectorization using
Pandas and Numpy. To that end, use a DataFrame to hold the population. The single most
important idea here is to be able to realize what tasks can be done in parallel. Make use of
vectorization, avoiding explicit loops and list comprehensions as far as practicable. (Hint:
Consider DataFrame.apply(). Look up the original docs.) Aim for no more than just a single
for loop in the entire program.

Please show the following in your report: 
(1) the population size n; 
(2) numerical values
of the d variables that cause the minimum value of the function to be achieved; 
(3) the
corresponding (minimum) value of the function; 
(4) the maximum number of iterations used,
(5) the first five and the last five rows of your final DataFrame.
