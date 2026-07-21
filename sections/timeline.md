Timeline
========

The timeline shows recent activity across your Basecamp account or within a specific project. It provides a chronological feed of events like messages posted, to-dos completed, files uploaded, and more.

Endpoints:

- [Get timeline](#get-timeline)
- [Get project timeline](#get-project-timeline)
- [Get person's timeline](#get-persons-timeline)

Get timeline
------------

* `GET /reports/progress.json` will return a [paginated list][pagination] of timeline events across all projects the authenticated user can access.

###### Example JSON Response
<!-- START GET /reports/progress.json -->
```json
[
  {
    "id": 1052474000,
    "created_at": "2026-07-21T01:05:54.364Z",
    "kind": "project_access_changed",
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
    "action": "Victor C. changed who can access this project",
    "target": null,
    "title": "Victor C. changed who can access this project",
    "summary_excerpt": "Amy Rivera was granted access.",
    "avatars_sample": [],
    "bucket": {
      "id": 2085958505,
      "name": "The Leto Laptop",
      "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
      "app_url": "https://3.basecamp.com/195539477/projects/2085958505"
    }
  },
  {
    "id": 1052474002,
    "created_at": "2026-07-21T01:05:55.290Z",
    "kind": "project_access_changed",
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
    "action": "Victor C. changed who can access this project",
    "target": null,
    "title": "Victor C. changed who can access this project",
    "summary_excerpt": "Steve Marsh was granted access.",
    "avatars_sample": [],
    "bucket": {
      "id": 2085958505,
      "name": "The Leto Laptop",
      "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
      "app_url": "https://3.basecamp.com/195539477/projects/2085958505"
    }
  },
  {
    "id": 1052473983,
    "created_at": "2026-07-21T01:05:46.075Z",
    "kind": "todo_created",
    "parent_recording_id": 1069480414,
    "url": "https://3.basecampapi.com/195539477/buckets/2085958514/todos/1069480417.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/todos/1069480417",
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
    "action": "Victor C. added a to-do",
    "target": "First things first",
    "title": "On “First things first”, Victor C. added",
    "summary_excerpt": "Install ShipShape",
    "avatars_sample": [],
    "bucket": {
      "id": 2085958514,
      "name": "New project from template",
      "url": "https://3.basecampapi.com/195539477/projects/2085958514.json",
      "app_url": "https://3.basecamp.com/195539477/projects/2085958514"
    },
    "attachments": []
  },
  {
    "id": 1052473982,
    "created_at": "2026-07-21T01:05:45.993Z",
    "kind": "todo_created",
    "parent_recording_id": 1069480414,
    "url": "https://3.basecampapi.com/195539477/buckets/2085958514/todos/1069480416.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/todos/1069480416",
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
    "action": "Victor C. added a to-do",
    "target": "First things first",
    "title": "On “First things first”, Victor C. added",
    "summary_excerpt": "Talk to Jerry about holidays",
    "avatars_sample": [],
    "bucket": {
      "id": 2085958514,
      "name": "New project from template",
      "url": "https://3.basecampapi.com/195539477/projects/2085958514.json",
      "app_url": "https://3.basecamp.com/195539477/projects/2085958514"
    },
    "attachments": []
  },
  {
    "id": 1052473981,
    "created_at": "2026-07-21T01:05:45.807Z",
    "kind": "todo_created",
    "parent_recording_id": 1069480414,
    "url": "https://3.basecampapi.com/195539477/buckets/2085958514/todos/1069480415.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/todos/1069480415",
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
    "action": "Victor C. added a to-do",
    "target": "First things first",
    "title": "On “First things first”, Victor C. added",
    "summary_excerpt": "Talk to Cheryl about benefits",
    "avatars_sample": [],
    "bucket": {
      "id": 2085958514,
      "name": "New project from template",
      "url": "https://3.basecampapi.com/195539477/projects/2085958514.json",
      "app_url": "https://3.basecamp.com/195539477/projects/2085958514"
    },
    "attachments": []
  }
]
```
<!-- END GET /reports/progress.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/reports/progress.json
```

Get project timeline
--------------------

* `GET /projects/1/timeline.json` will return a [paginated list][pagination] of timeline events in the project with an ID of `1`.

###### Example JSON Response
<!-- START GET /projects/1/timeline.json -->
```json
[
  {
    "id": 1052474002,
    "created_at": "2026-07-21T01:05:55.290Z",
    "kind": "project_access_changed",
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
    "action": "Victor C. changed who can access this project",
    "target": null,
    "title": "Victor C. changed who can access this project",
    "summary_excerpt": "Steve Marsh was granted access.",
    "avatars_sample": [],
    "bucket": {
      "id": 2085958505,
      "name": "The Leto Laptop",
      "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
      "app_url": "https://3.basecamp.com/195539477/projects/2085958505"
    }
  },
  {
    "id": 1052474000,
    "created_at": "2026-07-21T01:05:54.364Z",
    "kind": "project_access_changed",
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
    "action": "Victor C. changed who can access this project",
    "target": null,
    "title": "Victor C. changed who can access this project",
    "summary_excerpt": "Amy Rivera was granted access.",
    "avatars_sample": [],
    "bucket": {
      "id": 2085958505,
      "name": "The Leto Laptop",
      "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
      "app_url": "https://3.basecamp.com/195539477/projects/2085958505"
    }
  }
]
```
<!-- END GET /projects/1/timeline.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/projects/1/timeline.json
```

Get person's timeline
---------------------

* `GET /reports/users/progress/1.json` will return a JSON object containing the person plus a [paginated list][pagination] (`events`) of timeline events created by the person with an ID of `1`.

###### Example JSON Response
<!-- START GET /reports/users/progress/1.json -->
```json
{
  "person": {
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
  "events": [
    {
      "id": 1052474000,
      "created_at": "2026-07-21T01:05:54.364Z",
      "kind": "project_access_changed",
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
      "action": "Victor C. changed who can access this project",
      "target": null,
      "title": "Victor C. changed who can access this project",
      "summary_excerpt": "Amy Rivera was granted access.",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958505"
      }
    },
    {
      "id": 1052474002,
      "created_at": "2026-07-21T01:05:55.290Z",
      "kind": "project_access_changed",
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
      "action": "Victor C. changed who can access this project",
      "target": null,
      "title": "Victor C. changed who can access this project",
      "summary_excerpt": "Steve Marsh was granted access.",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958505"
      }
    },
    {
      "id": 1052473983,
      "created_at": "2026-07-21T01:05:46.075Z",
      "kind": "todo_created",
      "parent_recording_id": 1069480414,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958514/todos/1069480417.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/todos/1069480417",
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
      "action": "Victor C. added a to-do",
      "target": "First things first",
      "title": "On “First things first”, Victor C. added",
      "summary_excerpt": "Install ShipShape",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958514,
        "name": "New project from template",
        "url": "https://3.basecampapi.com/195539477/projects/2085958514.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958514"
      },
      "attachments": []
    },
    {
      "id": 1052473982,
      "created_at": "2026-07-21T01:05:45.993Z",
      "kind": "todo_created",
      "parent_recording_id": 1069480414,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958514/todos/1069480416.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/todos/1069480416",
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
      "action": "Victor C. added a to-do",
      "target": "First things first",
      "title": "On “First things first”, Victor C. added",
      "summary_excerpt": "Talk to Jerry about holidays",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958514,
        "name": "New project from template",
        "url": "https://3.basecampapi.com/195539477/projects/2085958514.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958514"
      },
      "attachments": []
    },
    {
      "id": 1052473981,
      "created_at": "2026-07-21T01:05:45.807Z",
      "kind": "todo_created",
      "parent_recording_id": 1069480414,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958514/todos/1069480415.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958514/todos/1069480415",
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
      "action": "Victor C. added a to-do",
      "target": "First things first",
      "title": "On “First things first”, Victor C. added",
      "summary_excerpt": "Talk to Cheryl about benefits",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958514,
        "name": "New project from template",
        "url": "https://3.basecampapi.com/195539477/projects/2085958514.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958514"
      },
      "attachments": []
    },
    {
      "id": 1052473975,
      "created_at": "2026-07-21T01:05:45.365Z",
      "kind": "dock_created",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958514/dock.json",
      "app_url": "https://3.basecamp.com/195539477/projects/2085958514",
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
      "action": "Victor C. started a new project called New project from template",
      "target": "New project from template",
      "title": "Victor C. started a new project called “New project from template”",
      "summary_excerpt": null,
      "avatars_sample": [],
      "bucket": {
        "id": 2085958514,
        "name": "New project from template",
        "url": "https://3.basecampapi.com/195539477/projects/2085958514.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958514"
      },
      "attachments": []
    },
    {
      "id": 1052473966,
      "created_at": "2026-07-21T01:05:29.832Z",
      "kind": "todo_completed",
      "parent_recording_id": 1069479863,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todos/1069480405.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todos/1069480405",
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
      "action": "Victor C. checked off a to-do",
      "target": "Background and research",
      "title": "On “Background and research”, Victor C. checked off",
      "summary_excerpt": "Confirm the launch-party caterer",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958505"
      },
      "attachments": []
    },
    {
      "id": 1052473964,
      "created_at": "2026-07-21T01:05:28.944Z",
      "kind": "todo_created",
      "parent_recording_id": 1069479863,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/todos/1069480405.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/todos/1069480405",
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
      "action": "Victor C. added a to-do",
      "target": "Background and research",
      "title": "On “Background and research”, Victor C. added",
      "summary_excerpt": "Confirm the launch-party caterer",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958505"
      },
      "attachments": []
    },
    {
      "id": 1052473934,
      "created_at": "2026-07-21T00:05:40.489Z",
      "kind": "project_access_changed",
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
      "action": "Victor C. changed who can access this project",
      "target": null,
      "title": "Victor C. changed who can access this project",
      "summary_excerpt": "Steve Marsh was granted access.",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958505"
      }
    },
    {
      "id": 1052473932,
      "created_at": "2026-07-21T00:05:38.268Z",
      "kind": "project_access_changed",
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
      "action": "Victor C. changed who can access this project",
      "target": null,
      "title": "Victor C. changed who can access this project",
      "summary_excerpt": "Amy Rivera was granted access.",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958505"
      }
    },
    {
      "id": 1052473916,
      "created_at": "2026-07-21T00:05:16.670Z",
      "kind": "todo_created",
      "parent_recording_id": 1069480375,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958513/todos/1069480379.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958513/todos/1069480379",
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
      "action": "Victor C. added a to-do",
      "target": "First things first",
      "title": "On “First things first”, Victor C. added",
      "summary_excerpt": "Install ShipShape",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958513,
        "name": "New project from template",
        "url": "https://3.basecampapi.com/195539477/projects/2085958513.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958513"
      },
      "attachments": []
    },
    {
      "id": 1052473915,
      "created_at": "2026-07-21T00:05:15.878Z",
      "kind": "todo_created",
      "parent_recording_id": 1069480375,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958513/todos/1069480378.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958513/todos/1069480378",
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
      "action": "Victor C. added a to-do",
      "target": "First things first",
      "title": "On “First things first”, Victor C. added",
      "summary_excerpt": "Talk to Jerry about holidays",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958513,
        "name": "New project from template",
        "url": "https://3.basecampapi.com/195539477/projects/2085958513.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958513"
      },
      "attachments": []
    },
    {
      "id": 1052473913,
      "created_at": "2026-07-21T00:05:14.877Z",
      "kind": "todo_created",
      "parent_recording_id": 1069480375,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958513/todos/1069480376.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958513/todos/1069480376",
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
      "action": "Victor C. added a to-do",
      "target": "First things first",
      "title": "On “First things first”, Victor C. added",
      "summary_excerpt": "Talk to Cheryl about benefits",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958513,
        "name": "New project from template",
        "url": "https://3.basecampapi.com/195539477/projects/2085958513.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958513"
      },
      "attachments": []
    },
    {
      "id": 1052473907,
      "created_at": "2026-07-21T00:05:11.535Z",
      "kind": "dock_created",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958513/dock.json",
      "app_url": "https://3.basecamp.com/195539477/projects/2085958513",
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
      "action": "Victor C. started a new project called New project from template",
      "target": "New project from template",
      "title": "Victor C. started a new project called “New project from template”",
      "summary_excerpt": null,
      "avatars_sample": [],
      "bucket": {
        "id": 2085958513,
        "name": "New project from template",
        "url": "https://3.basecampapi.com/195539477/projects/2085958513.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958513"
      },
      "attachments": []
    },
    {
      "id": 1052473894,
      "created_at": "2026-07-21T00:02:33.412Z",
      "kind": "google_document_created",
      "parent_recording_id": 1069479830,
      "url": "https://3.basecampapi.com/195539477/buckets/2085958505/google_documents/1069480366.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958505/google_documents/1069480366",
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
      "action": "Victor C. added a new Google Doc",
      "target": "Roadmap (draft)",
      "title": "Victor C. added a new Google Doc called “Roadmap (draft)”",
      "summary_excerpt": "Quarterly roadmap document",
      "avatars_sample": [],
      "bucket": {
        "id": 2085958505,
        "name": "The Leto Laptop",
        "url": "https://3.basecampapi.com/195539477/projects/2085958505.json",
        "app_url": "https://3.basecamp.com/195539477/projects/2085958505"
      },
      "attachments": []
    }
  ]
}
```
<!-- END GET /reports/users/progress/1.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/reports/users/progress/1.json
```

Event kinds
-----------

The `kind` field indicates what type of activity occurred. Common values include:

| Kind | Description |
|------|-------------|
| `message_created` | A new message was posted |
| `comment_created` | A comment was added |
| `todo_created` | A new to-do was added |
| `todo_completed` | A to-do was checked off |
| `upload_created` | A file was uploaded |
| `document_created` | A document was created |
| `schedule_entry_created` | A calendar event was added |
| `schedule_entry_rescheduled` | A calendar event was rescheduled |
| `question_created` | An automatic check-in was started |
| `question_answer_created` | Someone answered a check-in |
| `chat_transcript_rollup` | A summary of Campfire chat activity |
| `kanban_card_created` | A card was added to a Card Table |
| `kanban_card_completed` | A card was completed |
| `inbox_forward_created` | An email was forwarded |
| `client_correspondence_created` | A message was sent to a client |

Event fields
------------

Each timeline event includes these fields:

| Field | Description |
|-------|-------------|
| `id` | Unique identifier for the event |
| `created_at` | When the event occurred |
| `kind` | The type of activity (see [Event kinds](#event-kinds)) |
| `parent_recording_id` | ID of the parent container (e.g., to-do list for a to-do), if applicable |
| `url` | API URL to fetch the item |
| `app_url` | Link to view the item in Basecamp |
| `creator` | The [person][person] who performed the action |
| `action` | Human-readable description of the action |
| `target` | The name of the parent container or item affected |
| `title` | Combined action and target as a complete sentence |
| `summary_excerpt` | A brief excerpt of the content, if available |
| `avatars_sample` | Array of avatar URLs (used for chat rollups showing participants) |
| `bucket` | The [project][project] where the event occurred |
| `data` | Additional event-specific data (e.g., schedule entry times) |
| `attachments` | Array of attached files, if any |

Schedule entry data
-------------------

Events with `kind` of `schedule_entry_created` or `schedule_entry_rescheduled` include a `data` object with schedule details:

```json
{
  "data": {
    "all_day": false,
    "starts_at": "2025-10-30T10:00:00.000-05:00",
    "ends_at": "2025-10-30T11:00:00.000-05:00"
  }
}
```

[pagination]: ../README.md#pagination
[person]: people.md#people
[project]: projects.md#projects
