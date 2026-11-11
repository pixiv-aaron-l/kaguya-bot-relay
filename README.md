# Kaguya Bot Relay

Kaguya Bot Relay is a tool for subreddit moderators. It sends every new post of your subreddit to a Discord channel of your choice, as one tidy message.

## What the Discord message looks like

- The post title on top, as a link to the post.
- The post's first picture in the middle, when it has one. Text posts show a short preview instead.
- A line at the bottom: "by u/author on r/subreddit".
- A color of your choice, so each subreddit can have its own.
- Posts marked NSFW are sent with an [NSFW] tag and without a picture.

## How to use it

1. In Discord, open the channel that should receive the posts, then go to Settings, Integrations, Webhooks, New Webhook, and copy the webhook URL.
2. Install the app on your subreddit.
3. Open the app's settings for your subreddit and paste the webhook URL. Optionally enter a color as six hex digits, for example 7E57C2.
4. Create a post. About one minute later, it appears in your Discord channel.

## Timing and routing

The message is sent one minute after the post is created. Right after it, the app can send a short second message (the routing tag, for example #kaguya-love) so a Discord bot can tell which channel the post belongs to.

## Settings

- Discord webhook URL: the webhook of the channel that receives new posts. It must start with https://discord.com/api/webhooks/
- Embed color: six hex digits without the #.
- Routing tag: optional text sent as a second message right after the embed.

## Fetch Domains

- `discord.com`: used only to send a POST request to the Discord webhook URL that the subreddit moderator pasted into the app settings. The request contains public post information: title, link, author username, image URL and a short text preview. Nothing else is sent, and no data is read from Discord.

## Data stored

The app stores, in Devvit Redis, the IDs of recently relayed posts for seven days, only to avoid sending the same post twice. It does not use the Reddit API and does not post, comment, vote or moderate anything.

- [Terms and Conditions](TERMS.md)
- [Privacy Policy](PRIVACY.md)
