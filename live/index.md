---
layout: page
title: Shadow Den Streaming
permalink: /live
---

You can find me on Twitch at [NixillShadowFox](https://l.nixill.net/ttv)!

# Schedule
This schedule is subject to change without notice.

<span id="time-notice">💡 The days and times below are in US Eastern time. If you load this page with JavaScript enabled, it will attempt to detect your time zone.</span>

All streams run **<span id="startTime">6:00 PM</span>** through **<span id="endTime">10:00 PM</span>**.

* **<span id="tuesday">Tuesday</span>**: Pokémon Scarlet (Pokédex completion)
* **<span id="thursday">Thursday</span>**: Tryout Thursday (various games I wanna try)
* **<span id="saturday">Saturday</span>**: Ori and the Blind Forest (blind playthrough, no spoilers!)
* **The <span id="last">last</span> day of every month**: Mario Kart 8 Deluxe: Community Multiplayer

<span id="change-notice"></span>

<script src="/scripts/luxon.js"></script>
<script>
  var DateTime = luxon.DateTime;
  // Set the timezone to my own
  var now = DateTime.now().setZone("America/Detroit");
  // Save the following for testing
  // var now = DateTime.fromObject({
  //   year: 2023, month: 10, day: 15, hour: 0, minute: 0, second: 0
  // }, { zone: "America/Detroit" });
  // Set all the times and days correctly
  var streamStart = now.set({ hour: 18, minute: 0, second: 0 });
  var streamEnd = now.set({ hour: 22, minute: 0, second: 0 });
  var tuesday = streamStart.set({ weekday: 2 });
  var thursday = streamStart.set({ weekday: 4 });
  var saturday = streamStart.set({ weekday: 6 });
  // Set all timezones to the reader's
  var localZone = "local";
  var localStreamStart = streamStart.setZone(localZone);
  streamEnd = streamEnd.setZone(localZone);
  tuesday = tuesday.setZone(localZone);
  thursday = thursday.setZone(localZone);
  saturday = saturday.setZone(localZone);
  // And now set the spans above
  document.getElementById("startTime").innerText = localStreamStart.toLocaleString(DateTime.TIME_SIMPLE);
  document.getElementById("endTime").innerText = streamEnd.toLocaleString(DateTime.TIME_SIMPLE);
  document.getElementById("tuesday").innerText = tuesday.weekdayLong;
  document.getElementById("thursday").innerText = thursday.weekdayLong;
  document.getElementById("saturday").innerText = saturday.weekdayLong;
  document.getElementById("last").innerText = (tuesday.weekday == 2)?"last":"first";
  document.getElementById("time-notice").innerText = "✅ The days and times below are in your local time.";
  // Look ahead for time changes
  var lastHour = localStreamStart.hour;
  var changes = [];
  for (var i = 1; i <= 21; i++) {
    var localDay = streamStart.plus({ days: i }).setZone(localZone);
    var hour = localDay.hour;
    if (hour != lastHour) {
      changes.push(localDay);
    }
    lastHour = hour;
  }
  // Output time changes
  if (changes.length == 1) {
    document.getElementById("change-notice").innerText =
      "⚠ Stream time will be changing to " + changes[0].toLocaleString(DateTime.TIME_SIMPLE) +
      " on " + changes[0].toLocaleString({day: "numeric", month: "long"}) + ".";
  } else if (changes.length == 2) {
    document.getElementById("change-notice").innerText =
      "⚠ Stream time will be changing to " + changes[0].toLocaleString(DateTime.TIME_SIMPLE) +
      " on " + changes[0].toLocaleString({day: "numeric", month: "long"}) +
      ", and then to " + changes[1].toLocaleString(DateTime.TIME_SIMPLE) +
      " on " + changes[1].toLocaleString({day: "numeric", month: "long"}) + ".";
  }
</script>

# Chat rules
Please adhere to the following rules when chatting:

1. **Don't be a dick.** Hatred toward marginalized groups is absolutely NOT okay, and bad news can usually wait until after the stream.
2. **Don't link stuff without asking.** However, sharing clips of my current stream or anyone I'm streaming with is encouraged.
3. **Swearing in moderation is okay,** but any sexual content is not.
4. **I trust my mods,** and it will be extremely rare if ever that I overturn their decisions. Don't argue with or ignore them.
5. **Stick to English.** I'm learning German but can't read it on the fly during streams, and don't know any other languages.
6. **PLEASE mention technical issues!** I can't fix them if I don't know they're happening. This includes things like the UI buttons showing up in my "webcam", lack of game audio, or other technical errors.
7. **Please don't mention the viewer count.** I've hidden it from my views on purpose. I'll take a look after the stream.

I will not be impressed by attempts to find loopholes or edge cases to these rules, and reserve the right to be more or less lenient on them on a person-by-person or case-by-case basis.

## German streams
The following additional rules apply when I'm playing a game in German and translating it for stream:

1. **Don't translate it for me.** I want to try and translate it on my own first. Once I have, you can critique or correct my translations.
2. **Don't use online translation.** Please only offer critique if you actually know (or are learning) German yourself.
3. **The English source material is irrelevant.** There is no guarantee that the German localization is intended to be identical in meaning to the English.
4. **German is allowed in chat,** but expect me to be slow to acknowledge it and I will likely reply in English.