# create-pool-tool

## setup
### clone repo
```
git clone https://github.com/yugure-orca/create-pool-tool
cd create-pool-tool
yarn install
```

### set environment vars
for local validator
```
export ANCHOR_PROVIDER_URL=http://localhost:8899
export ANCHOR_WALLET=<your wallet>.json
```

for devnet
```
export ANCHOR_PROVIDER_URL=https://api.devnet.solana.com
export ANCHOR_WALLET=<your wallet>.json
```

## create accounts
### create WhirlpoolsConfig account
```
ts-node src/01_create_config.ts
```

example:
```
$ ts-node src/01_create_config.ts 
connection endpoint http://localhost:8899
wallet r21Gamwd9DtyjHeGywsneoQYR39C1VDwrw7tWxHAwh6
create WhirlpoolsConfig...
prompt: feeAuthorityPubkey:  r21Gamwd9DtyjHeGywsneoQYR39C1VDwrw7tWxHAwh6
prompt: collectProtocolFeesAuthorityPubkey:  r21Gamwd9DtyjHeGywsneoQYR39C1VDwrw7tWxHAwh6
prompt: rewardEmissionsSuperAuthorityPubkey:  r21Gamwd9DtyjHeGywsneoQYR39C1VDwrw7tWxHAwh6
prompt: defaultProtocolFeeRatePer10000:  300
tx: 5k733gttt65s2vAuABVhVcyGMkFDKRU3MQLhmxZ1crxCaxxXn2PsucntLN6rxqz3VeAv1jPTxfZoxUbkChbDngzT
whirlpoolsConfig address: 8raEdn1tNEft7MnbMQJ1ktBqTKmHLZu7NJ7teoBkEPKm
```
- WhirlpoolsConfig (8raEdn1tNEft7MnbMQJ1ktBqTKmHLZu7NJ7teoBkEPKm) have been created.

### create FeeTier account
```
ts-node src/02_create_feetier.ts
```

example:
```
$ ts-node src/02_create_feetier.ts 
connection endpoint http://localhost:8899
wallet r21Gamwd9DtyjHeGywsneoQYR39C1VDwrw7tWxHAwh6
create FeeTier...
prompt: whirlpoolsConfigPubkey:  8raEdn1tNEft7MnbMQJ1ktBqTKmHLZu7NJ7teoBkEPKm
prompt: tickSpacing:  64
prompt: defaultFeeRatePer1000000:  3000
tx: gomSUyS88MbjVFTfTw2JPgQumVGttDYgm2Si7kqR5JYaqCgLA1fnSycRhjdAxXdfUWbpK1FZJQxKHgfNJrXgn2h
feeTier address: BYUiw9LdPsn5n8qHQhL7SNphubKtLXKwQ4tsSioP6nTj
```
- WhirlpoolsConfig(8raEdn1tNEft7MnbMQJ1ktBqTKmHLZu7NJ7teoBkEPKm) is used.
- FeeTier(BYUiw9LdPsn5n8qHQhL7SNphubKtLXKwQ4tsSioP6nTj) for tickSpacing 64 have been created

### create Whirlpool account
```
ts-node src/03_create_whirlpool.ts
```

example:
```
$ ts-node src/03_create_whirlpool.ts 
connection endpoint http://localhost:8899
wallet r21Gamwd9DtyjHeGywsneoQYR39C1VDwrw7tWxHAwh6
create Whirlpool...
prompt: whirlpoolsConfigPubkey:  8raEdn1tNEft7MnbMQJ1ktBqTKmHLZu7NJ7teoBkEPKm
prompt: tokenMintAPubkey:  So11111111111111111111111111111111111111112
prompt: tokenMintBPubkey:  EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v
prompt: feeTierPubkey:  BYUiw9LdPsn5n8qHQhL7SNphubKtLXKwQ4tsSioP6nTj
prompt: initTickIndex:  0
is InitPrice 999.999999 OK ? (if it is OK, enter OK)
prompt: OK:  
prompt: initTickIndex:  -1000
is InitPrice 904.841941 OK ? (if it is OK, enter OK)
prompt: OK:  
prompt: initTickIndex:  -10000
is InitPrice 367.897834 OK ? (if it is OK, enter OK)
prompt: OK:  
prompt: initTickIndex:  -50000
is InitPrice 6.739631 OK ? (if it is OK, enter OK)
prompt: OK:  
prompt: initTickIndex:  -40000
is InitPrice 18.319302 OK ? (if it is OK, enter OK)
prompt: OK:  
prompt: initTickIndex:  -38000
is InitPrice 22.375022 OK ? (if it is OK, enter OK)
prompt: OK:  OK
setting... 
        whirlpoolsConfig 8raEdn1tNEft7MnbMQJ1ktBqTKmHLZu7NJ7teoBkEPKm 
        tokenMintA So11111111111111111111111111111111111111112 
        tokenMintB EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v 
        tickSpacing 64 
        initPrice 22.375022 B/A 
        tokenVaultA(gen) G5JMrgXxUdjjGXPVMezddTZAr5x7L9N4Nix6ZBS1FAwB 
        tokenVaultB(gen) 3wwdjzY7mAsoG5yYN3Ebo58p1HdihCCSeo8Qbwx8Yg5r

if the above is OK, enter YES
prompt: yesno:  YES
tx: X7pyW22o6fi5x1YmjDEacabvbtPYrqLyXaJpv88JJ6xLBi9eXra9QhuqeYuRmLGh72NsmQ11Kf8YCe3rPzqcc9r
whirlpool address: CJBunHdcRxtYSWGxkw8KarDpoz78KtNeMni2yU51TbPq
```
- WhirlpoolsConfig(8raEdn1tNEft7MnbMQJ1ktBqTKmHLZu7NJ7teoBkEPKm) is used.
- FeeTier(BYUiw9LdPsn5n8qHQhL7SNphubKtLXKwQ4tsSioP6nTj) is used.
- SOL/USDC whirlpool(CJBunHdcRxtYSWGxkw8KarDpoz78KtNeMni2yU51TbPq) have been created with 22.375022 USDC/SOL initial price.

### create TickArray accounts
```
ts-node src/04_create_tickarray.ts
```

examples:
```
$ ts-node src/04_create_tickarray.ts 
connection endpoint http://localhost:8899
wallet r21Gamwd9DtyjHeGywsneoQYR39C1VDwrw7tWxHAwh6
create TickArray...
prompt: whirlpoolPubkey:  CJBunHdcRxtYSWGxkw8KarDpoz78KtNeMni2yU51TbPq
neighring tickarrays...
   DUeNdqcFMo573Wg58GmRvYYhw3m9p5cZmzeg7kTxxLuy  NOT INITIALIZED start     -73216 covered range 0.661345 - 1.161477
   dufQnkLbrHTWZmbmuZGwxQgBCebKLVi2peTrdgmsq3S   NOT INITIALIZED start     -67584 covered range 1.161477 - 2.039827
   9Fj1szNFbzc7hwJxuGkHmjBreAGR7Yvqnt6FCwuyTd3w  NOT INITIALIZED start     -61952 covered range 2.039827 - 3.582413
   7tQ6FvFkm2PwbbyZ3tBnHyE5bqq8dw8ucnfLGBjHPbtD  NOT INITIALIZED start     -56320 covered range 3.582413 - 6.291557
   6f2k4NkMBR6jhy52QTqrMca7Hb7a7ArWdP1bWgtuxYij  NOT INITIALIZED start     -50688 covered range 6.291557 - 11.049448
   DpNHXExUnksYhmD1tQLr25W4BJSz3Ykk4a8DN7YtYgBG  NOT INITIALIZED start     -45056 covered range 11.049448 - 19.405419
>> 48W97WVPhfbLWHBP4Z5828GAWzgvmbr9YngkNbGmR7zr  NOT INITIALIZED start     -39424 covered range 19.405419 - 34.080460
   ck7UA3Hb68mC33hftDY5aGpyNzrTHaTu4ZShBV5yzqY   NOT INITIALIZED start     -33792 covered range 34.080460 - 59.853270
   BTHpoHPNh8TQq4HSoKAvxKBxee1BffyFAbxEZcxr4BYU  NOT INITIALIZED start     -28160 covered range 59.853270 - 105.116358
   3CMuyPQatYQQmyXsrUMQTDAghzcecpw1qXyiR1uczFe6  NOT INITIALIZED start     -22528 covered range 105.116358 - 184.608940
   By4Avt7jgymhiK5EaTzQnrDMMdzDWguEuuPLwJ1jazcS  NOT INITIALIZED start     -16896 covered range 184.608940 - 324.216530
   9qKqNjLf61YfyhnDBK5Nf35e1PCxkQqRnCiApqs9uJSo  NOT INITIALIZED start     -11264 covered range 324.216530 - 569.400149
   EzHNpv1X8KDwugXi1ALnkzV9wpJdsShXY5DdNcgCXoc4  NOT INITIALIZED start      -5632 covered range 569.400149 - 999.999999
prompt: tickArrayPubkey:  48W97WVPhfbLWHBP4Z5828GAWzgvmbr9YngkNbGmR7zr
tx: 5cxpJC4MDxiHxh1hSjKPtVxKjLR1CzNA3As3scBZu7vLYEmc6PPgUACG5tnnh2QYSFhM2h1nCkt6Ao5PRhq5G6b1
initialized tickArray address: 48W97WVPhfbLWHBP4Z5828GAWzgvmbr9YngkNbGmR7zr
```
- TickArray(48W97WVPhfbLWHBP4Z5828GAWzgvmbr9YngkNbGmR7zr) have been created.

## see also
you can clone arbitrary whirlpools in the mainnet-beta with Account microscope.

https://github.com/everlastingsong/account-microscope
