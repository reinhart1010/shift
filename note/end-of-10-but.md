# What *End of 10* does *not* tell you

**Last Updated:** 2025-06-25

This is a non-exhaustive list of our stance of *[End of 10]*, an ongoing effort to encourage people to switch to Linux to keep continuing their old hardware.

In general, *End of 10* tells you some good things about Linux:

+ **Unlike Windows (and macOS), you can use Linux on your aging computer.** So most likely you don't need to buy new (especially "recommended" Copilot+) PCs. *That's good for you and the environment!*
+ **Unlike Windows, you can have your best Linux distributions ("distros")** without having to [verifying any license keys or Certificate of Authenticity (CoA)](https://www.microsoft.com/en-us/howtotell/hardware-pc-purchase). That means Linux is available **for (mostly) free!**
+ **Some Linux desktops offer broader customizations than what Windows (even Windows 10) has to offer.** 10 years before the *[End of 10]*, Reinhart decides to switch his 64-bit computer from restrictive features of [Windows 7 Starter (32-bit only)](https://en.wikipedia.org/wiki/Windows_7_editions) to Linux.
+ **Linux has been proven to support your old hardware for even longer.** Although not explicitly mentioned in *[End of 10]*, the media says so...
  - ZDNET: ["Linux drops support for 486 and early Pentium processors - 20 years after Microsoft "](https://www.zdnet.com/article/linux-drops-support-for-486-and-early-pentium-processors-20-years-after-microsoft/)

Even though Linux is good, and Reinhart have been experienced with Linux distributions since 2015, the *End of 10* does not generally inform users of "what is totally different between Linux and Windows" (these may be explained on repair cafes set up by the initiative), because these info can be important to support our new user's work with Linux.

The *End of 10* is also sponsored by organizations who discreetly promotes certain political agendas, which is highly reflected in their communities. Even though you are just a user or a prominent contributor, you will be very likely to be exposed into these as well. Because just like the wider Free Software and Open Source communities, the Linux community generally influences you to contribute.

> Historically, Reinhart came to the Linux world after learning more about Mozilla with their separate open-source projects such as Firefox and [Firefox OS](https://en.wikipedia.org/wiki/Firefox_OS).
> 
> Reinhart's significant contributions to [OpenStreetMap](https://openstreetmap.org) also come *after* learning with the Linux community.
> 
> In most cases, one FLOSS contributor could easily be introduced to other FLOSS contributor. For example, from Linux to LibreOffice and Fediverse and GNU/FSF. This is why they share common ideologies and common strategies to invite new users, convert them to community members, before finally recruit them to continue the evolution of their projects.
> 
> Note that Reinhart does not discourage this recruitment pipeline&mdash;it's also the reason why he advanced through his tech career.

As part of Reinhart's mission of protecting *his* and partnering communities, we should ensure the adoption of these products should be frictionless, from the Consumption layer, up to the Business, Politics, and Philosophy. Any frictions between these layers could contribute conflicts between the expanding Linux communities with ours, which could make Linux feel unproductive and opposing to our people's philosophical goals.

This is why this document exists, guiding people to significant technical, political, and philosophical differences between "community-first" Linux and "business-first" Windows. Reinhart is also developing a separate document to carefully recommends Linux distributions to his communities, also accounting political and philosophical neutrality.

> Contributions are welcome, but we currently do not adopt certain Code of Conduct (like the Contributor Covenant) due to philosophical conflicts of interests between them and us.

## Unlike macOS and Windows, Linux is mostly a case-sensitive operating system.

That means when working with files, `Untitled 1.txt` (with uppercase U) will be treated differently with `untitled 1.txt` (with lowercase u).

Same with folders, too. `/home/ubuntu/Downloads` (the default Downloads folder comes with an uppercase D) will be considered different than `/home/ubuntu/downloads` (with lowercase d).

## You most likely cannot "mix-and-match" apps designed for different Desktop Environments (DEs).

When you decided to have someone to install Linux for you, make sure they give you some information about something called **Desktop Environment (DE)**.

Some people may try to hide this information from you for being "too complex to explain", but **this information is important as some apps are specifically written for specific desktop environments,** and installing them may **bloat your computer** as they install *parts* (not entirely all) of the other Desktop Environment they are preferred to work with.

For example, installing some great apps including [Elisa](https://flathub.org/apps/org.kde.elisa), [Kate](https://kate-editor.org/), and [Okular](https://flathub.org/apps/org.kde.okular) on your [Elementary OS](https://elementary.io/) will require you to install parts of the KDE Desktop Environment. This is usually automatically handled by your *package managers* like `apt`, `dnf`, `flatpak`, and `snap`.

Some of the well-known Desktop Environments include:

+ [Budgie](https://buddiesofbudgie.org/)
+ Cinnamon (default in [Linux Mint](https://www.linuxmint.com/))
+ COSMIC (default in System76)
+ Deepin
+ [GNOME](https://gnome.org/) (default in [Fedora Workstation](https://fedoraproject.org/workstation/), [PureOS (Purism)](https://pureos.net/); [Ubuntu](https://www.ubuntu.com/) with some modifications)
+ [KDE](https://kde.org/)
+ [LXDE](https://lxde.sourceforge.net/about.html) (deprecated in favor of LXQt)
+ [LXQt](https://lxqt-project.org/)
+ [MATE](https://mate-desktop.org/)
+ Pantheon (default in [Elementary OS](https://elementary.io/))
+ [Trinity](https://www.trinitydesktop.org/)
+ [XFCE](https://www.xfce.org/) (default in Linux Lite)

---

Fortunately, Linux developers made it easy for you to identify which Desktop Environment that is currently installed, and which apps work best with Desktop Environments.

Some Desktop Environments also provide their curated list of those DE-specific apps, including:

+ <https://appcenter.elementary.io/> for apps mostly designed for Elementary OS,
+ <https://apps.gnome.org/> for apps specifically designed for GNOME,
+ <https://apps.kde.org/> for apps specifically designed for KDE,

If you are unsure which apps do work best for your desktop, consult with your local Linux community.

## Some Linux projects who officially sponsor End of 10 embrace prohibitive political agendas.

The *[End of 10]* movement is coordinated between organizations that promote shared political views on Linux, and internally expects to discourage users who have differing views to contribute to the community.

Some of them include bold support for:

+ **Anti-capitalist agendas (i.e. against "Big Tech"/GAFAM companies, *Surveillance Capitalism*, "nonfree" software),** in which some imply that you should *only* use certain software that are politically correct to the community. Some practical examples include:
  - Certain communities **expect you to drop Google Search and Microsoft Bing** in favor of DuckDuckGo, Qwant, and Startpage for "improved privacy".
  - Certain communities **discourages you to use "nonfree" software.** This included software marketed as "free" (like Google Chrome, Spotify, and NVIDIA drivers) but require additional subscriptions, or does not allow you to build and distribute the software yourself. These are often considered as either proprietary [freemium](https://en.wikipedia.org/wiki/Freemium) or [shareware](https://en.wikipedia.org/wiki/Shareware), and Debian have some good reasons on [why they are not "Free Software"](https://people.debian.org/~bap/dfsg-faq.html).
  - Some community believes the solution to your "I-can't-install-this-software" problem is to *replace everything in your family and company with Free Software (and probably Creative Commons, too)*.
+ **Diversity, Equity, and Inclusion (DEI) as Code of Conduct (CoC),** which some communities imply their "users" to bound by their "inclusive" rules either to ask in their forums, mailing lists, or contribute to their projects.

We acknowledge a significant amount of users who wish to migrate to Linux but exercising their faith that effectively breaches these community rules, such as those concerning LGBTQIA+ users and contributors.

> **Random Fact:** The Indonesian community is dominated by Christian and Islam believers in which their religious teachings strictly prohibits homosexuality and transgenderism.

We acknowledge that our people also **need to use these capitalist tech companies' products** (e.g. Microsoft Teams), especially in your work or study. For example, Reinhart cannot entirely use GNU/Linux to study in Monash University due to [specialized software required for eExams](https://www.monash.edu/students/admin/assessments/exams/device-specs).

We would also present you some internal posts from certain Linux communities which promote significant political views. Yes, these are (still) not removed by moderators of those projects and communities:

+ GNOME contributors prominently supporting [left-wing politics](https://en.wikipedia.org/wiki/Left-wing_politics):
  - "F*ck Nazis, GNOME is Antifa": <https://blogs.gnome.org/tbernard/2025/04/23/the-elephant-in-the-room/>
  - "Wayland is gay, X is trans": <https://blogs.gnome.org/alatiera/2025/06/23/x11-session-removal-faq/#is-wayland-gay>
+ Lunduke (former prominent FLOSS contributor, currently maintaining *[The Lunduke Journal](https://lunduke.com/)*), and [Vaxry](https://vaxry.net/) (creator of Hyprland), who are banned from communities for having differing political views than their Left and DEI-infused initiatives.
  - Remember that the Left's Free Software licenses does not prohibit the others to fork off from their projects. See also: *[A reminder on fascism in free, libre, open-source (FLOSS) projects and communities](https://reinhart1010.id/blog/2025/05/01/a-reminder-on-fascism-in-free-libre-open-source-floss-projects-and-communities/) (Reinhart, May 2025)*.

[End of 10]: https://endof10.org/
