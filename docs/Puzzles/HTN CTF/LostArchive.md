---
layout: default
title: The Lost Archives (Puzzle 4)
parent: HackTheNorth CTF
nav_order: 4
---

# The Lost Archives

---
## Part 1 (For the first ⭐)

We first follow the instructions provided in the terminal by executing 

```
    $ fetch manual-000
```

After opening the link provided and skimming through you will see this at the bottom of the page.

> For archival, this manual is also provided
>in such format. \\
>• Common Tongue: manual-000 \\
>• dxmguqa: nhxlhg-000

As such our next intuition is to call 

```
    $ fetch nhxlhg-000
```

Opening `nhxlhg-000` we see that the entire file is written in the glyph language, as such we would need to build a translator in order to understand its contents. 

Thankfully the cipher used is a single subsitution cipher, additionally we are provided with 2 documents that contain the same contents but one in plaintext and the other in cipher text. As such, we can easily write a program that would allow us to decipher the document.

I used the following text

> The Archive Terminal provides access to authorized records within the Grand Library. Zealous
archivists quickly jump to fetch valuable knowledge buried in quartz-lined vaults. Tampering
with node pathways is expressly prohibited.

Along with (the corresponding text within `nhxlhg-000`)

>  tad howaurd tdonuxhg jofrubdq hwwdqq tf hltafouvdb odwfobq sutaux tad mohxb gucohoy.
vdhgflq howauruqtq zluwkgy ilnj tf edtwa rhglhcgd kxfsgdbmd cloudb ux zlhotv-guxdb rhlgtq.
thnjdouxm suta xfbd jhtashyq uq dpjodqqgy jofaucutdb.

To create the key.

Using the key we are able to decipher the line of text at the bottom of `nhxlhg-000` (which was "damaged" in manual-000) to reveal

    The employee conversation board is maintained in english. To access it, fetch page cfhob-141. 

Fetching `cfhob-141` and translating its contents we are presented with a conversation bewteen a few individuals

    board-141 
    
    Employee board rzfvhuu5xhlfw 
    
    Post: notes in the jar? 

    grenn.j 
    I can’t believe we’re hiding fortune cookie notes in the cookie jar. 
    maxe.p 
    Every time I grab a treat I find a note instead. 
    Feels like they want us to read our own secrets. 
    julu.k 
    Next thing you know, they’ll stash riddles in the sugar bowl. 
    jenn.o 
    Just be careful not to eat the paper by accident. 
    I already bit into a note this morning. 

    They say the next lead lies outside the box. 

Here's the step that took the longest for me, when they mention "hiding notes in the cookie jar" they're alluding to actual cookies that websites use. (If you paid attention in the "What you should do" section of the info tab they explicitly say you SHOULD *Inspect browser source code, file metadata, and cookies, etc*). 

To accomplish this step we access *Developer Tools* and under *Application* find the *Cookies* tab. In it we will spot a cookie with the name `archivists-memo-page` and it holds the value `intmemo-424`

Fetching `intmemo-424` will grant you the first ⭐

## ⭐ Acquired.

---
## Part 2 (For the second ⭐)


Opening up `intmemo-424` 

>Archivists,

>Has anyone gotten the `serve()` command we heard about in old manuals to work? I’ve heard
rumors it’s tied to `top-secret-999`, but I’ve never seen it succeed on any terminal we’ve got
access to. The parentheses are strange too … not a format I’ve seen in our usual commands.

>Maybe it’s designed for a different interface entirely. Hard to say xlncdoq.

>If anyone gets a result, document it and please let me know. Until then, I guess it’s a system
myth.

>Archivist Tycho Renn

The structure of the command `serve()`, the phrase *"Maybe it's designed for a different interface entirely..."* are big clues that you're supposed to use the **console within developer tools**. 

(If you try to use `serve()` within the terminal inside the website you'll be greeted with `serve: access denied - console authorization required`)

Accessing *Developer Tools* and accesing *Console* we can type in our command

```
    $ serve("top-secret-999")
```

And we'll be granted access to `top-secret-999`

> To the High Committee,

> Since the addition of the flag command to our documentation systems, we’ve observed a
concerning shift in translator behavior. Pages processed normally are beginning to show strange
inconsistencies: certain words are English, but appear in our archival glyph script. Others remain
in cipher, yet are embedded directly into standard-language paragraphs without proper
transformation. We are compiling affected documents for pattern analysis, but a preliminary scan
of our archives has revealed this behavior in 4 documents:

>• manual-000 \\
>• nhxlhg-000 \\
>• cfhob-141 \\
>• intmemo-424 

>No such behavior was observed prior to the update v8132 rev2 release4. The translators claim no
memory. Whether this is a miscommunication, a misalignment in training, or something more
deliberate, the irregularities are undeniable.

>Continued investigation is critical.

>Archivist General Lunebreach the Silent

Inside this file we are told that there are some strange bugs within the documents listed, where supposedly english documents contain words in glyph and documents in glyph contain english words.

| Document     | Misplaced Text    | Converted      |
|:-------------|:------------------|:---------------|
| `manual-000` | eghmuq            | flag is        |
| `nhxlhg-000` | sumof             | sum of         |
| `cfhob-141`  | overall5pages     | overall 5 pages|
| `intmemo-424`| xlncdoq           | numbers        |

**flag is sum of overall 5 pages numbers**

Here I will have the 5 pages and their respective numbers bolded (000 doesn't contribute anything to the sum so I will not bold it)

<details markdown="block">
<summary>manual-000</summary>

>manual-000
>
>ARCHIVE TERMINAL USER MANUAL
>
>System Version: v**8813** rev**1** release0
>
>The Archive Terminal provides access to authorized records within the Grand Library. Zealous
archivists quickly jump to fetch valuable knowledge buried in quartz-lined vaults. Tampering
with node pathways is expressly prohibited.
>
>Core Command
>
>Only one command is required for basic access:
>
>fetch <page-id>
>
>This command queries the system and yields a direct download link. All page identifiers follow
the HackyDecimal classification format eghmuq.
>
>Translations
>
>Documents may appear in archival glyph script. It is recommended translators build tools to
translate cyphers and then transcribe them into glyphs. For archival, this manual is also provided
in such format.
>
>• Common Tongue: manual-000\\
>• dxmguqa: nhxlhg-000
>
>[The remainder of this page is damaged and unreadable.]
</details>

<details markdown="block">
<summary>nhxlhg-000</summary>

> nhxlhg-000
>
> HOWAURD TDONUXHG LQDO NHXLHG
>
>Qyqtdn Rdoqufx: r**8813** odr**1** odgdhqd0
>
>tad howaurd tdonuxhg jofrubdq hwwdqq tf hltafouvdb odwfobq sutaux tad mohxb gucohoy.
vdhgflq howauruqtq zluwkgy ilnj tf edtwa rhglhcgd kxfsgdbmd cloudb ux zlhotv-guxdb rhlgtq.
thnjdouxm suta xfbd jhtashyq uq dpjodqqgy jofaucutdb.
>
>Wfod Wfnnhxb
>
>fxgy fxd wfnnhxb uq odzluodb efo chquw hwwdqq:
>
>fetch < jhmd-ub>
>
>tauq wfnnhxb zldoudq tad qyqtdn hxb yudgbq h buodwt bfsxgfhb guxk. hgg jhmd ubdxtueudoq
efggfs tad ahwkybdwunhg wghqqueuwhtufx efonht sumof.
>
>Tohxqghtufxq
>
>bfwlndxtq nhy hjjdho ux howaurhg mgyja qwoujt. ut uq odwfnndxbdb tohxqghtfoq clugb tffgq tf
tohxqghtd wyjadoq hxb tadx tohxqwoucd tadn uxtf mgyjaq. efo howaurhg, tauq nhxlhg uq hgqf
jofrubdb ux qlwa efonht.
>
>• Common Tongue: manual-000 \\
>• dxmguqa: nhxlhg-000
>
>tad dnjgfydd wfxrdoqhtufx cfhob uq nhuxthuxdb ux dxmguqa. tf hwwdqq ut, edtwa jhmd weafc-**141**.


</details> 

<details markdown="block">
<summary>cfhob-121</summary>

> cfhob-**141**
>
> dnjgfydd cfhob overall**5**pages
>
>jfqt: xftdq ux tad iho?
>
>modxx.i
>
>u whx’t cdgudrd sd’od aubuxm efotlxd wffkud xftdq ux tad wffkud iho.
>
>nhpd.j
>
>drdoy tund u mohc h todht, u euxb h xftd uxqtdhb.
>
>eddgq gukd tady shxt lq tf odhb flo fsx qdwodtq.
>
>ilgl.k
>
>xdpt tauxm yfl kxfs, tady’gg qthqa oubbgdq ux tad qlmho cfsg.
>
>idxx.f
>
>ilqt cd whodelg xft tf dht tad jhjdo cy hwwubdxt.
>
>u hgodhby cut uxtf h xftd tauq nfoxuxm.
>
>tady qhy tad xdpt gdhb gudq fltqubd tad cfp.
</details>

<details markdown="block">
<summary>intmemo-424</summary>

>intmemo-**424**\\
>\\
>INTERNAL MEMORANDUM\\
>\\
>Classification Level: Internal\\
> \\
>Archivists,\\
> \\
>Has anyone gotten the serve() command we heard about in old manuals to work? I’ve heard
rumors it’s tied to top-secret-**999**, but I’ve never seen it succeed on any terminal we’ve got
access to. The parentheses are strange too… not a format I’ve seen in our usual commands.\\
>\\
>Maybe it’s designed for a different interface entirely. Hard to say xlncdoq.\\
> \\
>If anyone gets a result, document it and please let me know. Until then, I guess it’s a system
myth. \\
> \\
>Archivist Tycho Renn
</details>

<details markdown="block">
<summary>top-secret-999</summary>

>top-secret-**999**\\
>\\
>COUNCIL MEMO: TRANSLATION IRREGULARITIES\\
>\\
>Classification Level: Top Secret\\
>\\
>To the High Committee,\\
>\\
>Since the addition of the flag command to our documentation systems, we’ve observed a
concerning shift in translator behavior. Pages processed normally are beginning to show strange
inconsistencies: certain words are English, but appear in our archival glyph script. Others remain
in cipher, yet are embedded directly into standard-language paragraphs without proper
transformation. We are compiling affected documents for pattern analysis, but a preliminary scan
of our archives has revealed this behavior in **4** documents:\\
>\\
>• manual-000\\
>• nhxlhg-000\\
>• cfhob-**141**\\
>• intmemo-**424** \\
> \\
>No such behavior was observed prior to the update v**8132** rev**2** release**4**. The translators claim no
memory. Whether this is a miscommunication, a misalignment in training, or something more
deliberate, the irregularities are undeniable.\\
>\\
>Continued investigation is critical.\\
>\\
>Archivist General Lunebreach the Silent

</details>

| Document       | Numbers                     | Sum            |
|:---------------|:----------------------------|:---------------|
| `manual-000`   | 8813, 1                     | 8814           |
| `nhxlhg-000`   | 8813, 1, 141                | 8955           |
| `cfhob-141`    | 141, 5                      | 146            |
| `intmemo-424`  | 424, 999                    | 1423           |
| `top-secre-999`| 999, 4, 141, 424, 8132, 2, 4| 9706           |

Total sum **29044**

Entering the command 
```
$ flag 29044
```
Will get you the second ⭐

## ⭐ Acquired.
