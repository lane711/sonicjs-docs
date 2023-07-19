<!-- export const description =
  'On this page, we’ll dive into the different content endpoints you can use to manage content programmatically.'

# Content

Content records are the primary entity in SonicJs — everything is content. This includes any custom content types that you
create which could be anything (books, blog posts, movies, etc). Even users are technically just content,
however they are accessed thru a separate API for security reason. {{ className: 'lead' }}

## The content model

The content model is simple as most of your data properties will be nested in the `data` property.

### Properties

<Properties>
  <Property name="key" type="string">
    Unique identifier for the content.
  </Property>
  <Property name="value" type="string">
    The Json string containing the content data
  </Property>
</Properties>

---

## List all content {{ tag: 'GET', label: '/v1/content' }}

<Row>
  <Col>

    This endpoint allows you to retrieve a paginated list of all your content. By default, a maximum of ten 10 records are shown per page.

    ### Optional attributes

    <Properties>
      <Property name="limit" type="integer">
        Limit the number of content records returned.
      </Property>
      <Property name="includeContentType" type="boolean">
        Includes the content type meta data along with the content record. This is used in the admin section when generating the edit form.
      </Property>
      <Property name="contentType" type="string">
        Only returns content of a certain content type (ie: 'blog', 'book')
      </Property>
      <Property name="keysOnly" type="boolean">
        Only list the keys (unique identifiers), does not include any data
      </Property>
    </Properties>

  </Col>
  <Col sticky>

    <CodeGroup title="Request" tag="GET" label="/v1/content">
    ```bash {{ title: 'cURL' }}

http://localhost:8788/v1/content
```
</CodeGroup>

    ```json {{ title: 'Response' }}
[
      {
        "key": "site1::content::blog::16861809259460000::4ppge8u",
        "systemId": "blog",
        "title": "What is the Fastest Headless CMS on the Market?",
        "body": "Maecenas sed diam...",
        "publishOn": "2023-06-07T12:00:00-07:00",
      },
      {
        "key": "site1::content::article::16861809259460000::4ppge8u",
        "systemId": "article",
        "title": "Top 5 Headless CMS of 2023",
        "body": "Sed posuere consecte...",
        "category" : "Headless CMS"
      }
]
```

  </Col>
</Row>

---

## Retrieve a content record {{ tag: 'GET', label: '/v1/content/:id' }}

<Row>
  <Col>

    This endpoint allows you to retrieve a single record.

    ### Optional attributes

    <Properties>
      <Property name="limit" type="integer">
        Limit the number of content records returned.
      </Property>
      <Property name="includeContentType" type="boolean">
        Includes the content type meta data along with the content record. This is used in the admin section when generating the edit form.
      </Property>
      <Property name="contentType" type="string">
        Only returns content of a certain content type (ie: 'blog', 'book')
      </Property>
      <Property name="keysOnly" type="boolean">
        Only list the keys (unique identifiers), does not include any data
      </Property>
    </Properties>

  </Col>
  <Col sticky>

    <CodeGroup title="Request" tag="GET" label="/v1/content/site1::content::article::16857474370560000::bpsxzzu">
    ```bash {{ title: 'cURL' }}

http://localhost:8788/v1/content/site1::content::article::16857474370560000::bpsxzzu
```
</CodeGroup>

    ```json {{ title: 'Response' }}

    {
      "key": "site1::content::article::16861809259460000::4ppge8u",
      "systemId": "article",
      "title": "Top 5 Headless CMS of 2023",
      "body": "Sed posuere consecte...",
      "category" : "Headless CMS"
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
