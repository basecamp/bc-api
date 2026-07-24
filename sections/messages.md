Messages
========

Endpoints:

- [Get messages](#get-messages)
- [Get a message](#get-a-message)
- [Create a message](#create-a-message)
- [Update a message](#update-a-message)
- [Pin a message](#pin-a-message)
- [Trash a message][1]

Get messages
------------

* `GET /message_boards/3/messages.json` will return a [paginated list][2] of active messages in the message board with ID of `3`.

To get the message board ID for a project, see the [Get message board][3] endpoint.

_Optional query parameters_:

* `sort` - Options: `created_at` or `updated_at`. Default: `created_at`.
* `direction` - Options: `desc` or `asc`. Default: `desc`.

###### Example JSON Response
<!-- START GET /message_boards/3/messages.json -->
```json
[
  {
    "id": 1069480022,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-05-14T18:52:00.000Z",
    "updated_at": "2026-07-21T00:01:12.850Z",
    "title": "Laptop high res glamour shots",
    "inherits_status": true,
    "type": "Message",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069480022.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069480022",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ4MDAyMj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--4f4ef75196ad916dbc020bb1720a11c3e27ff83c.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480022/subscription.json",
    "comments_count": 1,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480022/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069480022/boosts.json",
    "parent": {
      "id": 1069479828,
      "title": "Message Board",
      "type": "Message::Board",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/message_boards/1069479828.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/message_boards/1069479828"
    },
    "bucket": {
      "id": 2085958505,
      "name": "The Leto Laptop",
      "type": "Project"
    },
    "creator": {
      "id": 1049715929,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkyOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--d79103e78a10cd9f8ecda7470ea315674ac8a79a",
      "name": "Matt Donahue",
      "personable_type": "User",
      "title": "Global Data Strategist",
      "tagline": null,
      "location": null,
      "created_at": "2026-05-28T17:22:27.821Z",
      "updated_at": "2026-05-28T17:22:27.821Z",
      "email_address": "matt@honchodesign.com",
      "bio": null,
      "admin": false,
      "owner": false,
      "client": false,
      "employee": false,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBNlkkT4=--0f3c77d8c13069d514fd3f0ad694a67e426bad0f/avatar",
      "can_ping": true,
      "can_manage_projects": true,
      "can_manage_people": true,
      "can_access_timesheet": true,
      "can_access_hill_charts": true
    },
    "content": "Hey all, here are some high res shots of the laptop hardware that we can use. These are not public yet, so be careful with how you share them. We don't want any leaks at all with these images.<br><br><bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0NzU_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--60072a7f701afce5c5415c2f5b648edcde05e9f1\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/3243b8ef1545f2e08368bc6e8d6c529d54373466/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/3243b8ef1545f2e08368bc6e8d6c529d54373466/download/laptop_1\" filename=\"laptop_1\" filesize=\"14531\" width=\"630\" height=\"420\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/3243b8ef1545f2e08368bc6e8d6c529d54373466/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/3243b8ef1545f2e08368bc6e8d6c529d54373466/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/3243b8ef1545f2e08368bc6e8d6c529d54373466/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/3243b8ef1545f2e08368bc6e8d6c529d54373466/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/3243b8ef1545f2e08368bc6e8d6c529d54373466/previews/full\">\n  <figcaption>\n    laptop_1\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0NzY_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--78d6aeab5f5505ed418ed5425ba9a2d6c88969dd\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/cfd794c8fbfc72690a025c43d84b38039e634e46/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/cfd794c8fbfc72690a025c43d84b38039e634e46/download/laptop_2\" filename=\"laptop_2\" filesize=\"18545\" width=\"600\" height=\"337\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/cfd794c8fbfc72690a025c43d84b38039e634e46/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/cfd794c8fbfc72690a025c43d84b38039e634e46/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/cfd794c8fbfc72690a025c43d84b38039e634e46/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/cfd794c8fbfc72690a025c43d84b38039e634e46/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/cfd794c8fbfc72690a025c43d84b38039e634e46/previews/full\">\n  <figcaption>\n    laptop_2\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzc_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--6c08dffec34a6454ab069505cbe40744b95af86c\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/9e378b655648a83d179c5e1cea24229ce47d27fc/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/9e378b655648a83d179c5e1cea24229ce47d27fc/download/laptop_3\" filename=\"laptop_3\" filesize=\"11942\" width=\"610\" height=\"435\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/9e378b655648a83d179c5e1cea24229ce47d27fc/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/9e378b655648a83d179c5e1cea24229ce47d27fc/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/9e378b655648a83d179c5e1cea24229ce47d27fc/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/9e378b655648a83d179c5e1cea24229ce47d27fc/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/9e378b655648a83d179c5e1cea24229ce47d27fc/previews/full\">\n  <figcaption>\n    laptop_3\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzg_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--5ea06fe17cff52380f599939ee90060e2c1ad274\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/06ccb206c39b8e3733068755d92dec8950b9bbfc/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/06ccb206c39b8e3733068755d92dec8950b9bbfc/download/laptop_4\" filename=\"laptop_4\" filesize=\"10894\" width=\"700\" height=\"355\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/06ccb206c39b8e3733068755d92dec8950b9bbfc/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/06ccb206c39b8e3733068755d92dec8950b9bbfc/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/06ccb206c39b8e3733068755d92dec8950b9bbfc/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/06ccb206c39b8e3733068755d92dec8950b9bbfc/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/06ccb206c39b8e3733068755d92dec8950b9bbfc/previews/full\">\n  <figcaption>\n    laptop_4\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzk_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--38376bcaa1e52f3e344580ddaa112beba391b42a\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/61adc12477f400be55791300213409067b771974/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/61adc12477f400be55791300213409067b771974/download/laptop_5\" filename=\"laptop_5\" filesize=\"14497\" width=\"640\" height=\"427\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/61adc12477f400be55791300213409067b771974/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/61adc12477f400be55791300213409067b771974/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/61adc12477f400be55791300213409067b771974/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/61adc12477f400be55791300213409067b771974/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/61adc12477f400be55791300213409067b771974/previews/full\">\n  <figcaption>\n    laptop_5\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODA_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--db6d30f319fedea2072df5a9e533ae9b83372504\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/a82ccb835fbce9e23e92ce823bccaaf72eeba2e1/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/a82ccb835fbce9e23e92ce823bccaaf72eeba2e1/download/laptop_6\" filename=\"laptop_6\" filesize=\"9370\" width=\"520\" height=\"365\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/a82ccb835fbce9e23e92ce823bccaaf72eeba2e1/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/a82ccb835fbce9e23e92ce823bccaaf72eeba2e1/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/a82ccb835fbce9e23e92ce823bccaaf72eeba2e1/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/a82ccb835fbce9e23e92ce823bccaaf72eeba2e1/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/a82ccb835fbce9e23e92ce823bccaaf72eeba2e1/previews/full\">\n  <figcaption>\n    laptop_6\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODE_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--d2c070cd0872b6049fb79df6cd9ada7464e1757e\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/a013c0ed4add669675d3ad8e3580be2d8dcb340e/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/a013c0ed4add669675d3ad8e3580be2d8dcb340e/download/laptop_7\" filename=\"laptop_7\" filesize=\"48646\" width=\"700\" height=\"462\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/a013c0ed4add669675d3ad8e3580be2d8dcb340e/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/a013c0ed4add669675d3ad8e3580be2d8dcb340e/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/a013c0ed4add669675d3ad8e3580be2d8dcb340e/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/a013c0ed4add669675d3ad8e3580be2d8dcb340e/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/a013c0ed4add669675d3ad8e3580be2d8dcb340e/previews/full\">\n  <figcaption>\n    laptop_7\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODI_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--98023c4f0b4cdf0ff6ef6395ea0163aa774a3444\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/76a4c2a04ac3754f3e77f48a6af356d69f41100f/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/76a4c2a04ac3754f3e77f48a6af356d69f41100f/download/laptop_8\" filename=\"laptop_8\" filesize=\"12904\" width=\"540\" height=\"334\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/76a4c2a04ac3754f3e77f48a6af356d69f41100f/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/76a4c2a04ac3754f3e77f48a6af356d69f41100f/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/76a4c2a04ac3754f3e77f48a6af356d69f41100f/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/76a4c2a04ac3754f3e77f48a6af356d69f41100f/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/76a4c2a04ac3754f3e77f48a6af356d69f41100f/previews/full\">\n  <figcaption>\n    laptop_8\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODM_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--fbc4cc6ef8b067a79efaaf026444744a0a4b4393\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/1ab1187d4845ac5dd50778f1b15e81a1ed80b884/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/1ab1187d4845ac5dd50778f1b15e81a1ed80b884/download/laptop_9\" filename=\"laptop_9\" filesize=\"30919\" width=\"700\" height=\"394\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/1ab1187d4845ac5dd50778f1b15e81a1ed80b884/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/1ab1187d4845ac5dd50778f1b15e81a1ed80b884/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/1ab1187d4845ac5dd50778f1b15e81a1ed80b884/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/1ab1187d4845ac5dd50778f1b15e81a1ed80b884/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/1ab1187d4845ac5dd50778f1b15e81a1ed80b884/previews/full\">\n  <figcaption>\n    laptop_9\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODQ_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--c6b88bec2c004b4dfafbdc8a30b181d31da08db6\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/500197d2736c33318b55340cf67dab8c7dd5ab4d/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/500197d2736c33318b55340cf67dab8c7dd5ab4d/download/laptop_10\" filename=\"laptop_10\" filesize=\"7014\" width=\"620\" height=\"413\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/500197d2736c33318b55340cf67dab8c7dd5ab4d/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/500197d2736c33318b55340cf67dab8c7dd5ab4d/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/500197d2736c33318b55340cf67dab8c7dd5ab4d/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/500197d2736c33318b55340cf67dab8c7dd5ab4d/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/500197d2736c33318b55340cf67dab8c7dd5ab4d/previews/full\">\n  <figcaption>\n    laptop_10\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODU_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--419dc4a33710d0001fac8cf007bcf22bd187719b\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/15936fb62eb77c481f37191dd4ca76a7a9adac8d/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/15936fb62eb77c481f37191dd4ca76a7a9adac8d/download/laptop_11\" filename=\"laptop_11\" filesize=\"2693\" width=\"620\" height=\"413\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/15936fb62eb77c481f37191dd4ca76a7a9adac8d/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/15936fb62eb77c481f37191dd4ca76a7a9adac8d/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/15936fb62eb77c481f37191dd4ca76a7a9adac8d/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/15936fb62eb77c481f37191dd4ca76a7a9adac8d/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/15936fb62eb77c481f37191dd4ca76a7a9adac8d/previews/full\">\n  <figcaption>\n    laptop_11\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODY_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--58c62d34383210581f1fc79361a50307607df6f7\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/15a92aa218d272e909ad9328566672cce66b95d8/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/15a92aa218d272e909ad9328566672cce66b95d8/download/laptop_12\" filename=\"laptop_12\" filesize=\"23152\" width=\"700\" height=\"387\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/15a92aa218d272e909ad9328566672cce66b95d8/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/15a92aa218d272e909ad9328566672cce66b95d8/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/15a92aa218d272e909ad9328566672cce66b95d8/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/15a92aa218d272e909ad9328566672cce66b95d8/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/15a92aa218d272e909ad9328566672cce66b95d8/previews/full\">\n  <figcaption>\n    laptop_12\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODc_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--0feed7e80ebc54613d3b860ddec93492919ff470\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/8b89c0c9411d682b81b3e955a579862e438978c3/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/8b89c0c9411d682b81b3e955a579862e438978c3/download/laptop_13\" filename=\"laptop_13\" filesize=\"27751\" width=\"700\" height=\"466\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/8b89c0c9411d682b81b3e955a579862e438978c3/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/8b89c0c9411d682b81b3e955a579862e438978c3/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/8b89c0c9411d682b81b3e955a579862e438978c3/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/8b89c0c9411d682b81b3e955a579862e438978c3/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/8b89c0c9411d682b81b3e955a579862e438978c3/previews/full\">\n  <figcaption>\n    laptop_13\n  </figcaption>\n</figure></bc-attachment> <bc-attachment sgid=\"BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODg_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--7310094b0e002f2e888252d45ca93a224af64cd1\" content-type=\"image/avif\" url=\"https://3.basecampapi.com/195539477/blobs/10579991420c97cb6891a59c47eb848d4cb5fc8b/previews/full\" href=\"https://storage.3.basecamp.com/195539477/blobs/10579991420c97cb6891a59c47eb848d4cb5fc8b/download/laptop_14\" filename=\"laptop_14\" filesize=\"15988\" width=\"700\" height=\"466\" previewable=\"true\" data-bridge-previewable=\"true\" dir=\"auto\"><figure>\n    <img srcset=\"https://3.basecampapi.com/195539477/blobs/10579991420c97cb6891a59c47eb848d4cb5fc8b/previews/full?dppx=2 2x, https://3.basecampapi.com/195539477/blobs/10579991420c97cb6891a59c47eb848d4cb5fc8b/previews/full?dppx=1 1x, https://3.basecampapi.com/195539477/blobs/10579991420c97cb6891a59c47eb848d4cb5fc8b/previews/full?dppx=3 3x, https://3.basecampapi.com/195539477/blobs/10579991420c97cb6891a59c47eb848d4cb5fc8b/previews/full?dppx=4 4x\" loading=\"eager\" src=\"https://3.basecampapi.com/195539477/blobs/10579991420c97cb6891a59c47eb848d4cb5fc8b/previews/full\">\n  <figcaption>\n    laptop_14\n  </figcaption>\n</figure></bc-attachment>",
    "content_attachments": [
      {
        "id": 1046628475,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0NzU_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--60072a7f701afce5c5415c2f5b648edcde05e9f1",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0NzU_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--60072a7f701afce5c5415c2f5b648edcde05e9f1",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0NzU_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--60072a7f701afce5c5415c2f5b648edcde05e9f1.json",
        "caption": null,
        "byte_size": 14531,
        "content_type": "image/avif",
        "width": 630,
        "height": 420,
        "key": "3243b8ef1545f2e08368bc6e8d6c529d54373466",
        "filename": "laptop_1",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/3243b8ef1545f2e08368bc6e8d6c529d54373466/download/laptop_1",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/3243b8ef1545f2e08368bc6e8d6c529d54373466/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/3243b8ef1545f2e08368bc6e8d6c529d54373466/previews/card"
      },
      {
        "id": 1046628476,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0NzY_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--78d6aeab5f5505ed418ed5425ba9a2d6c88969dd",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0NzY_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--78d6aeab5f5505ed418ed5425ba9a2d6c88969dd",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0NzY_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--78d6aeab5f5505ed418ed5425ba9a2d6c88969dd.json",
        "caption": null,
        "byte_size": 18545,
        "content_type": "image/avif",
        "width": 600,
        "height": 337,
        "key": "cfd794c8fbfc72690a025c43d84b38039e634e46",
        "filename": "laptop_2",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/cfd794c8fbfc72690a025c43d84b38039e634e46/download/laptop_2",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/cfd794c8fbfc72690a025c43d84b38039e634e46/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/cfd794c8fbfc72690a025c43d84b38039e634e46/previews/card"
      },
      {
        "id": 1046628477,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzc_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--6c08dffec34a6454ab069505cbe40744b95af86c",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzc_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--6c08dffec34a6454ab069505cbe40744b95af86c",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzc_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--6c08dffec34a6454ab069505cbe40744b95af86c.json",
        "caption": null,
        "byte_size": 11942,
        "content_type": "image/avif",
        "width": 610,
        "height": 435,
        "key": "9e378b655648a83d179c5e1cea24229ce47d27fc",
        "filename": "laptop_3",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/9e378b655648a83d179c5e1cea24229ce47d27fc/download/laptop_3",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/9e378b655648a83d179c5e1cea24229ce47d27fc/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/9e378b655648a83d179c5e1cea24229ce47d27fc/previews/card"
      },
      {
        "id": 1046628478,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzg_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--5ea06fe17cff52380f599939ee90060e2c1ad274",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzg_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--5ea06fe17cff52380f599939ee90060e2c1ad274",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzg_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--5ea06fe17cff52380f599939ee90060e2c1ad274.json",
        "caption": null,
        "byte_size": 10894,
        "content_type": "image/avif",
        "width": 700,
        "height": 355,
        "key": "06ccb206c39b8e3733068755d92dec8950b9bbfc",
        "filename": "laptop_4",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/06ccb206c39b8e3733068755d92dec8950b9bbfc/download/laptop_4",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/06ccb206c39b8e3733068755d92dec8950b9bbfc/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/06ccb206c39b8e3733068755d92dec8950b9bbfc/previews/card"
      },
      {
        "id": 1046628479,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzk_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--38376bcaa1e52f3e344580ddaa112beba391b42a",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzk_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--38376bcaa1e52f3e344580ddaa112beba391b42a",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0Nzk_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--38376bcaa1e52f3e344580ddaa112beba391b42a.json",
        "caption": null,
        "byte_size": 14497,
        "content_type": "image/avif",
        "width": 640,
        "height": 427,
        "key": "61adc12477f400be55791300213409067b771974",
        "filename": "laptop_5",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/61adc12477f400be55791300213409067b771974/download/laptop_5",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/61adc12477f400be55791300213409067b771974/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/61adc12477f400be55791300213409067b771974/previews/card"
      },
      {
        "id": 1046628480,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODA_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--db6d30f319fedea2072df5a9e533ae9b83372504",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODA_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--db6d30f319fedea2072df5a9e533ae9b83372504",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODA_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--db6d30f319fedea2072df5a9e533ae9b83372504.json",
        "caption": null,
        "byte_size": 9370,
        "content_type": "image/avif",
        "width": 520,
        "height": 365,
        "key": "a82ccb835fbce9e23e92ce823bccaaf72eeba2e1",
        "filename": "laptop_6",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/a82ccb835fbce9e23e92ce823bccaaf72eeba2e1/download/laptop_6",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/a82ccb835fbce9e23e92ce823bccaaf72eeba2e1/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/a82ccb835fbce9e23e92ce823bccaaf72eeba2e1/previews/card"
      },
      {
        "id": 1046628481,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODE_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--d2c070cd0872b6049fb79df6cd9ada7464e1757e",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODE_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--d2c070cd0872b6049fb79df6cd9ada7464e1757e",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODE_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--d2c070cd0872b6049fb79df6cd9ada7464e1757e.json",
        "caption": null,
        "byte_size": 48646,
        "content_type": "image/avif",
        "width": 700,
        "height": 462,
        "key": "a013c0ed4add669675d3ad8e3580be2d8dcb340e",
        "filename": "laptop_7",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/a013c0ed4add669675d3ad8e3580be2d8dcb340e/download/laptop_7",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/a013c0ed4add669675d3ad8e3580be2d8dcb340e/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/a013c0ed4add669675d3ad8e3580be2d8dcb340e/previews/card"
      },
      {
        "id": 1046628482,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODI_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--98023c4f0b4cdf0ff6ef6395ea0163aa774a3444",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODI_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--98023c4f0b4cdf0ff6ef6395ea0163aa774a3444",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODI_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--98023c4f0b4cdf0ff6ef6395ea0163aa774a3444.json",
        "caption": null,
        "byte_size": 12904,
        "content_type": "image/avif",
        "width": 540,
        "height": 334,
        "key": "76a4c2a04ac3754f3e77f48a6af356d69f41100f",
        "filename": "laptop_8",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/76a4c2a04ac3754f3e77f48a6af356d69f41100f/download/laptop_8",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/76a4c2a04ac3754f3e77f48a6af356d69f41100f/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/76a4c2a04ac3754f3e77f48a6af356d69f41100f/previews/card"
      },
      {
        "id": 1046628483,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODM_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--fbc4cc6ef8b067a79efaaf026444744a0a4b4393",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODM_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--fbc4cc6ef8b067a79efaaf026444744a0a4b4393",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODM_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--fbc4cc6ef8b067a79efaaf026444744a0a4b4393.json",
        "caption": null,
        "byte_size": 30919,
        "content_type": "image/avif",
        "width": 700,
        "height": 394,
        "key": "1ab1187d4845ac5dd50778f1b15e81a1ed80b884",
        "filename": "laptop_9",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/1ab1187d4845ac5dd50778f1b15e81a1ed80b884/download/laptop_9",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/1ab1187d4845ac5dd50778f1b15e81a1ed80b884/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/1ab1187d4845ac5dd50778f1b15e81a1ed80b884/previews/card"
      },
      {
        "id": 1046628484,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODQ_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--c6b88bec2c004b4dfafbdc8a30b181d31da08db6",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODQ_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--c6b88bec2c004b4dfafbdc8a30b181d31da08db6",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODQ_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--c6b88bec2c004b4dfafbdc8a30b181d31da08db6.json",
        "caption": null,
        "byte_size": 7014,
        "content_type": "image/avif",
        "width": 620,
        "height": 413,
        "key": "500197d2736c33318b55340cf67dab8c7dd5ab4d",
        "filename": "laptop_10",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/500197d2736c33318b55340cf67dab8c7dd5ab4d/download/laptop_10",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/500197d2736c33318b55340cf67dab8c7dd5ab4d/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/500197d2736c33318b55340cf67dab8c7dd5ab4d/previews/card"
      },
      {
        "id": 1046628485,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODU_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--419dc4a33710d0001fac8cf007bcf22bd187719b",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODU_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--419dc4a33710d0001fac8cf007bcf22bd187719b",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODU_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--419dc4a33710d0001fac8cf007bcf22bd187719b.json",
        "caption": null,
        "byte_size": 2693,
        "content_type": "image/avif",
        "width": 620,
        "height": 413,
        "key": "15936fb62eb77c481f37191dd4ca76a7a9adac8d",
        "filename": "laptop_11",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/15936fb62eb77c481f37191dd4ca76a7a9adac8d/download/laptop_11",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/15936fb62eb77c481f37191dd4ca76a7a9adac8d/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/15936fb62eb77c481f37191dd4ca76a7a9adac8d/previews/card"
      },
      {
        "id": 1046628486,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODY_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--58c62d34383210581f1fc79361a50307607df6f7",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODY_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--58c62d34383210581f1fc79361a50307607df6f7",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODY_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--58c62d34383210581f1fc79361a50307607df6f7.json",
        "caption": null,
        "byte_size": 23152,
        "content_type": "image/avif",
        "width": 700,
        "height": 387,
        "key": "15a92aa218d272e909ad9328566672cce66b95d8",
        "filename": "laptop_12",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/15a92aa218d272e909ad9328566672cce66b95d8/download/laptop_12",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/15a92aa218d272e909ad9328566672cce66b95d8/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/15a92aa218d272e909ad9328566672cce66b95d8/previews/card"
      },
      {
        "id": 1046628487,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODc_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--0feed7e80ebc54613d3b860ddec93492919ff470",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODc_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--0feed7e80ebc54613d3b860ddec93492919ff470",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODc_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--0feed7e80ebc54613d3b860ddec93492919ff470.json",
        "caption": null,
        "byte_size": 27751,
        "content_type": "image/avif",
        "width": 700,
        "height": 466,
        "key": "8b89c0c9411d682b81b3e955a579862e438978c3",
        "filename": "laptop_13",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/8b89c0c9411d682b81b3e955a579862e438978c3/download/laptop_13",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/8b89c0c9411d682b81b3e955a579862e438978c3/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/8b89c0c9411d682b81b3e955a579862e438978c3/previews/card"
      },
      {
        "id": 1046628488,
        "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODg_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--7310094b0e002f2e888252d45ca93a224af64cd1",
        "sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODg_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--7310094b0e002f2e888252d45ca93a224af64cd1",
        "status_url": "https://3.basecampapi.com/195539477/attachments/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiL2dpZDovL2JjMy9BdHRhY2htZW50LzEwNDY2Mjg0ODg_ZXhwaXJlc19pbgY7AFRJIghwdXIGOwBUSSIPYXR0YWNoYWJsZQY7AFQ=--7310094b0e002f2e888252d45ca93a224af64cd1.json",
        "caption": null,
        "byte_size": 15988,
        "content_type": "image/avif",
        "width": 700,
        "height": 466,
        "key": "10579991420c97cb6891a59c47eb848d4cb5fc8b",
        "filename": "laptop_14",
        "download_url": "https://storage.3.basecamp.com/195539477/blobs/10579991420c97cb6891a59c47eb848d4cb5fc8b/download/laptop_14",
        "previewable": true,
        "preview_url": "https://3.basecampapi.com/195539477/blobs/10579991420c97cb6891a59c47eb848d4cb5fc8b/previews/full",
        "thumbnail_url": "https://3.basecampapi.com/195539477/blobs/10579991420c97cb6891a59c47eb848d4cb5fc8b/previews/card"
      }
    ],
    "subject": "Laptop high res glamour shots"
  }
]
```
<!-- END GET /message_boards/3/messages.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/message_boards/3/messages.json
```


Get a message
-------------

* `GET /messages/2.json` will return the message with an ID of `2`.

###### Example JSON Response
<!-- START GET /messages/2.json -->
```json
{
  "id": 1069479842,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-04-14T21:02:00.000Z",
  "updated_at": "2026-07-21T01:05:34.577Z",
  "title": "We won Leto!",
  "inherits_status": true,
  "type": "Message",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958505/messages/1069479842.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/messages/1069479842",
  "bookmark_url": "https://3.basecamp.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg0Mj9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--1708f8c9adb5dd70ebcc6837a0c054bacaf792fe",
  "subscription_url": "https://3.basecamp.com/195539477/buckets/2085958505/recordings/1069479842/subscription",
  "comments_count": 10,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479842/comments.json",
  "boosts_count": 5,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958505/recordings/1069479842/boosts.json",
  "parent": {
    "id": 1069479828,
    "title": "Message Board",
    "type": "Message::Board",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958505/message_boards/1069479828.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/message_boards/1069479828"
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
    "updated_at": "2026-07-21T00:05:55.167Z",
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
  "content": "Hey guys,<br><br>We won the Leto account! This is huge for us, it really marks a turning point for the company.<br><br>As you know we've been pursuing bigger clients in the consumer space, but we've done so carefully. We've never been about getting the biggest clients - those are easy to get. We've been trying to get the best clients for us - ones that will challenge us, grow us, make us better, and ultimately giving us a platform to show how awesome you guys all are. And now we have that!<br><br>A big congrats to everyone who worked so hard to make this happen, and now the fun really begins. Most of the pitch team will stay on as leading members of the first project, the Leto Microsite.<br><br>Again, great job everyone, and let's go kick some more butt!<br><br>-Victor",
  "content_attachments": [],
  "subject": "We won Leto!"
}
```
<!-- END GET /messages/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/messages/2.json
```


Create a message
----------------

* `POST /message_boards/3/messages.json` creates a message under the message board with an ID of `3`.

**Required parameters**: `subject` as the title of the message.

_Optional parameters_:

* `status` — set to `active` to publish the message immediately. **When `status` is omitted the message is created as a draft** (it defaults to `drafted`); a draft is not posted and notifies no one until you publish it. See [Publishing a draft](#publishing-a-draft).
* `content` as the body of the message. See our [Rich text guide][4] for what HTML tags are allowed.
* `category_id` to set a type for the message. To get a list of all the message types for a project, see the [Get message types][5] endpoint. 
* `subscriptions` an array of people IDs to be notified of the new message when it's posted and subscribed to it. If not present, all people on the project will be notified and subscribed.
* `visible_to_clients` - top-level boolean. When the project has clients enabled, whether the message is visible to them. Defaults to `false` (team callers creating directly under the docked tool); a **client** caller always creates client-visible records. See [Client visibility][client_visibility] to change it after creation.

This endpoint will return `201 Created` with the current JSON representation of the message if the creation was a success. See the [Get a message](#get-a-message) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "subject": "Kickoff",
  "content": "<div><strong>Welcome to Basecamp, everyone.</strong></div>",
  "status": "active"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"subject":"Kickoff","content":"<div><strong>Welcome to Basecamp, everyone.</strong></div>","status":"active"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/message_boards/3/messages.json
```


Update a message
----------------

* `PUT /messages/2.json` allows changing the `subject`, `content` and `category_id` of the message with an ID of `2`.

This endpoint will return `200 OK` with the current JSON representation of the message if the update was a success. See the [Get a message](#get-a-message) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "subject": "Spin-down",
  "content": "<div><strong>Oops, we lost that client.</strong></div>"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"subject":"Spin-down","content":"<div><strong>Oops, we lost that client.</strong></div>"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/messages/2.json
```

Publishing a draft
------------------

Publish a [draft](drafts.md) message by updating it with `status` set to `active`:

```json
{ "status": "active" }
```

A message update **merges** the fields you send, so you don't need to resend `subject` or `content` — the draft's existing content is preserved.

Publishing is what actually posts the message, and it happens exactly once. It records a single publication event; once the resulting `Event::RelayJob` runs, each subscriber who should hear about the message receives exactly one notification. Creating or re-saving a draft notifies no one — only publishing does. (Documents publish the same way; see [Publishing a draft](documents.md#publishing-a-draft) in the documents section.)


Pin a message
----------------

* `POST /recordings/2/pin.json` pins the message with ID `2`.
* `DELETE /recordings/2/pin.json` unpins the message with ID `2`.

This endpoint will return `204 No Content` if the operation was a success.

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X POST \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/pin.json
```
```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -X DELETE \
  https://3.basecampapi.com/$ACCOUNT_ID/recordings/2/pin.json
```


Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/message_boards/3/messages.json` → [Get messages](#get-messages)
* `GET /buckets/1/messages/2.json` → [Get a message](#get-a-message)
* `POST /buckets/1/message_boards/3/messages.json` → [Create a message](#create-a-message)
* `PUT /buckets/1/messages/2.json` → [Update a message](#update-a-message)
* `POST /buckets/1/recordings/2/pin.json` → [Pin a message](#pin-a-message)
* `DELETE /buckets/1/recordings/2/pin.json` → [Pin a message](#pin-a-message)

[1]: recordings.md#trash-a-recording
[2]: ../README.md#pagination
[3]: message_boards.md#message-boards
[4]: rich_text.md
[5]: message_types.md#get-message-types
[client_visibility]: client_visibility.md
