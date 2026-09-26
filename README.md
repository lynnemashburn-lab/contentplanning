# Content Planning

Content plans for Happily Ever Planned (Lynne Mashburn, Travel Advisor, a Travelmation agency).

**Starting a new plan?** Read [`trip-content-playbook.md`](trip-content-playbook.md). It has the method, the voice rules, the script format, and a brief to fill in.

## Disney World, Sept 26 – Oct 3, 2026

`disney-fall-2026/index.html` is **Happily Ever Filmed**: a phone-first content call sheet for the Mashburn family trip, staying at the Treehouse Villas at Disney's Saratoga Springs Resort, with two Mickey's Not-So-Scary Halloween Party nights (Sun 9/27 and Thu 10/1).

| Tab | What's in it |
|---|---|
| **Days** | One call sheet per day, Friday prep night through the posting plan after the trip. Each day is a timeline of shots, photos, stories, screen recordings and script takes, in the order they happen. |
| **Scripts** | 25 short-video scripts (14 marked must-film), split into takes. Each has on-screen text, a caption, a b-roll list and when to post. **Take mode** shows one take at a time in big type and keeps the screen awake. |
| **Kit** | Filming tips, Disney's gear rules, the party playbook ready to paste into DMs, calls to action, hashtag sets and the light/dark setting. |

**How checkmarks save:** every tap saves to the phone first, so it works with no signal in the parks. When the page is published as a Claude artifact, it also backs up to the artifact's own database, so the same checkmarks show up on the laptop.

**Where the facts come from:** park hours, showtimes, closures and Lightning Lane notes come from `trips/mashburn-fall-2026.json` in the Disney-trip-planner repo. The gear list comes from the packing list on that repo's packing-list branch. Tripod and selfie-stick rules come from [Disney's property rules](https://disneyworld.disney.go.com/park-rules/).

**Voice:** warm and professional, Disney-happy but not cheesy, no emoji. Words in `[brackets]` are fill-ins to say on camera (wait times, favorite dishes, verdicts).

### Editing

The plan data sits at the top of the `<script>` block in `index.html`, in three lists:

- `DAYS` holds each day's moments and checklist items.
- `SCRIPTS` holds the scripts and their takes.
- `KIT` holds the tips, playbook, calls to action and hashtags.

Item and script ids are the keys the saved checkmarks use, so change an id only if you're fine losing that item's checkmark.

Design patterns were adapted from [21st.dev](https://21st.dev) components: the bottom nav bar, the tubelight tab indicator, the bottom-sheet drawer, the card stack (Take mode) and the animated checkbox to-do list. They were rebuilt in plain HTML so the page needs no build step.
