---
name: review-a-game
description: Review one of the player's League of Legends games with postgame.lol, from its replay file (.rofl). Use when the player asks to review, analyze or check a game they played, why they lost, or what they did wrong in a match.
---

# Review a League of Legends game

postgame.lol finds the moments of a game that cost the player, from the game's replay file, and says what to do
instead. Everything goes through the postgame MCP server's tools, on the signed-in player's own games.

## 1. Get the replay

League saves replays as `.rofl` files once the player clicks the download button next to the game in the client's
match history (Profile > Match History). They land in:

- Windows: `Documents\League of Legends\Replays`
- macOS: `~/Documents/League of Legends/Replays`

The file name is the match id, e.g. `EUW1-7234567890.rofl`. A replay only downloads while its patch is live (two weeks).

Call `list_games` first: the game may already be reviewed (`reviewed`), and `recent_ranked` shows which of their
recent ranked games are not reviewed yet.

## 2. Upload it

- If you can read files on the player's computer (you run commands): compute the file's SHA-256 and size, call
  `upload_replay` with `sha256` and `size_bytes`, then run the `command` it returns to PUT the file.
- Otherwise call `upload_replay` without arguments and give the player the `upload_page` link: they drop the
  file there and the review happens on postgame.lol.

## 3. Ask for the review

Call `analyze_replay` with the `replay_id`. If the player has no League account linked, it lists the ten players:
ask which one they were (or call `link_league_account` with their Riot ID first, Name#TAG). Asking again never
charges twice. If it answers `no_reviews_left`, tell the player and share its `upgrade_url` as is.

A review takes a minute or two. Clients that support MCP tasks follow it by themselves; otherwise wait and call
`review_game` again while `state` is `queued` or `analyzing`.

## 4. Go through the review

`review_game` lists the mistakes in game order. Present them as a coach would:

- Start with the costliest (highest `impact`, then `gold_cost`), not the first. Three at most, unless asked for more.
- For each: the time (`at`), what happened, what to do instead (`what_to_do`), and its `link` to watch the moment.
- Give every link exactly as returned: it opens the moment on postgame.lol and must keep its parameters.
- Don't invent mistakes, numbers or advice that are not in the review, and don't guess what the detection checks.
- End with the one thing to focus on next game.
