## Bitreverse - A secp256k1 GPU BSGS Collider
#### Cuda & Windows x64
Based on [Etayson/BSGS-cuda](https://github.com/Etayson/BSGS-cuda)<br />
## Help command: Bitreverse.exe -h
```
C:\Users\User>Bitreverse.exe -h

  -t       Set the number of GPU threads, defaults to 512
  -b       Set the number of GPU blocks, defaults to 68
  -p       Set the number of param, defaults to 256
  -d       Select NVIDIA CUDA GPU IDs to use
 -pubkey   Set single uncompressed/compressed public key to search
 -start    Range start point, defaults to 800000000000000000000000000000
 -end      Range end point, defaults to the end of 256-bit range
 -babies   Set the number of baby items 2^N
 -htsz     Set the number of HashTable 2^N, defaults to 26
 -infile   Set file with public keys list to search for in uncompressed/compressed format (searches one-by-one)
 -state    Set a recovery file from which the current state will be able to be loaded from
 -timer    Set timer for autosaving current state, defaults to every 180seconds
```
### Colliding Speed: 
- RTX 3090 (24 GB) = 4.7 Ekeys/s
- RTX 3080 (10 GB) = 2.7 Ekeys/s
- RTX 2070 ( 8 GB) = 1.7 Ekeys/s
- GTX 1080 ( 8 GB) = 120 Pkeys/s
- 1 Ekeys = 1,000,000,000,000,000,000
- 1 Pkeys = 100,000,000,000,000,0000

### Search [Puzzles 120-160](https://privatekeys.pw/puzzles/bitcoin-puzzle-tx)<br />
#120 17s2b9ksz5y7abUm92cHwG8jEPCzK3dLnT<br />
-start 800000000000000000000000000000<br />
-end FFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pubkey 02CEB6CBBCDBDF5EF7150682150F4CE2C6F4807B349827DCDBDD1F2EFA885A2630<br /><br />

#125 1PXAyUB8ZoH3WD8n5zoAthYjN15yN5CVq5<br />
-start 10000000000000000000000000000000<br />
-end 1FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pubkey 0233709EB11E0D4439A729F21C2C443DEDB727528229713F0065721BA8FA46F00E<br /><br />

#130 1Fo65aKq8s8iquMt6weF1rku1moWVEd5Ua <br />
-start 200000000000000000000000000000000<br />
-end 3FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pubkey 03633CBE3EC02B9401C5EFFA144C5B4D22F87940259634858FC7E59B1C09937852<br /><br />

#135 16RGFo6hjq9ym6Pj7N5H7L1NR1rVPJyw2v<br />
-start 4000000000000000000000000000000000<br />
-end 7FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pubkey 02145D2611C823A396EF6712CE0F712F09B9B4F3135E3E0AA3230FB9B6D08D1E16<br /><br />

#140 1QKBaU6WAeycb3DbKbLBkX7vJiaS8r42Xo<br />
-start 80000000000000000000000000000000000<br />
-end FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pubkey 031F6A332D3C5C4F2DE2378C012F429CD109BA07D69690C6C701B6BB87860D6640<br /><br />

#145 19GpszRNUej5yYqxXoLnbZWKew3KdVLkXg<br />
-start 1000000000000000000000000000000000000<br />
-end 1FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pubkey 03AFDDA497369E219A2C1C369954A930E4D3740968E5E4352475BCFFCE3140DAE5<br /><br />

#150 1MUJSJYtGPVGkBCTqGspnxyHahpt5Te8jy<br />
-start 20000000000000000000000000000000000000<br />
-end 3FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pubkey 03137807790EA7DC6E97901C2BC87411F45ED74A5629315C4E4B03A0A102250C49<br /><br />

#155 1AoeP37TmHdFh8uN72fu9AqgtLrUwcv2wJ<br />
-start 400000000000000000000000000000000000000<br />
-end 7FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pubkey 035CD1854CAE45391CA4EC428CC7E6C7D9984424B954209A8EEA197B9E364C05F6<br /><br />

#160 1NBC8uXJy1GiJ6drkiZa1WuKn51ps7EPTv<br />
-start 8000000000000000000000000000000000000000<br />
-end FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pubkey 02E0A8B039282FAF6FE0FD769CFBC4B6B4CF8758BA68220EAC420E32B91DDFA673<br />

## Use:

|  Value     |  GPU Memory |
| ---------- | ----------- |  
|   -w 30    |  11.03 GB   |
|   -w 29    |   8.01 GB   |
|   -w 28    |   7.01 GB   |
|   -w 27    |   6.02 GB   |

|   Value    |     RAM     |
| ---------- | ----------- |
|   -w 30    |   -htsz 28  |
|   -w 29    |   -htsz 28  |
|   -w 28    |   -htsz 27  |
|   -w 27    |   -htsz 25  |

All arrays and hashtable saved to the disk for fast spinup solver next time. <br />
After you have the arrays saved, you will need less RAM to launch. <br />

## Building
- To compile Bitreverse you need [Purebasic v5.31](https://www.purebasic.com)
