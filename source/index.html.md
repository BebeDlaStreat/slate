---
title: EndoSkull API

language_tabs: # must be one of https://git.io/vQNgJ
  - html

toc_footers:
  - <a href='https://endoskull.net'>WebSite</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the EndoSkull API
  - name: keywords
    content: endoskull,API,Documentation,player,profile,profil,pvpkit,bedwars
---

# Introduction

Welcome on endoskull public api.

It will allow to get some informations about players.

Api limit is 60 requests per minute.

# Authentication

> To authorize, use this code:

```html
https://api.endoskull.fr/profile?token=myamazingtoken
```

> Make sure to replace `myamazingtoken` with your API token.

> If you used an available token:

```json
{
  "errorType": "Not Found",
  "errorMessage": "invalid name or uuid",
  "errorCode": 404
}
```

> If you don't used any token or a wrong token:

```json
{
  "errorType": "Unauthorized",
  "errorMessage": "Invalid token",
  "errorCode": 401
}
```

To generate a token you must execute `/api new` on the minecraft server (mc.endoskull.net) and it will send you your token in the chat. If you previously had a token it will erase it.

`Authorization: myamazingtoken`

<aside class="notice">
You must replace <code>myamazingtoken</code> with your personal API token.
</aside>

# Player Profile

## Get Player Profile

```html
https://api.endoskull.fr/profile?token=myamazingtoken&uuid=d2b7b4e0-d3ed-4230-ac83-1aa32dc97676
```

```html
https://api.endoskull.fr/profile?token=myamazingtoken&name=BebeDlaStreat
```

> It will return something like this:

```json
{
  "uuid": "d2b7b4e0-d3ed-4230-ac83-1aa32dc97676",
  "name": "BebeDlaStreat",
  "level": 1,
  "xp": 0,
  "money": 100,
  "firstJoin": 1648561638821,
  "lastLogin": 1656498720904,
  "lastLogout": 1656502332349,
  "pvpkit": {
    "kill": 0,
    "death": 0
  },
  "bedwars": {
    "kill": 0,
    "death": 0,
    "win": 0,
    "lose": 0,
    "finalKill": 0,
    "bedBroken": 0,
    "goulagWin": 0,
    "goulagLose": 0
  }
}
```

> If you gave invalid name/uuid:

````json
{
  "errorType": "Not Found",
  "errorMessage": "Dream is not in our database",
  "errorCode": 404
}
```

It will return any information we can provide about a player profile.

### HTTP Request

`GET https://api.endoskull.fr/profile?token=myamazingtoken&uuid=<uuid>`
`GET https://api.endoskull.fr/profile?token=myamazingtoken&name=<name>`

### Query Parameters

Parameter | Description
--------- | ------- | -----------
token | Use to authenticate you
name | To retrieve profile by his name
uuid | To retrieve profile by his uuid

<aside class="success">
If you give a uuid and a name in the same request it will take the uuid
</aside>