## Nolus Snapshot Guide
### Download snapshot
> http://88.198.18.88:8111/nolusdata.tar.gz

### Using snapshot on Linux server
##### Stop the service and reset the data

```bash
sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```

##### Download snapshot
```bash
wget http://88.198.18.88:8111/nolusdata.tar.gz && tar -xf nolusdata.tar.gz -C $HOME/.nolus
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
rm -rf nolusdata.tar.gz
```
##### Restart the service 
```bash
sudo systemctl restart nolusd && 
```
##### Check the log
```bash
sudo journalctl -u nolusd -f -o cat|grep indexed
```
