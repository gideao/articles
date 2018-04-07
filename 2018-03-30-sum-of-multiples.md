---
title: Sum of multiples
date: 2018-03-30 09:56:59 -03:00
layout: post
---
# Sum of multiples

## The problem
A simple but funny problem is find out the sum of all multiple of $n$ below $m$, where $n < m \text{ and } n, m \in \mathbb{N}$.

For identify a multiples of $n$ the number theory divisibility property can by used. If some number $a$ are multiple of $n$ then $a$ can be represented as $a = n.k$, if $k \in \mathbb{Z}$ then $a$.

$$n | a \iff n > 0 \text{ and } a = n.k \text{ fo all } k \in \mathbb{N}$$

In a example where $m$ is equal to 100 and $n$ equal to 3 the exemple the proprety can be observed. The least mutiple of 3 from 1 to 100 is 33.

$$ S = \sum_{i=1}^{33} 3.k_i $$

| k = 1 | k = 2 | k = 3 | k = 4 | ... | k = 32 | k = 33 |
|-------|-------|-------|-------|-----|--------|--------|
| 3 x 1 | 3 x 2 | 3 x 3 | 3 x 4 | ... | 3 x 32 | 3 x 33 |
| 3     | 6     |  9    | 12    | ... | 96     | 99     |

Oberving the arithmetic sequence above is possible denote 3 as common mutiple. Is possoble the sequance by a aritimetic progression with reason 3.

$$ S =  3 \times 1 + 3 \times 2 + 3 \times 3 + 3 \times 4 + \dotsc +3 \times 32 + 3 \times 33 $$
$$ S =  3 (1 + 2 + 3 + 4 + ... + 32 + 33) $$
$$S = 3 \bigg(33 \times \frac{1 + 33}{2} \bigg) \to S = 33 \bigg( \frac{3 + 99}{2} \bigg) $$