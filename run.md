## 0. Env

```bash
source .env
```

## 1. Build release

```bash
cargo build --release
```

## 2. Run RPC

```bash
./target/release/kora-rpc --private-key $KORA_PRIVATE_KEY --rpc-url $RPC_URL
```

## 3. Test request

### 3.1. Get supported tokens

```bash
curl -X POST http://localhost:8080 \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "getSupportedTokens",
    "params": []
  }'
```

### 3.2. Create transfer tx

```bash
curl -X POST http://localhost:8080 \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "transferTransaction",
    "params": [10, "BomroFd4tDAGmSRcNCt7TZLkeaeH815KYzfCpSTjHSfP", "AQHkdg51q7Nf8Rj9GEz3djNNjv5RCnv8Kz1rwztJ6LXL", "tV3KcUuubWxEXGDaozVSEYtMpMhTLpLQeaBW3mVbNFg"]
  }'
```

### 3.3. Estimate transaction fee

```bash
curl -X POST http://localhost:8080 \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "estimateTransactionFee",
    "params": ["<transaction_base58>", "<fee_token_address>"]
  }'
```

### 3.4. Sign a Transaction to submit to blockchain later

```bash
curl -X POST http://localhost:8080 \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "signTransaction",
    "params": ["<transaction_base58>"]
  }'
```

### 3.5. Sign and Submit a Transaction to blockchain

```bash
curl -X POST http://localhost:8080 \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "signAndSendTransaction",
    "params": ["<transaction_base58>"]
  }'
```