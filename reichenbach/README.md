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

**d)** Assuming we have the pair already formed, then we have `5!` possible orders for the pairs, we have to multiply this number with `2^5` because the memebers of the couple can switch position, so we end up with `5! x 2^5 = 120 x 32 = 3.840` seatings. If we need to consider also all the possible different pairs we can obtain then we have to multiply with the `5!` obtaining `460.800` possible arrangements.

<hr/>

### 2: The Cipher Arrays of Irene Adler
Irene Adler hides messages in sorted arrays of k distinct integers, each from 1 to n (e.g., 1 ≤ x[0] < x[1] < … < x[k-1] ≤ n). How many such arrays can she devise, as if concealing clues in a locked box?

Deduction: Unravel the pattern as if outwitting her guile.

#### Solution

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

##### a)

##### b)

##### c)

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

**a)**

**b)**

**c)**

<hr/>

### 5: The Binary Telegram of Baskerville
A telegraph sends M 0’s and N 1’s in random order. What’s the chance the first r bits hold exactly k 1’s, as if decoding a hound’s howl?

Deduction: Reason through the static as if time is running out.

#### Solution

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

**a)**

**b)**

**c)**

<hr/>

### 7: The Investments of Baker Street
Holmes secures £20 million to fund 4 shadowy enterprises, investing in £1 million units, each with a minimum stake: £1M, £2M, £3M, £4M.
<ol type="a">
  <li>If all 4 must be funded to foil Moriarty’s network, how many strategies exist?</li>
  <li>If at least 3 must be backed (to keep the web intact), how many plans work?</li>
</ol>

Deduction: Argue your totals as if pitching to a wary Watson.

#### Solutions

**a)**

**b)**

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

**a)**

**b)**

**c)**

<hr/>

### 9: The Passwords of the Naval Treaty
A spy tackles n distinct passwords, one unlocking a treaty:
<ol type="a">
  <li>Trying randomly and discarding failures, what’s the chance the k-th attempt succeeds?</li>
  <li>Trying randomly without discarding, stopping at success, what’s the chance the k-th try wins?</li>
</ol>

Deduction: Think like the spy—explain as if Holmes is one step ahead.

#### Solutions

**a)**

**b)**

<hr/>

### 10: The Dice of the Speckled Band
Holmes rolls a six-sided die six times to crack a gypsy code:
<ol type="a">
  <li>What’s the chance two numbers appear thrice each (e.g., three 4s, three 6s)?</li>
  <li>What’s the chance exactly one number hits thrice, no more, no less?</li>
</ol>

Deduction: Interpret the rolls as if they spell a fatal clue—mind the overlaps.

#### Solutions

**a)**

**b)**

<hr/>

### 11: The Letters of the Red-Headed League
Holmes dispatches 20 distinct letters to 12 unique informants, each landing randomly. What’s the chance 4 get exactly 2 letters and 3 get exactly 4, the rest empty-handed?

Deduction: Trace the mail as if thwarting a league plot.

#### Solution

<hr/>

### 12: The Buckets of Bohemia
m clues are hashed into N buckets by a rogue algorithm, all N^m outcomes equal. What’s the chance exactly k land in the first bucket?

Deduction: Model the scatter as if piecing together a broken photograph.

#### Solution

## Coding (Sherlock Holmes Edition)

### 13: The Game of the Final Problem
Holmes and Moriarty duel with a device spitting integers from 1 to 100. Holmes adds to S (from 0) until S > 100, noting his last number x. Moriarty resumes, adding until S > 200, noting y. The higher wins. Simulate 100,000 rounds in Python 3 and estimate Moriarty’s victory odds, as if outsmarting Holmes at Reichenbach.

Deduction: Code as if the fate of London hangs in the balance—comment your logic.

#### Solution
