---
swagger: "2.0"
x-collection-name: Mailgun
x-complete: 0
info:
  title: Mailgun API Message
  description: Gets a message.
  version: v2
host: api.mailgun.net
basePath: v2/
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  bounces/:
    get:
      summary: Bounces
      description: Fetches the list of bounces.
      operationId: getBounces
      x-api-path-slug: bounces-get
      parameters:
      - in: query
        name: limit
        description: Maximum number of records to return
      - in: query
        name: skip
        description: Number of records to skip
      responses:
        200:
          description: OK
      tags:
      - Bounces
    post:
      summary: Add Bounce
      description: Adds a permanent bounce to the bounces table. Updates the existing
        record if already here.
      operationId: postBounces
      x-api-path-slug: bounces-post
      parameters:
      - in: query
        name: address
        description: Email address to add to bounce list
      - in: query
        name: code
        description: Error code (default 550)
      - in: query
        name: error
        description: Error description, (default is empty)
      responses:
        200:
          description: OK
      tags:
      - Bounce
  bounces/{address}:
    delete:
      summary: Delete Bounce
      description: Clears a bounce event.
      operationId: deleteBouncesAddress
      x-api-path-slug: bouncesaddress-delete
      responses:
        200:
          description: OK
      tags:
      - Bounce
    get:
      summary: Bounce
      description: Fetches a single bounce event by a given email address. This is
        useful to check if a given email address has bounced before.
      operationId: getBouncesAddress
      x-api-path-slug: bouncesaddress-get
      parameters:
      - in: path
        name: address
        description: The email address to get bounce request for
      responses:
        200:
          description: OK
      tags:
      - Bounce
  complaints/:
    get:
      summary: Complaints
      description: Fetches the list of complaints.
      operationId: getComplaints
      x-api-path-slug: complaints-get
      parameters:
      - in: query
        name: limit
        description: Maximum number of records to return
      - in: query
        name: skip
        description: Number of records to skip
      responses:
        200:
          description: OK
      tags:
      - Complaints
    post:
      summary: Add Complaint
      description: Adds an address to the complaints table.
      operationId: postComplaints
      x-api-path-slug: complaints-post
      parameters:
      - in: query
        name: address
        description: Email address to add to the complaint list
      responses:
        200:
          description: OK
      tags:
      - Complaint
  complaints/{address}:
    delete:
      summary: Delete Complaint
      description: Removes a given spam complaint.
      operationId: deleteComplaintsAddress
      x-api-path-slug: complaintsaddress-delete
      parameters:
      - in: query
        name: address
        description: Email address of complaint to remove
      responses:
        200:
          description: OK
      tags:
      - Complaint
    get:
      summary: Complaint
      description: Fetches a single spam complaint by a given email address. This
        is useful to check if a particular user has complained.
      operationId: getComplaintsAddress
      x-api-path-slug: complaintsaddress-get
      parameters:
      - in: query
        name: address
        description: Email address of the complaint to get
      responses:
        200:
          description: OK
      tags:
      - Complaint
  lists:
    post:
      summary: Create List
      description: Creates a new mailing list.
      operationId: postLists
      x-api-path-slug: lists-post
      parameters:
      - in: query
        name: access_level
        description: 'List access level, one of: readonly (default), members, everyone'
      - in: query
        name: address
        description: A valid email address for the mailing list, e
      - in: query
        name: description
        description: A description
      - in: query
        name: name
        description: Mailing list name, e
      responses:
        200:
          description: OK
      tags:
      - List
  lists/:
    get:
      summary: Lists
      description: Returns a list of mailing lists under your account.
      operationId: getLists
      x-api-path-slug: lists-get
      parameters:
      - in: query
        name: access_level
        description: 'List access level, one of: readonly (default), members, everyone'
      - in: query
        name: address
        description: Find a mailing list by itu2019s address (optional)
      - in: query
        name: description
        description: Description string
      - in: query
        name: limit
        description: Maximum number of records to return (100 by default)
      - in: query
        name: namespace_id
        description: New name, e
      - in: query
        name: skip
        description: Records to skip (0 by default)
      responses:
        200:
          description: OK
      tags:
      - Lists
  lists/{address}:
    delete:
      summary: Delete List
      description: Deletes a mailing list.
      operationId: deleteListsAddress
      x-api-path-slug: listsaddress-delete
      parameters:
      - in: query
        name: address
        description: Address to remove
      responses:
        200:
          description: OK
      tags:
      - List
    get:
      summary: List
      description: Returns a single mailing list by a given address.
      operationId: getListsAddress
      x-api-path-slug: listsaddress-get
      parameters:
      - in: query
        name: address
        description: Address to return for a single list
      responses:
        200:
          description: OK
      tags:
      - List
    put:
      summary: Update List
      description: Update mailing list properties, such as address, description or
        name
      operationId: putListsAddress
      x-api-path-slug: listsaddress-put
      responses:
        200:
          description: OK
      tags:
      - List
  lists/{address}/members:
    get:
      summary: Add To List
      description: Adds a member to the mailing list.
      operationId: getListsAddressMembers
      x-api-path-slug: listsaddressmembers-get
      parameters:
      - in: query
        name: address
        description: Valid email address specification, e
      - in: query
        name: Name
        description: Optional member name
      - in: query
        name: subscribed
        description: yes to add as subscribed (default), no as unsubscribed
      - in: query
        name: upsert
        description: yes to update member if present, no to raise error in case of
          a duplicate member (default)
      - in: query
        name: vars
        description: JSON-encoded dictionary string with arbitrary parameters, e
      responses:
        200:
          description: OK
      tags:
      - List
  lists/{address}/members/:
    get:
      summary: List Members
      description: Fetches the list of mailing list members.
      operationId: getListsAddressMembers
      x-api-path-slug: listsaddressmembers-get
      parameters:
      - in: query
        name: limit
        description: Maximum number of records to return (100 by default)
      - in: query
        name: skip
        description: Records to skip (0 by default)
      - in: query
        name: subscribed
        description: yes to list subscribed, no for unsubscribed, list all if not
          set
      responses:
        200:
          description: OK
      tags:
      - List
      - Members
  lists/{address}/members/{member_address}:
    get:
      summary: List Member
      description: Retrieves a mailing list member.
      operationId: getListsAddressMembersMemberAddress
      x-api-path-slug: listsaddressmembersmember-address-get
      parameters:
      - in: query
        name: address
        description: Email address of commenter
      - in: query
        name: member_address
        description: Email address on the list
      responses:
        200:
          description: OK
      tags:
      - List
      - Member
  messages.mime:
    post:
      summary: Posts Mime Message
      description: 'Posts a message in MIME format. Note: you will need to build a
        MIME string yourself. Use a MIME library for your programming language to
        do this. Pass the resulting MIME string as message parameter.'
      operationId: postMessages.mime
      x-api-path-slug: messages-mime-post
      parameters:
      - in: query
        name: h:X-My-Header
        description: 'h: prefix followed by an arbitrary value allows to appendna
          custom MIME header to the message (X-My-Headernin this case)'
      - in: query
        name: message
        description: MIME string of the message
      - in: query
        name: o:campaign
        description: Id of the campaign the message belongs to
      - in: query
        name: o:deliverytime
        description: Desired time of delivery
      - in: query
        name: o:dkim
        description: Enables/disabled DKIM signatures on per-message basis
      - in: query
        name: o:tag
        description: Tag string
      - in: query
        name: o:testmode
        description: Enables sending in test mode
      - in: query
        name: o:tracking
        description: Toggles tracking on a per-message basis, seenTracking Messages
          for details
      - in: query
        name: o:tracking-clicks
        description: Toggles clicks tracking on a per-message basis
      - in: query
        name: o:tracking-opens
        description: Toggles opens tracking on a per-message basis
      - in: query
        name: to
        description: Email address of the recipient(s)
      - in: query
        name: v:my-var
        description: 'v: prefix followed by an arbitrary name allows tonattach a custom
          JSON data to the message'
      responses:
        200:
          description: OK
      tags:
      - S
      - Mime
      - Message
  messages/:
    post:
      summary: Send Message
      description: Sends a message by assembling it from the components. Note that
        you can specify most parameters multiple times, HTTP supports this out of
        the box. This makes sense for parameters like cc, to or attachment.
      operationId: postMessages
      x-api-path-slug: messages-post
      parameters:
      - in: query
        name: attachment
        description: File attachment
      - in: query
        name: bcc
        description: Same as To but for Bcc
      - in: query
        name: cc
        description: Same as To but for Cc
      - in: query
        name: from
        description: Email address for From header
      - in: query
        name: h:X-My-Header
        description: 'h: prefix followed by an arbitrary value allows to appendna
          custom MIME header to the message (X-My-Headernin this case)'
      - in: query
        name: html
        description: Body of the message
      - in: query
        name: inline
        description: Attachment with inline disposition
      - in: query
        name: o:campaign
        description: Id of the campaign the message belongs to
      - in: query
        name: o:deliverytime
        description: Desired time of delivery
      - in: query
        name: o:dkim
        description: Enables/disables DKIM signatures on per-message basis
      - in: query
        name: o:tag
        description: Tag string
      - in: query
        name: o:testmode
        description: Enables sending in test mode
      - in: query
        name: o:tracking
        description: Toggles tracking on a per-message basis, seenTracking Messages
          for details
      - in: query
        name: o:tracking-clicks
        description: Toggles clicks tracking on a per-message basis
      - in: query
        name: o:tracking-opens
        description: Toggles opens tracking on a per-message basis
      - in: query
        name: subject
        description: Message subject
      - in: query
        name: text
        description: Body of the message
      - in: query
        name: to
        description: Email address of the recipient(s)
      - in: query
        name: v:my-var
        description: 'v: prefix followed by an arbitrary name allows tonattach a custom
          JSON data to the message'
      responses:
        200:
          description: OK
      tags:
      - Send
      - Message
  messages/{id}:
    get:
      summary: Message
      description: Gets a message.
      operationId: getMessages
      x-api-path-slug: messagesid-get
      parameters:
      - in: query
        name: id
        description: ID of the message
      responses:
        200:
          description: OK
      tags:
      - Message
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---