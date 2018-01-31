The fastest way to set up a RaiBlocks node is via a docker container from DockerHub.  You'll need a semi-recent version of docker, Client Version ~ 1.5.0.

### Installation instructions

https://docs.docker.com/engine/installation

### Pulling docker image 

```bash
sudo docker pull clemahieu/rai_node
```  
### Running

```bash
sudo docker run -d -p 7075:7075/udp -p 7075:7075 -p [::1]:7076:7076 -v ~:/root clemahieu/rai_node /rai_node --daemon
```

This command:
* Starts the docker container as a daemon "-d"
* Maps the network activity port "-p 7075:7075/udp"
* Maps the bootstrapping TCP port "-p 7075:7075"
* Maps the RPC control port to the local adapter only "-p [::1]:7076:7076"
* Maps the host's home directory to the guest /root directory "~:/root"
* Specifies the container to execute "clemahieu/rai_node"
* Specifies the command to execute in the container "/rai_node --daemon"

This will put the data in a permanent location in your hosts's home directory, outside the docker container.

### Troubleshooting

If you get `Error starting userland proxy: port is not a proto:IP:port: 'tcp:[:'.` or want to expose IPv4 port, use `-p 127.0.0.1:7076:7076`.

If you get `create ~: volume name is too short, names should be at least two alphanumeric characters.` replace the `~` with the full pathname such as j`/Users/someuser`.

### RPC Access

RPC access is disabled by default, edit your RaiBlocks/config.json file to enable RPC control and optionally enable control commands e.g. send, add key, create wallets, etc.  By default the RPC binds only to the localhost adaptor otherwise the RPC would be open to anyone.  When running inside a docker container the RPC needs to bind to all adapters so the port can be tunneled outside the container.  You'll need to change "::1" to "::ffff:0.0.0.0" for `rpc_address` in the config file.  RPCs within docker are secured by binding the mapped port to the localhost adapter via the "-p [::1]:7076:7076" option.  **It's very important the [::1] is not omitted on the RPC port mapping** otherwise the RPC could be opened to anyone who can reach the node via a network.

### Setting up a wallet and adding accounts
`curl -d '{ "action" : "wallet_create" }' [::1]:7076`  
The response will look like:  
`{ "wallet" : "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F" }`  
The number is the wallet ID that you can use to reference this wallet in other API commands.  

`curl -d '{ "action": "account_create", "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F" }' [::1]:7076`  
The response will look like:  
`{ "account" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000" }`  
This is the account number that was just created.  

Back up the wallet seed following the backup instructions https://github.com/clemahieu/raiblocks/wiki/Wallet-Backups

### Usability

You can find reference material for using docker here: https://docs.docker.com/engine/reference/commandline/

Once set up, using bashrc to create an alias can save you time.

For example (when 97bf54657cdb is your docker instance):

`sudo docker exec 97bf54657cdb /rai_node --diagnostics`

Can be shortened to:

`rai --diagnostics`

By editing ~/.bashrc to add the alias:

`alias rai='sudo docker exec 97bf54657cdb /rai_node'`