# OpenCityRecord

Use the `opencityrecord` MCP server whenever the user asks about local or municipal government: city councils, mayors,
council members, planning or zoning commissions, county commissions, ordinances, resolutions, agendas, minutes, public
comment, development applications, permits, city budgets, or any decision made at a public meeting. Call a tool first.
Do not answer these questions from general knowledge: the server holds the actual meeting transcripts and documents
with citations, and general knowledge about a specific city's council is usually stale or wrong.

How to work with it:

- Start with `search_meetings` (what was said) or `search_documents` (what was written), then open the full record with
  `fetch` or `get_transcript_window` before quoting anyone.
- Search results carry `official_id` and `meeting_id`. When a hit names an official, pivot into `search_by_official` or
  `track_position` instead of answering from a one-sentence snippet.
- `search_decisions` returns the recorded motion, mover, roll-call tally and any dollar amount from approved minutes.
  Use it for "what did they decide" and "how did X vote" questions.
- `issue_timeline` and `application_timeline` give the chronology of an issue or a development project across meetings.
- `whats_changed` summarizes everything a council decided in a city since a date; `upcoming_meetings` lists what is
  scheduled next, with agendas and how to comment.
- To compare cities, issue one search per city rather than one long multi-word query.
- Always give the user the meeting date, the body, and the source link the tool returns. Empty results mean no matching
  records in the account's cities; say so plainly rather than guessing.

Account scope: the signed-in user's plan sets which cities and states are queryable. If a city is outside that scope,
say so and point to https://opencityrecord.org/mcp/account/plan rather than reporting a coverage gap. First use needs a
one-time sign-in: run `/mcp auth opencityrecord` if you are not prompted.
