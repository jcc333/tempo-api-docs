---
title: Writing Events
---

## Via HTTPS

TempoIQ accepts any valid JSON message as an event. In order to write data, you
will need to know your environment's hostname, as well as an API key and secret.
All this information can be found on your environment's Connect IQ page. 

**Endpoint**:  `GET https://<HOST>/api/channels/0/event`

**Accepts**: JSON-encoded body

**Returns**: HTTP Status 202 (Accepted) if body is valid.

**Example:**

    curl -i -u $(API_KEY):$(API_SECRET) \
        'https://acme-inc.pipelines.tempoiq.com/api/channels/0/event' \
        -d '{"voltage": 2.05, "device": "my-test-device"}'
