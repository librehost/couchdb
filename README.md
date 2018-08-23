Please note that CouchDB no longer autocreates system tables for you, so you will have to create _global_changes, _metadata, _replicator and _users manually (the admin interface has a "Setup" menu that does this for you (<YOURDOMAIN>/_utils/#/setup)).

For security reasons you should at least add one Admin Name and one Member Name to Permissions of every Database. If no members are defined, the database is public!

To secure your couchdb set the following options in the "Configuration" Interface (<YOURDOMAIN>/_utils/#_config/)
  
### chttpd

require_valid_user = true

### couch_httpd_auth

require_valid_user = true


Now all endpoints are secured by http-basic auth. Sadly this will break replication and you cant login to fauxton anymore  because of this bug: https://issues.apache.org/jira/browse/COUCHDB-1452 without executing the following in your browsers console first to get the login-cookie:

```javascript
fetch('/_session', {
  method: "POST",
  credentials: "include",
  cache: "no-cache",
  headers: {
    "Accept": "application/json",
    "Content-Type": "application/json",
    "Authorization": "Basic " + btoa("USERNAME:PASSWORD") },
    "body": JSON.stringify({name: 'USERNAME', password: 'PASSWORD'})
}).then(response => response.json());
```
