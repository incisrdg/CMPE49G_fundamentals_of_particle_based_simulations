# CMPE49G_fundamentals_of_particle_based_simulations

# Buffon's Needle Problem

Buffon's Needle problem, one of the earliest problems in geometric probability, was first proposed in the first half of the 18th century. The problem follows like this: Assume a floor made of parallel strips of wood of equal width and we drop a needle randomly onto the floor. What is the probability that the needle intersects a line separating two strips?

Let’s first dive into the analytical solution of the problem.

Revisit the question: Given a needle of length l dropped on a plane ruled with parallel lines D units apart, what is the probability that the needle will lie across a line between two strips? In part a, needle B represents the expected condition.

Assume that the needles are made of a homogeneous material. Let x be the distance from the center of mass (COM) of the needle to the closest parallel line, and let θ be the angle between the needle and the parallel line axis. The probability that the needle intersects a line depends on these two variables: x and θ.

Focusing on a single reference line, the probability density function (PDF) of x is defined over the interval 0 (part b, needle B where the COM lies on the line) to D/2 (part b, needle A where the needle is centered midway between two lines), and is given as in part b. For the second variable, θ, the probability density function (PDF) is defined over the interval 0 (part c, needle A lying parallel to the line) to π/2 (part c, needle B rotated by θ from the line), and is given as in part c. Since x and 0 are two independent random variables, the joint probability density function can be written as the product using the multiplication rule: P(A∩B)=P(A)×P(B) as given as in part d. The needle intersects the line only if it satisfies the condition given in part e. There are now two possible scenarios: (i) when the needle length is shorter than the distance between the strips (l≤D), and (ii) when the needle length is greater than the distance between the strips (l>D).
