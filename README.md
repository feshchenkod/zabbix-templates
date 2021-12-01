# zabbix-templates
Zabbix scripts and templates used for blockchain nodes monitoring.

## tornado-relayer
Link templates with host: `Docker-template.yaml` and `Tornado-relayer-template.yaml`. Set `{$URL}` macros to relayer host.

Items:
- [x] Docker containers monitoring
- [x] web check status page
- [x] parse status from status page
- [x] parse error from status page
- [ ] relayer container errors

## eth2 lighthouse:
Link templates with host: `Docker-template.yaml` and `Lighthouse-template.yaml`. Set `{$VALIDATORINDEX}` macros to lighthouse host. 

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
Link template `Cosmos-sdk-template.yaml` and set mascros for each host:
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
