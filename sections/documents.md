Documents
=========

Endpoints:

- [Get documents](#get-documents)
- [Get a document](#get-a-document)
- [Create a document](#create-a-document)
- [Update a document](#update-a-document)
- [Trash a document][trash]

Get documents
-------------

* `GET /vaults/2/documents.json` will return a [paginated list][pagination] of active documents in the [vault][vaults] with ID of `2`.

###### Example JSON Response
<!-- START GET /vaults/2/documents.json -->
```json
[
  {
    "id": 1069479147,
    "status": "active",
    "visible_to_clients": false,
    "created_at": "2026-01-04T04:36:00.000Z",
    "updated_at": "2026-02-12T06:09:14.202Z",
    "title": "New Hire Info, Benefits Summary, and Forms",
    "inherits_status": true,
    "type": "Document",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958502/documents/1069479147.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/documents/1069479147",
    "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTE0Nz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--7d1a4e571d9352315554d871bda4d46313701285.json",
    "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479147/subscription.json",
    "comments_count": 1,
    "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479147/comments.json",
    "boosts_count": 0,
    "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958502/recordings/1069479147/boosts.json",
    "position": 1,
    "parent": {
      "id": 1069479146,
      "title": "HR Stuff",
      "type": "Vault",
      "url": "https://3.basecampapi.com/195539477/buckets/2085958502/vaults/1069479146.json",
      "app_url": "https://3.basecamp.com/195539477/buckets/2085958502/vaults/1069479146"
    },
    "bucket": {
      "id": 2085958502,
      "name": "Honcho Design Newsroom",
      "type": "Project"
    },
    "creator": {
      "id": 1049715939,
      "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTkzOT9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--91bd4d39e2f4af1d814a0b480e809d15a51df239",
      "name": "Cheryl Walters",
      "email_address": "cheryl@honchodesign.com",
      "personable_type": "User",
      "title": "Corporate Integration Director",
      "bio": "A joke is a very serious thing",
      "location": null,
      "created_at": "2026-02-12T06:08:57.659Z",
      "updated_at": "2026-02-12T06:08:57.659Z",
      "admin": false,
      "owner": false,
      "client": false,
      "employee": true,
      "time_zone": "America/Chicago",
      "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBONkkT4=--b57b5a44335d4c3ba1a2585abd6e5c7e4c85fdd6/avatar",
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
    "content": "<strong>Health Insurance</strong>\nWe have just one health insurance policy. The company pays most of the premium, and you cover the rest. Domestic partnerships are covered, as well as marriages. Open enrollment starts in January.<br><br>\n\n<strong>401K Retirement Plan</strong>\nWe match dollar-for-dollar up to 10% of your salary that you contribute to the plan. You are eligible to enroll in the 401K plan after your first paycheck.<br><br>\n\n<strong>Flexible Spending Account (FSA)</strong>\nThe FSA is an account where you can set aside pre-tax money for out-of-pocket medical expenses, such as prescriptions, OTC medicine, vision care, etc.  You have to decide up front how much money you want to put in the account, and the max is $2500/year.<br><br>\n\n<strong>Continuing Education Allowance</strong>\nWe provide you with $500 a year to take classes that help you professionally. Really, anything that helps you with your job.<br><br>\n\n<strong>Matching Charitable Gifts</strong>\nWhen you donate money to a qualified charity, we will make a matching gift to that charity on your behalf. The maximum for the year is $500 per employee.<br><br>\n\n<strong>Paid Time Off</strong>\nPaid time off doesn't really exist here - if you need a day (or week!) off, you just need to clear it with your team or others who would be affected by your absence. You should try to take at least 3 weeks off a year."
  }
]
```
<!-- END GET /vaults/2/documents.json -->
###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/vaults/2/documents.json
```

Get a document
--------------

* `GET /documents/2.json` will return the document with an ID of `2`.

###### Example JSON Response
<!-- START GET /documents/2.json -->
```json
{
  "id": 1069479860,
  "status": "active",
  "visible_to_clients": false,
  "created_at": "2026-02-12T19:38:00.000Z",
  "updated_at": "2026-02-12T19:38:00.000Z",
  "title": "Project Tool Tips",
  "inherits_status": true,
  "type": "Document",
  "url": "https://3.basecampapi.com/195539477/buckets/2085958508/documents/1069479860.json",
  "app_url": "https://3.basecamp.com/195539477/buckets/2085958508/documents/1069479860",
  "bookmark_url": "https://3.basecampapi.com/195539477/my/bookmarks/BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiLmdpZDovL2JjMy9SZWNvcmRpbmcvMTA2OTQ3OTg2MD9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg1yZWFkYWJsZQY7AFQ=--6e3c21a333aa7ca5da3b9a9372022b4b19083f73.json",
  "subscription_url": "https://3.basecampapi.com/195539477/buckets/2085958508/recordings/1069479860/subscription.json",
  "comments_count": 0,
  "comments_url": "https://3.basecampapi.com/195539477/buckets/2085958508/recordings/1069479860/comments.json",
  "boosts_count": 0,
  "boosts_url": "https://3.basecampapi.com/195539477/buckets/2085958508/recordings/1069479860/boosts.json",
  "position": 1,
  "parent": {
    "id": 1069479845,
    "title": "Docs & Files",
    "type": "Vault",
    "url": "https://3.basecampapi.com/195539477/buckets/2085958508/vaults/1069479845.json",
    "app_url": "https://3.basecamp.com/195539477/buckets/2085958508/vaults/1069479845"
  },
  "bucket": {
    "id": 2085958508,
    "name": "Getting Started",
    "type": "Project"
  },
  "creator": {
    "id": 1049715953,
    "attachable_sgid": "BAh7BkkiC19yYWlscwY6BkVUewdJIglkYXRhBjsAVEkiK2dpZDovL2JjMy9QZXJzb24vMTA0OTcxNTk1Mz9leHBpcmVzX2luBjsAVEkiCHB1cgY7AFRJIg9hdHRhY2hhYmxlBjsAVA==--d8a46d8065dbf49cd0c5a9c75aabdcf58c1ef9f6",
    "name": "Basecamp",
    "email_address": null,
    "personable_type": "DummyUser",
    "title": null,
    "bio": null,
    "location": null,
    "created_at": "2026-02-12T06:10:09.265Z",
    "updated_at": "2026-02-12T06:10:09.265Z",
    "admin": false,
    "owner": false,
    "client": false,
    "employee": false,
    "time_zone": "America/Chicago",
    "avatar_url": "https://3.basecampapi.com/195539477/people/BAhpBPFkkT4=--684a9fd741b7edab076c407cfcc729da47aadbbf/avatar",
    "can_ping": true,
    "can_manage_projects": false,
    "can_manage_people": false,
    "can_access_timesheet": false,
    "can_access_hill_charts": false
  },
  "content": "This overview of the available project tools will help you know when and how to use them.           <br><br><strong>To-dos</strong><br>           To-dos keep everyone on a project in the loop about the work that needs to be done and who’s responsible. Let’s dig into to-dos.           <ul>             <li>\n<a href=\"https://5.basecamp-help.com/article/1077-to-dos#Assigning-and-scheduling-Ixwu6\" target=\"_blank\" rel=\"noreferrer\">Assignments</a> let you divvy up the work and manage accountability.</li>             <li>\n<a href=\"https://5.basecamp-help.com/article/1077-to-dos#Grouping-to-dos-gyRPS\" target=\"_blank\" rel=\"noreferrer\">Groups</a> are a great way to organize and color-code related tasks.</li>             <li>\n<a href=\"https://5.basecamp-help.com/article/1077-to-dos#Working-with-multiple-to-dos-sZy4q\" target=\"_blank\" rel=\"noreferrer\">Bulk actions</a> let you make multiple changes at once.</li>             <li>\n<a href=\"https://5.basecamp-help.com/article/1094-project-and-list-templates#Creating-a-template-PALZM\" target=\"_blank\" rel=\"noreferrer\">To-do templates</a> makes it possible to use the same list without recreating it every time.</li>           </ul>           <a href=\"https://5.basecamp-help.com/article/1077-to-dos\" target=\"_blank\" rel=\"noreferrer\">Learn more about To-dos</a>           <br><br><strong>Docs &amp; Files</strong><br>           Docs and Files are great for how-tos, best practices, shared files, photos, brand assets, and much more. Here are a few helpful details.           <ul>             <li>Files can be uploaded, linked from the cloud, or you can drag and drop them into Basecamp.</li>             <li>Documents can be edited by multiple people, but not at once.</li>             <li>Every version of a document is stored so you can see the history of changes. Click the three dot menu ••• on the doc, then View changes.</li>             <li>Folders let you group stuff together and can be color-coded to organize things visually.</li>           </ul>           <a href=\"https://5.basecamp-help.com/article/1079-docs-and-files\" target=\"_blank\" rel=\"noreferrer\">Learn more about Docs &amp; Files</a>           <br><br><strong>Message Board</strong><br>           When you want to make an announcement, start a discussion, or share progress, Messages are the answer. At Basecamp, messages have           replaced email internally. Everyone gets notified and can comment, boost, or ask questions in one place without a long email thread.           <ul>             <li>\n<a href=\"https://5.basecamp-help.com/article/1075-message-board#pinning-messages\" target=\"_blank\" rel=\"noreferrer\">Pin a message</a> to keep the important stuff at the top, whether a welcome message or the project overview.</li>             <li>\n<a href=\"https://5.basecamp-help.com/article/1075-message-board#categorizing-messages\" target=\"_blank\" rel=\"noreferrer\">Use categories</a> to organize your posts and gives the people context about the information they’re going to read. You can customize those categories for your organization, too. You’ll find the option in Adminland.</li>             <li>\n<a href=\"https://5.basecamp-help.com/article/1075-message-board#scheduling-a-message\" target=\"_blank\" rel=\"noreferrer\">Schedule a post</a> to publish it at the optimal time, perfect if you’re in another time zone from your team or are working after hours.</li>           </ul>           <a href=\"https://basecamp.com/learn/beyond-the-basics/message-board\" target=\"_blank\" rel=\"noreferrer\">Learn more about Messages</a>           <br><br><strong>Calendar</strong><br>           The Calendar keeps you on track for each project. In one place, you can see the meetings, milestones, and upcoming due dates. Let’s get into more tips:           <ul>             <li>Click <strong>My Events</strong> in the bottom bar to see events from across all of your projects.</li>             <li>Go to the specific project to <a href=\"https://5.basecamp-help.com/article/1120-calendar#Creating-an-event-BHuRJ\" target=\"_blank\" rel=\"noreferrer\">add events</a>.</li>             <li>\n<a href=\"https://5.basecamp-help.com/article/1120-calendar#Creating-an-event-BHuRJ\" target=\"_blank\" rel=\"noreferrer\">Create recurring events</a> for meetings that happen on a regular schedule.</li>             <li>Want your Basecamp calendar in your calendar app? <a href=\"https://5.basecamp-help.com/article/1120-calendar#Subscribing-to-a-calendar-0Cyj-\" target=\"_blank\" rel=\"noreferrer\">Here’s how to sync it</a>.</li>             <li>By default, the Calendar includes assignments with due dates. If you only want to see meetings and events, you can <a href=\"https://5.basecamp-help.com/article/1120-calendar#Choosing-what-the-calendar-shows-4-7Ny\" target=\"_blank\" rel=\"noreferrer\">change what’s shown</a>.</li>           </ul>           <a href=\"https://5.basecamp-help.com/article/1120-calendar\" target=\"_blank\" rel=\"noreferrer\">Learn more about the Calendar</a>           <br><br><strong>Card Table</strong><br>           Card tables are Basecamp’s way to manage process-driven and reactive work, similar to Kanban boards in other tools. A support team           that needs to triage customer requests? Card table. A creative team that needs to move an item from ideation through to completion?           Card table. From event planning to real estate, cards help you manage all kinds of work.           <ul>             <li>\n<a href=\"https://5.basecamp-help.com/article/1063-card-tables#Adding-a-card-SiaMA\" target=\"_blank\" rel=\"noreferrer\">Add a card</a>, then assign it to someone, give it a due date, and include any needed notes or attachments. All of the conversation about the card will happen right there.</li>             <li>\n<a href=\"https://5.basecamp-help.com/article/1063-card-tables#Working-with-cards-x0EGj\" target=\"_blank\" rel=\"noreferrer\">Add steps to cards</a> to break down the work into a checklist. You can assign each step and give it a due date, which is great for when multiple people are working together.</li>             <li>\n<a href=\"https://5.basecamp-help.com/article/1063-card-tables#Watching-a-column-5rMFm\" target=\"_blank\" rel=\"noreferrer\">Watch a column</a> to be notified about new cards added or moved to that space.</li>             <li>\n<a href=\"https://5.basecamp-help.com/article/1063-card-tables#Managing-columns-AcpjV\" target=\"_blank\" rel=\"noreferrer\">Organize the columns</a> so that each stage is relevant to the work.</li>           </ul>           <a href=\"https://basecamp.com/learn/beyond-the-basics/card-table\" target=\"_blank\" rel=\"noreferrer\">Learn more about Card Tables</a>           <br><br><strong>Chat</strong><br>           Chat is where real-time group conversation happens in a project. Sometimes getting on the same page requires live conversation and Chat is a           great solution.<br><br>It’s also a fun place to say good morning and share a bit about your day, the water cooler conversations that           keeps people connected. If the chatter is ever too much, you can turn off notifications from within the chat itself.           <br><br>           Curious when to use Chat, Pings, or Messages? <a href=\"https://basecamp.com/learn/beyond-the-basics/communication-tools\" target=\"_blank\" rel=\"noreferrer\">This short video</a>           will walk you through it.           <br><br>           <a href=\"https://5.basecamp-help.com/article/1052-chat\" target=\"_blank\" rel=\"noreferrer\">Learn more about Chat</a>           <br><br><strong>Automatic Check-ins</strong><br>           Automatic check-ins allow everyone on the project to share responses to the same prompt, collected in one place. You can set up           questions for just about anything, on any cadence. These questions can be project related, goal specific, or just for fun.           <br><br>           <a href=\"https://basecamp.com/learn/beyond-the-basics/automatic-check-ins\" target=\"_blank\" rel=\"noreferrer\">Watch this quick video</a> to learn more and see how we           use check-ins at Basecamp."
}
```
<!-- END GET /documents/2.json -->

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" https://3.basecampapi.com/$ACCOUNT_ID/documents/2.json
```

Create a document
-----------------

* `POST /vaults/2/documents.json` publishes a document under the vault with an ID of `2`.

**Required parameters**: `title` as the title of the document, and `content` as the body of the document. See our [Rich text guide][rich] for what HTML tags are allowed.

_Optional parameters_: . `status`, set to `active` to publish immediately.

This endpoint will return `201 Created` with the current JSON representation of the document if the creation was a success. See the [Get a document](#get-a-document) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "title": "New Hire Info",
  "content": "<div><strong>Getting started</strong></div>",
  "status": "active"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"title":"New Hire Info","content":"<div><strong>Getting started</strong></div>","status":"active"}' \
  https://3.basecampapi.com/$ACCOUNT_ID/vaults/2/documents.json
```

Update a document
-----------------

* `PUT /documents/2.json` allows changing the title and content of the document with an ID of `2`.

This endpoint will return `200 OK` with the current JSON representation of the document if the update was a success. See the [Get a document](#get-a-document) endpoint for more info on the payload.

###### Example JSON Request

```json
{
  "title": "New Hire Information",
  "content": "<div><strong>Let's get started</strong></div>"
}
```

###### Copy as cURL

```shell
curl -s -H "Authorization: Bearer $ACCESS_TOKEN" -H "Content-Type: application/json" \
  -d '{"title":"New Hire Information","content":"<div><strong>Let's get started</strong></div>"}' -X PUT \
  https://3.basecampapi.com/$ACCOUNT_ID/documents/2.json
```

Legacy project-scoped routes
-----------------------------

The following project-scoped routes are still supported and will remain available, but flat routes above are the canonical form for new integrations.

* `GET /buckets/1/vaults/2/documents.json` → [Get documents](#get-documents)
* `GET /buckets/1/documents/2.json` → [Get a document](#get-a-document)
* `POST /buckets/1/vaults/2/documents.json` → [Create a document](#create-a-document)
* `PUT /buckets/1/documents/2.json` → [Update a document](#update-a-document)

[pagination]: ../README.md#pagination
[trash]: recordings.md#trash-a-recording
[vaults]: vaults.md#vaults
[rich]: rich_text.md
