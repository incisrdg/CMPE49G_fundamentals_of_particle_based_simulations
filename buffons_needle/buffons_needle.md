# Buffon's Needle Problem

Buffon's Needle problem, one of the earliest problems in geometric probability, was first proposed in the first half of the 18th century. The problem follows like this: Assume a floor made of parallel strips of wood of equal width and we drop a needle randomly onto the floor. What is the probability that the needle intersects a line separating two strips?

Let’s first dive into the analytical solution of the problem.

Revisit the question: Given a needle of length l dropped on a plane ruled with parallel lines D units apart, what is the probability that the needle will lie across a line between two strips? In part a, needle B represents the expected condition.

Assume that the needles are made of a homogeneous material. Let x be the distance from the center of mass (COM) of the needle to the closest parallel line, and let θ be the angle between the needle and the parallel line axis. The probability that the needle intersects a line depends on these two variables: x and θ.

Focusing on a single reference line, the probability density function (PDF) of x is defined over the interval 0 (part b, needle B where the COM lies on the line) to D/2 (part b, needle A where the needle is centered midway between two lines), and is given as in part b. For the second variable, θ, the probability density function (PDF) is defined over the interval 0 (part c, needle A lying parallel to the line) to π/2 (part c, needle B rotated by θ from the line), and is given as in part c. Since x and 0 are two independent random variables, the joint probability density function can be written as the product using the multiplication rule: P(A∩B)=P(A)×P(B) as given as in part d. The needle intersects the line only if it satisfies the condition given in part e. There are now two possible scenarios: (i) when the needle length is shorter than the distance between the strips (l≤D), and (ii) when the needle length is greater than the distance between the strips (l>D). For ease of analytical solution, we will focus only on the first case (l≤D). Integrating the joint probability density function over dx and dθ as in part f (for l≤D) yields the probability that the needle crosses a line, which depends on l and D.

<img width="1713" height="1384" alt="Not 19 Şub 2026 20_54_54" src="https://github.com/user-attachments/assets/7c04b4f2-8b85-4bc8-8963-141bb686a840" />

Based on the analytical solution derived above, we can use a Monte Carlo simulation of the crossing probability (p=2L/Dπ) to estimate the value of π. The script buffons_needle_part1 simulates the system with 10², 10³, 10⁴, 10⁵, and 10⁶ needles and tracks how many cross a line to estimate the crossing probability using Monte Carlo simulation. Results are given below.

<img width="5670" height="4013" alt="buffons_needle_part1" src="https://github.com/user-attachments/assets/290be4c0-d8b7-4c78-b6a9-8abf1b594a14" />

N	Pi_L=0.25, D=2.0	Pi_L=0.5, D=2.0	Pi_L=1.0, D=2.0	Pi_L=0.25, D=0.5	Pi_L=0.25, D=1.0	Pi_L=2.0, D=4.0	Pi_L=6.0, D=8.0
100	2.083333	2.941176	2.857143	3.333333	1.923077	3.846154	2.830189
1,000	2.808989	2.994012	3.174603	3.154574	3.378378	2.994012	3.118503
10,000	3.136763	3.046923	3.155570	3.170577	3.103662	3.119152	3.151923
100,000	3.196114	3.124609	3.151194	3.146237	3.161755	3.133912	3.156034
1,000,000	3.121021	3.130694	3.142164	3.145416	3.142283	3.145168	3.142697




