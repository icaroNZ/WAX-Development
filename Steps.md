## Start Nodeos
```bash
nodeos -e -p eosio \
--plugin eosio::producer_plugin \
--plugin eosio::chain_api_plugin \
--plugin eosio::http_plugin \
--access-control-allow-origin='*' \
--contracts-console \
--http-validate-host=false \
--verbose-http-errors >> nodeos.log 2>&1 &
```

## Create a wallet

```bash
cleos wallet create --to-console
```
PW5JgN8aLjYxayPK58Qv7TrYrzAmqrPHgaRC7vpxnn5AjyAgttB3C
```bash
cleos wallet open
cleos wallet list
cleos wallet unlock --password PW5JgN8aLjYxayPK58Qv7TrYrzAmqrPHgaRC7vpxnn5AjyAgttB3C
cleos wallet list
```

## Import Development key

```
5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3
```

```bash 
cleos wallet import --private-key 5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3
```

```
EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV
```

## Test Blockchain
```bash
curl --request POST \
  --url http://127.0.0.1:8888/v1/chain/get_info \
  --header 'content-type: application/x-www-form-urlencoded; charset=UTF-8'
```

## Create an Account

```bash
cleos wallet create_key
```
```
EOS8RsYdsZxZ7Ku1E5EMbzmNeruY6yaM3qRo7BLgT3Zmm6Y9Erc7h
```
```bash
cleos create account eosio waxsc EOS8RsYdsZxZ7Ku1E5EMbzmNeruY6yaM3qRo7BLgT3Zmm6Y9Erc7h
```

## Check account

```bash
cleos get account waxsc
```

# Create a Smart Contract

```bash
eosio-init -project game
```

## build

```bash
cd game/build
cmake ..
make
```

## Deploy the build

```bash 
cd game
cleos set contract waxsc .  -p waxsc@active
```

## Call the ACTION

```bash 
cleos push action waxsc hi '["test"]' -p waxsc@active
```