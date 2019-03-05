---
layout: archive
title: "Research (by Area)"
permalink: /research/
author_profile: true
---

- - -

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
The paper is quite long and technical, so I write a short [summary](https://dl.dropboxusercontent.com/u/45090901/Reading_MC_notes.pdf) of this paper (informal notes). See also [[slides](https://www.dropbox.com/s/2adtsjrd2ldap4c/MC_Sun_Slides.pdf?dl=0)].  
   * Ruoyu Sun, Zhi-Quan Luo, "[Guaranteed Matrix Completion via Nonconvex Factorization](https://arxiv.org/abs/1411.8003) ”, available on arxiv; FOCS 2015.
   * Ruoyu Sun, [Matrix Completion via Nonconvex Factorization: Algorithms and Theory](https://conservancy.umn.edu/bitstream/handle/11299/175344/Sun_umn_0130E_15998.pdf?sequence=1&isAllowed=y), PhD Dissertation, University of Minnesota, May 2015.
   
Interference Alignment
======
**Background:** The capacity of many-to-many wireless networks remains a long-time open question. This question was partially answered in 2008, when Cadambe and Jafar showed that the maximum DoF of a K-to-K interference channel is K/2, where the DoF is the first-order approximation of capacity. Compared to the 1 DoF achieved by OFDM, this surprising result reveals that the theoretical limit is O(K) times higher than the current practice. However, the achievable scheme by Cadambe and Jafar requires an exponential (in K^2) number of independent channel extensions. It is thus of great interest to study the achievable DoF with a limited number of possibly dependent channel extensions.  
**Our contribution:**  
1. Theory. We prove the first DoF upper bound for any number of users, any number of channel extensions and any diversity order (dimension of the channel matrix space, a notion that captures dependence of channel extensions), in the single-beam case. We propose a unified channel model that covers many practical channels. Compared to the O(K) DoF in infinite data stream case, we establish an O(sqrt(K)) bound for the single-beam case, and an O(1) bound for the single-beam case with independent channel extensions. 
2. Clarifications. We provide some clarifications for the counting argument (i.e. count the number of variables and equations to claim feasibility). We also provide a detailed discussion of Bernstein's theorem, which is a bit tricky and easy to misunderstand.
3. Math techniques. The mathematical difficulty is how to deal with a hybrid system of equations and inequalities, which differs from previous works that consider simple scenarios in which only equations are needed. We develop an induction analysis framework to utilize the inequalities (full-rank conditions), which combined with algebraic geometry tools can deal with the hybrid system.
**Math tool:** Algebraic geometry.
   * Ruoyu Sun, Zhi-Quan Luo, "[Interference Alignment using Finite and Dependent Channel Extensions: the Single Beam Case](https://arxiv.org/abs/1307.6125)", IEEE Trans. on Information Theory, vol. 61, no.1, pp.239,255, Jan. 2015. [[link](https://ieeexplore.ieee.org/document/6951516?tp=&arnumber=6951516&url=http:%2F%2Fieeexplore.ieee.org%2Fxpls%2Fabs_all.jsp%3Farnumber%3D6951516)] [[arxiv](https://arxiv.org/abs/1307.6125)] [[slides](https://dl.dropboxusercontent.com/u/45090901/slides_SunLuo_IA%20finite.pdf)]
   
Base Station Association
======
***Background:*** In next generation wireless networks, base stations will be much more densely deployed, making the association of mobile users to base stations a big challenge. Mathematically speaking, the problem of joint base station association and power control (or beamformer design) involves both discrete variables and continuous variables. The computational complexity of this problem is not known before.  
**Our contributions:** We show that the uplink problem, though with both integer and continuous variables, is polynomial time solvable (quite unexpected) [B1], and the downlink problem is NP-hard [B2]. Moreover, a bit surprisingly, we show that a QoS constrained version of the downlink problem is polynomial time solvable (transformed to maximum weighted bipartite matching problem and solved by the well-known auction algorithm) [B2].  
Other works: We also consider a more general setting where one user can be served by multiple users (called CoMP) and use group sparsity penalty to control the number of BSs that serve a single user [B3]. In a more practical scenario that BS association is updated less frequently than beamformers, we propose a  stochastic sparse optimization based approach [B4].
   * [B1] Wei Liu, Ruoyu Sun (corresponding author), Zhi-Quan Luo, Jian-Dong Li, "[Globally Optimal Uplink Joint Base Station Association and Beamforming](https://arxiv.org/abs/1512.04927)”, available on arxiv. Part of this paper has appeared at ICASSP 2014.
   * [B2] Ruoyu Sun, Mingyi Hong, Zhi-Quan Luo, “[Joint Downlink Base Station Association and Power Control for Max-Min Fairness:Computation and Complexity](https://arxiv.org/abs/1407.2791)”, IEEE Journal of Selected Areas in Communications (JSAC),vol.33, no.6, pp.1040-1054, June 2015.
   * [B3] Mingyi Hong, Ruoyu Sun, Zhi-Quan Luo, "[Joint Base Station Clustering and Beamformer Design for Partial Coordinated Transmission in Heterogenous Networks](https://arxiv.org/abs/1203.6390)", IEEE Journal on Selected Areas in Communications, special issues on Large-Scale multiple antenna systems , vol. 31, no. 2, pp. 226-240, Feb. 2013.
   * [B4] Ruoyu Sun, Hadi Baligh, Zhi-Quan Luo, "[Long-term Transmit Point Associationfor Coordinated Multipoint Transmission by Stochastic Optimization](https://ieeexplore.ieee.org/document/6612066?tp=&arnumber=6612066&queryText%3DLong-term%20Transmit%20Point%20Association%20for%20Coordinated%20Mult=)", Proc. IEEE SPAWC 2013.
