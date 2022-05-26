This aims to automate the deployment of multiple CouchDB nodes replicating to each other. Theoretically, you could expand this further, make a CouchDB cluster within a single region, and use replication between regions.

Note that by default CouchDB only uses HTTP (not secure!). 

This script was tested on Debian 11 Servers.

This script should be fairly easy to edit for any other setups or to add SSL/TLS setup. It could likely be improved to follow a more ansible-complete setup (sorry, new to using ansible!), instead of bash scripts it uses for some functions. I tried using debconf instead but had issues getting it working exactly. Also, in this setup, we are technically making all the CouchDB nodes standalone nodes that do not require a node name or erlang cookie (used for clustering), however, this script does set that up anyway. I had issues not setting those values with unattended setup, and using the normal GUI-guided setup for CouchDB even with standalone selected asks for en erlang cookie anyway.



# Usage

Configure your inventory.yml (Set up hosts)

ansible-playbook -i "sample-inventory.yml" "couchdb.yml"


There is another playbook made to automatically create and set up of replication of a specific database.

ansible-playbook -i "sample-inventory.yml" "replicate_any_db.yml"