Card tables
================

A card table is made of multiple columns which contain cards. It can also hold wormholes: portals that send cards dropped into them to a column on another card table.

Endpoints:

- [Get a card table](#get-a-card-table)
- [Move a card on the board](#move-a-card-on-the-board)

Get a card table
--------------------

* `GET /card_tables/2.json` will return the card table with an ID of `2`.

###### Example JSON Response
<!-- START GET /card_tables/2.json -->
```json
{
  "id": 1069479833,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-05-28T17:23:17.403Z",
  "updated_at": "2026-07-20T04:30:19.909Z",
  "title": "Card Table",
  "inherits_status": true,
  "type": "Kanban::Board",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479833.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479833",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgzMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--f7f92817aeb592070d6fe17763467906a179ccee.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479833/subscription.json",
  "position": 7,
  "bucket": {
    "id": 2085958505,
    "name": "The Leto Laptop",
    "type": "Project"
  },
  "creator": {
    "id": 1049715913,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
    "name": "Victor Cooper",
    "personable_type": "User",
    "title": "Chief Strategist",
    "tagline": "Don't let your dreams be dreams",
    "location": "Chicago, IL",
    "created_at": "2026-05-28T17:22:22.069Z",
    "updated_at": "2026-07-21T01:06:02.483Z",
    "email_address": "victor@honchodesign.com",
    "bio": "Don't let your dreams be dreams",
    "admin": true,
    "owner": true,
    "client": false,
    "employee": true,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
    "company": {
      "id": 1033447817,
      "name": "Honcho Design"
    },
    "can_ping": true,
    "can_manage_projects": true,
    "can_manage_people": true,
    "can_access_timesheet": true,
    "can_access_hill_charts": true
  },
  "subscribers": [
    {
      "id": 1049715913,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
      "name": "Victor Cooper",
      "personable_type": "User",
      "title": "Chief Strategist",
      "tagline": "Don't let your dreams be dreams",
      "location": "Chicago, IL",
      "created_at": "2026-05-28T17:22:22.069Z",
      "updated_at": "2026-07-21T01:06:02.483Z",
      "email_address": "victor@honchodesign.com",
      "bio": "Don't let your dreams be dreams",
      "admin": true,
      "owner": true,
      "client": false,
      "employee": true,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
      "company": {
        "id": 1033447817,
        "name": "Honcho Design"
      },
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    }
  ],
  "public_link_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479833/publication",
  "lists": [
    {
      "id": 1069479834,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-05-28T17:23:17.411Z",
      "updated_at": "2026-05-28T17:23:29.745Z",
      "title": "Triage",
      "inherits_status": true,
      "type": "Kanban::Triage",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/columns/1069479834.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/columns/1069479834",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgzND9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--44239f0fef95aba53d92f958278965ef8e9959c5.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479834/subscription.json",
      "parent": {
        "id": 1069479833,
        "title": "Card Table",
        "type": "Kanban::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479833.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479833"
      },
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "type": "Project"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-05-28T17:22:22.069Z",
        "updated_at": "2026-07-21T01:06:02.483Z",
        "email_address": "victor@honchodesign.com",
        "bio": "Don't let your dreams be dreams",
        "admin": true,
        "owner": true,
        "client": false,
        "employee": true,
        "time_zone": "America/Chicago",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
        "company": {
          "id": 1033447817,
          "name": "Honcho Design"
        },
        "can_ping": true,
        "can_manage_projects": true,
        "can_manage_people": true,
        "can_access_timesheet": true,
        "can_access_hill_charts": true
      },
      "description": null,
      "subscribers": [
        {
          "id": 1049715913,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
          "name": "Victor Cooper",
          "personable_type": "User",
          "title": "Chief Strategist",
          "tagline": "Don't let your dreams be dreams",
          "location": "Chicago, IL",
          "created_at": "2026-05-28T17:22:22.069Z",
          "updated_at": "2026-07-21T01:06:02.483Z",
          "email_address": "victor@honchodesign.com",
          "bio": "Don't let your dreams be dreams",
          "admin": true,
          "owner": true,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
          "company": {
            "id": 1033447817,
            "name": "Honcho Design"
          },
          "can_ping": true,
          "can_manage_projects": true,
          "can_manage_people": true,
          "can_access_timesheet": true,
          "can_access_hill_charts": true
        }
      ],
      "color": null,
      "cards_count": 1,
      "comment_count": 0,
      "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/lists/1069479834/cards.json"
    },
    {
      "id": 1069479835,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-05-28T17:23:17.426Z",
      "updated_at": "2026-07-20T04:30:19.826Z",
      "title": "Not now",
      "inherits_status": true,
      "type": "Kanban::NotNowColumn",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/columns/1069479835.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/columns/1069479835",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgzNT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1bd70e47352972fce8c34156a797c1a48839a8dc.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479835/subscription.json",
      "parent": {
        "id": 1069479833,
        "title": "Card Table",
        "type": "Kanban::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479833.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479833"
      },
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "type": "Project"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-05-28T17:22:22.069Z",
        "updated_at": "2026-07-21T01:06:02.483Z",
        "email_address": "victor@honchodesign.com",
        "bio": "Don't let your dreams be dreams",
        "admin": true,
        "owner": true,
        "client": false,
        "employee": true,
        "time_zone": "America/Chicago",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
        "company": {
          "id": 1033447817,
          "name": "Honcho Design"
        },
        "can_ping": true,
        "can_manage_projects": true,
        "can_manage_people": true,
        "can_access_timesheet": true,
        "can_access_hill_charts": true
      },
      "description": null,
      "subscribers": [
        {
          "id": 1049715913,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
          "name": "Victor Cooper",
          "personable_type": "User",
          "title": "Chief Strategist",
          "tagline": "Don't let your dreams be dreams",
          "location": "Chicago, IL",
          "created_at": "2026-05-28T17:22:22.069Z",
          "updated_at": "2026-07-21T01:06:02.483Z",
          "email_address": "victor@honchodesign.com",
          "bio": "Don't let your dreams be dreams",
          "admin": true,
          "owner": true,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
          "company": {
            "id": 1033447817,
            "name": "Honcho Design"
          },
          "can_ping": true,
          "can_manage_projects": true,
          "can_manage_people": true,
          "can_access_timesheet": true,
          "can_access_hill_charts": true
        }
      ],
      "color": null,
      "cards_count": 1,
      "comment_count": 0,
      "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/lists/1069479835/cards.json"
    },
    {
      "id": 1069479836,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-05-28T17:23:17.441Z",
      "updated_at": "2026-07-20T04:30:19.651Z",
      "title": "Figuring it out",
      "inherits_status": true,
      "type": "Kanban::Column",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/columns/1069479836.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/columns/1069479836",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgzNj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--b79543d94bd8f35cfbe4dc05ae0913e626c51402.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479836/subscription.json",
      "position": 1,
      "parent": {
        "id": 1069479833,
        "title": "Card Table",
        "type": "Kanban::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479833.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479833"
      },
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "type": "Project"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-05-28T17:22:22.069Z",
        "updated_at": "2026-07-21T01:06:02.483Z",
        "email_address": "victor@honchodesign.com",
        "bio": "Don't let your dreams be dreams",
        "admin": true,
        "owner": true,
        "client": false,
        "employee": true,
        "time_zone": "America/Chicago",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
        "company": {
          "id": 1033447817,
          "name": "Honcho Design"
        },
        "can_ping": true,
        "can_manage_projects": true,
        "can_manage_people": true,
        "can_access_timesheet": true,
        "can_access_hill_charts": true
      },
      "description": null,
      "subscribers": [
        {
          "id": 1049715913,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
          "name": "Victor Cooper",
          "personable_type": "User",
          "title": "Chief Strategist",
          "tagline": "Don't let your dreams be dreams",
          "location": "Chicago, IL",
          "created_at": "2026-05-28T17:22:22.069Z",
          "updated_at": "2026-07-21T01:06:02.483Z",
          "email_address": "victor@honchodesign.com",
          "bio": "Don't let your dreams be dreams",
          "admin": true,
          "owner": true,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
          "company": {
            "id": 1033447817,
            "name": "Honcho Design"
          },
          "can_ping": true,
          "can_manage_projects": true,
          "can_manage_people": true,
          "can_access_timesheet": true,
          "can_access_hill_charts": true
        }
      ],
      "color": "purple",
      "cards_count": 1,
      "comment_count": 0,
      "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/lists/1069479836/cards.json"
    },
    {
      "id": 1069479837,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-05-28T17:23:17.463Z",
      "updated_at": "2026-07-20T04:30:19.908Z",
      "title": "In progress",
      "inherits_status": true,
      "type": "Kanban::Column",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/columns/1069479837.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/columns/1069479837",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgzNz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--418ee03861ef579a180c2c063465af533b11f85d.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479837/subscription.json",
      "position": 2,
      "parent": {
        "id": 1069479833,
        "title": "Card Table",
        "type": "Kanban::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479833.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479833"
      },
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "type": "Project"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-05-28T17:22:22.069Z",
        "updated_at": "2026-07-21T01:06:02.483Z",
        "email_address": "victor@honchodesign.com",
        "bio": "Don't let your dreams be dreams",
        "admin": true,
        "owner": true,
        "client": false,
        "employee": true,
        "time_zone": "America/Chicago",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
        "company": {
          "id": 1033447817,
          "name": "Honcho Design"
        },
        "can_ping": true,
        "can_manage_projects": true,
        "can_manage_people": true,
        "can_access_timesheet": true,
        "can_access_hill_charts": true
      },
      "description": null,
      "subscribers": [
        {
          "id": 1049715913,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
          "name": "Victor Cooper",
          "personable_type": "User",
          "title": "Chief Strategist",
          "tagline": "Don't let your dreams be dreams",
          "location": "Chicago, IL",
          "created_at": "2026-05-28T17:22:22.069Z",
          "updated_at": "2026-07-21T01:06:02.483Z",
          "email_address": "victor@honchodesign.com",
          "bio": "Don't let your dreams be dreams",
          "admin": true,
          "owner": true,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
          "company": {
            "id": 1033447817,
            "name": "Honcho Design"
          },
          "can_ping": true,
          "can_manage_projects": true,
          "can_manage_people": true,
          "can_access_timesheet": true,
          "can_access_hill_charts": true
        }
      ],
      "color": "orange",
      "cards_count": 1,
      "comment_count": 0,
      "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/lists/1069479837/cards.json"
    },
    {
      "id": 1069479838,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-05-28T17:23:17.483Z",
      "updated_at": "2026-05-28T17:23:17.490Z",
      "title": "Done",
      "inherits_status": true,
      "type": "Kanban::DoneColumn",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/columns/1069479838.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/columns/1069479838",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTgzOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--0a6d4ee4640e461a9689709d91111787f344b8d7.json",
      "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479838/subscription.json",
      "parent": {
        "id": 1069479833,
        "title": "Card Table",
        "type": "Kanban::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479833.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479833"
      },
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "type": "Project"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-05-28T17:22:22.069Z",
        "updated_at": "2026-07-21T01:06:02.483Z",
        "email_address": "victor@honchodesign.com",
        "bio": "Don't let your dreams be dreams",
        "admin": true,
        "owner": true,
        "client": false,
        "employee": true,
        "time_zone": "America/Chicago",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
        "company": {
          "id": 1033447817,
          "name": "Honcho Design"
        },
        "can_ping": true,
        "can_manage_projects": true,
        "can_manage_people": true,
        "can_access_timesheet": true,
        "can_access_hill_charts": true
      },
      "description": null,
      "subscribers": [
        {
          "id": 1049715913,
          "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
          "name": "Victor Cooper",
          "personable_type": "User",
          "title": "Chief Strategist",
          "tagline": "Don't let your dreams be dreams",
          "location": "Chicago, IL",
          "created_at": "2026-05-28T17:22:22.069Z",
          "updated_at": "2026-07-21T01:06:02.483Z",
          "email_address": "victor@honchodesign.com",
          "bio": "Don't let your dreams be dreams",
          "admin": true,
          "owner": true,
          "client": false,
          "employee": true,
          "time_zone": "America/Chicago",
          "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
          "company": {
            "id": 1033447817,
            "name": "Honcho Design"
          },
          "can_ping": true,
          "can_manage_projects": true,
          "can_manage_people": true,
          "can_access_timesheet": true,
          "can_access_hill_charts": true
        }
      ],
      "color": null,
      "cards_count": 0,
      "comment_count": 0,
      "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/lists/1069479838/cards.json"
    }
  ],
  "wormholes": [
    {
      "id": 1069480287,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-07-20T04:05:47.287Z",
      "updated_at": "2026-07-20T04:05:47.287Z",
      "title": "The Leto Locator › Card Table › Triage",
      "inherits_status": true,
      "type": "Kanban::Wormhole",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479833.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479833",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI4Nz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--dc0bb2723bf3371fb688607d2676f4c728702a9f.json",
      "parent": {
        "id": 1069479833,
        "title": "Card Table",
        "type": "Kanban::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958505/card_tables/1069479833.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/card_tables/1069479833"
      },
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "type": "Project"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-05-28T17:22:22.069Z",
        "updated_at": "2026-07-21T01:06:02.483Z",
        "email_address": "victor@honchodesign.com",
        "bio": "Don't let your dreams be dreams",
        "admin": true,
        "owner": true,
        "client": false,
        "employee": true,
        "time_zone": "America/Chicago",
        "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBMlkkT4=--5fe7b70fbee7a7f0e2e1e19df7579e5d880c753d/avatar",
        "company": {
          "id": 1033447817,
          "name": "Honcho Design"
        },
        "can_ping": true,
        "can_manage_projects": true,
        "can_manage_people": true,
        "can_access_timesheet": true,
        "can_access_hill_charts": true
      },
      "color": null,
      "linked": false,
      "destination_url": null
    }
  ]
}
```
<!-- END GET /card_tables/2.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/card_tables/2.json
```

The `wormholes` array lists the card table's wormholes. Wormholes are only listed for people who can reach the destination — a wormhole whose destination project the requester can't reach is omitted entirely. A wormhole is `linked` while its destination column still exists and its card table is enabled, and `destination_url` points at the destination column — it is `null` while the wormhole is unlinked. To send a card through a wormhole, pass the wormhole's `id` as the `column_id` when [moving a card](card_table_cards.md#move-a-card). Wormholes are managed through the [card table wormholes](card_table_wormholes.md) endpoints.

Move a card on the board
------------------------

* `POST /card_tables/2/moves.json` moves a card to a different column or position on the card table with ID `2`.

This is the same endpoint documented in the [card table columns][columns] section as **Move a column**. When moving a card, pass the card's recording ID as `source_id` and the destination column's recording ID as `target_id`.

**Required parameters**:

* `source_id` – the card recording ID to move.
* `target_id` – the destination column recording ID.
* `position` – zero-indexed position within the destination column.

This endpoint will return `204 No Content` if successful.

###### Example JSON Request

```json
{
  "source_id": 3,
  "target_id": 4,
  "position": 0
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"source_id": 3, "target_id": 4, "position": 0}' -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/card_tables/2/moves.json
```

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/card_tables/2.json` → [Get a card table](#get-a-card-table)
* `POST /buckets/1/card_tables/2/moves.json` → [Move a card on the board](#move-a-card-on-the-board)

[columns]: card_table_columns.md#move-a-column
