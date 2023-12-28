---
layout: post
title:  "The Return of the Yeti"
date:   2023-12-11 15:00:00 +0000
categories: 
- CTF
- TryHackMe
- AOC23-SQ
---

# Return Of The Yeti

[toc]

I had the Advent of Cyber '23 on my calendar for Dec 1, and I wasn't sure what I was in for, this would be my first AOC, so, while I had some free time I logged the day before only to see there's another room released on my dashboard

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/newRoom.png)

Ooh! A Side Quest, I wonder if I can do something there while I wait for the main event

## QR code social media, finding the room

So in the try hack me [Advent of Cyber '23 Side Quest](https://tryhackme.com/room/adventofcyber23sidequest) room it says the first of four challenges will be a hidden room that you can get access to via QR code parts hidden in their social pages between Tuesday, 28th November and Thursday, 30th November, hey! Today is the 30th, so I can go looking for them ahead of time and be prepared.

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/socialmedia.png)

so let's get looking

first I try there linked-in, scroll to find what was posted on the dates provided in the clue (between Tuesday, 28th November and Thursday, 30th November)

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/socaLinkedin.png)

huh, 🥚👀 let's see what that link gets us

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/qr_codes/809cd.png)

ahh, so it's a bisected qr-code, I thought it would be multiple QR codes with data in them that you had to read, but this is interesting because if there's only one QR code maybe I can use the parts of it to figure out the rest, but first I should find what else is available

Well they gave us a list, so let's follow it in order.

There discord is up next, I'm already there so let's see what's up

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/discordSearch.png)

a text channel made just for this room, let's see, pinned messages

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/discordQRCode.png)

ooh nice, now there's only one more part replaced, social media on the list no 3

Instagram, oh well time to make a fake account, so I can access the posts

>![note] Instagram is being horrid, and while writing this I wasn't able to get a screenshot
>nevertheless:

Aha! Here it is
![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/qr_codes/0f93a.png)

hmm, ok, so I have most of the qr code, but not that top left section,

let's see what each part dose and see if we can still get the data

## repairing the qr code early

So, what is a qr code made of ?

A quick google brought me here: <https://www.maketecheasier.com/how-qr-codes-work/>

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/qr-code-anatomy-overview.png.webp)

mmhm mhmm, lots of reading, probably important,

looks like I'm missing one of those positioning markers, the timing data, format info, and "content" cool

What is that though?

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/QR-Character-Placement.png.webp)

ok so, I'm missing error correction information and maybe some data too, or at least part of it will be missing

lest smooch what I have already together, and add in a marker and some timing patterns

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/qr_codes/assembledQRcodes3.png)

k then, I can't decode that from my phone, there might be a tool to recover it maybe?

Google led me to this site <https://merri.cx/qrazybox/>
a qr code Analysis and Recovery Toolkit, nice

What happens when I upload my art project to it?

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/QrazyBox1.png)

detected nice, OOH tools, I like those

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/toollist.png)

yes yes yes give me the data

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/decode1.png)

wooo I did it yayyy

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/firefoxfail.png)

Aww 302, redirect, shucks, wrong link. Or at least It's not entirely garbage, just something isn't right

Lets sanity check first, is the room even there?

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/discordChat1.png)

dms :

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/discordDM1.png)

later in the main chat

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/discordChat2.png)

alright then, let's see what's wrong with my qr code

let's look at that tool list and try something else, data sequence analysis, sounds good, I know some of the data is corrupt because it was split in 4 parts and I don't think an open bracket can be part of a URL

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/qrboxParts.png)

aah yeah, that message data is being read wrong because the missing data was just replaced with white or 0 values

Well the edit tool lets us paint each bit as either black 1, white 0, or Gray ?

Let's pain the missing bits and try to get the data again

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/qrboxData2.png)

yep missing data, let's see what we can use to help us, back in that tools section there was something called Reed-Soloman Decoder, used for "errors and erasures correction"

now that sounds like a Wikipedia rabbit hole waiting to happen so ima ignore that and just press buttons and see what happens :3

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/reed-solomondecode.png)

well that's good, there's some reed-soloman blocks detected, let's try it

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/decodefinal.png)

HA, pure skill, biggest brain ez no luck needed

## Into the room

and I'm the first person in the room 0w0

>![note]
>hi I'm currently writing this post bursting though this room, and didn't actually take any screenshots, but here's a timeline from the room showing the 4 people to get into the room before the final part of the QR code is released
>![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/roomscore.png)
>I got in at about 14:44 on the 30th, but I wasn't alone for long  

I have to make use of this head start and get onto the tasks

OK SO DON'T PANIC, YOU MIGHT BE ABLE TO FINISH THIS ROOM BEFORE ANYONE ELSE

what do we have (clue vision active)

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/roomInfo.png)

and the questions

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/Q-All.png)

Ooh! A packet dump from a Wi-Fi connection, Wireshark time :3

### Wireshark

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_firstload.png)

well that's question 1 done :3

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/q1a.png)

>"What's the password to access the Wi-Fi network?"

Well we have a lot of data here, and first thing I always do in Wireshark is get a higher level view of what's going on with its statistics tools, first thing first, what kind of data do we have, let's look at the protocol hierarchy

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_protocolHMenu.png)

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wiresharkProtocol1.png)

ok lots of Wi-Fi stuff, lots of data, but most interestingly a little slither of 802.1x authentication stuff, let's filter for that using the right click menus

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_protocolFilter.png)

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_4wayhsEPOLfilter.png)

Ooh nice, 2 [4-way-handshake](https://www.wifi-professionals.com/2019/01/4-way-handshake) authentications, and its wep/wp2 ?

#### 4-way Handshake

google time
and today we get : <https://securitytutorials.co.uk/how-to-capture-crack-wpa-wpa2-wireless-passwords/>

Nice. So we can use aircrack-ng to crack this, if I save it as a pcap format, and this is a ctf so its probably in the rockyou.txt wordlist

```aircrack-ng Downloads/van.pcap -w /usr/share/wordlists/rockyou.txt```

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/awesomeAircrackGif.gif)
![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/aircrackResults.png)

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/q2a.png)

heh nice, so let's put that into [Wireshark to decrypt the traffic](https://wiki.wireshark.org/HowToDecrypt802.11)
and go back to the protocol hierarchy to see what we have now

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_prototcpdecrpt.png)

Ok so some TCP data, a lot is TLS encrypted, some is RDP, and some is just unencrypted data.

Let's look at this another way, now we have decrypted the 802.1x data, we should see addresses, so let's go to another one of the few tools in Wireshark I know, the Conversations view

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_convoV1.png)

Ok 3 devices, 8.8.8.8 is just googles DNS, so we can ignore that, what's going on in TCP land?
And let's sort by packets, so we see what's most chatty

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_convoVTCP.png)

ok so; lots of small packet examples that only last a tiny amount of time, from the same device, across a lot of ports, so that's a packet scanner

But the other two very chatty ports are 3389 and 4444
3389 is RDP, so we were kind of expecting that, but what's 4444?

Cant find anything on Google, let's look at the traffic

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_convoApplyasfilter.png)

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_filteredTCP4444.png)

Oh! Hello is that the word PowerShell I see !

Let's follow the TCP stream

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_followTCPstream.png)

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_tcpstream4444.png)

Oh! Someone has been very naughty this year

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/q3a.png)

but they did leave me a gift

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/wireshark_tcp444_b64.png)

#### RDP Certificate

Looks to be the local Remote Desktop certificate in base64
so let's reverse that with a tool provided to us by GCHQ! Everyone's favorite [CyberChef!](https://gchq.github.io/CyberChef)

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/cyberchef_b64-pfx.png)

And hey presto, we get a certificate! And It's got a password... less nice,

I tried Christmas the Wi-Fi password, I tried BFC123, the password in the intro text, but no luck

It's at this point dear reader, that I realize someone else has joined the room and has answered all the questions I have, spooked, I want to get that first place!

So I try cracking that certificate to try and read the RDP data and see what it could hold
a bit of [googling](https://stackoverflow.com/questions/53547386/how-to-run-john-ripper-attack-to-p12-password-educative-pruposes) tells me that you can use john the ripper to crack a pkcs12

So off I go crackin again, this is just a CTF, so it should be relatively easy, just throw rockyou.txt at it, right?

Well after a long LONG time (1h)

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/john_result.png)

GAAAH, I waited on all of rockyou and an hour of john brute-forceing just to get the word I already filled in for question 3  

fine, we have the certificate, let's see what we get when we now decrypt the RDP traffic

#### RDP Clipboard

google powers fire up again [I found this from unit42-palo altone networks](https://unit42.paloaltonetworks.com/wireshark-tutorial-decrypting-rdp-traffic/)

so let's get the key, then add it into Wireshark

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/Wireshark_rdp1.png)

great, more layers of readable data, so let's look at the updated protocol hierarchy to see what we can read

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/Wireshark_postRDP_Protocol.png)

ooh! Clipboard plaintext :3 let's sort this by length to try and find big chunks of text

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/Wireshark_clipbord_email.png)

ooh

```plaintext
anks for looking into this 
Having Frost-eau in the case is for sure great!
ps I'll copy the weird file I found and send
 it to you through a more secure channel
 Regards
 Elf McSkidy
```

so something is getting sent, and we can try to figure out whats happening though the clipboard text

ill go though all of the 53 packets and try and pull out all the text in timeline order

```plaintext
https://mail.google.com/mail/u/0/?tab=rm&ogbl#inbox

1337-0

hanks for looking into this 
Having Frost-eau in the case is for sure great!
ps I'll copy the weird file I found and send
 it to you through a more secure channel
 Regards
 Elf McSkidy

yetikey1.txt

dpxSet-Clipboard -value (Get-Content \Desktop\secret.txt.txt)

1-1f9548f
[REDACTED - you will have to do the room yourself to get this one]
154ef2834

```

well that looks like the rest of our questions answered

![Image](/attachments/2023-12-11-The-Return-of-the-Yeti/firefox_answers_final.png)
