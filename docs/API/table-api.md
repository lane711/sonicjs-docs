<!-- export const description =
  'On this page, we’ll dive into the different table endpoints you can use to manage content programmatically.'

# Tables API

SonicJs automatically generates CRUD based API endpoints for each table defined in your [schema](/tables#schema). It does this without generating code (a good thing!) and 
can be easily extended or modified based on your needs. {{ className: 'lead' }}

## The Users table

For our examples below, we'll use the  `users` table defined here: `/src/db/schema.ts`, however the API is dynamic based on your custom 
defined [schema](/tables#schema).

There is an admin page in the SonicJs UI that will list out the generated APIs for your reference:
<a target="_blank" href="http://127.0.0.1:8788/admin/api">http://127.0.0.1:8788/admin/api</a>

---
## List table records {{ tag: 'GET', label: '/v1/:tableName' }}
---

## Example: List users table records {{ tag: 'GET', label: '/v1/users' }}

<Row>
  <Col>

    This endpoint allows you to retrieve a paginated list of your table data.

    ### Optional attributes

    <Properties>
      <Property name="limit" type="integer">
        Limit the number of content records returned.
      </Property>
      <Property name="offset" type="integer">
        The offset used for paging results.
      </Property>
      <Property name="sortBy" type="string">
        The field used for sorting results.
      </Property>
      <Property name="sortDirection" type="string">
        The sort direction used for sorting results. Options are `asc` (default) or `desc`.
      </Property>
      <Property name="includeContentType" type="boolean">
        Includes the content type meta data along with the content record. This is used in the admin section when generating the edit form.
      </Property>
      <Property name="filters" type="array">
        Coming soon. This will allow you to contruct a sql `where` clause.
      </Property>
    </Properties>

  </Col>
  <Col sticky>

    <CodeGroup title="Request" tag="GET" label="/v1/users">
    ```bash {{ title: 'cURL' }}

http://localhost:8788/v1/content
```
</CodeGroup>

    ```json {{ title: 'Response' }}
[
      {
        "id": "9d370085-c116-47c9-9b22-7f33061ec7b1",
        "name": "John",
        "email": "john@somewhere.com",
        "role": "admin",
        "created_on": 1688780261122,
        "updated_on": 1688780261122
      },
      {
        "id": "90bb70b9-333d-4265-a68e-cc6f86b299fd",
        "name": "Kate",
        "email": "kate@somewhere.com",
        "role": "user",
        "created_on": 1689293023190,
        "updated_on": 1689293023190
      },
]
```

  </Col>
</Row>

---

## Retrieve a single table record {{ tag: 'GET', label: '/v1/users/:id' }}

<Row>
  <Col>

    This endpoint allows you to retrieve a single record.

    ### Optional attributes

    <Properties>
      <Property name="id" type="guid">
        The id of the record to be returned.
      </Property>
      <Property name="includeRelations" type="boolean">
        Comming soon. This will allow you to retrieve the records related data. 
      </Property>
    </Properties>

  </Col>
  <Col sticky>

    <CodeGroup title="Request" tag="GET" label="/v1/users/9d370085-c116-47c9-9b22-7f33061ec7b1">
    ```bash {{ title: 'cURL' }}

http://localhost:8788/v1/users/9d370085-c116-47c9-9b22-7f33061ec7b1
```
</CodeGroup>

    ```json {{ title: 'Response' }}
    {
      "id": "9d370085-c116-47c9-9b22-7f33061ec7b1",
      "name": "John",
      "email": "john@somewhere.com",
      "role": "admin",
      "created_on": 1688780261122,
      "updated_on": 1688780261122
    }
```

  </Col>
</Row>

---

## Create/Update content {{ tag: 'POST', label: '/v1/content' }}

<Row>
  <Col>

    This endpoint allows you to add a new content. It is an upsert, so you can create or update content with the same endpoint.

    ### Required attributes

    <Properties>
  <Property name="key" type="string">
    Unique identifier for the content. Do not include the key property for new content.
  </Property>
  <Property name="data" type="string">
    The Json string containing the content data. This can include any shape of
  </Property>
    </Properties>

  </Col>
  <Col sticky>

    <CodeGroup title="Request" tag="POST" label="/v1/content">

    ```json {{ title: 'body' }}
{
      "key" :"site1::content::blog::16861809562680000::vbeqmvt",
      "data":
        {
          "systemId": "blog",
          "title": "Top 5 Headless CMS of 2023",
          "body" : "Sed posuere consectetur est...",
          "publishOn" : "2023-06-29T12:00:00-07:00"
        }
  }
```

    </CodeGroup>

    ```json {{ title: 'Response' }}
    {
      "id": "xgQQXg3hrtjh7AvZ",
      "contact_id": "WAz8eIbvDR60rouK",
      "group_id": null,
      "pinned_message_id": null,
      "is_pinned": false,
      "is_muted": false,
      "last_active_at": null,
      "last_opened_at": null,
      "created_at": 692233200,
      "archived_at": null
    }
    ```

  </Col>
</Row>
 -->
