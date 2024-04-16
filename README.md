![alt text](https://www.datocms-assets.com/2885/1506458488-blog-vault-list.svg "Vault")

# Hashicorp Vault Learining

**Note:** This is a playground for using Vault with postgres and LDAP, all required keys for unseal and play around with vault vault are not provided:

    - Unseal KEY1 = 
    - Unseal KEY2 = 
    - Unseal KEY3 = 
    - Unseal KEY4 = 
    - Unseal KEY5 = 
    - ROOT_TOKEN  = 

Vault needs to be initialized with 5 keys and a key threshold of 3. When the Vault is re-sealed, restarted, or stopped, you must provide at least 3 of these keys to unseal it again.

For the different configurations please have a look at the *vault_notes.txt* file where you can find some commands that were used for vault's configuration.

## Spining up the demo

### Prerequisites
1. [Docker installed] (https://docs.docker.com/install/)
2. [Vault installed] (https://www.vaultproject.io/intro/getting-started/install.html)

### Steps
1. Start the environment: ```docker-compose up -d```
2. Set the Vault server host: ```export VAULT_ADDR='http://127.0.0.1:8200'```
3. Unseal Vault: repeat 3 times ```vault operator unseal <KEY>```
4. Login to Vault: ```vault login <ROOT_TOKEN>```
5. Get a postgres credential: ```vault read database/creds/readonly```

### Validate postgres user was created
1. connect to postgres container ```docker exec -it postgres /bin/bash```
2. inside the container, connect to db ```psql -h localhost -U postgres myapp```
3. inside postrgres db, check the users: ```myapp> \du```


