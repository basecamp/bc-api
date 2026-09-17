Card table templates
====================

Endpoints:

- [Get the card table templates](#get-the-card-table-templates)
- [Create a card table template](#create-a-card-table-template)
- [Create a card table from a template](#create-a-card-table-from-a-template)

Card table templates live in the same template library as [to-do list templates](template_library.md), in their own container.

Get the card table templates
----------------------------

* `GET /template_library/card_tables.json` returns the account's template library, the container that holds its card table templates, and its active card table templates in title order.

The bucket and card table IDs can be used with the existing [card table](card_tables.md), [column](card_table_columns.md), and [card](card_table_cards.md) endpoints to manage template contents. `kanban_boardset` is `null` for a library that has never held a card table template; creating the first one adds the container.

###### Example JSON Response
<!-- START GET /template_library/card_tables.json -->
```json
{
  "bucket": {
    "id": 2085958495,
    "name": "To-do List Templates",
    "type": "TemplateLibrary"
  },
  "kanban_boardset": {
    "id": 1069478891,
    "title": "Card Table Templates",
    "type": "Kanban::Boardset",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958495/boardsets/1069478891.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/boardsets/1069478891"
  },
  "card_tables": [
    {
      "id": 1069480295,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-09-12T08:21:52.130Z",
      "updated_at": "2026-09-12T08:21:52.238Z",
      "title": "Client onboarding",
      "inherits_status": true,
      "type": "Kanban::Board",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/1069480295.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/1069480295",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI5NT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1c03f5d8c2bb14bcbc8e01fceda94830530f2ad6.json",
      "parent": {
        "id": 1069478891,
        "title": "Card Table Templates",
        "type": "Kanban::Boardset",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958495/boardsets/1069478891.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/boardsets/1069478891"
      },
      "bucket": {
        "id": 2085958495,
        "name": "To-do List Templates",
        "type": "TemplateLibrary"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-09-12T08:17:09.797Z",
        "updated_at": "2026-09-12T08:17:10.372Z",
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
    }
  ]
}
```
<!-- END GET /template_library/card_tables.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
  https://3.basecampapi.com/$ACCOUNT_ID/template_library/card_tables.json
```

Create a card table template
----------------------------

* `POST /template_library/card_tables.json` creates a card table template with the default columns.

**Required parameters**: `name` of the template.

###### Example JSON Request

<!-- START POST PAYLOAD /template_library/card_tables.json -->
```json
{
  "name": "Client onboarding"
}
```
<!-- END POST PAYLOAD /template_library/card_tables.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"name":"Client onboarding"}' -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/template_library/card_tables.json
```

A successful request returns `201 Created` with the new [card table](card_tables.md). Its `parent` is the library's card table container, never the library's dock: a card table only counts as a template when it lives in that container, so a card table can't be added to the template library as a [dock tool](tools.md).

<!-- START POST /template_library/card_tables.json -->
```json
{
  "id": 1069480295,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-09-12T08:21:52.130Z",
  "updated_at": "2026-09-12T08:21:52.238Z",
  "title": "Client onboarding",
  "inherits_status": true,
  "type": "Kanban::Board",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/1069480295.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/1069480295",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI5NT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1c03f5d8c2bb14bcbc8e01fceda94830530f2ad6.json",
  "parent": {
    "id": 1069478891,
    "title": "Card Table Templates",
    "type": "Kanban::Boardset",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958495/boardsets/1069478891.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/boardsets/1069478891"
  },
  "bucket": {
    "id": 2085958495,
    "name": "To-do List Templates",
    "type": "TemplateLibrary"
  },
  "creator": {
    "id": 1049715913,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
    "name": "Victor Cooper",
    "personable_type": "User",
    "title": "Chief Strategist",
    "tagline": "Don't let your dreams be dreams",
    "location": "Chicago, IL",
    "created_at": "2026-09-12T08:17:09.797Z",
    "updated_at": "2026-09-12T03:17:10.372-05:00",
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
  "subscribers": [],
  "public_link_url": "https://3.basecampapi.com/195539477/buckets/2085958495/recordings/1069480295/publication",
  "lists": [
    {
      "id": 1069480296,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-09-12T08:21:52.142Z",
      "updated_at": "2026-09-12T08:21:52.142Z",
      "title": "Triage",
      "inherits_status": true,
      "type": "Kanban::Triage",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/columns/1069480296.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/columns/1069480296",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI5Nj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1d91948cb6130a83128e6e2b6d86f05abc6bd622.json",
      "parent": {
        "id": 1069480295,
        "title": "Client onboarding",
        "type": "Kanban::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/1069480295.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/1069480295"
      },
      "bucket": {
        "id": 2085958495,
        "name": "To-do List Templates",
        "type": "TemplateLibrary"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-09-12T08:17:09.797Z",
        "updated_at": "2026-09-12T08:17:10.372Z",
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
      "subscribers": [],
      "color": null,
      "cards_count": 0,
      "comment_count": 0,
      "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/lists/1069480296/cards.json"
    },
    {
      "id": 1069480297,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-09-12T08:21:52.191Z",
      "updated_at": "2026-09-12T08:21:52.191Z",
      "title": "Not now",
      "inherits_status": true,
      "type": "Kanban::NotNowColumn",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/columns/1069480297.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/columns/1069480297",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI5Nz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--f7f18821b60e3052ed7b30fe1b8e2fc627782fd4.json",
      "parent": {
        "id": 1069480295,
        "title": "Client onboarding",
        "type": "Kanban::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/1069480295.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/1069480295"
      },
      "bucket": {
        "id": 2085958495,
        "name": "To-do List Templates",
        "type": "TemplateLibrary"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-09-12T08:17:09.797Z",
        "updated_at": "2026-09-12T08:17:10.372Z",
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
      "subscribers": [],
      "color": null,
      "cards_count": 0,
      "comment_count": 0,
      "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/lists/1069480297/cards.json"
    },
    {
      "id": 1069480298,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-09-12T08:21:52.200Z",
      "updated_at": "2026-09-12T08:21:52.200Z",
      "title": "Figuring it out",
      "inherits_status": true,
      "type": "Kanban::Column",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/columns/1069480298.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/columns/1069480298",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI5OD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--a03a94461126863f9a47d9fe095fbb50c9976a88.json",
      "position": 1,
      "parent": {
        "id": 1069480295,
        "title": "Client onboarding",
        "type": "Kanban::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/1069480295.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/1069480295"
      },
      "bucket": {
        "id": 2085958495,
        "name": "To-do List Templates",
        "type": "TemplateLibrary"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-09-12T08:17:09.797Z",
        "updated_at": "2026-09-12T08:17:10.372Z",
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
      "subscribers": [],
      "color": "purple",
      "cards_count": 0,
      "comment_count": 0,
      "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/lists/1069480298/cards.json"
    },
    {
      "id": 1069480299,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-09-12T08:21:52.219Z",
      "updated_at": "2026-09-12T08:21:52.219Z",
      "title": "In progress",
      "inherits_status": true,
      "type": "Kanban::Column",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/columns/1069480299.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/columns/1069480299",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDI5OT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--e050da945fd200ac948118efc116a17b6135f57f.json",
      "position": 2,
      "parent": {
        "id": 1069480295,
        "title": "Client onboarding",
        "type": "Kanban::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/1069480295.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/1069480295"
      },
      "bucket": {
        "id": 2085958495,
        "name": "To-do List Templates",
        "type": "TemplateLibrary"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-09-12T08:17:09.797Z",
        "updated_at": "2026-09-12T08:17:10.372Z",
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
      "subscribers": [],
      "color": "orange",
      "cards_count": 0,
      "comment_count": 0,
      "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/lists/1069480299/cards.json"
    },
    {
      "id": 1069480300,
      "status": "active",
      "visible_to_clients": false,
      "created_at": "2026-09-12T08:21:52.238Z",
      "updated_at": "2026-09-12T08:21:52.238Z",
      "title": "Done",
      "inherits_status": true,
      "type": "Kanban::DoneColumn",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/columns/1069480300.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/columns/1069480300",
      "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMwMD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--39c9513ef33d6a8a2fbc6c6c49a65fb77ebdc3a2.json",
      "parent": {
        "id": 1069480295,
        "title": "Client onboarding",
        "type": "Kanban::Board",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/1069480295.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958495/card_tables/1069480295"
      },
      "bucket": {
        "id": 2085958495,
        "name": "To-do List Templates",
        "type": "TemplateLibrary"
      },
      "creator": {
        "id": 1049715913,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkxMz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--e627c45e6b34e08862da23906862412620e4d5d9",
        "name": "Victor Cooper",
        "personable_type": "User",
        "title": "Chief Strategist",
        "tagline": "Don't let your dreams be dreams",
        "location": "Chicago, IL",
        "created_at": "2026-09-12T08:17:09.797Z",
        "updated_at": "2026-09-12T08:17:10.372Z",
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
      "subscribers": [],
      "color": null,
      "cards_count": 0,
      "comment_count": 0,
      "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958495/card_tables/lists/1069480300/cards.json"
    }
  ],
  "wormholes": []
}
```
<!-- END POST /template_library/card_tables.json -->

Create a card table from a template
-----------------------------------

* `POST /template_library/copies.json` starts copying a card table template onto a project's dock.

**Required parameters**:

* `template_recording_id` - the ID of a card table in the template library.
* `destination_project_id` - the ID of the [project](projects.md) to copy into. The card table lands on its dock.

A `destination_parent_id` naming the dock recording is accepted instead, for callers that already have one.

###### Example JSON Request

<!-- START POST PAYLOAD /template_library/copies.json (card table) -->
```json
{
  "template_recording_id": 1069480295,
  "destination_project_id": 2085958504
}
```
<!-- END POST PAYLOAD /template_library/copies.json (card table) -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"template_recording_id":1069480295,"destination_project_id":2085958504}' -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/template_library/copies.json
```

The copy resource, its people confirmation step, and polling work exactly as for a [to-do list template](template_library.md#create-a-to-do-list-from-a-template). A completed copy includes the new card table as `destination_card_table`:

<!-- START GET /template_library/copies/2.json (card table) -->
```json
{
  "id": 1,
  "status": "completed",
  "source_recording_id": 1069480295,
  "destination_parent_id": 1069479828,
  "url": "https://3.basecampapi.com/195539477/template_library/copies/1.json",
  "destination_card_table": {
    "id": 1069480307,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-09-12T08:21:55.232Z",
    "updated_at": "2026-09-12T08:21:55.560Z",
    "title": "Client onboarding",
    "inherits_status": true,
    "type": "Kanban::Board",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069480307.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069480307",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMwNz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--aeb04e386efa900d1be6e97dea023e3245f44646.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480307/subscription.json",
    "position": 8,
    "bucket": {
      "id": 2085958504,
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
      "created_at": "2026-09-12T08:17:09.797Z",
      "updated_at": "2026-09-12T08:17:10.372Z",
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
        "created_at": "2026-09-12T08:17:09.797Z",
        "updated_at": "2026-09-12T08:17:10.372Z",
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
    "public_link_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480307/publication",
    "lists": [
      {
        "id": 1069480308,
        "status": "active",
        "visible_to_clients": false,
        "created_at": "2026-09-12T08:21:55.271Z",
        "updated_at": "2026-09-12T08:21:55.280Z",
        "title": "Triage",
        "inherits_status": true,
        "type": "Kanban::Triage",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/columns/1069480308.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/columns/1069480308",
        "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMwOD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1441007829dbc9fc8dd210472f1509df0d20c4f3.json",
        "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480308/subscription.json",
        "parent": {
          "id": 1069480307,
          "title": "Client onboarding",
          "type": "Kanban::Board",
          "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069480307.json",
          "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069480307"
        },
        "bucket": {
          "id": 2085958504,
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
          "created_at": "2026-09-12T08:17:09.797Z",
          "updated_at": "2026-09-12T08:17:10.372Z",
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
            "created_at": "2026-09-12T08:17:09.797Z",
            "updated_at": "2026-09-12T08:17:10.372Z",
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
        "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/lists/1069480308/cards.json"
      },
      {
        "id": 1069480309,
        "status": "active",
        "visible_to_clients": false,
        "created_at": "2026-09-12T08:21:55.299Z",
        "updated_at": "2026-09-12T08:21:55.312Z",
        "title": "Not now",
        "inherits_status": true,
        "type": "Kanban::NotNowColumn",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/columns/1069480309.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/columns/1069480309",
        "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMwOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--7fc939445bf671bcc7340b0cd836ab622d0d15a2.json",
        "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480309/subscription.json",
        "parent": {
          "id": 1069480307,
          "title": "Client onboarding",
          "type": "Kanban::Board",
          "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069480307.json",
          "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069480307"
        },
        "bucket": {
          "id": 2085958504,
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
          "created_at": "2026-09-12T08:17:09.797Z",
          "updated_at": "2026-09-12T08:17:10.372Z",
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
            "created_at": "2026-09-12T08:17:09.797Z",
            "updated_at": "2026-09-12T08:17:10.372Z",
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
        "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/lists/1069480309/cards.json"
      },
      {
        "id": 1069480310,
        "status": "active",
        "visible_to_clients": false,
        "created_at": "2026-09-12T08:21:55.336Z",
        "updated_at": "2026-09-12T08:21:55.355Z",
        "title": "Figuring it out",
        "inherits_status": true,
        "type": "Kanban::Column",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/columns/1069480310.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/columns/1069480310",
        "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMxMD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--b191977e44bd8b6541605970bcc32a217739f277.json",
        "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480310/subscription.json",
        "position": 1,
        "parent": {
          "id": 1069480307,
          "title": "Client onboarding",
          "type": "Kanban::Board",
          "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069480307.json",
          "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069480307"
        },
        "bucket": {
          "id": 2085958504,
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
          "created_at": "2026-09-12T08:17:09.797Z",
          "updated_at": "2026-09-12T08:17:10.372Z",
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
            "created_at": "2026-09-12T08:17:09.797Z",
            "updated_at": "2026-09-12T08:17:10.372Z",
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
        "cards_count": 0,
        "comment_count": 0,
        "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/lists/1069480310/cards.json"
      },
      {
        "id": 1069480311,
        "status": "active",
        "visible_to_clients": false,
        "created_at": "2026-09-12T08:21:55.392Z",
        "updated_at": "2026-09-12T08:21:55.438Z",
        "title": "In progress",
        "inherits_status": true,
        "type": "Kanban::Column",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/columns/1069480311.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/columns/1069480311",
        "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMxMT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1316493d97fbabd8b36e6182478163aa85d528ce.json",
        "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480311/subscription.json",
        "position": 2,
        "parent": {
          "id": 1069480307,
          "title": "Client onboarding",
          "type": "Kanban::Board",
          "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069480307.json",
          "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069480307"
        },
        "bucket": {
          "id": 2085958504,
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
          "created_at": "2026-09-12T08:17:09.797Z",
          "updated_at": "2026-09-12T08:17:10.372Z",
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
            "created_at": "2026-09-12T08:17:09.797Z",
            "updated_at": "2026-09-12T08:17:10.372Z",
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
        "cards_count": 0,
        "comment_count": 0,
        "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/lists/1069480311/cards.json"
      },
      {
        "id": 1069480312,
        "status": "active",
        "visible_to_clients": false,
        "created_at": "2026-09-12T08:21:55.496Z",
        "updated_at": "2026-09-12T08:21:55.521Z",
        "title": "Done",
        "inherits_status": true,
        "type": "Kanban::DoneColumn",
        "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/columns/1069480312.json",
        "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/columns/1069480312",
        "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDMxMj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--3803ab4f4972d4bf8a0d324b084341e3e7b546a9.json",
        "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958504/recordings/1069480312/subscription.json",
        "parent": {
          "id": 1069480307,
          "title": "Client onboarding",
          "type": "Kanban::Board",
          "url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/1069480307.json",
          "app_url": "https://3.basecamp.com/195539477/buckets/2085958504/card_tables/1069480307"
        },
        "bucket": {
          "id": 2085958504,
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
          "created_at": "2026-09-12T08:17:09.797Z",
          "updated_at": "2026-09-12T08:17:10.372Z",
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
            "created_at": "2026-09-12T08:17:09.797Z",
            "updated_at": "2026-09-12T08:17:10.372Z",
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
        "cards_url": "https://3.basecampapi.com/195539477/buckets/2085958504/card_tables/lists/1069480312/cards.json"
      }
    ],
    "wormholes": []
  }
}
```
<!-- END GET /template_library/copies/2.json (card table) -->
