# Buffon's Needle Problem

## Classical Problem

Buffon’s Needle Problem, one of the earliest problems in geometric probability, was first proposed in the first half of the 18th century. The problem follows like this: Assume a floor made of parallel strips of wood separated by equal widths, and we drop a needle randomly onto the floor (Fig.1.1f). What is the probability that the needle intersects a line separating two strips on the floor?

![buffons_needle](https://github.com/user-attachments/assets/4db0f428-154e-4062-9ada-246415aba42b)

Fig.1

Let’s first dive into the analytical solution of the problem. Revisit the question: Given a needle of length l dropped on a plane ruled with parallel lines D units apart, what is the probability that the needle will lie across a line? In this case, Fig.1.1a needle B represents the expected condition. Assume that the needles are made of a homogeneous material. Let x be the distance from the center of mass (COM) of the needle to the closest parallel line, and let θ be the angle between the needle and the parallel line axis. The probability that the needle intersects a line depends on these two variables: x and θ. Focusing on a single reference line, the probability density function (PDF) of x is defined over the interval 0 (Fig.1.1b, needle B where the COM lies on the line) to D/2 (Fig.1.1b, needle A where the needle is centered midway between two lines). For the second variable, θ, the probability density function (PDF) is defined over the interval 0 (Fig.1.1c, needle A lying parallel to the line) to π/2 (Fig.1.1c, needle B rotated by θ degrees from the line). In other words, this problem’s domain can be defined over the given intervals of x and θ in Fig.1.1b,c. Since x and θ are two independent random variables, the joint probability density function can be written as the product using the multiplication rule: P(AB)=P(A)×P(B) as given in part Fig.1.1d. The needle intersects the line only if it satisfies the condition given in Fig.1.1e, when the needle length is shorter than the distance between the strips (l≤D). 
<img width="5670" height="4014" alt="prob" src="https://github.com/user-attachments/assets/73308234-7ce2-40f0-b3be-aacb5c495a18" />

Fig.2

Integrating the joint probability density function over dx and dθ (for l≤D) yields the probability below in Eq.1 that the needle crosses a line, which depends on l and D.


<img width="562" height="64" alt="Screenshot 2026-03-04 at 05 05 41" src="https://github.com/user-attachments/assets/f0e941ab-1c06-495a-913f-790c1766bd50" />

Eq.1

