couchdb_boilerplate
===================

Simple a quick way to bootstrap a couchdb based REST api.

Documentation
=============

Couchdb let you group rewrites rules, views and many other nice stuff into "Design documents". You can see these special types of documents as apps and in our case 1 design document = 1 api version

http://guide.couchdb.org/editions/1/en/design.html

``` "_id": "_design/v1  ```

Represents your API version number (v1) so that it's very easy to hanlde API versioning and make many version of your API co-exists.

``` "rewrites":[] ```

This is actually the array where we model or declare our APIs by defining rewrites rules, authorized verbs and query arguments.

http://wiki.apache.org/couchdb/Rewriting_urls

*tips* rules are interpreted in the order you declare them in the document so be sure to not intercept broader case at the top of the list, otherwise you will never reach your more precise rules.

``` "views":{} ```

Views are pre defined queries, Couchdb will build and maintain full index for each one of your views for later and fast lookup.
CouchDb is a schemaless document oriented repository, so this is where you will retrieve and map your data to normalize the output.

http://guide.couchdb.org/editions/1/en/views.html


``` "filters":{} ```

Filters can be compared to specialized views. They let you generate parametrized change feed to issue notifications.

http://guide.couchdb.org/editions/1/en/notifications.html


``` "validate_doc_update" ```

Special function to enforce permission and structure for crud operation on documents.

http://guide.couchdb.org/editions/1/en/validation.html
