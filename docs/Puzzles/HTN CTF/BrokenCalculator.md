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
> Here's what I mean by **maps to**
>
> If `x` **maps to ** `y`, then in an equation replace every instance of `x` with `y`.

{: .obs }
> Observation 1:
>
> It is likely that
>
> 3 maps to 2
>
> 5 maps to 7
>
> 8 maps to 10

{: .obs }
> Observation 2:
>
> `+` maps to `*`
>
> `-` maps to `+`

From this we can conclude that `8 - 8` which is really `10 + 10` will give us our desired answer.
</details>

---
### Part 2
<details markdown="block">
<summary>Solution for Part 2</summary>
Now that we have solved part 1 the premise for parts 2 and 3 are likely the same.
For part 2 the only difference we have is

- We need to get `315`
- We're allowed acces to: 2, 4, 6, *, +, =, C


Like I kicked off the problem by calculating a few things

| Calculation  | Result            |  
|:-------------|:------------------|
| 4 + 4 =      | 49                | 
| 2 + 2 =      | 25                | 
| 6 + 6 =      | 81                | 
| 4 * 4 =      | 14                | 
| 2 + 2 =      | 10                | 
| 6 + 6 =      | 18                |

From these calculations you can make 2 observations 

{: .important }
> Here's what I mean by **maps to**
>
> If `x` **maps to ** `y`, then in an equation replace every instance of `x` with `y`.

{: .obs }
> Observation 1:
>
> It is likely that
>
> 2 maps to 5
>
> 4 maps to 7
>
> 6 maps to 9

{: .obs }
> Observation 2:
>
> `+` maps to `*`, and vice versa

Since the prime factorization of `315` is `5 * 7 * 9`, by reversing the mapping we defined above we know that for our calculator `315 = 2 + 4 + 6`

Our final answer is **2 + 4 + 6**
</details>

---
### Part 3
<details markdown="block">
<summary>Solution for Part 3</summary>
Now for the last part

- We need to get `123`
- We're allowed acces to: 2, 3, 4, ÷, +, =, C


Like I kicked off the problem by calculating a few things

| Calculation  | Result            |  
|:-------------|:------------------|
| 2 + 2 =      | 3125              | 
| 3 + 3 =      | 27                | 
| 4 + 4 =      | 4                 | 
| 4 + 2 =      | 32                | 
| 2 + 3 =      | 125               | 
| 3 + 2 =      | 243               |

This problem is more complicated than the last one, from these calculations I believe that 

{: .important }
 Here's what I mean by **maps to**

 If `x` **maps to ** `y`, then in an equation replace every instance of `x` with `y`.

{: .obs }
 Observation 1:

 It is likely that

 2 maps to 5

 4 maps to 2

 3 maps to 3

{: .obs }
 Observation 2:

 `+` maps to `^`

Then I did a few more calculations targeted towards `÷`

| Calculation  | Result            |  
|:-------------|:------------------|
| 2 ÷ 2 =      | 0                 | 
| 3 ÷ 3 =      | 0                 | 
| 4 ÷ 2 =      | -3                | 
| 3 ÷ 2 =      | -2                | 
| 2 ÷ 3 =      | 2                 | 
| 2 ÷ 4 =      | 3                 |

After these calculations I am fairly convinced that 

{: .obs }
 Observation 3:

 `÷` maps to `-`

Since we can write `123` as `125 - 2` or `5 ^ 3 - 2`, reversing the mapping we defined above we can write that as `2 + 3 ÷ 4`

Our final answer is **2 + 3 ÷ 4**
</details