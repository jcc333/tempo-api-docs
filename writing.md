---
title: Writing Events
---

## Via HTTPS

TempoIQ accepts any valid JSON message as an event. In order to write data, you
will need to know your environment's hostname, as well as an API key and secret.
All this information can be found on your environment's Connect IQ page. 

### Single events

**Endpoint**: `POST https://<HOST>/api/channels/0/event`

**Accepts**: JSON object

**Returns**: HTTP Status 202 (Accepted) if body is valid.

**Example:**

    curl -i -u "my-api-key:my-api-secret" \
        'https://acme-inc.pipelines.tempoiq.com/api/channels/0/event' \
        -d '{"voltage": 2.05, "device": "my-test-device"}'

### Bulk writes

The bulk write endpoint allows you to send an array of events in a 
single request. Events may specify different timestamps from each other,
and any events that omit a timestamp will be timestamped as they are received.

**Endpoint**: `POST https://<HOST>/api/channels/0/event`

**Accepts**: JSON object with `events` array

**Returns**: HTTP Status 202 (Accepted) if body is valid.

**Example:**

    curl -i -u "my-api-key:my-api-secret" \
        'https://acme-inc.pipelines.tempoiq.com/api/channels/0/events' \
        -d '{"events": [ {"voltage": 2.05, "device": "my-test-device"} ] }'
