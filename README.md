Please note that CouchDB no longer autocreates system tables for you, so you will have to create _global_changes, _metadata, _replicator and _users manually (the admin interface has a "Setup" menu that does this for you (<YOURDOMAIN>/_utils/#/setup)).



For security reasons you should at least add one Admin Name and one Member Name to Permissions of every new Database. If no members are defined, the database is public!

To secure all new created databases set the following option in the "Configuration" Interface (<YOURDOMAIN>/_utils/#_config/)

### couchdb

default_security = admin_only


Also the following settings are recommended:

### chttpd

bind_address = 0.0.0.0

### httpd

bind_address = 0.0.0.0
