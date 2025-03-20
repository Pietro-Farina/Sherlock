# The Reichenbach Reckoning: Sherlock Holmes’ Mathematical Mysteries

These quests are infused with the atmosphere of Victorian mystery, deductive reasoning, and the intrigue of 221B Baker Street. The problems are now framed as cases or puzzles Holmes and Watson might encounter, requiring clever twists and contextual reasoning.

## Written Problems

### 1: The Seating of the Diogenes Club
Sherlock Holmes investigates a clandestine meeting at the Diogenes Club, where 10 distinct members must sit in a row under strict protocols:
<ol type="a">
  <li>If no rules bind their arrangement, how many ways can the silent gentlemen be seated?</li>
  <li>Suppose Mycroft Holmes and his aide, bound by mutual distrust, must sit side-by-side to monitor each other—how many arrangements are possible?</li>
  <li>If 5 are seasoned inspectors and 5 are novice constables, and no two of the same rank may sit adjacent (lest rivalries flare), how many seating orders hold?</li>
  <li>If the 10 form 5 pairs of informants and handlers, each pair inseparable due to whispered secrets, how many arrangements emerge?</li>
</ol>

Deduction: Explain your reasoning as if briefing Watson on the club’s hidden hierarchy.

#### Solutions

**a)** The members are distinct so we can use the perfmutation rule: a permutation is an ordered arrangement of n distinct objects. Thus, the silent gentlemen can be seated in `10! = 3.628.800` different ways.

**b)** We can think of Mycroft Holmes and his aide as a inseperable couple, or better as a single unit. By doing so, we have to count the possible arrengments of 9 unit (8 gentlemen + 1 couple), which again is a permutation, and multiply it by two because the member of the couple can switch position (x,y) or (y,x). So, there are `2 x 9!= 2 x 362880 = 725.760` arrangements.

**c)** Since the two classes have to sit alternated to avoid discussion, we can count the seatings between the same classes independently and then multiply them together. So the number of seatings between the same class is `5! = 120`.
Now, we need to take into account that all the inspectors will either all sit on an even seat or all sit on an odd seat. Thus, the final number of seatings will be `(5! x 5!) x 2 = 14.400 x 2 = 28.800`

**d)** Assuming we have the pair already formed, then we have `5!` possible orders for the pairs, we have to multiply this number with `2^5` because the memebers of the couple can switch position, so we end up with `5! x 2^5 = 120 x 32 = 3.840` seatings. If we need to consider also all the possible different pairs we can obtain, then we have to multiply with the `5!` obtaining `460.800` possible arrangements.

<hr/>

### 2: The Cipher Arrays of Irene Adler
Irene Adler hides messages in sorted arrays of k distinct integers, each from 1 to n (e.g., 1 ≤ x[0] < x[1] < … < x[k-1] ≤ n). How many such arrays can she devise, as if concealing clues in a locked box?

Deduction: Unravel the pattern as if outwitting her guile.

#### Solution

We have a set of integers: {1, ..., n), and we need to pick k different integer in an increasing order since the alogirthm are sorted.
The fact that they are sorted means that we can discard the other possible permutations of the same choosen subset.
Given this, given this we can reduce the problem to combinations of distinct objects: a combination is an unordered selection of r objects from a set of n objects: `n!/(k! x (n-k)!)`.

Note: here Chatgpt helped Sherlock to understand the problem.

<hr/>

### 3: The Paths of the Hound
A mechanical hound roams an n × m grid from (1,1) to (n,m), moving only right or down:
<ol type="a">
  <li>With no bounds, how many trails can it leave?</li>
  <li>If it must first lurch right (a faulty gear), how many paths remain?</li>
  <li>If it switches direction exactly thrice (right-to-down or down-to-right), how many routes obey?</li>
</ol>

Deduction: Track its steps as if hunting it across the moors.

#### Solutions

**a)** To move from (1,1) to (n,m), the hound need to take precisely (n-1) down steps and (m-1) right steps. So, every path is a sequence of (n-1) + (m-1) steps, which can be rewritten as (n+m-2). The problem reduces to _"how many ways can we arrange (n−1) down steps and (m−1) right steps in a sequence of length (n+m−2)?"_, and here fellow Chatgpt suggested that we need to choose positions for the (n-1) down steps, or alternatively (m-1) right steps, and it remembered that since binomial coefficients are symmetric, both choices lead to the identical result.
After here it was _elementary_ to deduce the solutions was `(n+m-2)!/(n-1)! x (m-1)!`

**b)** Given the fact that the first move is fixed as a right, then we have to arrange only (n-1) down steps and (m-2) right steps, in a sequence of length (n-1)+(m-2)=(n+m-3). So, the number of paths are `(n+m-3)!/(n-1)! x (m-2)!`

**c)** Here Sherlock had to ask again help to Chatgpt, which explained that we can divide the number of moves into 4 segments:
`x1+x2+x3+x4=n+m−2`, where two segments correspond to right moves and two segments correspond to down moves. Each segment must be at least one move long (otherwise, it wouldn’t be a proper switch), so we require: `x1​,x2​,x3​,x4​≥1`, which translates into `x1+x2+x3+x4=n+m−6`. The number of valid solutions to this equation in non-negative integers is given by the stars and bars formula: `(n+m-3)!/3!x(n+m-6)!`, which represents the number of ways to distribute the remaining n+m−6n+m−6 moves among the 4 segments. We have a 3 below since they represents the three dividers in the sequence of moves.

<hr/>

### 4: The Poker Game at Reichenbach
Holmes faces Moriarty at a poker table, where all 5-card hands from a 52-card deck are equally likely:
<ol type="a">
  <li>What’s the chance of a flush (all same suit), including straight flushes?</li>
  <li>What’s the chance of two pairs (a, a, b, b, c, distinct values)?</li>
  <li>What’s the chance of four of a kind (a, a, a, a, b, distinct)?</li>
</ol>

Deduction: Compute the odds as if spotting Moriarty’s bluff.

#### Solutions

**a)** The total number of possible distinct hands are `C(52,5) = 2.598.960`. A flush of a given suit can be done in `C(13,5) =  1287` different ways, and since we have four suit we have `4 x 1287 = 5148` possible flushes. The chance of having a flush, including straight ones, are `5148/2.598.960` which is approximately `0,1980%`.

**b)** First let's choose two different values of the cards that will be pairs, in our case a and b: `C(13,2)`, for each of these values, pick two suits from the four suits available: `C(4,2) x C(4,2)`. Let's take the last different card c and its suit: `C(11,1) x C(4,1)`. The final result is `C(13,2) x C(4,2) x C(4,2) x (11,1) x (4,1) / C(52,5) = 78 x 6 x 6 x 11 x 4 / 2.598.960 = 123.552 / 2.598.960 = 0,04753`, which is approximately `47,53%`.

**c)** For a four of a kind we can take the card a: `C(13,1) x (4,4)`, and the different card b: `C(11,1) x (4,1)`. This result in `C(13,1) x (4,4) x C(12,1) x (4,1) / C(52,5) = 13 x 1 x 12 x 4 / 2.598.960 = 624 / 2.598.960 = 0,00024`, which is around `0,024%`.

<hr/>

### 5: The Binary Telegram of Baskerville
A telegraph sends M 0’s and N 1’s in random order. What’s the chance the first r bits hold exactly k 1’s, as if decoding a hound’s howl?

Deduction: Reason through the static as if time is running out.

#### Solution

The possible subsequences (or prefix) of the telegraph with length r are given by C(M+N, r), we can enforce the constraint of having exactly k 1's by `C(N, k) x C(M, r-k)`, which represents having exactly k 1's and r-k 0's. So, the final result is given by `C(N, k) x C(M, r-k) / C(M+N, r)`.

<hr/>

### 6: The Menagerie of Moriarty
Holmes uncovers Professor Moriarty’s scheme to display 3 bird species and 3 reptile species, selected from 8 birds and 6 reptiles, in a sinister zoo:
<ol type="a">
  <li>If Moriarty chooses freely, how many exhibits can he craft?</li>
  <li>Two birds—one a hawk with a piercing cry, the other a raven with a deadly glare—cannot coexist without chaos. How many exhibits avoid this peril?</li>
  <li>A venomous parrot and a cobra, when paired, unleash a toxic fog. How many exhibits dodge this trap?</li>
</ol>

Deduction: Justify your counts as if tracing Moriarty’s twisted logic.

#### Solutions

**a)** Assuming that the birds and reptiles are of different species, Mortiary can choose freely three bird for his exhibit: C(8,3), and 3 reptiles: C(6,3). So, he can craft a total of `C(8,3) x C(6,3) = 56 x 20 = 1.120` exhibits.

**b)** Here Chatgpt gave a hint about the reasoning, the idea is to subtract from the total number of exhibits, the number of invalid ones, which are the one with the two birds. The chance of getting the two birds which are `C(2,2)=1` and a third bird from the remaining 6: C(6,1). The choices of reptiles is the same as before: C(6,3). So, in summary we have `1.120 - (1 x C(6,1) x C(6,3) (invalid cases) = 1.120 - (6 x 20) = 1.000` exhibits that avoid the dangerous peril.

**c)** We can perform a similar reasoning for this problem, in particular we have 1 venoumous parrot and two other birds to pick: C(7,2), a cobra and other two reptile C(5,2). So, the amount of exhibits that dodge the venomous trap are `1.120 - (C(7,2) x C(5,2)) = 1.120 - (21 x 10) = 910`

<hr/>

### 7: The Investments of Baker Street
Holmes secures £20 million to fund 4 shadowy enterprises, investing in £1 million units, each with a minimum stake: £1M, £2M, £3M, £4M.
<ol type="a">
  <li>If all 4 must be funded to foil Moriarty’s network, how many strategies exist?</li>
  <li>If at least 3 must be backed (to keep the web intact), how many plans work?</li>
</ol>

Deduction: Argue your totals as if pitching to a wary Watson.

#### Solutions

**a)** We had to ask help to the investor Chatpgt, which suggested to reduce the problem into a "stars and bars" one. The starting assumption is that each enterprise has its own distinct minimum, so the remiaining budget across all 4 enterprieses will be of 10M.
Now we can use the "stars and bars" formula to distribute 10 indistinguishable units among 4 distinguishable enterprises. The formula for distributing n identical items among k bins is: C(n+k-1, k-1). So, our case we will have `C(10+4-1, 4-1) = C(13,3) = 286` possible strategies.

**b)** Now, if we add the possibility of not funding one enterprise, we will have a higher budget for the other three, which depends on the minimum budget of the not funded one. So, we need to count each case:
1. Removing Enterprise 1 (£1M Minimum): remaining budget is 11M among 3 enterprises resulting in `C(13, 2) = 78` different ways.
2. Removing Enterprise 2 (£2M Minimum): remaining budget is 12M among 3 enterprises resulting in `C(14, 2) = 91` different ways.
3. Removing Enterprise 3 (£3M Minimum): remaining budget is 13M among 3 enterprises resulting in `C(15, 2) = 105` different ways.
4. Removing Enterprise 4 (£4M Minimum): remaining budget is 14M among 3 enterprises resulting in `C(16, 2) = 120` different ways.

So, the final number of possible plans is `286 + 78 + 91 + 105 + 120 = 680`

<hr/>

### 8: The Coding Conundrum of Scotland Yard
Holmes probes a cryptography school where 100 agents study 3 courses—Java, C++, Python—under Lestrade’s watch:
Java: 27 agents; C++: 28; Python: 20.
12 crack Java and C++; 5 master Java and Python; 8 excel in C++ and Python.
2 prodigies conquer all three.
<ol type="a">
  <li>What’s the chance a random agent has evaded all courses, lurking in the shadows?</li>
  <li>What’s the chance an agent studies exactly one, avoiding the others’ scrutiny?</li>
  <li>If two agents are nabbed, what’s the odds at least one knows a course? Give a final number?</li>
</ol>

Deduction: Map the overlaps as if decoding a Yard cipher—explain each step.

#### Solutions

**a)** The problem of agents can be reduced to the problem of inclusion-exclusion with three events: C++, Python and Java; we will use just C, P and J. Since they are not musually exclusive we can count the probability of an agent attending at least one course with the following formula `P(C or P or J) = P(C) + P(P) + P(J) - P(C and P) - P(C and J) - P(P and J) + P(C and P and J) = 27 + 28 + 20 - 8 - 12 - 5 + 2 = 52`. So, the number of agents studying zero courses are `100 - 52 = 48`, from here the chance a random agent has evaded all courses is `48%`. 

**b)** Since we want agents studying exactly one we must compute all the following chances:
1. `P(C and not P and not J) = P(C) - (P(C and P) - P(C and J) - P(C and P and J)) =  28 - (8 + 12 - 2) = 28 - 18 = 10`
2. `P(P and not C and not J) = P(P) - (P(C and P) - P(P and J) - P(C and P and J)) =  20 - (8 + 5 - 2)  = 20 - 11 = 9`
3. `P(J and not C and not P) = P(J) - (P(J and P) - P(C and J) - P(C and P and J)) =  27 - (5 + 12 - 2) = 27 - 15 = 12`
So, the total agent studying exactly one course is `10 + 9 + 12 = 31`, thus the probability is `0,31` or `31%`.

**c)** By nabbing two students, the probability that at least one knows a course is 1 minus the probability of both agents evading all courses: `1 - (0.48 x 0.48) = 1 - 0.2304 = 0,7696`, approximately `77%`

<hr/>

### 9: The Passwords of the Naval Treaty
A spy tackles n distinct passwords, one unlocking a treaty:
<ol type="a">
  <li>Trying randomly and discarding failures, what’s the chance the k-th attempt succeeds?</li>
  <li>Trying randomly without discarding, stopping at success, what’s the chance the k-th try wins?</li>
</ol>

Deduction: Think like the spy—explain as if Holmes is one step ahead.

#### Solutions

**a)** Each password has a chance of `1/n` to be picked. Since we are discarding the failures after drawing a wrong password, the next one will be picked by the `(n-1)` remaining passwords, and so on till reaching the k-th tries which will be picked from the `(n-k+1)` passwords left. Since we want to get the right password at the excatly k-th try, then we have to always pick a wrong password before. For example, at the first try we have n wrong passwords minus the right one over all the passwords n: `(n-1)/n`, at the second tries we will have `(n-2)/(n-1)` because we have discarded a password. So, we will have: `(n-1)/n * (n-2)/(n-1) * ... * (n-k+1)/(n-k+2)` which represents picking the wrong password until the (k-1)-th attempt, we can simplify it as `(n-k+1)/n`. This has to be multplied to the probability of picking the right passsword at the k-th try which is: `1/(n-k+1)`. So, the final result is `(n-k+1)/n * 1/(n-k+1) = 1/n`.

**b)** In this case, since the spy don't discrd the failures, it will have to repeat picking the wrong password for `(k-1)` tries, each with a probability of `(n-1)/n`, and finnally pick the right result at k-th try with a probability of `1/n`. So, the the chance to win at the k-th try is: `((n-1)/n)^(k-1) * 1/n`.

<hr/>

### 10: The Dice of the Speckled Band
Holmes rolls a six-sided die six times to crack a gypsy code:
<ol type="a">
  <li>What’s the chance two numbers appear thrice each (e.g., three 4s, three 6s)?</li>
  <li>What’s the chance exactly one number hits thrice, no more, no less?</li>
</ol>

Deduction: Interpret the rolls as if they spell a fatal clue—mind the overlaps.

#### Solutions

**a)** Chatgpt came to the rescue once again, explaining we are dealing with a distribution of six numbers in a sequence of six independent trials. The general idea is to multiply: `numbers of possible two numbers x number of ways to arrange three of the two numbers x probability of a particular sequence`:
1. The possible combinations of number is easy: `C(6,2) = 15`.
2. The number of ways to arrange three times two different numbers corresponds to the Permutations of Indistinct Objects, which is given by `6!/(3! x 3!) = 20`, because we have two numbers, each one is appearing three times in the sequence and we dont make distinction between the same numbers.
3. Finnally, each roll has 1/6 chance of landing on any numbers, so the probability of any given sequence is `(1/6)^6 = 1/46.656`.
We can obtain the final result which is: `300/46.656 = 0,00643` which is around `0,64%`.

**b)** Similarly, if exactly one number hits thrice, it means that the others number can appears at most two times. We can have two cases:
1. one number appearing thrice, one number appearing twice, one number appearing once, three numbers don't appear. Thus, we have 6 choices for the number appearing thrice, 5 choices for one number appearing twice, and 4 choices for the last number, for a total of 120 choices. The rolls can be arranged similarly as we did before: `6!/(3! x 2!) = 60`. For a total of `7.200/46.656` probabilities.
2. one number appearing thrice, three numbers appear once and two numbers don't appear. Again, we have `6 x C(5,3) = 60` choices, with `6!/3! = 120` arrangements. For a total of `7.200/46.656` probabilities. This time we did not have repetition between the remaining three numbers and that's why we used combination of distinct object.

We can then sum together the two cases to have the final chance of having exactly one number hits thrice: `(7.200 + 7.200)/46.656 = 0,3086` which is close to `30,86%`. 



<hr/>

### 11: The Letters of the Red-Headed League
Holmes dispatches 20 distinct letters to 12 unique informants, each landing randomly. What’s the chance 4 get exactly 2 letters and 3 get exactly 4, the rest empty-handed?

Deduction: Trace the mail as if thwarting a league plot.

#### Solution

From the Bucketing with Distinct Objects we have 12^20 possible ways to distribute the letters among the informant. We can choose the informant that will get 2 letters with `C(12,4)` and the informants that will receive 4 letters with `C(8,3)`.
The first group can receive letters in the following different ways: `C(20,2) x C(18,2) x C(16,2) x C(14,2)`. For the second group instead: `C(12,4) x C(8,4) x C(4,4)`.

Finnally, the chance that 4 informants get exactly 2 letters, 3 get exactly 4, and the rest empty-handed is `{[C(12,4) x C(8,3)] x [C(20,2) x C(18,2) x C(16,2) x C(14,2)] x [C(12,4) x C(8,4) x C(4,4)]}/12^20`.

<hr/>

### 12: The Buckets of Bohemia
m clues are hashed into N buckets by a rogue algorithm, all N^m outcomes equal. What’s the chance exactly k land in the first bucket?

Deduction: Model the scatter as if piecing together a broken photograph.

#### Solution

The probability of one clue landing in a precise bucket is `1/N`. There are `C(m,k)` possible ways to choose the k clues that enter the first bucket, for each of those clue the probability of landing in the first bucket is `1/N`, thus the probability of k clues landing in the first bucket is `(1/N)^k`. Since we have exactly k clues in the first bucket, all the others clues cannot enter in the first bucket and they do so with a probability of `(N-1/N)` each, so the probability of all other m-k clues landing in a bucket different from the first is `(N-1/N)^m-k`.
Thus, the chance exactly k land in the first bucket is `C(m,k) x (1/N)^k x (N-1/N)^m-k`.

## Coding (Sherlock Holmes Edition)

### 13: The Game of the Final Problem
Holmes and Moriarty duel with a device spitting integers from 1 to 100. Holmes adds to S (from 0) until S > 100, noting his last number x. Moriarty resumes, adding until S > 200, noting y. The higher wins. Simulate 100,000 rounds in Python 3 and estimate Moriarty’s victory odds, as if outsmarting Holmes at Reichenbach.

Deduction: Code as if the fate of London hangs in the balance—comment your logic.

#### Solution

We can write the following code to estimate Moriarty’s victory odds:

```
import random

class Spitter_Device:    
    def __init__(self, seed = 10):
        random.seed(seed)
    
    def spit_integer(self):
        values = random.randint(1, 100)
        
        return values

def play_one_round(device):
    s, x, y = 0, 0, 0
    
    while (s<=100):
        x = device.spit_integer()
        s += x
    
    while (s<=200):
        y = device.spit_integer()
        s += y
    
    return x, y

def simulate_many_rounds(rounds):
    device = Spitter_Device()
    
    holmes, moriarty, draws, current_round = 0, 0, 0, 0
    
    while (current_round < rounds):
        x, y = play_one_round(device)

        if (x == y):
            draws += 1
        elif (x > y):
            holmes += 1
        else:
            moriarty += 1
            
        current_round += 1
        
        if ((current_round % 10000) == 0):
            print(f'Status: {round(current_round/10000)} / {round(rounds/10000)}')
    
    print(f'Final stats: Holmes with {holmes} wins and Moriarty with {moriarty} wins, draws {draws}')
    
    p_total = holmes + moriarty + draws
    p_holmes = holmes / p_total
    p_moriarty = moriarty / p_total
    p_draws = draws / p_total

    print(f'Prob of Holmes winning {round(p_holmes * 100, 1)}%\nProb of Moriarty winning {round(p_moriarty * 100, 1)}%\nProb of draws {round(p_draws * 100, 1)}%')

simulate_many_rounds(100000)
```

which will output:

```
Final stats: Holmes with 46484 wins and Moriarty with 52231 wins, draws 1285
Prob of Holmes winning 46.5%
Prob of Moriarty winning 52.2%
Prob of draws 1.3%
```
