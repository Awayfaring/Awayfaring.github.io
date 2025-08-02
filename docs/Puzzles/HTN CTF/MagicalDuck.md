---
layout: default
title: The Talking Cartographer (Puzzle 3)
parent: HackTheNorth CTF
nav_order: 3
---
# The Talking Cartographer 

This puzzle is a bit scuffed, either information is time dependent or it just takes alot of baseless snooping around. So unlike Puzzle 1/2 in which I mostly used logic to move forward, alot of what I say here is just "I snooped around and found useful information".

---
### Stage 1

We are given the following prompt

    Stage 1: The mystical goose appears before you, eyes glowing with ancient wisdom.

    "Honk! Traveler, you seek the path through shadows deep. Listen well...

    You must trace the path from where the gathering begins... to where creation flows.

    Along your journey, near University and Albert, you'll glimpse a chariot of the city-marked with numbers and destination.

    What words does the vessel bear?"

I think significant context to this question is the fact that HTN is hosted by [University of Waterloo].

From this I gathered that the following line likely takes us to the physical campus of waterloo

    You must trace the path from where the gathering begins... to where creation flows.

In this context **University** and **Albert** sound like street names.

Going onto Google Maps and going to the intersection of *University* and *Albert* you will a bus labled **19B Northfield Station**
If you do not see this you will need to change the street view to **June 2024**

Our answer for this stage is **19B Northfield Station**

---
### Part 2

We are given the following prompt 

    Stage 2: The path brightens, and the goose's eyes gleam with approval.

    "Well done, traveler! The digital realm has revealed its secrets to you.
    But now you must bridge the worlds - virtual and physical unite.

    Hidden whispers have been scattered like feathers in the digital wind.
    Inspect the realm beneath the surface, where developers speak in silence.
    These whispers hold coordinates to a sacred monument of this land.

    Decode the ancient tongue, then venture forth with your own feet!
    The true pilgrimage demands your physical presence.
    Upon the monument, thick with paint, lies the next key."

I think the key word for this part of the puzzle is **Inspect**. There was a point in time where "Developer Tools" was simply known as "Inspect".
Going off this hunch I opened developer tools and clicked through the tabs.

Once I got to console I was greeted with the following message. *(In hindsight "developers speak in silence" alludes to the terminal/console. When you use the console it's akin to "speaking" to it but you obviously aren't making any sound)*

```js
    A feather lands...
    Whisper: NDMuNDcwNSAtODAuNTM5Mg==
```
After trying a bunch of deciphering tools online the one that revealed any info was **Base 64**.

The base 64 conversion of the *Whisper* returns

    43.4705 -80.5392

Going to google maps and plugging in these coordinates you are taken to this [Statue]. The image of the statue on google maps doesn't have any relevant text. However, a [Reddit Post] was made during the CTF and upon careful inspection of the first image attached you can spot the words **Northbound Echo** written in the base of the statue.

Our answer for this stage is **Northbound Echo**


----
### Part 3


---

[University of Waterloo]: https://en.wikipedia.org/wiki/University_of_Waterloo
[Reddit Post]: https://www.reddit.com/r/uwaterloo/comments/1ln3y53/waterloo_statue_appreciation_post/
[Statue]: https://www.google.com/maps/place/43%C2%B028'13.8%22N+80%C2%B032'21.1%22W/@43.4705084,-80.5392093,2a,60y,108.92h,87.79t/data=!3m7!1e1!3m5!1sJGbkOemsyPURj_SDlBZEmA!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D2.208027556179161%26panoid%3DJGbkOemsyPURj_SDlBZEmA%26yaw%3D108.91709372934048!7i13312!8i6656!4m4!3m3!8m2!3d43.4705!4d-80.5392?entry=ttu&g_ep=EgoyMDI1MDcyOC4wIKXMDSoASAFQAw%3D%3D