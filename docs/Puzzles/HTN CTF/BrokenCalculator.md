---
layout: default
title: Broken Calculator (Puzzle 1)
parent: HackTheNorth CTF
nav_order: 1
---

# Broken Calculator

This puzzle is split into 3 different parts. 

---
### Part 1
<details markdown="block">
<summary>Solution for Part 1</summary>
Immediately we are presented with a few pieces of information.

- We know the `calculator` is *broken* so we shouldn't expect anything to work right.
- We are restricted to using the following `keys`: 8, 5, 3, +, - , =, C
- We need to somehow use the numbers to calculate 20.

The first thing I did was to calculate the following

| Calculation  | Result            |  
|:-------------|:------------------|
| 3 + 3 =      | 4                 | 
| 3 - 3 =      | 4                 | 
| 5 + 5 =      | 49                | 
| 5 - 5 =      | 14                | 
| 8 + 8 =      | 100               | 
| 3 + 5 =      | 14                |
| 5 + 8 =      | 70                |

From these calculations you can make 2 observations 

{: .important }
> Observation 1:
>
> It is likely that
>
> 3 maps to 2
>
> 5 maps to 7
>
> 8 maps to 10

{: .important }
> Observation 2:
>
> `+` performs the operation of `*`
>
> `-` performs thr operation of `+`

From this we can conclude that `8 - 8` which is really `10 + 10` will give us our desired answer.
</details>

---
### Part 2
<summary>Solution for Part 1</summary>


</details>

---
### Part 3
<summary>Solution for Part 1</summary>


</details>