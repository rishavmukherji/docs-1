# Neynar Feed API

`GET v2/farcaster/feed`

This page documents how to build three different kinds of feeds with Neynar APIs

- Following feed - shows content from people you follow ranked in descending chronological order
- For You feed - shows content based on people you follow ranked in algorithmic order
- Channel feed - shows content from a specific channel ordered how you want

The hostname is always `https://api.neynar.com`.

## Authentication

[Neynar](https://neynar.com) API key passed in as `x-api-key`.

## Concepts

- Channels: Warpcast has the concept of channels which build upon FIP-2 (setting `parentUrl` on casts). You can read more
  about channels in the [documentation](https://www.notion.so/warpcast/Channels-4f249d22575348a5a0488b5d86f0dd1c?pvs=4).
- `viewer_fid`: FID of the user looking at the feed

## Sample Feed requests

#### Following

Fetching for [vitalik.eth](https://warpcast.com/vitalik.eth). Full API documentation [here](https://docs.neynar.com/reference/feed-following).

```bash
curl --request GET \
     --url 'https://api.neynar.com/v2/farcaster/feed/following?fid=5650&viewer_fid=5650&with_recasts=true&limit=1' \
     --header 'accept: application/json' \
     --header 'x-api-key: NEYNAR_API_DOCS'
```

#### For You

Fetching for [vitalik.eth](https://warpcast.com/vitalik.eth). Full API documentation [here](https://docs.neynar.com/reference/feed-for-you).

```bash
curl --request GET \
     --url 'https://api.neynar.com/v2/farcaster/feed/for_you?fid=5650&viewer_fid=5650&provider=openrank&limit=1' \
     --header 'accept: application/json' \
     --header 'x-api-key: NEYNAR_API_DOCS'
```

#### Channel feed

```bash
curl --request GET \
     --url 'https://api.neynar.com/v2/farcaster/feed/channels?channel_ids=warpcast&with_recasts=true&viewer_fid=3&with_replies=false&members_only=true&limit=1' \
     --header 'accept: application/json' \
     --header 'x-api-key: NEYNAR_API_DOCS'
```

## Response

All feed responses have the following response structure

```json
{
  "casts": [
    {
      "object": "cast",
      "hash": "0x66e50fb834b3c21d2729556e1a5f3e325f6cea34",
      "thread_hash": "0x66e50fb834b3c21d2729556e1a5f3e325f6cea34",
      "parent_hash": null,
      "parent_url": "https://warpcast.com/~/channel/the-pond",
      "root_parent_url": "https://warpcast.com/~/channel/the-pond",
      "parent_author": {
        "fid": null
      },
      "author": {
        "object": "user",
        "fid": 4199,
        "username": "frog",
        "display_name": "Michael Gingras (lilfrog)",
        "pfp_url": "https://i.imgur.com/YIQMdE9.jpg",
        "custody_address": "0xf0a56d6d70c8a39f5bd03bad0d0ab325a5493b23",
        "profile": {
          "bio": {
            "text": "Crypto, nouns, malleable software, interfaces, running. // working on @agora // https://0xmcg.com // /the-pond"
          }
        },
        "follower_count": 585,
        "following_count": 421,
        "verifications": ["0x65a3870f48b5237f27f674ec42ea1e017e111d63"],
        "verified_addresses": {
          "eth_addresses": ["0x65a3870f48b5237f27f674ec42ea1e017e111d63"],
          "sol_addresses": []
        },
        "verified_accounts": null,
        "active_status": "inactive",
        "power_badge": true,
        "viewer_context": {
          "following": false,
          "followed_by": true,
          "blocking": false,
          "blocked_by": false
        }
      },
      "text": "https://studio.ribbonfarm.com/p/cozytech",
      "timestamp": "2024-10-15T19:50:09.000Z",
      "embeds": [
        {
          "url": "https://studio.ribbonfarm.com/p/cozytech",
          "metadata": {
            "content_type": "text/html;charset=utf-8",
            "content_length": null,
            "_status": "RESOLVED",
            "html": {
              "ogUrl": "https://studio.ribbonfarm.com/p/cozytech",
              "author": "Venkatesh Rao",
              "jsonLD": [
                {
                  "url": "https://studio.ribbonfarm.com/p/cozytech",
                  "@type": "NewsArticle",
                  "image": [
                    {
                      "url": "https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2c4c2050-84f1-4669-bfc7-12bf94e907ec_1800x1200.png",
                      "@type": "ImageObject"
                    }
                  ],
                  "author": [
                    {
                      "url": "https://substack.com/@vgrao",
                      "name": "Venkatesh Rao",
                      "@type": "Person",
                      "image": {
                        "@type": "ImageObject",
                        "contentUrl": "https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F562e590a-9494-4f66-87f0-330c1be204c2_500x500.jpeg",
                        "thumbnailUrl": "https://substackcdn.com/image/fetch/w_128,h_128,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F562e590a-9494-4f66-87f0-330c1be204c2_500x500.jpeg"
                      },
                      "identifier": "user:2264734",
                      "description": "I’ve been writing the ribbonfarm blog since 2007, and the ribbonfarm studio newsletter since 2019."
                    }
                  ],
                  "@context": "https://schema.org",
                  "headline": "Cozytech",
                  "publisher": {
                    "url": "https://studio.ribbonfarm.com",
                    "logo": {
                      "url": "https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Ff139bf53-f5dc-4d6a-a159-4478fe7cd529_1280x1280.png",
                      "@type": "ImageObject",
                      "contentUrl": "https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Ff139bf53-f5dc-4d6a-a159-4478fe7cd529_1280x1280.png",
                      "thumbnailUrl": "https://substackcdn.com/image/fetch/w_128,h_128,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Ff139bf53-f5dc-4d6a-a159-4478fe7cd529_1280x1280.png"
                    },
                    "name": "Ribbonfarm Studio",
                    "@type": "Organization",
                    "image": {
                      "url": "https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Ff139bf53-f5dc-4d6a-a159-4478fe7cd529_1280x1280.png",
                      "@type": "ImageObject",
                      "contentUrl": "https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Ff139bf53-f5dc-4d6a-a159-4478fe7cd529_1280x1280.png",
                      "thumbnailUrl": "https://substackcdn.com/image/fetch/w_128,h_128,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Ff139bf53-f5dc-4d6a-a159-4478fe7cd529_1280x1280.png"
                    },
                    "sameAs": ["https://twitter.com/ribbonfarm"],
                    "identifier": "pub:9973",
                    "description": "Ribbonfarm Studio: Serialized projects from the Ribbonfarm blog",
                    "interactionStatistic": {
                      "name": "Subscribers",
                      "@type": "InteractionCounter",
                      "interactionType": "https://schema.org/SubscribeAction",
                      "userInteractionCount": 10000
                    }
                  },
                  "description": "Towards a viable alt-tech philosophy made up of individually delusional, collectively rational parts",
                  "dateModified": "2024-08-16T22:39:33+00:00",
                  "datePublished": "2024-08-16T22:39:33+00:00",
                  "mainEntityOfPage": "https://studio.ribbonfarm.com/p/cozytech",
                  "isAccessibleForFree": false
                }
              ],
              "ogType": "article",
              "charset": "utf-8",
              "favicon": "https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F441045fd-3465-40ad-871a-b5ffc9d9455f%2Ffavicon.ico",
              "ogImage": [
                {
                  "url": "https://substackcdn.com/image/fetch/w_1200,h_600,c_fill,f_jpg,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2c4c2050-84f1-4669-bfc7-12bf94e907ec_1800x1200.png",
                  "type": "png"
                }
              ],
              "ogTitle": "Cozytech",
              "ogLocale": "en",
              "twitterCard": "summary_large_image",
              "twitterImage": [
                {
                  "url": "https://substackcdn.com/image/fetch/f_auto,q_auto:best,fl_progressive:steep/https%3A%2F%2Fribbonfarmstudio.substack.com%2Fapi%2Fv1%2Fpost_preview%2F147790335%2Ftwitter.jpg%3Fversion%3D4"
                }
              ],
              "twitterTitle": "Cozytech",
              "ogDescription": "Towards a viable alt-tech philosophy made up of individually delusional, collectively rational parts",
              "twitterDescription": "Towards a viable alt-tech philosophy made up of individually delusional, collectively rational parts"
            }
          }
        }
      ],
      "reactions": {
        "likes_count": 4,
        "recasts_count": 1,
        "likes": [
          {
            "fid": 1287,
            "fname": "july"
          },
          {
            "fid": 4383,
            "fname": "pingfeng"
          },
          {
            "fid": 17905,
            "fname": "arsent"
          },
          {
            "fid": 1841,
            "fname": "martin"
          }
        ],
        "recasts": [
          {
            "fid": 1287,
            "fname": "july",
            "viewer_context": {
              "following": true
            }
          }
        ]
      },
      "replies": {
        "count": 0
      },
      "channel": {
        "object": "channel_dehydrated",
        "id": "the-pond",
        "name": "The pond",
        "image_url": "https://imagedelivery.net/BXluQx4ige9GuW0Ia56BHw/e57e15bc-b0ac-4bd8-f5fb-1cc7217d5300/original",
        "viewer_context": {
          "following": false
        }
      },
      "mentioned_profiles": [],
      "viewer_context": {
        "liked": false,
        "recasted": false
      },
      "author_channel_context": {
        "role": "moderator",
        "following": true
      },
      "inclusion_context": {
        "is_following_author": false,
        "is_following_recaster": true,
        "is_self_authored": false
      }
    }
  ],
  "next": {
    "cursor": "eyJ0aW1lc3RhbXAiOiIyMDI0LTEwLTE1IDE5OjUwOjA5LjAwMDAwMDAifQ%3D%3D"
  }
}
```
