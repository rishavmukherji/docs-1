# Neynar Conversation API

`GET /v2/farcaster/cast/conversation`

This page documents how to get full replies to a given cast. The replies can be sorted algorithmically and lower quality replies can be optionally hidden below the fold.

The hostname is always `https://api.neynar.com`.

## Authentication

[Neynar](https://neynar.com) API key passed in as `x-api-key`.

## Concepts

- `viewer_fid` is the fid of the user looking at the user profile being fetched.
- `reply_depth` is the depth of replies in the conversation that will be returned in the response object
- `sort_type` can be `chron` or `algorithmic`, the latter downranks lower quality replies
- `fold` can be `above`, `below` or `null` to get conversation above or below the fold or the entire thread if the param isn't passed in

## Sample request ([link](https://docs.neynar.com/reference/cast-conversation))

```bash
curl --request GET \
     --url 'https://api.neynar.com/v2/farcaster/cast/conversation?identifier=https%3A%2F%2Fwarpcast.com%2Frish%2F0x9288c1&type=url&reply_depth=1&include_chronological_parent_casts=false&viewer_fid=3&sort_type=algorithmic&fold=above&limit=1' \
     --header 'accept: application/json' \
     --header 'x-api-key: NEYNAR_API_DOCS'
     --header 'x-client-id: docs.farcaster.xyz'
```

## Response

Responds with an conversation array of cast objects

```json
{
  "conversation": {
    "cast": {
      "object": "cast",
      "hash": "0x9288c1e862aa72bd69d0e383a28b9a76b63cbdb4",
      "thread_hash": "0x9288c1e862aa72bd69d0e383a28b9a76b63cbdb4",
      "parent_hash": null,
      "parent_url": "chain://eip155:7777777/erc721:0x4f86113fc3e9783cf3ec9a552cbb566716a57628",
      "root_parent_url": "chain://eip155:7777777/erc721:0x4f86113fc3e9783cf3ec9a552cbb566716a57628",
      "parent_author": {
        "fid": null
      },
      "author": {
        "object": "user",
        "fid": 194,
        "username": "rish",
        "display_name": "rish",
        "pfp_url": "https://i.imgur.com/naZWL9n.gif",
        "custody_address": "0xb95dc10483be18f7c69ddf78d4baafecc01c5530",
        "profile": {
          "bio": {
            "text": "working on farcaster infrastructure @ /neynar, neynar.com  🪐   /rish "
          }
        },
        "follower_count": 251967,
        "following_count": 781,
        "verifications": [
          "0x5a927ac639636e534b678e81768ca19e2c6280b7",
          "0xe9e261852ea62150eee685807df8fe3f211310a0",
          "0xe1fac64cebe0855d984ac7c3feb8b7612c6b4176"
        ],
        "verified_addresses": {
          "eth_addresses": [
            "0x5a927ac639636e534b678e81768ca19e2c6280b7",
            "0xe9e261852ea62150eee685807df8fe3f211310a0",
            "0xe1fac64cebe0855d984ac7c3feb8b7612c6b4176"
          ],
          "sol_addresses": []
        },
        "verified_accounts": [
          {
            "platform": "x",
            "username": "rish_neynar"
          }
        ],
        "active_status": "inactive",
        "power_badge": true,
        "viewer_context": {
          "following": true,
          "followed_by": true,
          "blocking": false,
          "blocked_by": false
        }
      },
      "text": ".@fun built out hatecast.xyz based on a random conversation we had about app ideas for Farcaster.\n\nThere are many things we'd love to build at @neynar if we had the time but spoiler alert: we don't. So would love to see others build these! \nhttps://paragraph.xyz/@neynar/farcaster-ideas \n\n🪐",
      "timestamp": "2023-09-13T22:10:22.000Z",
      "embeds": [
        {
          "url": "https://paragraph.xyz/@neynar/farcaster-ideas",
          "metadata": {
            "content_type": "text/html;charset=utf-8",
            "content_length": null,
            "_status": "RESOLVED"
          }
        }
      ],
      "reactions": {
        "likes_count": 55,
        "recasts_count": 18,
        "likes": [
          {
            "fid": 2390,
            "fname": "dhadrien.eth"
          },
          {
            "fid": 19315,
            "fname": "sonofsun"
          },
          {
            "fid": 4461,
            "fname": "limone.eth"
          },
          {
            "fid": 8639,
            "fname": "scotthconner"
          },
          {
            "fid": 8147,
            "fname": "jayonchain.eth"
          }
        ],
        "recasts": [
          {
            "fid": 23039,
            "fname": "0mbre"
          },
          {
            "fid": 19691,
            "fname": "rafael12"
          },
          {
            "fid": 17848,
            "fname": "saeid1088"
          },
          {
            "fid": 17213,
            "fname": "4337"
          },
          {
            "fid": 18136,
            "fname": "javad126070"
          }
        ]
      },
      "replies": {
        "count": 10
      },
      "channel": {
        "object": "channel_dehydrated",
        "id": "farcaster",
        "name": "Farcaster",
        "image_url": "https://ipfs.decentralized-content.com/ipfs/bafkreialf5usxssf2eu3e5ct37zzdd553d7lg7oywvdszmrg5p2zpkta7u",
        "viewer_context": {
          "role": "moderator",
          "following": true
        }
      },
      "mentioned_profiles": [
        {
          "object": "user",
          "fid": 5620,
          "custody_address": "0xbee82d68f49ee2aa8408f8111db64d92e4d61971",
          "username": "fun",
          "display_name": "welter",
          "pfp_url": "https://i.imgur.com/4mRk8Xo.png",
          "profile": {
            "bio": {
              "text": "building farcasterstudio.com & reel.farm",
              "mentioned_profiles": []
            }
          },
          "follower_count": 72054,
          "following_count": 359,
          "verifications": ["0x02ac33835070d0c90bef87c273514e67aea36ef8"],
          "verified_addresses": {
            "eth_addresses": ["0x02ac33835070d0c90bef87c273514e67aea36ef8"],
            "sol_addresses": []
          },
          "active_status": "inactive",
          "power_badge": true
        },
        {
          "object": "user",
          "fid": 6131,
          "custody_address": "0xa6a8736f18f383f1cc2d938576933e5ea7df01a1",
          "username": "neynar",
          "display_name": "Neynar",
          "pfp_url": "https://i.imgur.com/UjBZ3pV.png",
          "profile": {
            "bio": {
              "text": "best farcaster developers build on neynar.com | /neynar",
              "mentioned_profiles": []
            }
          },
          "follower_count": 5749,
          "following_count": 47,
          "verifications": ["0xa6a8736f18f383f1cc2d938576933e5ea7df01a1"],
          "verified_addresses": {
            "eth_addresses": ["0xa6a8736f18f383f1cc2d938576933e5ea7df01a1"],
            "sol_addresses": []
          },
          "active_status": "inactive",
          "power_badge": false
        }
      ],
      "viewer_context": {
        "liked": false,
        "recasted": false
      },
      "author_channel_context": {
        "role": "member",
        "following": true
      },
      "direct_replies": [
        {
          "object": "cast",
          "hash": "0xfc08d60cc1ed5856acad520711a0f0571f388747",
          "thread_hash": "0x9288c1e862aa72bd69d0e383a28b9a76b63cbdb4",
          "parent_hash": "0x9288c1e862aa72bd69d0e383a28b9a76b63cbdb4",
          "parent_url": null,
          "root_parent_url": "chain://eip155:7777777/erc721:0x4f86113fc3e9783cf3ec9a552cbb566716a57628",
          "parent_author": {
            "fid": 194
          },
          "author": {
            "object": "user",
            "fid": 602,
            "username": "betashop.eth",
            "display_name": "Jason Goldberg Ⓜ️ 💜",
            "pfp_url": "https://imagedelivery.net/BXluQx4ige9GuW0Ia56BHw/2965dc69-edd0-44d7-0121-dd628021e500/original",
            "custody_address": "0x66bd69c7064d35d146ca78e6b186e57679fba249",
            "profile": {
              "bio": {
                "text": "chef at Moxie 👾"
              }
            },
            "follower_count": 189746,
            "following_count": 2598,
            "verifications": [
              "0x66bd69c7064d35d146ca78e6b186e57679fba249",
              "0xb8e5bfe308e3ff4fc2c5c02022b884b38c34bf9b",
              "0xeaf55242a90bb3289db8184772b0b98562053559",
              "0x83aca9ba40b877788ad87e7403ae6b798965ca50",
              "0x7d56aded74d0d5d67ded96a55fb9cfef9bb095ac"
            ],
            "verified_addresses": {
              "eth_addresses": [
                "0x66bd69c7064d35d146ca78e6b186e57679fba249",
                "0xb8e5bfe308e3ff4fc2c5c02022b884b38c34bf9b",
                "0xeaf55242a90bb3289db8184772b0b98562053559",
                "0x83aca9ba40b877788ad87e7403ae6b798965ca50",
                "0x7d56aded74d0d5d67ded96a55fb9cfef9bb095ac"
              ],
              "sol_addresses": []
            },
            "verified_accounts": [
              {
                "platform": "x",
                "username": "betashop"
              }
            ],
            "active_status": "inactive",
            "power_badge": true,
            "viewer_context": {
              "following": true,
              "followed_by": true,
              "blocking": false,
              "blocked_by": false
            }
          },
          "text": "@fun v cool! \n\nWith 1 api call to Airstack we can fix this",
          "timestamp": "2023-09-14T02:00:28.000Z",
          "embeds": [
            {
              "url": "https://i.imgur.com/LeKlmQF.jpg",
              "metadata": {
                "content_type": "image/jpeg",
                "content_length": 354756,
                "_status": "RESOLVED",
                "image": {
                  "width_px": 923,
                  "height_px": 2000
                }
              }
            }
          ],
          "reactions": {
            "likes_count": 0,
            "recasts_count": 0,
            "likes": [],
            "recasts": []
          },
          "replies": {
            "count": 1
          },
          "channel": {
            "object": "channel_dehydrated",
            "id": "farcaster",
            "name": "Farcaster",
            "image_url": "https://ipfs.decentralized-content.com/ipfs/bafkreialf5usxssf2eu3e5ct37zzdd553d7lg7oywvdszmrg5p2zpkta7u",
            "viewer_context": {
              "role": "moderator",
              "following": true
            }
          },
          "mentioned_profiles": [
            {
              "object": "user",
              "fid": 5620,
              "custody_address": "0xbee82d68f49ee2aa8408f8111db64d92e4d61971",
              "username": "fun",
              "display_name": "welter",
              "pfp_url": "https://i.imgur.com/4mRk8Xo.png",
              "profile": {
                "bio": {
                  "text": "building farcasterstudio.com & reel.farm",
                  "mentioned_profiles": []
                }
              },
              "follower_count": 72054,
              "following_count": 359,
              "verifications": ["0x02ac33835070d0c90bef87c273514e67aea36ef8"],
              "verified_addresses": {
                "eth_addresses": ["0x02ac33835070d0c90bef87c273514e67aea36ef8"],
                "sol_addresses": []
              },
              "active_status": "inactive",
              "power_badge": true
            }
          ],
          "viewer_context": {
            "liked": false,
            "recasted": false
          },
          "author_channel_context": {
            "role": "member",
            "following": true
          },
          "direct_replies": []
        }
      ]
    }
  },
  "next": {
    "cursor": "eyJpc19ieV9vcmlnaW5hbF9hdXRob3IiOmZhbHNlLCJlbmdhZ2VtZW50X3Njb3JlIjoiMC4wMDk3MjgyMTg0Mjg3OTA1NyIsInRpbWVzdGFtcCI6IjIwMjMtMDktMTQgMDI6MDA6MjguMDAwMDAwMCJ9"
  }
}
```
