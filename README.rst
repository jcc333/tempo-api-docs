Tempo HTTP API
=============

The Tempo API exposes Tempo resources, such as historical data storage, to 
downstream clients.  These resources may be accessed using the HTTP methods
GET, POST, PUT, and DELETE.


Reading historical data
-----------------------

**Full URI**::

  https://$(YOUR_HOST).pipelines.tempoiq.com/api/pipelines/name/$(PIPELINE_NAME)/history

**Supported HTTP methods:** *GET*

**Parameters:**

=========  =================  =======================================================
Parameter  Type               Description
=========  =================  =======================================================
key        String             The group-by key to read from
start      ISO8601 timestamp  The start of the time interval for the desired data
end        ISO8601 timestamp  The end of the time interval for the desired data
limit      Int                (optional, default=10000) How many events to read total
=========  =================  =======================================================

**CURL example**::

  curl https://acme-inc.pipelines.tempoiq.com/api/pipelines/name/PowerGeneration/history?key=IL&start=2015-01-01&end=2015-02-01 -v -u $(API_KEY):$(API_SECRET)
