# X Marks the Spot

## Challenge Information

| Field | Details |
|:---|:---|
| **Competition** | [DeadFace 2026](https://ctf.deadface.io/) |
| **Category** | Cryptography |
| **Points** | 30 |
| **Author** | @syyntax |

## Description

Zero Trace's network sensors picked up this outbound packet from a host registered to Spectre Technology. The payload is hex-encoded. Decrypt it to find what spookyboi is hiding.

`02362b2964302c2164372c25202b3337642b226417342127303621641021272c2a2b282b233d7e6420212520222527213f3c2b361b751b263d30771b70301b701b3075297739`

Submit the flag as deadface{flag-text}.

## Solution

First things first: don't panic! Everything is almost right there in front of us... well, almost.

Let's start with the hint we've already been given: "hex-encoded". That should immediately tell us we're dealing with hexadecimal, so that's where we'll begin. 

And we're back to CyberChef, because I try to avoid writing scripts until the very last moment. Why make life easier for myself when I apparently have so much time on my hands? (I don't.) But jokes aside, let's get to work.

We start by using From Hex in CyberChef to decode the hexadecimal payload into bytes.
`6+)d0,!d7,% +37d+"d4!'06!d!',*+(+#=~d !% "%'!?<+6u&=0wp0p0u)w9`

And what do we get? A beautiful mess of unreadable characters. Absolutely gorgeous... and absolutely useless at first glance. So, let's start eliminating possible approaches and figure out what kind of encryption we're dealing with.


1. Base64
Let's start with Base64. We can rule it out because the decoded output doesn't resemble a valid Base64 string: it contains characters outside the Base64 alphabet. The expected padding character = is also missing, although its absence alone wouldn't be enough to rule Base64 out.

2. Caesar / ROT
Next up: Caesar and ROT ciphers. Sure, we have letters in the mix, but the output doesn't look like something a simple letter shift would turn into readable text. So, let's set this option aside for now.

3. XOR
Now, this is a frequent guest in CTF challenges: XOR. A single-byte XOR cipher has only 256 possible byte values to check. That's a pretty manageable number of attempts, especially when you're hoping one of them will reveal the hidden message.
I decided to give it a shot simply because it's easy to test in a couple of minutes. If it doesn't work, we can always move on to the next idea.

Luckily, my favourite CyberChef has a very handy feature called **XOR Brute Force**. It tests the possible single-byte XOR keys, leaving you to inspect the results and see whether anything looks promising.

And there it is!
With the key shown as 44 in CyberChef (hexadecimal 0x44), we get the following plaintext:
`From the shadows of Spectre Technology: deadface{xor_1_byt3_4t_4_t1m3}`

Now that's much more like it!

<details>
<summary>Click to reveal the flag</summary>
deadface{xor_1_byt3_4t_4_t1m3}
</details>
