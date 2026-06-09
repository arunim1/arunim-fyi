---
id: note_01jn5ey8t8fkyspd8zkjwkvs0s
public: true
---

A description of my defense-in-depth approach to site-blocking, aka a list things that keep me more productive than I otherwise would be.

![swiss cheese model textless|388](https://imgs.search.brave.com/A0e5Eu3VeCytZWMqGSXrvGSR6K6E163CSW2yLIqzIgs/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly91cGxv/YWQud2lraW1lZGlh/Lm9yZy93aWtpcGVk/aWEvY29tbW9ucy9h/L2E3L1N3aXNzX2No/ZWVzZV9tb2RlbF90/ZXh0bGVzcy5zdmc)

## Browser extensions:

[LeechBlock](https://www.proginosko.com/leechblock/): I use this to fully block a large number of websites (games, content, social media, workarounds) and time-limit others (prediction markets, linkedin, typing practice sites)

[Clearspace](https://www.getclearspace.com/): I use this to block some sites, mostly social media, such that I'm prompted to breathe and pause before bypassing any other restrictions. I also use this to feedblock most social media on my laptop (i.e. hiding all feeds, recommendations, etc.)

[Redirector](https://chromewebstore.google.com/detail/redirector/ocgpenflpmgnfapjedencafcfakcekcd): as the name might suggest, I use this to redirect bad URLs to random wikipedia articles or more specific URLs

[uBlock Origin](https://chromewebstore.google.com/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm): I use the option it has to block YouTube, I think, but can't tell whether it works, given all the other layers blocking the site.

## Arc boosts:

see the list [here](https://docs.google.com/document/d/1VOODkzzWsRlh-rOKQp_Ki8FOcKjADIRBWQee4giNxnk/edit?tab=t.0#heading=h.gipimruj2ewc)

Used to feedblock most sites, remove comments, hide unnecessary features, etc.. Also used to e.g. block Gmail outside of pre-determined times.

## Apple Screen Time

Settings -> Focus

- Do Not Disturb Focus, which activates an iMessage Filter (hides all non-pinned messages in the app when the focus is activated)

Settings -> Screen Time

- Password set by a friend, such that I don't know it.
- Shared across all devices.
- -> Downtime
	- No app access after 10:30pm except for "Always Allowed" below
- -> App Limits
	- Social media, browsers (which would let me bypass site blocking) etc., including apps that I've since deleted
	- Double / triple check that these require passwords to unblock, common error!
- -> Always Allowed
	- Phone, Messages, FaceTime
	- ClearSpace
	- Google Maps, Uber
	- Logseq, Readwise / Anki (my [[spaced repetition]] apps)
	- Spotify
- -> Communication Limits
	- During Downtime: No one besides my parents. There is in fact no one depending on me late at night such that it can not wait until the next morning.
- -> Content & Privacy
	- Restrictions enabled
	- -> App Store, Media, Web -> Web Content:
		- Limit Adult Websites + Blocklist of ~100 sites

## Laptop:

/etc/hosts file which blocklists ~100 sites

Time tracker script

[[morale|Morale]] tracker script

crontab script with 30-min check-ins

System Settings -> Control Center -> Announce the time

Apple Screen Time, see above

## Phone:

[Clearspace](https://www.getclearspace.com/)

Apple Screen Time, see above

Settings -> Accessibility -> Display & Text Size -> Color Filters: Grayscale

Empty home screen

Shutdown shortcut

Automations which toggle Do Not Disturb automatically every 3 hours