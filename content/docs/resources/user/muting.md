---
title: "User Muting"
---

# Muting

* TOC
{:toc}

## Mute a User

Hide all posts for a User in all streams. *Note: if you still explicitly request this User's stream or a Post from this User, it will not be hidden.*

<%= general_params_note_for "user" %>

<%= endpoint "POST", "users/[user_id]/mute", "User", "follow" %>

<%= url_params [
  ["user_id","The id of the User to mute. You can also specify <code>@username</code> as a <code>user_id</code>."]
]%>

#### Example

> POST https://alpha-api.app.net/stream/0/users/1/mute

~~~ js
{
    "data": {
        "id": "1", // note this is a string
        "username": "mthurman",
        "name": "Mark Thurman",
        "description": {
           "text": "Hi, I'm Mark Thurman and I'm teaching you about the @appdotnet Stream #API.",
           "html": "Hi, I'm Mark Thurman and I'm <a href=\"https://github.com/appdotnet/api_spec\" rel=\"nofollow\">teaching you</a> about the <span itemprop=\"mention\" data-mention-name=\"appdotnet\" data-mention-id=\"3\">@appdotnet</span> Stream #<span itemprop=\"hashtag\" data-hashtag-name=\"api\">API</span>.",
           "entities": {
               "mentions": [{
                   "name": "appdotnet",
                   "id": "3",
                   "pos": 52,
                   "len": 10
               }],
               "hashtags": [{
                   "name": "api",
                   "pos": 70,
                   "len": 4
               }],
               "links": [{
                   "text": "teaching you",
                   "url": "https://github.com/appdotnet/api-spec",
                   "pos": 29,
                   "len": 12
               }]
            }
        },
        "timezone": "US/Pacific",
        "locale": "en_US",
        "avatar_image": {
            "height": 512,
            "width": 512,
            "url": "https://example.com/avatar_image.jpg",
            "is_default": false
        },
        "cover_image": {
            "height": 118,
            "width": 320,
            "url": "https://example.com/cover_image.jpg",
            "is_default": false
        },
        "type": "human",
        "created_at": "2012-07-16T17:23:34Z",
        "counts": {
            "following": 100,
            "followers": 200,
            "posts": 24,
            "stars": 76
        },
        "follows_you": false,
        "you_follow": true,
        "you_muted": true,
    },
    "meta": {
        "code": 200
    }
}
~~~

## Unmute a User

Stop hiding all posts for a given user.

<%= general_params_note_for "user" %>

*Remember, access tokens can not be passed in a HTTP body for ```DELETE``` requests. Please refer to the [authentication documentation](/docs/authentication/#making-authenticated-api-requests).*

<%= endpoint "DELETE", "users/[user_id]/mute", "User", "follow" %>

<%= url_params [
  ["user_id","The id of the User to mute. You can also specify <code>@username</code> as a <code>user_id</code>."]
]%>

#### Example

> DELETE https://alpha-api.app.net/stream/0/users/1/mute

~~~ js
{
    "data": {
        "id": "1", // note this is a string
        "username": "mthurman",
        "name": "Mark Thurman",
        "description": {
           "text": "Hi, I'm Mark Thurman and I'm teaching you about the @appdotnet Stream #API.",
           "html": "Hi, I'm Mark Thurman and I'm <a href=\"https://github.com/appdotnet/api_spec\" rel=\"nofollow\">teaching you</a> about the <span itemprop=\"mention\" data-mention-name=\"appdotnet\" data-mention-id=\"3\">@appdotnet</span> Stream #<span itemprop=\"hashtag\" data-hashtag-name=\"api\">API</span>.",
           "entities": {
               "mentions": [{
                   "name": "appdotnet",
                   "id": "3",
                   "pos": 52,
                   "len": 10
               }],
               "hashtags": [{
                   "name": "api",
                   "pos": 70,
                   "len": 4
               }],
               "links": [{
                   "text": "teaching you",
                   "url": "https://github.com/appdotnet/api-spec",
                   "pos": 29,
                   "len": 12
               }]
            }
        },
        "timezone": "US/Pacific",
        "locale": "en_US",
        "avatar_image": {
            "height": 512,
            "width": 512,
            "url": "https://example.com/avatar_image.jpg",
            "is_default": false
        },
        "cover_image": {
            "height": 118,
            "width": 320,
            "url": "https://example.com/cover_image.jpg",
            "is_default": false
        },
        "type": "human",
        "created_at": "2012-07-16T17:23:34Z",
        "counts": {
            "following": 100,
            "followers": 200,
            "posts": 24,
            "stars": 76
        },
        "follows_you": false,
        "you_follow": true,
        "you_muted": false,
    },
    "meta": {
        "code": 200
    }
}
~~~

## List muted Users

Retrieve a list of muted users.

<%= general_params_note_for "user" %>

<%= endpoint "GET", "users/[user_id]/muted", "Any" %>

<%= url_params [
  ["user_id",'The id of the user to retrieve a list of muted users for. If requested with a <a href="/docs/authentication/#access-tokens">user token</a> you can request muted users for the current user by using <code>me</code> as the user id. If requested with an <a href="/docs/authentication/#access-tokens">app token</a> you can request muted users for any user that has authorized your app.']
]%>

#### Example

> GET https://alpha-api.app.net/stream/0/users/me/muted

~~~ js
{
    "data": [
        {
            "id": "1", // note this is a string
            "username": "mthurman",
            "name": "Mark Thurman",
            "description": {
               "text": "Hi, I'm Mark Thurman and I'm teaching you about the @appdotnet Stream #API.",
               "html": "Hi, I'm Mark Thurman and I'm <a href=\"https://github.com/appdotnet/api_spec\" rel=\"nofollow\">teaching you</a> about the <span itemprop=\"mention\" data-mention-name=\"appdotnet\" data-mention-id=\"3\">@appdotnet</span> Stream #<span itemprop=\"hashtag\" data-hashtag-name=\"api\">API</span>.",
               "entities": {
                   "mentions": [{
                       "name": "appdotnet",
                       "id": "3",
                       "pos": 52,
                       "len": 10
                   }],
                   "hashtags": [{
                       "name": "api",
                       "pos": 70,
                       "len": 4
                   }],
                   "links": [{
                       "text": "teaching you",
                       "url": "https://github.com/appdotnet/api-spec",
                       "pos": 29,
                       "len": 12
                   }]
                }
            },
            "timezone": "US/Pacific",
            "locale": "en_US",
            "avatar_image": {
                "height": 512,
                "width": 512,
                "url": "https://example.com/avatar_image.jpg",
                "is_default": false
            },
            "cover_image": {
                "height": 118,
                "width": 320,
                "url": "https://example.com/cover_image.jpg",
                "is_default": false
            },
            "type": "human",
            "created_at": "2012-07-16T17:23:34Z",
            "counts": {
                "following": 100,
                "followers": 200,
                "posts": 24,
                "stars": 76
            },
            "follows_you": false,
            "you_follow": true,
            "you_muted": true,
        },
        ...
    ],
    "meta": {
        "code": 200
    }
}
~~~

## Retrieve muted User IDs for multiple Users

Returns a list of muted User ids for each User id requested. At most 200 User ids can be requested.

<%= endpoint "GET", "users/muted/ids", "App" %>

<%= query_params [
  ["ids","A comma separated list of User ids to retrieve muted User ids for."]
]%>

#### Example

> GET https://alpha-api.app.net/stream/0/users/muted/ids?ids=1,2

~~~ js
{
    "data": {
        "1": [
            "3",
            "29"
        ],
        "2": []
    },
    "meta": {
        "code": 200
    }
}
~~~