# zabbix-templates
Zabbix scripts and templates used for blockchain nodes monitoring.

## RPC nodes (GETH, BSC, BOR, etc)
Link templates with host: [Docker-template.yaml](/templates/Docker-template.yaml) and [RPC-nodes-template.yaml](/templates/RPC-nodes-template.yaml). Set macros `{$RPC_NODES}` - list of all nodes on the host in JSON format: `[{"name": "GETH"},{"name": "XDAI"}]` or `[{"name": "BSC"}]`. Set for each blockchain node in the `RPC_NODES` list `_URL` and `_PUB` macros.

Example for host with `XDAI` and `BSC` nodes must have the following macros with your values:
* `{$RPC_NODES}` = `[{"name": "XDAI"},{"name": "BSC"}]` - names in the list must consist of letters without numbers and other symbols;
* `{$XDAI_URL}` = `https://your-xdai-node.url/` - your XDAI RPC url;
* `{$XDAI_PUB}` = `https://rpc.xdaichain.com/` - public XDAI RPC for height comparison;
* `{$BSC_URL}` = `http://your-bsc-host:8545/` - your BSC RPC url;
* `{$BSC_PUB}` = `https://bsc-dataseed4.binance.org/` - public BSC RPC for height comparison.

Items:
- [x] Node RPC height
- [x] Public RPC height
- [x] Height diff (pub.height - local.height)
- [x] synchronization status
- [x] number of currently connected peers

## tornado-relayer
Link templates with host: [Docker-template.yaml](/templates/Docker-template.yaml) and [Tornado-relayer-template.yaml](/templates/Tornado-relayer-template.yaml). Set `{$URL}` macros to relayer host, example `http://localhost/v1/status`, `https://domain/v1/status`.

Items:
- [x] Docker containers monitoring
- [x] web check status page
- [x] parse status from status page
- [x] parse error from status page
- [ ] relayer container errors

## eth2 lighthouse:
Link templates with host: [Docker-template.yaml](/templates/Docker-template.yaml) and [Lighthouse-template.yaml](/templates/Lighthouse-template.yaml). Set `{$VALIDATORINDEX}` macros to lighthouse host. 

Items:
- [x] beacon node synced
- [x] eth1 node connected
- [x] validator enabled
- [x] validator balance
- [x] validator status
- [x] validator slashed
- [x] validator attestation effectiveness
- [ ] discovery rule for enabled validators

## cosmos-sdk
Link template [Cosmos-sdk-template.yaml](/templates/Cosmos-sdk-template.yaml) and set macros for each host:
* `{$NODE}` - node RPC URL, example `http://127.0.0.1:26657/`;
* `{$PORT}` - node RPC port, example `26657`; 
* `{$NODE_PS}` - running process name, example `gaiad`, `osmosisd`, `cosmovisor` etc;
* `{$RPC}` - public rpc to compare height, example `https://rpc.cosmos.network/status`.

Items:
- [x] Node height
- [x] pub-rpc height
- [x] peers count
- [x] port listen
- [x] proc running
- [ ] missed blocks
