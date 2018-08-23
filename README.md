Please note that CouchDB no longer autocreates system tables for you, so you will have to create _global_changes, _metadata, _replicator and _users manually (the admin interface has a "Setup" menu that does this for you (<YOURDOMAIN>/_utils/#/setup)).

To secure your couchdb set the following options in the "Configuration" Interface (<YOURDOMAIN>/_utils/#_config/)
  
chttpd
require_valid_user = true

couch_httpd_auth
require_valid_user = true

httpd
www-authenticate = Basic realm="administrator"
