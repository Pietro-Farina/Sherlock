# Howgwarts Quests

### Authors: Pietro Farina, Jacopo Corrao

## Written Problems

### 1
You are tracking the distance to the Hogwarts Express. A magical instrument reports it’s 100 leagues away. Before the reading, your belief about
the distance $D$ was a Gaussian $D ∼ N (μ = 98, σ^2 = 16)$. The instrument’s reading is the true distance plus Gaussian noise $(N (0, 4))$.
<ol type="a">
  <li>What is the PDF of your prior belief of the train’s true distance?</li>
  <li>What is the probability density of seeing a reading of 100 leagues, given the true distance is t?</li>
  <li>What is the PDF of your posterior belief (after the reading) of the train’s true distance? (You can leave a constant and don’t need to simplify).</li>
</ol>

#### Solutions

**a)** Given the belief about the distance $D$ is a Gaussian $D ∼ N (μ = 98, σ^2 = 16)$. Then the PDF of the prior belief is:

$$
f_D(d) = \frac{1}{4 \sqrt{2 \pi}} e^{ -\frac{1}{2} \left(  \frac{d - 98}{4}   \right)^2  }
$$

**b)** Given the true distance is $t$, the PDF of seeing a reading is a normal PDF centered at $t$: $N(t,4)$. The reading is a linear transformation of the distribution of the instrument's error. So, the probability of a reading of 100 leagues is:

$$
P(reading = 100| D = t) = \frac{1}{2 \sqrt{2 \pi}} e^{ -\frac{1}{2} \left(  \frac{100 - t}{2}   \right)^2  }
$$

**c)**

**Prior belief**:  

$$
D \sim \mathcal{N}(\mu_0 = 98,\, \sigma_0^2 = 16)
$$

**Posterior**:  
The instrument measures \( z = D + Noise \), where Distance is 100 and Noise is Gaussian:

$$
\mathcal{N}(0,\, 4)
$$

Since both prior and likelihood are Gaussian, the posterior is also Gaussian.

At this point we can update the mean and the variance:

$$
\mu_{\text{post}} = \frac{\sigma_z^2 \mu_0 + \sigma_0^2 z}{\sigma_0^2 + \sigma_z^2} = \frac{4 \cdot 98 + 16 \cdot 100}{16 + 4} = \frac{1992}{20} = \frac{498}{5} = 99.6
$$

$$
\sigma_{\text{post}}^2 = \frac{\sigma_0^2 \sigma_z^2}{\sigma_0^2 + \sigma_z^2} = \frac{16 \cdot 4}{20} = \frac{16}{5} = 3.2
$$

So the posterior PDF is:

$$
p(D \mid z=100) = \frac{1}{\sqrt{2\pi \cdot 3.2}} \exp\left( -\frac{(D - 99.6)^2}{2 \cdot 3.2} \right)
$$

Note: chatgpt used for this exercise.

<hr/>

### 2
On average, 5.5 owls arrive at the Owlery per minute. What is the probability that:
<ol type="a">
  <li>More than 7 owls will arrive in the next minute?</li>
  <li>More than 13 owls will arrive in the next 2 minutes?</li>
  <li>More than 15 owls will arrive in the next 3 minutes?</li>
</ol>

#### Solution

**a)** The events of owls arriving per minute follows a Poisson distribution: $X ∼ Poi(5.5)$. 
Given the generic PMF equation of a $X ∼ Poi(\lambda)$ is $P(X=x)=\frac{\lambda^x \cdot e^{-\lambda}}{x!}$, 
the probability of more than 7 owls arriving in the next minute is:
$P(X > 7) = 1 - P(X \leq 7) = 1 - (0.004 + 0.022 + 0.062 + 0.113 + 0.156 + 0.171 + 0.157 + 0.123  ) = 1 - 0.808 = 0.191$.

**b)** If we want to know the rate in another unit of time, we just need to mulitply the original rate $(5.5)$ by the new time rate, in this case by two:
$X' \sim Poi(11)$. Again we can find the solution through the previous reasoning:

$$
P(X' > 13) = 1 - P(X' \leq 13) = 1 - \sum_{x=0}^{13} { \frac{11^x e^{-11}}{x!} } \approx 1 - 0.781  = 0.219
$$

**c)** Similarly as we did above, $X'' \sim  Poi(16.5)$:


$$
P(X'' > 15) = 1 - P(X' \leq 15) = 1 - \sum_{x=0}^{15} { \frac{16.5^x e^{-16.5}}{x!} } \approx 1 - 0.418  = 0.582
$$

The python code used for the summations is the following:

```
import math
lam = 5.5 * 2
l = 13
sum = 0
for x in range(0, l+1):
    fact = math.factorial(x)
    e = math.exp(- lam)
    sum = sum + (((lam ** x) * e) / fact)
print(sum)
```

<hr/>

### 3
The median of a continuous random variable (like the height of a gnome) having cumulative distribution
function $F$ is the value $m$ such that $F(m) = 0.5$.
Find the median of $X$ (in terms of distribution parameters) if:
<ol type="a">
  <li>$X ∼ Uni(a, b)$ (Uniform distribution, like the spread of Floo powder).</li>
  <li>$X ∼ N (μ, σ^2)$ (Normal distribution, like scores on the O.W.L.s).</li>
</ol>

#### Solutions

**a)** The CDF of a uniform distribution $X \sim Uni(a, b)$ is:

$$
F(x) = 
\begin{cases}
\frac{x - a}{b - a}, & \text{if } a \leq x \leq b \\
0, & \text{if } x < a \\
1, & \text{if } x > b
\end{cases}
$$

We can substitute $m$ in the equation:

$$F(m) = \frac{m - a}{b -a} \quad \textrm{and given} \quad F(m) = \frac{1}{2} $$

$$ \frac{m - a}{b -a} = \frac{1}{2} $$

$$ 2m -2a = b - a $$

$$ 2m = b + a $$

$$ m = \frac{b + a}{2} $$


**b)** The CDF of a normal distribution $X \sim N(\mu, \sigma ^2)$ is:

$$
F(x) = \Phi \left( \frac{x - \mu}{\sigma} \right)
$$

Again, we can set $x=m$ and $F(m)=\frac{1}{2}$ :

$$
\Phi \left( \frac{m - \mu}{\sigma} \right) = \frac{1}{2}
$$

From the properties of the $\Phi$ (CDF of standard normal), we know that $\Phi(0) = 1/2$, thus we obtain the following:

$$ \frac{m - \mu}{\sigma} = 0  $$

This equation have one solution which is $m = \mu$. This result follows naturally from the symmetry of the normal distribution around its mean.

<hr/>

### 4
Let $X_i$ be the number of students visiting the Hogwarts library in week $i$, where $X_i ∼ N (2200, 52900)$. Assume weekly visits $X_i$ are independent.
<ol type="a">
  <li>What is the probability that the total number of visitors in the next two weeks exceeds 5000?</li>
  <li>What is the probability that the weekly number of visitors exceeds 2000 in at least 2 of the next 3 weeks?</li>
</ol>

#### Solutions

**a)** For any two independent normal random variables $X ∼ N (μ_1, σ_1^2)$ and $Y ∼ N (μ_2, σ_2^2)$
the sum of those two random variables is another normal: $X + Y ∼ N (μ_1 + μ_2, σ_1^2 + σ_2^2)$. Since we are assuming that
weekly visits are independent the probability requested is $P(X_1 + X_2 > 5000) = P(X' > 5000)$,
where $X' \sim N(\mu_{X'}, \sigma_{X'}^2)$ and $\mu_{X'} = 4400, \sigma_{X'} = \sqrt(105'800)$:



$$
P(X_1 + X_2 > 5000) = P(X' > 5000) = P \left( \frac{X' - \mu_{X'}}{\sigma_{X'}} > \frac{5000 - \mu_{X'}}{\sigma_{X'}} \right) =
P \left( Z > \frac{5000 - \mu_{X'}}{\sigma_{X'}}  \right) = 1 - P \left( Z \leq \frac{5000 - \mu_{X'}}{\sigma_{X'}}  \right) =
$$

$$
1 - P \left( Z \leq \frac{5000 - \mu_{X'}}{\sigma_{X'}}  \right)
\approx 1 - \Phi \left( \frac{5000 - 4400}{325,27}  \right) \approx 1 - \Phi \left( 1,845 \right) \approx 1 - 0.967 = 0.033
$$


**b)** Let's calculate the probability of $P(X_i > 2000)$ as follows:

$$
P(X_i > 2000) = P \left( Z > \frac{2000 - 2200}{230}  \right) \approx P ( Z > -0.87 ) = 1 - P(Z \leq -0.87) = 
$$

$$
1 - P(Z \leq -0.87) = 1 - \Phi(-0.87) = 1 - (1 - \Phi(0.87)) = \Phi(0.87) \approx 0.8078
$$

Now we can define $Y$ as the number of weeks the visitors exceed 2000 in 3 weeks. $Y$ is a binomial distribution: $Y \sim Bin(n = 3, p = 0.8078)$. Since we want at least two weeks we will have to compute:

$$
P(Y \geq 2) = P(Y = 2) + P(Y = 3)
$$

$$
P(Y = 2) = \binom{3}{2} (0.8078)^2 (1 - 0.8078)^1 \approx 0.376
$$

$$
P(Y = 3) = \binom{3}{3} (0.8078)^3 (1 - 0.8078)^0 \approx 0.527
$$

So, the final result is $P(Y \geq 2) \approx  0.376  +   0.527  = 0.903$

<hr/>

### 5

Let $X$, $Y$, and $Z$ be independent random variables representing the magical power levels of three Hogwarts students, where $X ∼ N (μ_1, σ_1^2)$
(Gryffindor), $Y ∼ N (μ_2, σ_2^2)$ (Hufflepuff), and $Z ∼ N (μ_3, σ_3^2)$ (Ravenclaw).
<ol type="a">
  <li>
    Let $A = X + Y$. What is the distribution of the combined power $A$?
  </li>
  <li>
    Let $B = 5X + 2$. What is the distribution of $B$ (perhaps after a powerenhancing charm)?
  </li>
  <li>
    Let $C = aX − bY + c^2Z$, where $a$, $b$, and $c$ are real-valued constants representing spell modifiers. What is the distribution (and parameters) for $C$? Show how you derived your answer.
  </li>
</ol>

#### Solution

**a)** For any two independent normal random variables $X ∼ N (μ_1, σ_1^2)$ and $Y ∼ N (μ_2, σ_2^2)$
the sum of those two random variables is another normal: $X + Y ∼ N (μ_1 + μ_2, σ_1^2 + σ_2^2)$.
Thus, we can define the distribution of $A = X + Y$ as follows $A \sim N (μ_1 + μ_2, σ_1^2 + σ_2^2)$.

**b)** From the property of linear transformation of normal distribution: If $X$ is a Normal such that $X ∼ N (μ, σ^2)$
and $Y$ is a linear transform of $X$ such that $Y = aX + b$ then $Y$ is also a Normal where: $Y ∼ N (aμ + b, a^2σ^2)$.
Given $B = 5X + 2$, then $B \sim N (5μ_1 + 2, 25σ_1^2)$.

**c)** To obtain the distribution $C$ we can use the previous properties. Let's define three new distribution X', Y' and Z':

1. $X' = aX, \quad X' \sim N(a \mu_1, a^2 \sigma_1^2)$
2. $Y' = -bY, \quad Y' \sim N(-b \mu_2, b^2 \sigma_2^2)$
3. $Z' = c^2Y, \quad Y' \sim N(c^2 \mu_3, c^4 \sigma_3^2)$

We can rewrite the definition of $C$ as $C = X' + Y' + Z'$. Since it is a sum of normal distribution, also $C$ will
be a normal distribution:

$$
C \sim N( a \mu_1 -b \mu_2 + c^2 \mu_3, \quad a^2 \sigma_1^2 + b^2 \sigma_2^2 + c^4 \sigma_3^2 ) .
$$

<hr/>

### 6
The joint probability density function of continuous random variables $X$ (skill in Potions) and $Y$ (skill in Charms)
is given by $f_{X,Y} (x, y) = c\frac{y}{x}$ , where $0 < y < x < 1$.
<ol type="a">
  <li>
    What is the value of c for this to be a valid probability density function?
  </li>
  <li>
    Are Potion skill $(X)$ and Charm skill $(Y)$ independent? Explain.
  </li>
  <li>
    What is the marginal density function of $X$?
  </li>
  <li>
    What is the marginal density function of $Y$?
  </li>
</ol>


#### Solutions

**a)** To be a valid probability density function it must integrate to 1 over the region $0 < y < x < 1$.

$$
\int_{0}^{1} \int_{0}^{x}           c \cdot \frac{y}{x}           \\,dy \\,dx = 1
$$

Let's solve the first integral with respect to $y$.

$$
\int_{0}^{1} \frac{c}{x} \int_{0}^{x}           y           \\,dy \\,dx = 1
$$

$$
\int_{0}^{1} \frac{c}{x}      \left[ \frac{y^2}{2}   \right]^x_0       \\,dx = 1
$$

$$
\int_{0}^{1} \frac{c}{x}       \cdot \frac{x^2}{2}            \\,dx = 1
$$

$$
\int_{0}^{1} \frac{c}{2}    \cdot x           \\,dx = 1
$$

Let's integrate with respect to $x$:

$$
\frac{c}{2} \int_{0}^{1} x           \\,dx = 1
$$

$$
\frac{c}{2} \cdot \left[ \frac{x^2}{2}   \right]^1_0 = 1
$$

$$
\frac{c}{2} \cdot \frac{1}{2} = 1
$$

We obtain that $c = 4$.

**b)** For $X$ and $Y$ to be independet, the following equation must be satisfied $f_{X,Y}(x,y) \stackrel{?}{=} f_X(x) \cdot f_Y(y)$. We will anticpate exercise (c) and (d) by computing now the marginal distributions:

$$
f_X(x) = \int_{0}^{x} f_{X,Y}(x,y) \\,dy  = \int_{0}^{x} 4 \cdot \frac{y}{x} \\,dy  =  \frac{4}{x} \cdot \left[ \frac{y^2}{2}   \right]^x_0 = \frac{4}{x} \frac{x^2}{2} = 2x
$$

$$
f_Y(y) = \int_{y}^{1} f_{X,Y}(x,y) \\,dx  = \int_{y}^{1} 4 \cdot \frac{y}{x} \\,dx  = 4y \int_{y}^{1} \frac{1}{x} \\,dx = 
4y \cdot \left[ \ln(x) \right]^1_y = 4y \cdot \left[ \ln(1) - \ln(y) \right] = -4 y \ln(y)
$$

So, we obtained that:

$$
f_X(x) = 2x \quad \textrm{for} \quad 0 < x < 1 \quad \textrm{and} \quad f_Y(y) = -4 y \ln(y) \quad \textrm{for} \quad 0 < y < 1 .
$$

Thus, $f_X(x) \cdot f_Y(y) = -8xy \ln(y)$. As we can see:

$$
f_{X,Y}(x,y) = \frac{4y}{x} \neq -8xy \ln(y) = f_X(x) \cdot f_Y(y)
$$

So, $X$ and $Y$ are not independent. This can also be observed by the mutual dependency between $x$ and $y$ given by the domain $0 < y < x < 1$, since knowing either one of the variables narrows the possibilities for the other one.


**c)** As we obtained in the exercise (b):

$$
f_X(x) = 2x \quad \textrm{for} \quad 0 < x < 1 .
$$

**d)** As we obtained in the exercise (b):

$$
f_Y(y) = -4 y \ln(y) \quad \textrm{for} \quad 0 < y < 1 .
$$

Note: chatgpt used to remember how double integrals work (it is been a while after I passed Analysis 1).
<hr/>

### 7
Choose a number $X$ at random from the set of house points ${1, 2, 3, 4, 5, 6}$
awarded by Professor McGonagall. Now choose a number $Y$ at random
from the subset of points no larger than $X$, $\\{1, ..., X\\}$.
<ol type="a">
  <li>
    Determine the joint probability mass function of $X$ (initial points) and
$Y$ (second random selection).
  </li>
  <li>
    Determine the conditional mass function $P (X = j|Y = i)$ as a function
of $i$ and $j$.
  </li>
  <li>
    Are $X$ and $Y$ independent? Explain
  </li>
</ol>

#### Solutions

**a)**  First we have the PDF of $X$ which is $P(X = x) = \frac{1}{6}, x \in \\\{1, 2, 3, 4, 5, 6\\\}$. We also have the PDF of $Y$ given $X$: $P(Y = y | X = x) = \frac{1}{x}, y \in \\{1, 2, ..., x\\}$.

From the definition of Conditional Probability we have that $P(E|F) = \frac{P(E \\, and \\, F)}{P(F)}$. So, $P(E \\, and \\, F) = P(E|F)P(F)$.

$$
P(X = x, Y = y) = P(X = x) \cdot P(Y = y | X = x) = \frac{1}{6} \cdot \frac{1}{x}, \quad
\textrm{for } y \in \\{1, 2, ..., x\\} \textrm{ and } x \in \\{1, 2, 3, 4, 5, 6\\} .
$$

$$
P(X = x, Y = y) = 
\begin{cases}
\frac{1}{6} \cdot \frac{1}{x}, & \text{if } y \in \\{1, 2, ..., x\\} \textrm{ and } x \in \\{1, 2, 3, 4, 5, 6\\} \\
0, & \text{otherwise }
\end{cases} .
$$

Note that $x \geq y$ due the bound on the extraction of $Y$.

**b)** We can obtain the conditional mass function $P(X = j| Y = i)$ from the conditional probability formula:
$P(X = j| Y = i) = \frac{P(X = j, Y = i)}{P(Y = i)}$.

We have already obtained $P(X = j, Y = i) = \frac{1}{6j} \textrm{ for } j \geq i$ from the previous exercise.
To find $P(Y = i)$ we can use the law of total probability $P(E) = \sum_{i=1}^n P(E \textrm{ and } F_i)$ :

$$
P(Y = i) = \sum_{j=i}^6 P(X = j, Y = i) = \sum_{j=i}^6 \frac{1}{6j} =
\frac{1}{6} \cdot \sum_{j=i}^6 \frac{1}{j} = \frac{1}{6} \cdot \left(  \frac{1}{i} + \frac{1}{i+1} + ... \frac{1}{6}  \right)
$$

So, the conditional mass function $P(X = j| Y = i)$ is:

$$
P(X = j| Y = i) = \frac{P(X = j, Y = i)}{P(Y = i)} = \frac{\frac{1}{6j}}{\frac{1}{6} \cdot \left(  \frac{1}{i} + \frac{1}{i+1} + ... \frac{1}{6}  \right)} =
\frac{\frac{1}{j}}{ \frac{1}{i} + \frac{1}{i+1} + ... \frac{1}{6}  }, \quad \textrm{for } i \leq j \leq 6.
$$

**c)** For $X$ and $Y$ to be independet, the following equation must be satisfied $P(X = x, Y =y) \stackrel{?}{=} P(X = x) \cdot P(Y = y)$.

$$
P(X = x, Y = y) = \frac{1}{6x} \stackrel{?}{=} \frac{1}{6} \cdot \sum_{y=x}^6 \frac{1}{6x} = P(X = x) \cdot P(Y = y)
$$

We see that $P(X=x,Y=y)$ does not factor as $P(X=x) \cdot P(Y=y)$, we can simply pick the values $(x=6, y=6)$ to show that since it lead to $\frac{1}{36} \neq \frac{1}{6} \cdot \frac{1}{36}$. Therefore, $X$ and $Y$ are not independent. Again by reasoning $X$ and $Y$ are dependent because the outcome of $X$ impacts the distribution of $Y$.
