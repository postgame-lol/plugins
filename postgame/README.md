# postgame

[postgame.lol](https://postgame.lol) reviews your League of Legends games from their replay files (`.rofl`): it
finds the moments that cost you (deaths you could have avoided, lost objectives, missing vision, items bought
late), says what to do instead, and links each one so you can watch it. Across games, it shows the mistakes you
keep making and whether you are getting better.

This plugin connects your AI assistant to your postgame.lol account. Ask it to review your last game, explain a
mistake, or tell you what to work on to climb.

## What it contains

- **An MCP server**, remote: `https://mcp.postgame.lol/mcp`. The first time, your assistant opens postgame.lol in
  your browser: you sign in with Google and allow the connection (OAuth). You can disconnect it anytime in
  postgame.lol's Settings.
- **Two skills**: `review-a-game` (find a replay, upload it, get its review and walk through the costliest
  mistakes) and `coach-me` (the mistakes you keep making across games, and one thing to focus on).

## What it sends and where

Everything goes to postgame.lol's own server at `mcp.postgame.lol`, over HTTPS, and only for your account:
the replay files you choose to upload, your Riot ID if you link it, and the tool calls your assistant makes.
Nothing runs on your computer and the plugin reads no files by itself; to upload a replay, your assistant either
gives you a postgame.lol page to drop it on, or, if it can run commands, uploads the file you point it to.
Usage of the tools is measured (which tool, how long, errors) to improve the service; see the
[privacy policy](https://postgame.lol/legal#privacy).

## Your account

The plugin works with the postgame.lol account you sign in with, and the reviews your account includes. The plans
are described at [postgame.lol/pro](https://postgame.lol/pro).

postgame.lol isn't endorsed by Riot Games and doesn't reflect the views or opinions of Riot Games or anyone
officially involved in producing or managing Riot Games properties.
