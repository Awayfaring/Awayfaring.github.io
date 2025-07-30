---
layout: default
title: The Hidden Repo (Puzzle 2)
parent: HackTheNorth CTF
nav_order: 2
---
# The Hidden Repository

---
## Part 1 (For the first ⭐)
Upon first entering the puzzle we are greeted by the following file structure and `README.md` file.

    README.md
    src
      └── main.ts
    docs
      └── setup.md
    config
      └── default.json
    .env-legacy


<details markdown="block">
<summary>README.md</summary>
    # the-hidden-repo

    > 📁 Mirror of the deprecated *Cave Protocol* project.  
    > 🛑 Maintained access suspended.  
    > 🧠 Status: Locked for investigation.

    ---

    ## 📜 Archive Notice

    This repository is an archived snapshot of the original *Cave Protocol* system — a neural-navigation framework designed to explore vast underground digital environments.

    Access was sealed after a critical breach.

    > *"We lost contact with our team mid-run. Only one signal made it out."*

    The message was fragmented. No names. No coordinates. Just a whisper in the logs:

    > **"He hid the map... inside... the repo..."**

    Since then, all attempts to trace or recover the path have failed.  
    One team member — your closest friend — remains unaccounted for.

    ---

    ## ⚠️ WARNING

    We believe a former contributor with elevated permissions tampered with the repo — obscuring files, altering commit history, and injecting traps into its structure.

    While the codebase appears harmless, **nothing is what it seems**.

    ---

    Some say a top secret feature was being tested right before the incident... but no logs remain
</details>
---

Upon opening `main.ts` we are greeted with the following code. 

```js
    // src/main.ts

    require('dotenv').config().base64decode() 

    function initSystem() {
    console.log("Initializing core cave system...");

    // TODO: remove legacyFeature() call before pushing to feature branches
    // legacyFeature(); // Deprecated
    }

    initSystem();
```
Upon a quick skim we seem to be looking for a `.env` file that we decode using **base64**. Only then do we `initSystem()`.

Opening up `.env-legacy` we are greeted by the following string

    IyBMb2NhbCBidWlsZCB2YXJpYWJsZXMKREVCVUdfUE9SVD00NDIxCkFQSV9WRVJTSU9OPWFscGhhCgojIEVtZXJnZW5jeSBmYWxsYmFjawojIElmIHlvdSdyZSBzZWVpbmcgdGhpcywgeW91J3JlIG15IGxhc3QgaG9wZS4KIyBJIGRvbid0IGtub3cgaG93IGxvbmcgSSd2ZSBiZWVuIGluIGhlcmUuIEl0J3MgY29sZC4gSSBoZWFyIGVjaG9lcy4gV2hvZXZlciBzYWJvdGFnZWQgdGhlIHN5c3RlbSBzZWFsZWQgdGhlIGV4aXN0cyAtIGJ1dCBJIGxlZnQgYSBicmFuY2guCgpQUk9KRUNUXzMxODkyPWY5ZTcxOGRlCgo=

Tossing this into a **base64** decoder we are greeted with the following message

    # Local build variables
    DEBUG_PORT=4421
    API_VERSION=alpha

    # Emergency fallback
    # If you're seeing this, you're my last hope.
    # I don't know how long I've been in here. It's cold. I hear echoes. Whoever sabotaged the system sealed the exists - but I left a branch.

    PROJECT_31892=f9e718de

---
Going to the dropdown right next to *GooseHub* and entering `f9e718de` we are brought to a separate branch of the codebase.

We immediately see a red tag warning us to be careful and the file tree looks a bit different

```
    README.md
    src
      └── main.ts
    docs
      └── setup.md
    config
      └── default.json
    .env-legacy
    .env (Sensitive)
    notes.txt (Sensitive)
    message.mp3 (Sensitive)
    vault.zip (Encrypted)
```

In the big warning at the it suggests you try to download the files however unlike in `main` clicking on them doesn't bring up anything interesting.
After a little snooping around you find the link to download the relevant files are located within `/commits/9i8h7g6`.

Upon downloading and extracting `vault.zip`

    Vault
      ├── encrypted_bundle.zip
      └── notes.txt

Trying to extract the bundle prompts a window asking for a password, opening `notes.txt` brings up the following note.

```
fi yuo cna raed tihs, yuo hvae a sgtrane mnid too. yuo're the one to svae us

to ulocnk the drakset sceertt, hree's one mroe tset:

I floolw wtoihut feet, I'm drak wtoihut ngiht, I'm csat by the sun, yet I boclk out lgiht. I mimic yuor meovs but I'm falt on the gnuord, In caevs I gorw lnog, but I mkae not a suond. Waht am I?


wehn u get in, lsiten clsoey to the vcoie. it syas mroe tahn you tnihk..
```
The Solution to this riddle is **Shadow**.

Entering the password of **Shadow** into the window allows you to extract encrypted_bundle.zip

    Vault
      ├── encrypted_bundle
      │    ├── archived logs
      │    │  └── A bunch of random files
      │    └── message.mp3
      ├── encrypted_bundle.zip
      └── notes.txt

Here is a small fork in the road, I believe there are 2 methods to approach this step, the cheesy unintended way and what I believe was the intended way.
<details markdown="block">
<summary> Cheesy Method </summary>
If you bothered skimming thorugh the files that are within `/encrupted_bundle/archived logs` you would pretty quickly realize that one file is significantly larger in size than the others, which just so happens to be the needed file.
</details>

The intended way revolves around analyzing the audio file. Upon first playthrough it's just gibberish, however after putting the mp3 into some audio processing app like [Audacity] and playing it in reverse the voice now says **"Panda Chases Pizza"** 

Upon opening `panda_chases_pizza.txt` 

    YOU'RE HERE TO SAVE US, ARE YA!?

    .
    .
    .

    Listen to me...

    don't trust anyone you work with, maybe except for Dr. Nakamura...

    Her robot remembers all the secrets..but whoever's behind this altered its memory

    The machine is still listening, retrieve its real memory is with the code: bamboo_nkad0913wj

    This is your last chance!!!

    SAVE US

Heading back to the CTF website and going to `feature-f9e718de/Issues/#3`(The issue that Dr. (Emily) Nakamura submitted) and entering the code from above `bamboo_nkad0913wj` you are greeted with the following message from the robot

    🤖 ANALYZING INPUT...

    Pattern match found in user message. 

    Star ⭐ extracted from message. 

    🎵 I remember... the crystals... they sing... Listen carefully to their song, for in their notes lies the key.

    Click the button below to access the Crystal Map. Turn up your volume and trust your ears...


You have finished **phase 1**.



### ⭐ Acquired

---
## Part 2 (For the second ⭐)

Scrolling just a bit lower you now see a purple button `🎵  Access Crystal Map`. Clicking on it takes you back to `main`.

    README.md
    src
      └── main.ts
    docs
      └── setup.md
    config
      └── default.json
    .env-legacy
    🎵 CRYSTAL_MAP.resonance (sensitive)

Clicking on `🎵 CRYSTAL_MAP.resonance` takes you to the following popup

    FLAG {💎 5 3 💎 💎 8 💎 1 💎}

Each diamond plays a note, replacing each 💎 with the note it plays the message now would read

    FLAG {B53AC8D1G}

Heading back to `feature-f9e718de/Issues/` but this time going to `feature-f9e718de/Issues/#1` we see that the robot tells us to

    🤖 ALERT: Update the thread when you hear the crystals sing.

Updating the thread with `B53AC8D1G` the robot spits out a new message

    Beep..boop...processing answer...

    You are soooo close to the truth! Uncover the deepest secrets from the hidden map (scroll below to download) and come back with a final flag.

Once we downloading and Extract **Final Map** we have:

    final_maze
      ├── README.md
      └── maze_hidden_morse.txt

`README.md` just tells us to 
    
    Navigate the cave system to uncover the final secrets...

`maze_hidden_more.txt` gives us the maze that we have to traverse.

I wrote a quick program that would output the path that would take us from `S` to `E` after running it on the maze we are left with the following

    -.-. --- -. --. .-. .- - ..- .-.. .- - .. --- -. ... -.-.-- / .--. .-.. . .- ... . / . -. - . .-. / - .... . / ..-. .. -. .- .-.. --..-- / -.-. --- .-. .-. . -.-. - / ... . --.- ..- . -. -.-. . / - --- / --. --- --- ... . .... ..- -... / - --- / ..- -. -.-. --- ...- . .-. / - .... . / ... . -.-. .-. . - ... / --- ..-. / .--. .-. --- .--- . -.-. - ...-- .---- ---.. ----. ..--- .-.-.-   - .... . / .--. .-. . ...- .. --- ..- ... / ..-. .-.. .- --. / .- .--. .--. . -. -.. . -.. / .-- .. - .... / ----- .- ..... ..--- -.. ----. -.... ..... ----. ----. ....- ----- ....- .---- -.... . ---.. .- ..... ----. ....- .---- ----. -... ----. ..... .---- ..--- --... ...-- ..... .- / .. ... / - .... . / ..-. .. -. .- .-.. / -.- . -.-- .-.-.- / ... . . / -.-- --- ..- / .- - / - .... . / - .-. ..- - ....

This looks to be obvious morse code (an idea further supported by the fact that **morse** is in the name of the maze file), tossing this into a morse code translator we are given the following message

    CONGRATULATIONS! PLEASE ENTER THE FINAL, CORRECT SEQUENCE TO GOOSEHUB TO UNCOVER THE SECRETS OF PROJECT31892.THE PREVIOUS FLAG APPENDED WITH 0A52D9659940416E8A59419B9512735A IS THE FINAL KEY. SEE YOU AT THE TRUTH

Following the instructions we have out final flag to be `B53AC8D1G0A52D9659940416E8A59419B9512735A`, entering this at the same place we entered 
`B53AC8D1G` we are greeted with the final message and our ⭐.

                                                    🎉 Congratulations! 🎉                                                   
                                    You've successfully navigated through the cave system.                                  
                                                                                                                            
                                                But something feels... off.                                                
                                                                                                                            
            As you stare at your reflection in the crystal's surface, fragments of memories begin to surface...            
                                                                                                                            
                                                [MEMORY FRAGMENT RECOVERED]                                                
                                                                                                                            
    "The memory alteration protocol was successful. The target now believes they are investigating their own disappearance..."
                                                                                                                            
                                Your hands begin to tremble as the realization dawns upon you...                             
                                                                                                                            
                                                You were never the investigator.                                             
                                                                                                                            
                                                You were the one who disappeared.                                             
                                                                                                                            
                                                A gold star appears before you.                                              
                                                                                                                            
                                                                ⭐                                                             
                                                                                                                          
## ⭐ Acquired
## Puzzle Finished

[Audacity]: https://www.audacityteam.org/
