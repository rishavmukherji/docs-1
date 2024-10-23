# Neynar Follow Graph API

This page documents how to get followers, following, suggested followes and relevant followers for a user

The hostname is always `https://api.neynar.com`.

## Authentication

[Neynar](https://neynar.com) API key passed in as `x-api-key`.

## Optional query params

- `viewer_fid` is the fid of the user looking at the user profile being fetched.
- `sort_type` as a query param can rank the list as `desc_chron` or `algorithmic`

## Social graph

#### Followers for a user ([link](https://docs.neynar.com/reference/followers-v2))

i.e. Alice's followers

```bash
curl --request GET \
     --url 'https://api.neynar.com/v2/farcaster/followers?fid=3&viewer_fid=3&sort_type=algorithmic&limit=1' \
     --header 'accept: application/json' \
     --header 'x-api-key: NEYNAR_API_DOCS'
     --header 'x-client-id: docs.farcaster.xyz'
```

#### Following for a user ([link](https://docs.neynar.com/reference/following-v2))

i.e. list of users Alice follows

```bash
curl --request GET \
     --url 'https://api.neynar.com/v2/farcaster/following?fid=2&viewer_fid=3&sort_type=algorithmic&limit=1' \
     --header 'accept: application/json' \
     --header 'x-api-key: NEYNAR_API_DOCS'
     --header 'x-client-id: docs.farcaster.xyz'
```

Both above APIs return an array of follow objects

```json
{
  "users": [
    {
      "object": "follow",
      "user": {
        "object": "user",
        "fid": 867223,
        "username": "klugwinmomos",
        "display_name": "KlugWinMomos",
        "pfp_url": "https://imagedelivery.net/BXluQx4ige9GuW0Ia56BHw/3efc6042-eb84-422a-7a6c-be1d22f81c00/rectcrop3",
        "custody_address": "0x7ad3b1695f6da889b74a09181dd9297d2779c0fd",
        "profile": {
          "bio": {
            "text": "Urban gardener growing my own food."
          }
        },
        "follower_count": 7,
        "following_count": 6,
        "verifications": [],
        "verified_addresses": {
          "eth_addresses": [],
          "sol_addresses": []
        },
        "verified_accounts": null,
        "active_status": "inactive",
        "power_badge": false,
        "viewer_context": {
          "following": false,
          "followed_by": false,
          "blocking": false,
          "blocked_by": false
        }
      }
    }
  ],
  "next": {
    "cursor": "eyJ0aW1lc3RhbXAiOiIyMDI0LTEwLTIzIDAzOjA3OjI2LjAwMDAwMDAiLCJmaWQiOjg2NzIyM30%3D"
  }
}
```

## Recommendations

#### Suggested followers for a user ([link](https://docs.neynar.com/reference/suggested-follows))

i.e. list of suggested users Alice should follow

```bash
curl --request GET \
     --url 'https://api.neynar.com/v2/farcaster/following/suggested?fid=2&viewer_fid=3&limit=1' \
     --header 'accept: application/json' \
     --header 'x-api-key: NEYNAR_API_DOCS'
     --header 'x-client-id: docs.farcaster.xyz'
```

Returns a list of user objects

```json
{
  "users": [
    {
      "object": "user",
      "fid": 404,
      "username": "viksit",
      "display_name": "viksit.eth",
      "pfp_url": "https://lh3.googleusercontent.com/Ur4lZjOkB5UfXtng-b-j0Ius-IaLN3AdJ9dkOrW5Gr9FMnAyISzf7KSAwjE2WQyIwCQki6Loh8NPyHccDvGuXrCLh9BY_TYXBaYPdw",
      "custody_address": "0x5bb02bd1b6f9a40ef153f8fb588550f73c4c4d2f",
      "profile": {
        "bio": {
          "text": "building solarplex.xyz - social marketplace for content creators"
        }
      },
      "follower_count": 188,
      "following_count": 93,
      "verifications": ["0xf4d352194e519eedc9be1eb89f2b5e0123e9ee12"],
      "verified_addresses": {
        "eth_addresses": ["0xf4d352194e519eedc9be1eb89f2b5e0123e9ee12"],
        "sol_addresses": []
      },
      "verified_accounts": null,
      "active_status": "inactive",
      "power_badge": false,
      "viewer_context": {
        "following": true,
        "followed_by": true,
        "blocking": false,
        "blocked_by": false
      }
    }
  ],
  "next": {
    "cursor": null
  }
}
```

#### Relevant followers for a user ([link](https://docs.neynar.com/reference/relevant-followers))

i.e. if Alice is looking at Bob's profile, Alice will see the users she follows who also follow Bob

```bash
curl --request GET \
     --url 'https://api.neynar.com/v2/farcaster/followers/relevant?target_fid=3&viewer_fid=2' \
     --header 'accept: application/json' \
     --header 'x-api-key: NEYNAR_API_DOCS'
     --header 'x-client-id: docs.farcaster.xyz'
```

Returns a set of hydrated follow objects for top relevant followers and dehydrated user objects for the remaining followers

```json
{
  "top_relevant_followers_hydrated": [
    {
      "object": "follow",
      "user": {
        "object": "user",
        "fid": 99,
        "username": "jessepollak",
        "display_name": "jesse.base.eth 🔵",
        "pfp_url": "https://imagedelivery.net/BXluQx4ige9GuW0Ia56BHw/1013b0f6-1bf4-4f4e-15fb-34be06fede00/original",
        "custody_address": "0x4ce34af3378a00c640125e4dbf4c9e64dff4c93b",
        "profile": {
          "bio": {
            "text": "@base builder #001; onchain cities w/ OAK & city3"
          }
        },
        "follower_count": 449423,
        "following_count": 1450,
        "verifications": [
          "0x849151d7d0bf1f34b70d5cad5149d28cc2308bf1",
          "0xe73f9c181b571cac2bf3173634d04a9921b7ffcf",
          "0x6e0d9c6dd8a08509bb625caa35dc61a991406f62",
          "0x2211d1d0020daea8039e46cf1367962070d77da9",
          "0x8e86e5331d3a020909c9e42ea9051675555f5e49",
          "0x6adea326faea1b688af33df59e18f7a819bcaa4f"
        ],
        "verified_addresses": {
          "eth_addresses": [
            "0x849151d7d0bf1f34b70d5cad5149d28cc2308bf1",
            "0xe73f9c181b571cac2bf3173634d04a9921b7ffcf",
            "0x6e0d9c6dd8a08509bb625caa35dc61a991406f62",
            "0x2211d1d0020daea8039e46cf1367962070d77da9",
            "0x8e86e5331d3a020909c9e42ea9051675555f5e49",
            "0x6adea326faea1b688af33df59e18f7a819bcaa4f"
          ],
          "sol_addresses": []
        },
        "verified_accounts": null,
        "active_status": "inactive",
        "power_badge": true
      }
    }
  ],
  "all_relevant_followers_dehydrated": [
    {
      "object": "follow",
      "user": {
        "object": "user_dehydrated",
        "fid": 99
      }
    }
  ]
}
```
