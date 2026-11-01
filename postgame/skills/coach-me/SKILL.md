---
name: coach-me
description: Coach the player on the League of Legends mistakes they keep making across their games, with postgame.lol. Use when the player asks what to work on, how to climb or improve, what their bad habits are, or whether they are getting better.
---

# Coach across games

Use the postgame MCP server's tools on the player's reviewed games.

1. Call `recurring_mistakes`. It ranks the mistakes the player made in the most games, with how often per game
   (oldest first), a `trend` (better, same, worse) and links to the latest times.
2. Pick one focus, two at most: the mistake in the most games, preferring one marked `worse` or `same`. A short,
   concrete focus beats a list.
3. Call `mistake_history` for it and show two or three recent times it happened, with their links, so the player
   sees the pattern in their own games.
4. Turn its `what_to_do` into a habit for the next games ("every time X, do Y"), and say how they will know it
   worked: the count per game should drop in the next reviews.
5. If there are fewer than 3 reviewed games, say the picture is still thin and suggest reviewing more games
   (see the review-a-game skill).

Rules:

- Use only what the tools return: no invented numbers, rules or advice.
- Give links exactly as returned.
- Don't talk about plans, prices or upgrading.
