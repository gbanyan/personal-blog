---
locale: en
translation_status: translated
translation_id: "posts/露天購買HTC A9 紀實"
title: Record of Buying an HTC A9 on Ruten
slug: ruten-buying-phone-record
ghost_id: 67e4131930b4100001537204
type: post
status: published
visibility: public
featured: false
created_at: '2025-03-26T14:45:45.000Z'
updated_at: '2025-03-26T14:49:34.000Z'
published_at: '2017-02-24T22:48:00.000Z'
custom_excerpt: This article is about the experience of buying an HTC A9 on the Ruten trading platform. It was a bit complicated, so I want to share the detailed process with everyone.
tags:
- Hardware - 硬體
authors:
- Gbanyan
feature_image: ../assets/phonecover.jpg
---

This article is about the experience of buying an HTC A9 on the Ruten trading platform. It was a bit complicated, so I want to share the detailed process with everyone.

### Origins

A friend's old phone was about to break, so she picked out an HTC A9 on Ruten and wanted to buy it. While she was actively comparing prices across various platforms, perhaps because it was the season for new phone releases, many retailers had already cleared their inventory and had no stock. Furthermore, the item she found from a seller on Ruten (the product description stated it was a brand-new, unopened unit with Taiwanese communication specifications) was cheaper than the average market price, so she asked me to buy it on her behalf. After receiving it, we opened the packaging together (it had complete plastic shrink wrap), transferred the Line chat history from her old phone to the new one, and completed some necessary settings. She then happily took it to use. Compared to her old phone, she was quite satisfied with the shell color and smoothness of the HTC A9, but she felt that the three rows at the bottom consisting of the menu bar, the HTC Logo, and the fingerprint recognition button took up too much screen space, so she wanted to turn them off. It is said that the option to turn it off wasn't available at first, but subsequent Sense updates included it. However, just as she was about to update, the system interface kept getting stuck on the loading spinner during the update. Whether she changed the network, waited a few hours, or even waited until the next day, it remained the same. She found this a bit troubling and originally wanted to just let it go, but I felt uneasy about it. So I borrowed the phone to test all the various reasons I could think of, and I actually managed to find the problem.

### The Process

I thought of the problem because I had spent some time researching custom ROM flashing in the past. I knew that official system updates would fail if the Recovery was not the original factory version but a third-party one. Additionally, while inspecting, I miraculously saw a "TWRP" folder in the phone's internal storage space, which clearly belongs to a third-party Recovery. Various signs made me increasingly suspicious, so I rebooted and entered the phone's download mode. Ta-da~~ I actually saw S-OFF; I actually saw S-OFF... (echoing)


￼Normally, the retail version sold officially in Taiwan should be S-ON, yet this phone showed S-OFF. However, in download mode, it also showed as Locked. At this point, my thinking was caught in a dilemma. I really did not want to resort to returning the goods, because it would require spending time handling data transfer, negotiating with the seller, and dealing with returns and refunds. If not handled well, it might even escalate into a consumer dispute or end up in court. If it was just a flashed Recovery, and I could update the original ROM by studying the flashing steps, I could handle it. But what about the subsequent warranty? If the system could not update automatically, could my friend maintain it herself without going through me? As for returning it, I had no strong evidence on hand, only this single issue of S-OFF. Would the seller accept it? I pondered for a long time and decided to post on a forum to ask for advice.

### The Mystery of Its Origins

In my understanding, only a device that has been tampered with, such as flashed or Rooted, would display S-OFF. However, after I posted to ask for advice, someone saw the version number and the search results revealed: this was the Sprint version from the United States (known from hiaewhl in the picture), so it must have been imported as parallel goods from abroad. Recalling the initial setup screen at the very beginning, the default language and region were indeed set to the United States.

Although some netizens joked that because it was S-OFF it was easier to flash custom ROMs, and if I didn't want it I could sell it to them cheaply, others also pointed out that foreign radio communication frequency bands might not necessarily be usable in Taiwan. I went to Wiki to check the detailed specifications of the HTC A9, and sure enough, they did not completely match.

Originally, I wasn't so sure that this phone had been toyed with by someone flashing ROMs, but out of curiosity I entered Recovery Mode once. As a result... TWRP Recovery appeared. This probably isn't the Recovery equipped by the original factory, sigh.

Synthesizing the above results, after discussing with my friend, we decided to return it. At the same time, we remembered to take photos as evidence, recording the information that appeared in download mode and recovery mode to prevent subsequent disputes.

### Subsequent Handling

After contacting the merchant, the seller agreed to the return and refund, and asked me to write down the reason for the return clearly. I was originally worried that the seller was fake, but both the phone number and address were real, so I felt relieved.

The troublesome part was that because my friend was already using this phone, her Google account was logged in, and various services involving personal privacy like Facebook and Line had also been downloaded. After backing up and transferring the Line chats, in order to wipe the phone's data, we executed a factory reset and went to the Google Account Center to remove the device. However, I suddenly realized later that the phone's internal storage space seemed not to have been cleared. But since the system had already been initialized, I had a sudden inspiration: why not just go into this TWRP Recovery and use its built-in Format function to reformat it? After ensuring all data was cleared, we packed it up and sent it back.

> If you haven't played with custom ROM flashing and don't know about Root, Recovery, Fastboot mode, and some advanced Android system knowledge, upon first encountering a phone that cannot undergo automatic system updates, you would have absolutely no way of knowing the traces of it having been flashed by someone. After this experience, my friend and I will never dare to seek cheap bargains on Ruten again, preferring to buy through trusted channels.
