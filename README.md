# foobad documentation
this document will show you how to properly configure foobad to fit your needs.

### latest, default config.json file:
```json
{
    "foobtrade_token": "your foobtra.de token",
    "rolimons_cookies": [
        "your rolimon's _RoliVerification cookie"
    ],
    "roblox_cookies": [
        "your roblox .ROBLOSECURITY cookie"
    ],
    "stay_online": true,
    "alert_on_2fa_needed": true,

    "post_delay": 15,
    "post_delay_variance": 3,

    "only_request_tags": false,
    "tag_request_percent": 40,
    "use_any_tag_only_when_needed": false,
    "use_complete_tag_override": false,
    "tag_override": [],

    "item_give_prioritize": [],
    "item_give_blacklist": [],
    "item_give_min_amount": 2,
    "item_give_max_amount": 3,

    "post_webhook": "https://discord.com/api/webhooks/...",
    "error_webhook": "https://discord.com/api/webhooks/...",
    "webhook_color": "#6f32a8"
}
```

## guides for each value
### foobtrade_token
you can get this from [foobtra.de/dashboard](https://foobtra.de/dashboard), then press the "get token" button.

### rolimons_cookies
an array of your rolimon's `_RoliVerification` cookies. ([guide for getting your `_RoliVerification` cookie](https://foob.cc/i/1ePdbeg.png))
```json
"rolimons_cookies": [
  "cookie1",
  "cookie2",
  "cookie3"
],
```
(notice the commas, foobad will be unable to read your config file if one is misplaced.)

### roblox_cookies
an array of your roblox account cookies. required for posting trade ads that don't contain just trading tags.
```json
"roblox_cookies": [
  "cookie1",
  "cookie2",
  "cookie2"
],
```
(notice the commas, foobad will be unable to read your config file if one is misplaced.)

### stay_online
sets the presence on [roblox.com](https://roblox.com) for each provided roblox account cookie to online. 

(value can be either `true` for yes or `false` for no)
```json
"stay_online": true,
```

### alert_on_2fa_needed
sends a webhook message to the provided webhook in your `error_webhook` option with the roblox account requesting 2fa.
this feature **ONLY** works for accounts that you've provided the roblox cookie for

(value can be either `true` for yes or `false` for no)
```json
"alert_on_2fa_needed": true,
```

### post_delay
minimum delay in minutes between trade ad posts, forced minimum of `15` minutes
```json
"post_delay": true,
```

### post_delay_variance
variance between trade ad posts, example of how it works:
```
post_delay of 15 & variance of 3 = post delay between [15] and [18] mins
post_delay of 20 & variance of 5 = post delay between [20] and [25] mins
```
```json
"post_delay_variance": 0,
```

### only_request_tags
only send trade ads that request the standard, vague tags such as `downgrade`, `upgrade`, or `any`.

rolimon's cookies without a linked roblox account cookie will be forced to repost only trade ad tags

(value can be either `true` for yes or `false` for no)
```json
"only_request_tags": true,
```

### tag_request_percent
percent chance to post just trade tags instead of reposting an outbound trade. 

rolimon's cookies without a linked roblox account cookie will be unable to repost outbounds

```json
"tag_request_percent": 50,
````

### use_any_tag_only_when_needed
if this is set to `false`, foobad will use the `any` trading tag more often

(value can be either `true` for yes or `false` for no)
```json
"use_any_tag_only_when_needed": false,
```

### tag_override
randomly uses as many of the specified tags in every trade ad's request

the tags can be the following: `any, demand, rares, rap, robux, upgrade, downgrade`
```json
"tag_override": [
    "rap", "demand", "any"
]
```

### use_complete_tag_override
if enabled, doesn't add upgrade/downgrade/any tags automatically to your trades

value can be `true` or `false` and `tag_override` must have data
```json
"use_complete_tag_override": false, 
```

### item_give_prioritize
overriden by outbound trade reposting.

items to prioritize being offered
```json
"item_give_prioritize": [
  123123,
  123123
],
```
(notice the commas, foobad will be unable to read your config file if one is misplaced.)

### item_give_blacklist
overriden by outbound trade reposting.

items to blacklist from being offered
```json
"item_give_blacklist": [
  123123,
  123123
],
```

### item_give_min_amount
overriden by outbound trade reposting.

the minimum amount of items on the offer side
```json
"item_give_min_amount": 2,
```

### item_give_max_amount
overriden by outbound trade reposting.

the maximum amount of items on the offer side
```json
"item_give_max_amount": 3,
```

### post_webhook
the discord webhook url to send successful trade ad posts to 
```json
"post_webhook": "https://discord.com/api/webhooks/...",
```

### error_webhook
the discord webhook url to send errors, invalidated cookies, and 2fa required messages to
```json
"error_webhook": "https://discord.com/api/webhooks/...",
```

### webhook_color
the color for the discord trade ad posted webhook

takes a color code hex value
```json
"webhook_color": "#6f32a8",
```
