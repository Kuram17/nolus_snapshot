#Snapshot
<b>Stop the service and reset the data</b>

```
sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```

<b>Download data</b>

```
wget http://162.55.169.70/nolus/data_nolus-rila.tar
tar -xf data_nolus-rila.tar -C $HOME/.nolus/data/
rm data_nolus-rila.tar
```

<b>Download wasm</b>

```
wget http://162.55.169.70/nolus/wasm_nolus-rila.tar
mkdir $HOME/.nolus/wasm/
tar -xf wasm_nolus-rila.tar -C $HOME/.nolus/wasm/
rm wasm_nolus-rila.tar
```

<b>Restore your priv_validator_state.json</b>
```
mv $HOME/priv_validator_state.json $HOME/.nolus/data/priv_validator_state.json
```
<b>Start service and check the logs</b>
```
sudo systemctl start nolusd 
sudo journalctl -u nolusd -f -o cat
```
