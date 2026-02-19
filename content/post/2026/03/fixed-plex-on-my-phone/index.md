---
date: '2026-02-17T21:34:12-05:00'
title: 'How I Fixed Plex on My Phone'
categories:
  - projects
tags:
  - iOS
  - plex
  - self-hosting
  - media
weight: 1
---

## The iOS Plex App Still Sucks, Here is How I Fixed It

Almost a [year](https://www.plex.tv/blog/its-go-time-the-new-plex-experience-is-here/) after its release, the new Plex
experience still sucks. At least for me.

It's been memed to death on the Plex subreddit, and the community is tired of hearing the complaints. But that doesn't
make them any less valid. To this day, the new mobile client remains incredibly unstable and missing features the old
app had.

I was skeptical from the start. When Plex announced the rollout, I joined the iOS beta to test the new experience, and
it did not work well. The app crashed constantly. Subtitles were malformed. Libraries were perpetually "unavailable."
Video scrubbing was virtually impossible. None of that stopped them from pushing it to production. I could go on.

And from my experience, nothing has changed. The latest version of the app (pre-February 2026) still suffers from every
problem I reported in beta.

When I first heard Plex was moving forward with the rollout, I immediately turned off automatic updates on all my
devices. I was content to wait—to stay in my happy place with my out-of-date version and my pretty custom icons (a
feature that didn't return to the app until
[December](https://www.reddit.com/r/PleX/comments/1puvodx/custom_app_icon_is_back/)). I made it about a month and a half
before human error kicked in and I accidentally upgraded my mobile client.

I cursed myself at least once a week for that mistake. The app was (and still is) unusable. At least for me.

I tried to tolerate it. But when an app essentially only lets you press play on a video before crashing, hope fades
fast. I stopped using Plex on my phone entirely.

Nine months later, I'm tired of it. There was a version of that app that worked, and I want it back.

---

Now, downgrading iOS apps is not something Apple wants users to do. But the open source community is full of beautiful,
smart human beings who found ways around that. (See end for more detailed instructions).

Enter [IPATool](https://github.com/majd/ipatool)—a command line utility that lets you search the App Store and download
copies of app packages directly. By combining it with the build number of the previous app version, I was able to get my
hands on the old Plex client.

Once I had the file, the process was simple: remove the current version from my device, transfer the desired version to
my phone (I used AirDrop—yes, I've been in the walled garden too long), and tap to install.

Now I can watch my Plex library with a mobile client that actually works. And if I accidentally update the app again? I
finally know how to fix it.

---

IPATool Instructions:

These instructions are for MacOS. Linux and Windows users, sorry I'm a little lazy. Usage instructions can be found on
IPATool's repo.

**1. Install ipatool**

You can install `ipatool` using [Homebrew](https://brew.sh).

`$ brew install ipatool`

**2. Log into the App Store**

`$ ipatool auth login -e YOUR_APP_STORE_EMAIL`

**3. Find the app's `bundleId`**

For Plex it's `com.plexapp.plex`. To find that I ran:

`$ ipatool search Plex`

**4. Find the desired `buildId`**

This I cheated on. The
[community](https://forums.plex.tv/t/downgrade-to-old-ios-version-and-turn-off-updates-only-for-plex-howto-no-jailbreak-required/911516)
already found it for me: `871812101`. But you can get all of the available `buildId`s with the following command.
Trouble is parsing out which one you want. It helps if the version you're looking for is fairly recent.

`$ ipatool list-versions -b com.plexapp.plex`

**5. Download the app bundle**

This will download an `.ipa` file.

`$ ipatool download -b com.plexapp.plex --external-version-id 871812101`

**6. Transfer the `.ipa` file to your phone**

Like I said, I used AirDrop.

**7. Remove the current version**

Make sure the undesired version has been deleted (I don't know what happens if you don't, I doubt you want to be the
guinea pig).

**8. Install the app**

Just tap the file on your phone.

**9. Enjoy!**

It took me less than ten minutes to do this. Best spent ten minutes of my life.
