MAKE SURE YOU HAVE WASMD INSTALLED

Ok, here's how you set it up

We have a shit ton of enviroment variables to set for this to work.

I put them in `malga.env`

Then run

```bash
$ source ./malga.env
```

Now we need to set up our wallet on the blockchain

```bash
$ wasmd keys add wallet
```

We should get something like this

```bash- name: wallet
  type: local
  address: wasm1wukxp2kldxae36rgjz28umqtq792twtxdfe6ux
  pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"A8pamTZH8x8+8UAFjndrvU4x7foJbCvcz78buyQ8q7+k"}'
  mnemonic: ""
...
```

Now we need to add funds to this wallet

```bash
$ curl -X POST --header "Content-Type: application/json" \
  --data '{ "denom": "umlg", "address": "wasm1wukxp2kldxae36rgjz28umqtq792twtxdfe6ux" }' \
  https://faucet.malaga-420.cosmwasm.com/credit
```

MAKE SURE THE ADDRESS IS THE SAME AS YOUR WALLET ADDRESS GENERATED

Check the funds on your wallet by doing this 

```bash
$ wasmd query bank balances $NODE 

wasm1wukxp2kldxae36rgjz28umqtq792twtxdfe6ux
balances:
- amount: "100000000"
  denom: umlg
pagination:
  next_key: null
  total: "0"
```