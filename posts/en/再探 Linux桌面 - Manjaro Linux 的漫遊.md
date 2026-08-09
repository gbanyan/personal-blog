---
locale: en
translation_status: translated
translation_id: "posts/再探 Linux桌面 - Manjaro Linux 的漫遊"
title: Revisiting the Linux Desktop - A Roaming Through Manjaro Linux
slug: manjaro-linux-desktop-wandering
ghost_id: 67e4ad0ec5a22a00013544de
type: post
status: published
visibility: public
featured: false
created_at: '2025-03-27T01:42:38.000Z'
updated_at: '2025-03-27T01:44:39.000Z'
published_at: '2021-06-15T13:16:00.000Z'
custom_excerpt: Linux is mainly used for server web development. Attempts to use a desktop environment for actual work are not nonexistent, but being busy with studies, I didn't have the extra energy to squash bugs, so it always ended in mental exhaustion.
tags:
- Linux
authors:
- Gbanyan
feature_image: ../assets/photo-1629654297299-c8506221ca97.jpg
---

## Preface

### Linux in My Memory

I have been in contact with Linux since elementary school. After slowly understanding the Linux ecosystem and architecture, I developed a love-hate relationship with its high customizability. In the later stages, Linux was mainly used for server web development. Attempts to use a desktop environment for actual work were not nonexistent, but being busy with my studies, I didn't have the extra energy to squash bugs, so it always ended in mental and physical exhaustion.

However, being accustomed to the Unix architecture, I wanted to find a relatively stable desktop environment that could at least balance academics and work. So in 2013, I bought a Macbook Air and stepped into the Apple ecosystem, where I remain to this day.

### A Few Thoughts on the Linux Desktop Environment

Since I am, after all, a layman in software development, some of my thoughts on the development of the Linux desktop may seem superficial. However, I feel that the problems with Linux desktop environment development actually stem from the open-source development community. Different components are maintained by different individual developers or groups, and their ideas are not always aligned. You may even encounter situations where differing opinions lead to arguments that remain unresolved.

Furthermore, the components of Linux are scattered across many upstream, midstream, and downstream parts. It is difficult to demand that the development team of each component perform comprehensive compatibility testing for the countless other components. Consequently, users are required to have a certain level of debugging capability. To some extent, this has affected the popularization of the Linux desktop.

The Linux community is essentially composed of people from all over the world; it is vibrant but loose, free and open without binding constraints. Anyone who wants to contribute can join or quit at any time, and they can always disagree with others' ideas and build their own from scratch. On distrowatch.org, you can see countless distributions, and each distribution may have a different mission and philosophy. You could say that compared to corporations, the resulting products lack the guarantee of long-term support, but there is no right or wrong in this. It is exactly this characteristic of the Linux community that has shaped the landscape of Linux today.

### Disadvantages and Progress Compared to Windows and macOS

The author feels that compared to complete operating systems, Linux has several disadvantages when it comes to developing a desktop system:

1. Graphics card vendor support
2. UI design guidelines, like Apple's Human Interface Guidelines
3. A complete debugging and testing team to minimize issues upon delivery to the user end
4. A mature application ecosystem

Regarding point 1, support for the Linux desktop from Nvidia and AMD has been improving in recent years, and it is no longer as fragmented as it used to be. As for the third point, it becomes necessary to consider the characteristics of each distribution. Some Linux desktop distributions are supported by comprehensive community teams and have clearly announced testing cycle schedules from package testing to official release.

For the fourth point, it must be said that with the development of Chrome and Node.js, Web Apps and the electron framework have narrowed the gap between Linux applications and other operating systems (macOS has also benefited from this). Many lightweight applications can even be handled directly through a browser.

## Revisiting Linux - Starting from Ubuntu 20.04

I built a new PC to occasionally play single-player PC games. My mac mini is taken to the office for work purposes, and I didn't want to use Windows for my primary work environment at home, so the idea of using Linux again arose.

To avoid trouble, I chose Ubuntu 20.04, thinking that a long-term stable distribution supported by a corporation should be very stable, right?

But after using it for a while, I still changed the operating system and reinstalled. Reflecting on it later, Ubuntu didn't actually have major problems; it was just minor system UI bugs that affected the overall perception of the details.

For example, being accustomed to macOS's reverse scrolling direction, I enabled it in the system settings, only to be frustrated to find that it would reset every time I rebooted.

The default Gnome desktop was too plain. Although I tried to convince myself to just get used to it, I still wanted to tweak it. As a result, I found that installing too many Gnome Extensions would cause various weird bugs to appear on the desktop.

Overall, I was not quite satisfied, so I decided to switch to Manjaro.

## Manjaro KDE - Assertive Chaos

From this point on, the author violated the initial intention: to lower maintenance costs and focus on production use.
Instead, I started spending a lot of time playing around with experimental features, but it didn't result in a much better unified experience.

Manjaro's default GUI installer is actually quite good, but because I wanted to use Btrfs and its snapshot feature, I used manjaro-architect to build it from the command line. The snapshot feature of Btrfs is very convenient, but it caused the memory function of grub-reboot to fail, meaning I couldn't reboot into Windows and have it automatically switch back to Windows next time.

Unfamiliar with the compositional structure of Btrfs partitions, I also had to spend some time researching where to start when something went wrong and needed rescuing.

Additionally, the desktop features of KDE are very comprehensive, showing an all-encompassing development route. However, there are too many settings and hidden bugs. Frequently switching and checking felt very troublesome. Also, KDE didn't seem to get along well with Nvidia, resulting in screen rendering bugs. At the same time, Wayland completely failed to launch.

Later, trying to hold my ground, I also installed i3-wm, a tiling window manager, and stuck with it for a while. Once you get used to i3-wm, managing windows is indeed very smooth, and thinking about the purpose of a window before laying it out also helps keep your mind clear. However, the problem with i3-wm is that it is, after all, an external component developed independently from various desktop systems. Therefore, when the internal components of KDE or Gnome desktop systems integrate, they do not consider compatibility with i3-wm. After prolonged use, you can still clearly see the strange behavior of some system windows under i3-wm.

## Manjaro Gnome - The Beauty of Default Installation

As mentioned earlier, after much tossing and turning, I still felt the system had various imperfections large and small. Later, I made a resolute decision and simply wiped out Manjaro and reinstalled it, using all the default values of the GUI installer and ignoring the Btrfs format entirely.

I chose Gnome for the desktop, selected the Traditional Chinese locale, and installed it all the way through.

To my surprise, I found it quite smooth to use, noticeably better than when I previously installed it via manjaro-architect.

I think the main reasons are as follows:

1. Manjaro Gnome comes pre-installed with a whole set of useful Gnome Extensions, making up for the deficiencies of the native Gnome desktop.
2. The provided Layout Switcher allows switching the Dock position according to your needs and also has a minimalist tiling style.
3. The Gnome-style system settings are simpler and not as complex as KDE's.

Of course, it's not without flaws. The drawback of the Gnome desktop is that many features rely on Extensions to be supplemented, but the compatibility among Extensions isn't always great. If you install too many, conflicts when adjusting the settings of various Extensions can easily cause the desktop to crash. This happens even when tweaking the default settings provided by Manjaro.

As for the backup solution after abandoning Btrfs... I just directly run a scheduled rsync of the /home folder to the NAS folder.

What surprised me the most about Manjaro Gnome is that it has the Pop OS! tiling window extension built-in, directly providing functionality similar to i3-wm. The text configuration files I used to write painstakingly for i3-wm now seem like a huge waste of time.

## Conclusion

In short, I am now staying with the Manjaro Gnome desktop environment. At least with the built-in desktop extensions, code editor, browser, and VMWare installed, it is usable for everyday tasks. Although Manjaro is derived from Arch Linux, its stability means it won't blow up every few days.
