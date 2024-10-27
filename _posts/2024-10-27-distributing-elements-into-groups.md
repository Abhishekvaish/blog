---
layout: post
title: "Distributing elements into groups all variants"
tags: "combinatorics, maths, partition, number theory"
---

Grouping of elements into groups depends on 3 conditions

1. whether the elements are distinct or identical.
2. whether the groups are distinct or identical.
3. whether groups can be empty or not.

So we have 8 possible combinations of above 3 conditions.

- [Number of ways to distribute _n_ **identical** elements into _m_ **distinct** non-empty groups.](#1-number-of-ways-to-distribute-n-identical-elements-into-m-distinct-non-empty-groups)
- [Number of ways to distribute _n_ **identical** elements into _m_ **distinct** groups.](#2-number-of-ways-to-distribute-n-identical-elements-into-m-distinct-groups)

---

- [Number of ways to distribute _n_ **distinct** elements into _m_ **identical** non-empty groups.](#3-number-of-ways-to-distribute-n-distinct-elements-into-m-identical-non-empty-groups)
- [Number of ways to distribute _n_ **distinct** elements into _m_ **identical** groups.](#4-number-of-ways-to-distribute-n-distinct-elements-into-m-identical-groups)

---

- [Number of ways to distribute _n_ **identical** elements into _m_ **identical** non-empty groups.](#5-number-of-ways-to-distribute-n-identical-elements-into-m-identical-non-empty-groups)
- [Number of ways to distribute _n_ **identical** elements into _m_ **identical** groups.](#6-number-of-ways-to-distribute-n-identical-elements-into-m-identical-groups)

---

- [Number of ways to distribute _n_ **distinct** elements into _m_ **distinct** groups.](#7-number-of-ways-to-distribute-n-distinct-elements-into-m-distinct-groups)
- [Number of ways to distribute _n_ **distinct** elements into _m_ **distinct** non-empty groups.](#8-number-of-ways-to-distribute-n-distinct-elements-into-m-distinct-non-empty-groups)

## 1. Number of ways to distribute n identical elements into m distinct non-empty groups.

- Number of ways to distribute 2 balls into a bag and a bucket such that no bag is empty.
<center> { { 1 in bucket,1 in bag } } </center>

- [Stars and Bars Theorem 1](<https://en.wikipedia.org/wiki/Stars_and_bars_(combinatorics)#Theorem_one_proof>)

  If we want to divide 5 star into 3 groups we need 2 bars (⭐ ⭐ ❚ ⭐ ⭐ ❚ ⭐) with the conditions that.

  1. the bars cannot be at the extremes
  2. there must be at least 1 star between 2 bars

  This means we need to place the 2 bars in one of the following 4 positions:
  <center>
    ⭐ __ ⭐ __ ⭐ __ ⭐ __ ⭐
  </center>

  Total number of ways = <sup>4</sup>C<sub>2</sub>

- Total ways = <sup>(n-1)</sup> C <sub>(m-1)</sub>

## 2. Number of ways to distribute n identical elements into m distinct groups.

- Number of ways to distribute 2 balls into a bag and a bucket
  <center> { { 0 in bucket, 2 in bag }, { 1 in bucket, 1 in bag }, { 2 in bucket, 0 in bag } } </center>

- [Stars and Bars Theorem 2](<https://en.wikipedia.org/wiki/Stars_and_bars_(combinatorics)#Theorem_two_proof>)

  To divide 5 star into 3 groups you would need 2 bars.
  <center>
      ⭐ ⭐ ❚ ⭐ ⭐ ❚ ⭐
  </center>

  Out of 7 possible position the bars can be at any two position.<br/>
  Total number of ways = <sup>7</sup>C<sub>2<sub>

- Total ways = <sup>(n+m-1)</sup> C <sub>(m-1)<sub>

## 3. Number of ways to distribute n distinct elements into m identical non-empty groups.

- Number of ways to distribute a red ball and a blue ball into 2 bags such that no bag is empty
  <center> { {both in different bags } } </center>

  Any other arrangement will either make one bag empty or will mirror
  above scenario since both bags are identical.

- This is given by [Stirling numbers of second kind](https://en.wikipedia.org/wiki/Stirling_numbers_of_the_second_kind) S(n,m) which counts the number of ways to partition a set of n elements into m non-empty subsets.

- S(n,m) = m \* S(n-1,m) + S(n-1,m-1)

  - m \* S(n-1,m) <br/>
    This term refers to the case where the n-th element is added to one
    of the existing m sets that have already been formed from the n−1 elements.
  - S(n-1,m-1) <br/>
    This term refers to the case where the n-th element is placed in
    its own new set, which means it becomes the only element in that set.
  - Base Cases
    - S(0,0) = 1: There's exactly one way to partition zero elements into zero sets (the empty partition).
    - S(n,0) = 0 for n>0: You cannot partition a non-zero number of elements into zero non-empty sets.
    - S(n,1) = 1: There's exactly one way to partition n elements into 1 set (all elements in one set).

- Total ways = S(n,m) = m \* S(n-1,m) + S(n-1,m-1)

## 4. Number of ways to distribute n distinct elements into m identical groups.

- Number of ways to distribute a red ball and a blue ball into 2 bags.
  <center> { { both in same bag }, { both in different bags } } </center>

- If some groups are empty, we can count the number of ways
  to distribute elements into remaining non-empty groups using the above result
  i.e. **S(n, m - number of empty groups)** ways.
  This can occur with no groups empty, 1 group empty, 2 groups empty, .... so on till m-1 groups.

- Total ways = S(n,1) + S(n,2) + ..... + S(n,m)

  This is closely related to the [Bell Number (Bn)](https://en.wikipedia.org/wiki/Bell_number) which counts the different ways to partitions a set of n elements into any number of groups. Bn = S(n,1) + S(n,2) + S(n,3) + .... S(n,n)

## 5. Number of ways to distribute n identical elements into m identical non-empty groups.

- Number of ways to distribute 2 balls into 2 bags such that no bags are empty.
  <center> { {1,1} } </center>

- Since elements are identical only the count of element in each group matters.
  and since the groups are identical the order of the groups do not matter.
  So {2,1} is same as {1,2} one way to achieve this is to keep the count in weakly decreasing order.

- This situation is very similar to [Integer Partition](https://en.wikipedia.org/wiki/Integer_partition) problem which counts
  all possible unordered set of positive numbers that have sum n.

- A very nice visual explanation for the recursive relation is on [Youtube](https://youtu.be/F4zYDx-EfZI?si=UzKYkLhOPR47BERZ)

- The recursive relation is defined as:
  P(n,m) = P(n-1,m-1) + P(n-m,m)

  - If a group has 1 element , when we remove that group
    we get all possible ways to distriubte n-1 elements into m-1 groups given by P(n-1,m-1)
  - If no group has 1 element i.e all groups have atleast 2 elements
    In this case removing 1 element from each group will give us all possible ways
    to distribute n-m elements into m groups given by P(n-m,m)

- Total ways = P(n,m) = P(n-1,m-1) + P(n-m,m)

## 6. Number of ways to distribute n identical elements into m identical groups.

- Number of ways to distribute 2 balls into 2 bags <center> { {1,1}, {0,2} } </center>
  Here, {2,0} is samse to {0,2} because groups are identical

- Similar to [case #4](#4-number-of-ways-to-distribute-n-distinct-elements-into-m-identical-groups) If some groups are empty then we can count the number of ways
  to distribute elements into remaining non-empty groups using the above result
  i.e. **P(n, m - number_of_empty_groups)** ways.
  we can have no groups empty, 1 group empty , 2 groups empty, .... so on till m-1 groups.

- Total ways = P(n,1) + P(n,2) + ..... + P(n,m)

## 7. Number of ways to distribute n distinct elements into m distinct groups.

- Number of ways to distribute a red ball and a blue ball into a bucket and a bag.

  <center> { { None in bucket, both in bag }, { both in bucket, None in bag }, <br/> { red ball in bucket, blue ball in bag }, { blue ball in bucket, red ball in bag } } , </center>

- For each element we have m groups to choose from.
- Total Number of ways = m _ m _ m \* m .... (n times) = **m<sup>n</sup>**

## 8. Number of ways to distribute n distinct elements into m distinct non-empty groups.

- Number of ways to distribute a red ball and a blue ball into a bucket and a bag such that neither is empty.
  <center> { { red ball in bucket, blue ball in bag }, {blue ball in bucket, red ball in bag } } </center>

- **Method 1**: Using [Inclusion-Exclusion Principle](https://en.wikipedia.org/wiki/Inclusion%E2%80%93exclusion_principle)

  - we know that we can have m<sup>n</sup> ways if we allow empty groups <br/>
    from this we need to subtract number of ways in which some groups are empty.
  - total ways of having empty groups can be expressed as <br/>
    no. of ways 1 group is empty - no. of ways 2 groups are empty + no. of ways 3 groups are empty - ...... + (-1)<sup>m</sup> \* no. of ways m-1 groups are empty
  - number of ways 1 group = <sup>m</sup>C<sub>1</sub> \* (m-1)<sup>n</sup> <br/>
    <sup>m</sup>C<sub>1</sub> is the number of ways to choose any one group from m groups.
    And since we are left with m-1 groups number of ways to distribute is (m-1)<sup>n</sup> instead of m<sup>n</sup>.

  - Total ways = m<sup>n</sup> - **[** <sup>m</sup>C<sub>1</sub> \* (m-1)<sup>n</sup> - <sup>m</sup>C<sub>2</sub> \* (m-2)<sup>n</sup> + <sup>m</sup>C<sub>3</sub> \* (m-3)<sup>n</sup> - .... + (-1) <sup>m</sup> \* <sup>m</sup>C<sub>m-1</sub> \* (1)<sup>n</sup> **]** <br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; = m<sup>n</sup> - <sup>m</sup>C<sub>1</sub> \* (m-1)<sup>n</sup> + <sup>m</sup>C<sub>2</sub> \* (m-2)<sup>n</sup> - <sup>m</sup>C<sub>3</sub> \* (m-3)<sup>n</sup> + .... + (-1) <sup>m</sup> \* <sup>m</sup>C<sub>m-1</sub> \* (1)<sup>n</sup>

    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; = (i=0 to m)∑ (-1)<sup>i</sup> \* <sup>m</sup>C<sub>i</sub> \* (m-i)<sup>n</sup>

- **Method 2**: Using Stirlings Numbers of Second kind

  - we know that Stirlings Number of Second kind is the number of ways to distribute
    n distinct items into m identical non-empty groups. we can multiply this number by m!
    which is the number of ways groups can be arranged since they are distinct.

  - Total ways = m! \* S(n,m)

- Total ways = (i=0 to m) ∑ (-1)<sup>i</sup> \* <sup>m</sup>C<sub>i</sub> \* (m-i)<sup>n</sup> = m! \* S(n,m)
