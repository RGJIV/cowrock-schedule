# cowrock-schedule

Public crew schedule page for Cow Rock Construction, served by GitHub Pages at
https://rgjiv.github.io/cowrock-schedule/

- `index.html`: the page. A "This week" list and a Gantt chart; tapping a job opens Google Maps driving directions
  to the job (from the viewer's current location).
- `schedule.json`: the data the page reads. **Public**: only job name, neighborhood, map point and dates. Never
  put headcounts, notes, client names, gate codes or prices here; those stay in the hub and AI_Files.
- `logo.png`: Cow Rock mark (from the `CRC` website repo).

## Privacy rule (Richard, Oct 14, 2026)

A job is on the page only while it is scheduled or underway. **Once a job is complete it comes off the public
schedule**: the hub publishes only active items that have not ended, the page hides anything whose end date has passed,
and every publish replaces this repo's history with a single commit so finished jobs' map points do not linger in
old versions. Subs need the location during a project; after it, nothing here should point to the house.

## Data format

```json
{"updated": "YYYY-MM-DD",
 "jobs": [{"id": "hattink", "name": "Hattink", "area": "Lonesome Valley",
           "lat": 35.14524, "lon": -83.0672, "start": "2026-10-12", "end": "2026-11-20", "tentative": false}]}
```

- Dates are inclusive. A job drops off the day after its end date; the chart starts on the current Monday.
- `tentative: true` draws a lighter dashed bar ("Dates not final").
- Map points come from the NC 911 address points (AddressNC geocoder), the same source as the hub's `weather.job_sites`.

## Updating

The hub owns the schedule and pushes `schedule.json` here when it changes (see `hub/schedule/` in `cowrock-hub`).
Until that is live, edit `schedule.json` and push to `gh-pages` (the published branch); Pages republishes in about a minute.

`robots.txt` and a `noindex` meta tag keep search engines from listing the page. The link is public to anyone who has it.
