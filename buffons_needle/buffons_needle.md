# Buffon's Needle Problem

Buffon's Needle problem, one of the earliest problems in geometric probability, was first proposed in the first half of the 18th century. The problem follows like this: Assume a floor made of parallel strips of wood of equal width and we drop a needle randomly onto the floor. What is the probability that the needle intersects a line separating two strips?

Let’s first dive into the analytical solution of the problem.

Revisit the question: Given a needle of length l dropped on a plane ruled with parallel lines D units apart, what is the probability that the needle will lie across a line between two strips? In part a, needle B represents the expected condition.

Assume that the needles are made of a homogeneous material. Let x be the distance from the center of mass (COM) of the needle to the closest parallel line, and let θ be the angle between the needle and the parallel line axis. The probability that the needle intersects a line depends on these two variables: x and θ.

Focusing on a single reference line, the probability density function (PDF) of x is defined over the interval 0 (part b, needle B where the COM lies on the line) to D/2 (part b, needle A where the needle is centered midway between two lines), and is given as in part b. For the second variable, θ, the probability density function (PDF) is defined over the interval 0 (part c, needle A lying parallel to the line) to π/2 (part c, needle B rotated by θ from the line), and is given as in part c. Since x and 0 are two independent random variables, the joint probability density function can be written as the product using the multiplication rule: P(A∩B)=P(A)×P(B) as given as in part d. The needle intersects the line only if it satisfies the condition given in part e. There are now two possible scenarios: (i) when the needle length is shorter than the distance between the strips (l≤D), and (ii) when the needle length is greater than the distance between the strips (l>D). For ease of analytical solution, we will focus only on the first case (l≤D). Integrating the joint probability density function over dx and dθ as in part f (for l≤D) yields the probability that the needle crosses a line, which depends on l and D.

<img width="1713" height="1384" alt="Not 19 Şub 2026 20_54_54" src="https://github.com/user-attachments/assets/7c04b4f2-8b85-4bc8-8963-141bb686a840" />

Based on the analytical solution derived above, we can use a Monte Carlo simulation of the crossing probability (P=2L/Dπ) to estimate the value of π. The script buffons_needle_part1 simulates the system with 10², 10³, 10⁴, 10⁵, and 10⁶ needles and tracks how many cross a line to estimate the crossing probability using Monte Carlo simulation. Results are given below.

<img width="5670" height="4013" alt="buffons_needle_part1" src="https://github.com/user-attachments/assets/290be4c0-d8b7-4c78-b6a9-8abf1b594a14" />

<img width="2724" height="642" alt="buffons_needle_part1_table" src="https://github.com/user-attachments/assets/5ea24f1f-6b85-4e1d-b1ba-39506619f6fb" />

Monte Carlo simulations across seven distinct L and D configurations provide an empirical validation of the analytical solution for Buffon’s Needle problem in part 1, which states that the probability (P) of a needle crossing a line is 2L/Dπ for L≤D. By tracking the number of crossing needles across five orders of magnitude (10², 10³, 10⁴, 10⁵, and 10⁶), the data shows a classic convergence toward this theoretical limit.

At the lowest replication count of n=100, the estimates for π are highly volatile and exhibit noise, with values ranging from a low of 1.923077 (L=0.25,D=1.0) to a high of 3.846154 (L=2.0,D=4.0). This stochastic fluctuation is expected due to the inherent variance in small-sample Monte Carlo simulations where short-term probabilistic deviations from the expected mean can disproportionately skew the results. However, as the law of large numbers takes effect, the fluctuations dampen significantly; by n=10⁴, the estimation results begin to cluster around the true value of ~3.14159, and by n=10⁶, every single tested configuration converges well with accurate approximation of π.

Specifically, the L=1.0,D=2.0 setup at 10⁶ needles yielded a π estimate of 3.142164, representing a minute relative error. These results confirm that while different L and D ratios shift the baseline probability, as seen in the first plot where probabilities range from approximately 0.08 to 0.48, the underlying relationship P∝1/π remains invariant. The simulation effectively demonstrates that increasing the sample size is the main driver for precision, successfully filtering out stochastic noise to reveal the underlying mathematical constant.

