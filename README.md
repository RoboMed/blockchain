# Robomed Blockchain Api


## Public endpoints:

#### MainNet

- Moscow - https://ru.rbmchain.com
- Frankfurt - https://fr.rbmchain.com
- Singapore - https://sg.rbmchain.com
- Bangalore - https://in.rbmchain.com

#### TestNet

- Moscow - https://ru.testnet.rbmchain.com
- Frankfurt - https://fr.testnet.rbmchain.com
- Singapore - https://sg.testnet.rbmchain.com
- Bangalore - https://in.testnet.rbmchain.com


## API

[JSON](http://json.org) is a lightweight data-interchange format. It can represent numbers, strings, ordered sequences of values, and collections of name/value pairs.

[JSON-RPC](http://www.jsonrpc.org/specification) is a stateless, light-weight remote procedure call (RPC) protocol. Primarily this specification defines several data structures and the rules around their processing. It is transport agnostic in that the concepts can be used within the same process, over sockets, over HTTP, or in many various message passing environments. It uses JSON (RFC 4627) as data format.


*** Endpoint ***

```
http://{host_name}/jrpc
```

### Public methods
* [get_info](#get_info)
* [get_latest](#get_latest)
* [get_block](#get_block)
* [get_block_by_index](#get_block_by_index)
* [get_transaction](#get_transaction)
* [get_contract](#get_contract)

### Privet methods

* [add_peers](#add_peers)
* [get_peers](#get_peers)
* [start_mining](#start_mining)
* [stop_mining](#stop_mining)

### Wallet
* [get_balance](#get_balance)
* [get_address](#get_address)


### Transaction
* [send](#send)

### Contract
* [new_order](#new_order)
* [pay_order](#pay_order)
* [done_order](#done_order)
* [check_order](#check_order)



#### get_info

Returns index of last block

**Parameters**

none

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"get_info","params":[],"id":1}'

// Response
{
	"id": 1,
	"jsonrpc": "2.0",
	"result": 0
}
```


#### get_latest

Returns last block data

**Parameters**

none

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"get_info","params":[],"id":1}'

// Response
{
	"id": 1,
	"jsonrpc": "2.0",
	"result": 0
}
```

#### get_block

Returns block data

**Parameters**

1. `Hash` - block hash

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"get_info","params":["4cf098bd4a50439935b5e6f846907b7118006996f008663d82e64ab531c2f015"],"id":1}'

// Response
{
	"id": 1,
	"jsonrpc": "2.0",
	"result": {
		"data": "",
		"hash": "4cf098bd4a50439935b5e6f846907b7118006996f008663d82e64ab531c2f015",
		"header": {
			"previous_hash": "5feceb66ffc86f38d952786c6d696c79c2dbc239dd4e91b46729d73a27fb57e9",
			"root": "693c57b14ebb52de31be25321b37f8d4ba3d9b503b515157708cde310f1b9f02",
			"state_root": "5df6e0e2761359d30a8275058e299fcc0381534545f55cf43e41983f5d4c9456",
			"target": 1000,
			"timestamp": 1532379600000
		},
		"index": 0,
		"public_key": "03869597448e269caefe73cbb88c90f6ac1fc42f55e505d0dc5c9702c39f89d966",
		"signature": "30460221008c436a21025c0d32ab6fbcf6e3e69fb4948cf439f6fcf851f6fe84aeb1c383d0022100f0aac6b99936aad0cc04c26e4bf155b767d9a12f42be479ef948f8042d43be31",
		"txs_hashes": [
			"6f3a50d4edc54528db06a1ddea256e68f714fed944ce724485da2778f60406cf"
		]
	}
}
```

#### get_block_by_index

Return block data by index

**Parameters**

1. `Index` -

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"get_block_by_index","params":[0],"id":1}'

// Response
{
	"id": 1,
	"jsonrpc": "2.0",
	"result": {
		"data": "",
		"hash": "4cf098bd4a50439935b5e6f846907b7118006996f008663d82e64ab531c2f015",
		"header": {
			"previous_hash": "5feceb66ffc86f38d952786c6d696c79c2dbc239dd4e91b46729d73a27fb57e9",
			"root": "693c57b14ebb52de31be25321b37f8d4ba3d9b503b515157708cde310f1b9f02",
			"state_root": "5df6e0e2761359d30a8275058e299fcc0381534545f55cf43e41983f5d4c9456",
			"target": 1000,
			"timestamp": 1532379600000
		},
		"index": 0,
		"public_key": "03869597448e269caefe73cbb88c90f6ac1fc42f55e505d0dc5c9702c39f89d966",
		"signature": "30460221008c436a21025c0d32ab6fbcf6e3e69fb4948cf439f6fcf851f6fe84aeb1c383d0022100f0aac6b99936aad0cc04c26e4bf155b767d9a12f42be479ef948f8042d43be31",
		"txs_hashes": [
			"6f3a50d4edc54528db06a1ddea256e68f714fed944ce724485da2778f60406cf"
		]
	}
}
```

#### get_transaction

Return transaction data

**Parameters**

1. `Hash` - transaction hash

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"get_transaction","params":["6f3a50d4edc54528db06a1ddea256e68f714fed944ce724485da2778f60406cf"],"id":1}'

// Response
{
	"id": 1,
	"jsonrpc": "2.0",
	"result": {
		"block_hash": "4cf098bd4a50439935b5e6f846907b7118006996f008663d82e64ab531c2f015",
		"data": "",
		"hash": "6f3a50d4edc54528db06a1ddea256e68f714fed944ce724485da2778f60406cf",
		"inputs": [],
		"outputs": [
			{
				"address": "rL75gNZjXpTbL4d9XWEhyZj3sRjxNQNoCu",
				"amount": 10,
				"vout": 0
			}
		],
		"public_key": "03869597448e269caefe73cbb88c90f6ac1fc42f55e505d0dc5c9702c39f89d966",
		"signature": "30450221008bc95ac517624faac172eec746034c7575cb2f4d216a73cd2bee8f07fd10d81f0220436f849aa4536d6eb147c6e45dcac6ed7359a662b79ae10a74ecc54acf83ea7d",
		"timestamp": 1532379600000
	}
}
```

#### get_contract

Return contract transactions

**Parameters**

1. `Order_id` - id contract order

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"get_contract","params":["ubpLCTJFK3Yrech86feDkUqF49VSLravPe"],"id":1}'

// Response
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": {
    "agent": "tNYYp5AhPX6HBBk5jXzn7qroZZuH4REGb1",
    "amount": 1000,
    "check_order_tx": nil,
    "done_order_tx": nil,
    "new_order_tx": {
      "block_hash": "530bcc4399ebc546f7b31ba92f5befbb60d5c5b771edcbd27b53753c82e595c3",
      "data": "00b9233749bb8240e94a7bc471cdd70931360a311c000001982644d2f9285d9affededf59997ae591812fd0830f5678d1c3f4dbb897c1fdf702d0a78991b0aa600000000000003e80003000001000002000003",
      "hash": "adc5a3db6d372b7209cac305f19ede7b3161a1aec931dde4aab1423b8f387ef6",
      "inputs": [
        {
          "txid": "f87616713834df8aab0c2be4eed074f23b4789ab82835fd60ec9e468fbca7b30",
          "vout": 0
        }
      ],
      "outputs": [
        {
          "address": "tLo6bv4B5imyREKaebuJQC5z1x2fv3ZRSy",
          "amount": 761999000,
          "vout": 0
        }
      ],
      "public_key": "0397150f0046ea8348cef67f21b3ca4af4a9400c6b4a00b65a9d5e34933b64532f",
      "signature": "30450220512b1bf126acf07d07d72fe48f0d1f45c55bb02b89b05e261a08a8996fa19e44022100947ac27bf9a97ba8a90f2fcabfd7784d97c1dff2be2631b2032733f31489a24b",
      "timestamp": 1540510702821
    },
    "pay_order_tx": nil,
    "recipient": "tBPUU17AnCvgcnqVAjAhh6eZiWLS5shMKD",
    "requester": "tLo6bv4B5imyREKaebuJQC5z1x2fv3ZRSy",
    "services": [1, 2, 3],
    "status": "new_order"
  }
}
```

#### add_peers

Add peers to node

**Parameters**

1. `Peers` - array peers

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"","params":[["127.0.0.1:5000","127.0.0.2:5000"]],"id":1}'

// Response
{
	"id": 1,
	"jsonrpc": "2.0",
	"result": "ok"
}
```

#### get_peers


**Parameters**

Return knowledge peers

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"get_peers","params":[],"id":1}'

// Response
{
	"id": 1,
	"jsonrpc": "2.0",
	"result": ["127.0.0.1:5000","127.0.0.2:5000"]
}
```

#### start_mining


**Parameters**

Starting mining on node

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"start_mining","params":[],"id":1}'

// Response

```

#### stop_mining


**Parameters**

Stop mining on node

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"stop_mining","params":[],"id":1}'

// Response
{
	"id": 1,
	"jsonrpc": "2.0",
	"result": "ok"
}
```

#### get_balance

Return balance

**Parameters**

none

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"get_balance","params":[],"id":1}'

// Response
{
	"id": 1,
	"jsonrpc": "2.0",
	"result": 10
}
```

#### get_address

Return address in node

**Parameters**

none

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"","params":[],"id":1}'

// Response
{
	"id": 1,
	"jsonrpc": "2.0",
	"result": "rRMP8o1sYwn1M21M1t8kfVgoxNSvrF7ByQ"
}
```


#### add_transaction



##### send

Send token to address

**Parameters**

1. `type` - "send"
2. `address` - address to send
3. `amount` - amount to send

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"add_transaction","params":["send", "rRMP8o1sYwn1M21M1t8kfVgoxNSvrF7ByQ", 20000],"id":1}'

// Response
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "sent transaction"
}
```

#### new_order


**Parameters**

1. `type` - "new_order"
2. `address` - address to make new_order
3. `amount` - amount to make new_order
4. `services` - list of services for new_order

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"add_transaction","params":["rRMP8o1sYwn1M21M1t8kfVgoxNSvrF7ByQ", 5000, [2, 6, 32]],"id":1}'

// Response
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "ucE8t6twSS76nCtkA3E5EcBFR5euM79fdC"
}
```

#### pay_order


**Parameters**

1. `type` - "pay_order"
2. `address` - contract address
3. `amount` - amount to pay

**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"add_transaction","params":["ucE8t6twSS76nCtkA3E5EcBFR5euM79fdC", 5000],"id":1}'

// Response
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "sent a call to a smart contract"
}
```

#### done_order


**Parameters**

1. `type` - "done_order"
2. `address` - contract address
3. `checklists` - list of checklists

**Example**

```js
// Request
curl -X POST --data ''{"jsonrpc":"2.0","method":"add_transaction","params":["done_order", "ucE8t6twSS76nCtkA3E5EcBFR5euM79fdC", [{
  "anamnesis": true,
  "anamnesis_long": false,
  "anamnesis_valid": true,
  "complaints": true,
  "complaints_valid": true,
  "diagnostics_big_plan": false,
  "diagnostics_plan": false,
  "file_lis": true,
  "file_loaded": true,
  "file_paks": true,
  "mkb_10": true,
  "objective_status": false,
  "presence": true,
  "protocol_open": false,
  "protocol_printed": false,
  "protocol_saved": false,
  "protocol_signed": false,
  "pulse": true,
  "reception_duration": 298,
  "reception_recorded": false,
  "reception_repeating": true,
  "reception_time": 1540511455,
  "start": 103,
  "therapy_big_plan": false,
  "therapy_plan": false,
  "voice_anamnesis": false,
  "voice_appointment": true,
  "voice_checkup": true,
  "voice_complaints": false,
  "voice_diagnosis_mkb": false
}]],"id":1}''

// Response
{
  "id": 1,
	"jsonrpc": "2.0",
  "result": "sent a call to a smart contract"
}
```

#### check_order


**Parameters**



**Example**

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"add_transaction","params":["check_order", "ucE8t6twSS76nCtkA3E5EcBFR5euM79fdC", [true]],"id":1}'

// Response
{
  "id": 1,
	"jsonrpc": "2.0",
  "result": "sent a call to a smart contract"
}
```
