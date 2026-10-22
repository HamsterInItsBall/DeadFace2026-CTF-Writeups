# Hail Caesar

## Challenge Information

| Field | Details |
|:---|:---|
| **Competition** | [DeadFace 2026](https://ctf.deadface.io/) |
| **Category** | Cryptography |
| **Points** | 5 |
| **Author** | @syyntax |

## Description

One of the faculty at Night Veil University thought it would be clever to write sensitive information on notes by their computer. This sensitive information includes a very easy-to-decipher password hint. Judging by the drawing of a dog on the photo, we assume the password hint is the name of the individual's dog.

Submit the flag with the dog's name as: deadface{dog's name}

![pass-hint](./images/pass_hint.png)

## Solution

The first thing I noticed when opening the photo was the adorable doggo, which initially distracted me from the actual task. But we're more interested in the black text itself:

`Zl qbt'f anzr vf Srgpu`

For this challenge, I turned to one of my best helpers, CyberChef, which is also available online.

The title, "Hail Caesar," already gives us a pretty good idea that we're dealing with a Caesar cipher. So, naturally, I headed straight for ROT13 — a simple Caesar substitution cipher that rotates each letter of the alphabet by a specified number of positions (13 by default).

And luckily, the text was encoded using exactly 13 rotations!

Applying ROT13 to `Zl qbt'f anzr vf Srgpu` gives us:

`My dog's name is Fetch`

The challenge description tells us exactly what to do next: submit the dog's name in the format deadface{dog's name}.

So, our flag is:

<summary>Click to reveal the flag</summary>
deadface{Fetch}
</details>
