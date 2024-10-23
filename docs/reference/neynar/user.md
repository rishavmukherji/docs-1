# Neynar User API

`GET /v2/farcaster/user`

This page documents how to get full user profile data using fid, username or wallet address.

The hostname is always `https://api.neynar.com`.

## Authentication

[Neynar](https://neynar.com) API key passed in as `x-api-key`.

## Concepts

`viewer_fid` is the fid of the user looking at the user profile being fetched.

## Sample requests

#### User by fid ([link](https://docs.neynar.com/reference/user-bulk))

```bash
curl --request GET \
     curl --request GET \
     --url 'https://api.neynar.com/v2/farcaster/user/bulk?fids=194%2C%20191%2C%206131&viewer_fid=3' \
     --header 'accept: application/json' \
     --header 'x-api-key: NEYNAR_API_DOCS'
     --header 'x-client-id: docs.farcaster.xyz'
```

#### User by address ([link](https://docs.neynar.com/reference/user-bulk-by-address))

Fetching for [vitalik.eth](https://warpcast.com/vitalik.eth). Full API documentation [here](https://docs.neynar.com/reference/feed-for-you).

```bash
curl --request GET \
     --url 'https://api.neynar.com/v2/farcaster/user/bulk-by-address?addresses=0xa6a8736f18f383f1cc2d938576933e5ea7df01a1%2C0x7cac817861e5c3384753403fb6c0c556c204b1ce&address_types=custody_address%2Cverified_address&viewer_fid=3' \
     --header 'accept: application/json' \
     --header 'x-api-key: NEYNAR_API_DOCS'
     --header 'x-client-id: docs.farcaster.xyz'
     --header 'x-client-id: docs.farcaster.xyz'
```

#### User by username([link](https://docs.neynar.com/reference/user-by-username-v2))

```bash
curl --request GET \
     --url 'https://api.neynar.com/v2/farcaster/user/by_username?username=neynar&viewer_fid=3' \
     --header 'accept: application/json' \
     --header 'x-api-key: NEYNAR_API_DOCS'
     --header 'x-client-id: docs.farcaster.xyz'
```

## Response

All above API requests response with either a singular or an array of user objects

```json
{
  "user": {
    "object": "user",
    "fid": 6131,
    "username": "neynar",
    "display_name": "Neynar",
    "pfp_url": "https://i.imgur.com/UjBZ3pV.png",
    "custody_address": "0xa6a8736f18f383f1cc2d938576933e5ea7df01a1",
    "profile": {
      "bio": {
        "text": "best farcaster developers build on neynar.com | /neynar"
      }
    },
    "follower_count": 5749,
    "following_count": 47,
    "verifications": ["0xa6a8736f18f383f1cc2d938576933e5ea7df01a1"],
    "verified_addresses": {
      "eth_addresses": ["0xa6a8736f18f383f1cc2d938576933e5ea7df01a1"],
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
}
```

To create new user accounts on Farcaster, see [here](https://docs.neynar.com/docs/how-to-create-a-new-farcaster-account-with-neynar).
