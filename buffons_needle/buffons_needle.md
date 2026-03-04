# Buffon's Needle Problem

## Classical Problem

Buffon’s Needle Problem, one of the earliest problems in geometric probability, was first proposed in the first half of the 18th century. The problem follows like this: Assume a floor made of parallel strips of wood separated by equal widths, and we drop a needle randomly onto the floor (Fig.1f). What is the probability that the needle intersects a line separating two strips on the floor?

![buffons_needle](https://github.com/user-attachments/assets/4db0f428-154e-4062-9ada-246415aba42b)

Fig.1: Analytical solution for Buffon’s Needle Problem

Let’s first dive into the analytical solution of the problem. Revisit the question: Given a needle of length l dropped on a plane ruled with parallel lines D units apart, what is the probability that the needle will lie across a line? In this case, Fig.1a needle B represents the expected condition. Assume that the needles are made of a homogeneous material. Let x be the distance from the center of mass (COM) of the needle to the closest parallel line, and let θ be the angle between the needle and the parallel line axis. The probability that the needle intersects a line depends on these two variables: x and θ. Focusing on a single reference line, the probability density function (PDF) of x is defined over the interval 0 (Fig.1b, needle B where the COM lies on the line) to D/2 (Fig.1b, needle A where the needle is centered midway between two lines). For the second variable, θ, the probability density function (PDF) is defined over the interval 0 (Fig.1c, needle A lying parallel to the line) to π/2 (Fig.1c, needle B rotated by θ degrees from the line). In other words, this problem’s domain can be defined over the given intervals of x and θ in Fig.1b,c. Since x and θ are two independent random variables, the joint probability density function can be written as the product using the multiplication rule: P(A∩B)=P(A)×P(B) as given in part Fig.1d. The needle intersects the line only if it satisfies the condition given in Fig.1e, when the needle length is shorter than the distance between the strips (l≤D). 

Integrating the joint probability density function over dx and dθ (for l≤D) yields the probability below in Eq.1 that the needle crosses a line, which depends on l and D.


<img width="562" height="64" alt="Screenshot 2026-03-04 at 05 05 41" src="https://github.com/user-attachments/assets/f0e941ab-1c06-495a-913f-790c1766bd50" />

Eq.1

<img width="5670" height="4014" alt="prob" src="https://github.com/user-attachments/assets/73308234-7ce2-40f0-b3be-aacb5c495a18" />

Fig.2: π estimation and probability results for seven l/D pairs, calculated across five orders of magnitude of needle counts.

Based on the analytical solution derived above, we can use a Monte Carlo simulation of the crossing probability (2l/πD) to estimate the value of π. The script [here](https://github.com/incisrdg/CMPE49G_fundamentals_of_particle_based_simulations/blob/main/buffons_needle/buffons_needle_part1.ipynb) simulates the system with 10^2, 10^3, 10^4, 10^5, and 10^6 needles and estimates the crossing probability using Monte Carlo simulation. Results are given Fig.2. Monte Carlo simulations across seven distinct l and D pairs provide an empirical validation of the analytical solution for Buffon’s Needle Problem discussed above, where the probability of crossing a line is 2l/πD for l≤D. By tracking the number of needles across five orders of
magnitude (10^2, 10^3, 10^4, 10^5, and 10^6), the data shows a classic convergence toward the theoretical value in Fig.2 below and Table 1. At the lowest replication count of n=100, π estimation is highly volatile and exhibiting noise. This stochastic fluctuation is expected due to the inherent variance in small-sample Monte Carlo simulations. However, as the law of large sample size takes effect, the fluctuations dampen significantly, converging well with
accurate approximation of π (Table 1). Specifically, the l=1.0, D=2.0 setup at 106 needles estimated π as 3.142164, representing a minute error. Additionally, Fig.2 above shows that the probability is governed by the ratio l/D rather than the individual values; cases with the same ratio produce overlapping probability curves.

Table 1:  Convergence of π estimates

<img width="481" height="124" alt="Screenshot 2026-03-04 at 05 10 40" src="https://github.com/user-attachments/assets/16bc80de-2d6a-49c5-a1ce-8980419434be" />


## Modern/Revisited Version 

In this case, instead of assuming a floor made of parallel strips of wood separated by equal widths as given in the classical version of the problem, we are going to consider an infinite-size sheet of paper containing con-centric circles radiating from the center and we will drop again a needle of size l randomly to the floor, where the smallest circle has a radius equal to 𝐷 and the distance between consecutive circles is 𝐷  (i.e., radii of the following circles are 2𝐷, 3𝐷, 4𝐷, …) with satisfying 𝐿 < 𝐷). Rain frops would be a well-suited analogy for such a setup.

![604c375392238df7dca063726db65555](https://github.com/user-attachments/assets/dc24f2af-e066-49df-865e-cdd0ff35f247)


In the classical Buffon’s Needle problem, we used the center of the needle and its distance to the nearest parallel line because the geometry is linear and periodic. However, for the modern version of the problem, we will use the tips (d1 and d2) instead of the COM since the concentric circles breaks the linearity and requires coordinate transformation. For analytical approach to the modern problem, we will define the position of a needle of length l (where l≤D) using following three parameters:

- r: The radial distance from the center of the concentric circles to the midpoint of the needle.

- θ: The angle the needle makes with the radial vector pointing to its center.

- R: The radius of a specific circle in the concentric set.

The coordinates of the needle's two endpoints (d1 and d2), relative to the center of the circles can be calculated as given in Fig. 3a and the distances of the end points from the origin. 

![buffons_needle_2](https://github.com/user-attachments/assets/2862931b-8e67-43aa-a979-9ffab7b97322)

Fig. 3: Analytical solution for the modern version of Buffon's Needle Problem

A needle crosses a circle of radius R only if one of the endpoints is inside the circle and the other is outside the circle. For crossing condition, d2<R<d1 (for cosθ>0) needs to be satisfied (Fig.3b). Squaring the calculated distances to simplify the solution leads to inequality in Fig.3b. Isolating the angular term shows that a crossing occurs only if the critical angle for 0 obeys the given inequality in Fig.3b. From the critical 0 condition, it can be observed that the "success" range for the angle θ depends on the radial distance r. For a fixed r near a circle of radius R, the probability that the needle crosses that specific circle is the ratio of favorable angles to the total possible range of angles (0 to 2π due to symmetry). This probability can be calculated by multiplying critical angle 0 with 4 and then dividing into the total probability 2π given in Eq.2. The multiplication by 4 comes from the symmetry of the circle and the needle's orientation. When you drop a needle, it can land at any angle θ between 0 and 2π. However, because a needle is symmetric, in other words, the "head" and the "tail" are identical, a needle at angle θ is physically the same as a needle at θ+π. This immediately reduces the domain of the problem to a range of π. We can simplify this even further. Whether the needle points "up and right" or "down and right," the crossing condition remains the same this time due to the horizontal symmetry of the radial line r. Therefore, we can define the "total possible angles" in our simplified model using a single quadrant as the domain: 0 to π/2 (Eq.2).

<img width="393" height="55" alt="Screenshot 2026-03-04 at 05 25 10" src="https://github.com/user-attachments/assets/bb94d6ae-a9af-43f4-8bac-5fec441e3329" />

Eq.2

Once we obtained the local probability in Eq.2, we can calculate the total probability P, by averaging the local probability over all possible positions r. Since the needle center is equally likely to land anywhere in the area between two circles, we integrate across the radial zone and divide by the total distance D. The integration is performed over the interval (R−L/2,R+L/2), representing a physical range of all possible positions of the needle center r where a crossing of a circle with radius R is geometrically possible. Based on this integration, pay attention that as R becomes very large, the curvature of the concentric circles becomes negligible, acting like parallel strips, and this integral converges to the probability of P= 2l/πD found in the classical solution (Fig.1).
​	
<img width="5200" height="3566" alt="buffons_needle_part2" src="https://github.com/user-attachments/assets/48ce3bf1-15b5-495c-a0cf-7ca08e74b9f0" />

Fig. 4: π estimation and probability results for l/D pairs, calculated across five orders of magnitude of needle counts.

The Monte Carlo simulation results (script can be found ( [here](https://github.com/incisrdg/CMPE49G_fundamentals_of_particle_based_simulations/blob/main/buffons_needle/buffons_needle_part1.ipynb) ) for the concentric circle system demonstrate a clear convergence toward the theoretical analytical solutions as the number of replications increases in Fig.4. At low needle counts, significant fluctuations are visible in both the crossing probability (P) and the π estimation, reflecting high statistical variance. However, as the sample size increases, the estimated values stabilize and align closely with the theoretical probability P=2L/Dπ. This trend confirms that despite the circular geometry, the system behaves predictably in an infinite-size sheet, where the curvature becomes locally negligible and acts linearly for very large radii. The final π estimates for all (L,D) pairs asymptotically approach the true value of π≈3.14159, validating the robustness of the simulation approach and the geometric derivation based on needle tip distances (Table 2).

Table 2

<img width="472" height="143" alt="Screenshot 2026-03-04 at 06 38 30" src="https://github.com/user-attachments/assets/65316470-f655-4739-af4e-3d07fc59dca3" />


