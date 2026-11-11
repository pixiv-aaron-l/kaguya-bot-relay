# Kaguya Relay

A small Devvit app for moderators. When a new post is created in a subreddit where the app is installed, it sends a formatted message (an embed) to a Discord channel through a webhook that the moderator configures.

Each message contains the post title (linked to the post), the first image when the post has one, a short text preview for text posts, and the footer "by u/author on r/subreddit".

## Settings

Set per subreddit on the app's install settings page:

- Discord webhook URL: the webhook of the channel that should receive new posts.
- Embed color: six hex digits, so each subreddit can have its own color.

## Fetch Domains

- `discord.com`: used only to send a POST request to the Discord webhook URL that the subreddit moderator pasted into the app settings. The request contains public post information: title, link, author username, image URL and a short text preview. Nothing else is sent, and no data is read from Discord.

## Data stored

The app stores, in Devvit Redis, the IDs of recently relayed posts for seven days, only to avoid sending the same post twice.

- [Terms and Conditions](TERMS.md)
- [Privacy Policy](PRIVACY.md)
