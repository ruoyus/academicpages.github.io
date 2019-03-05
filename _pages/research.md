---
layout: archive
title: "Research (by Area)"
permalink: /research/
author_profile: true
---

ADMM
======
**Background:** ADMM (Alternating Direction Method of Multipliers) was proposed 40 years ago and recently attracted lots of attention. The convergence of 2-block ADMM for convex problems was known; however, a recent paper in 2014 showed that multi-block ADMM can diverge even for solving a 3*3 linear system. Interestingly, if we randomly permuted the update order in each cycle (e.g. (132), (231),... compared to traditional cyclic order (123), (123),...), then the algorithm converges. The question is: why?  

**Our contribution:**  
1. Result. We show that for solving linear systems RP-ADMM (randomly permuted ADMM) converges in expectation for any number of blocks.  
2. High-level idea. One simple explanation for this phenomenon is "symmetrization'': the update matrix of cyclic ADMM is a non-symmetric matrix with complex eigenvalues, and random permutation partially symmetrize the update matrix to make the eigenvalues have a nicer distribution. In fact, the key result is that the eigenvalues of the update matrix of RP-CD (randomly permuted coordinate descent) lies in (-1/3, 1), a smaller region than that of cyclic CD which is(-1,1).  
3. Implications.  
   1. Problem level: RP-ADMM can potentially be a good solver for large-scale linearly constrained problems (LP, SDP, etc.)  
   2. Algorithm level: It was widely believed that RP rule is better than cyclic rule; however, little theory is established. This work provides one of the first theoretical results that RP rule is better than the cyclic rule.  
      * On the Expected Convergence of Randomly Permuted ADMM  Ruoyu Sun, Zhi-Quan Luo, Yinyu Ye.  

Matrix Completion
======
**--Updated 07/2016. Highlight the local geometry nature of our proof. New slides with a cleaner summary of the proof sketch.**  

**Background:** Motivated by applications such as recommender systems (e.g. Netflix prize),  the problem of recovering a low-rank matrix from a few observations has been popular recently. It is a prototype example of how to utilize the low-rank structure to deal with big data.  There are two popular approaches to impose the low-rank structure: nuclear norm based approach and matrix factorization (MF) based approach. The latter approach is especially amenable for big data problems, and has served as the basic component of most competing algorithms for Netflix prize. However, due to the non-convexity, it seems to be difficult to obtain a theoretical guarantee.  

**Our contribution:**  
1. *Result.* We show that many standard algorithms for a *non-convex* MF based formulation converge to the *global optima*, thus exactly recover the unknown low-rank matrix. Our result covers gradient descent, alternating-type methods (including two-block alternating minimization) and SGD (stochastic gradient descent).

2. *High-level idea.* The intuition is that the objective function has certain geometrical property (the property is related to, but different from *local strong convexity*), even though it is non-convex in the entire space.  
   <br>
   The proof consists of three steps. 
   * Step 1: analyze the local geometry of matrix factorization (ignoring sampling).
   * Step 2: due to random sampling the size of local region is small, so we need to add regularizer/constraint to enforce row-norms to be bounded.
   * Step 3: since the local geometry is somewhat destroyed by the incoherence regularizer, we add an additional regularizer to "restore" the local geometry.

3. Some distinct aspects, compared to other non-convex optimization works.
   1. Our paper is one of the first to analyze the (local) geometry of the problem. .
   2. We deal with non-symmetric matrix factorization which has a more bizarre geometry than symmetric matrix factorization and some other models. 
   3. One difficulty of our problem essentially lies in nonconvex constrained optimization (though we consider the closely related regularized form).

4. *General insight* for non-convex optimization.
   1. Regularization or bounding norms changes geometry/landscape. .
   2. Non-convexity caused by XY' is even more difficult to deal with than that of Grassman manifold factorization or symmetric factorization.

5. *Math techniques.*  
   The first step deals with the ambiguity of the factorization, leading us to establish the "coupled" perturbation analysis, i.e. when XY'-M is small, constructing a factorization M = UV' such that U,V satisfy a few conditions including being close to X,Y respectively. This is a way to connect "product space" to Euclidean space.  The second difficulty comes from the random sampling. The third step requires  a rather involved but quite intuitive perturbation analysis, with some additional constraints on X,Y.

**Math tools:** Matrix perturbation analysis, Random graph theory.  
<br>
The paper is quite long and technical, so I write a short summary of this paper (informal notes). See also [slides].  
   * Ruoyu Sun, Zhi-Quan Luo, "Guaranteed Matrix Completion via Nonconvex Factorization ”, available on arxiv; FOCS 2015.
   * Ruoyu Sun, Matrix Completion via Nonconvex Factorization: Algorithms and Theory, PhD Dissertation, University of Minnesota, May 2015.
