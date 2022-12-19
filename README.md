## Bitreverse - A secp256k1 GPU BSGS Collider
#### Cuda & Windows x64
Based on [Etayson/BSGS-cuda](https://github.com/Etayson/BSGS-cuda)<br />
## Help command: Bitreverse.exe -h
```
C:\Users\User>Bitreverse.exe -h

-t       Number of GPU threads, Default 512
-b       Number of GPU blocks, Default 68
-p       Number of pparam, Default 256
-d       Select GPU IDs, Default 0 (-d 1,2,3)
-pb      Set single uncompressed/compressed pubkey for searching
-pk      Range start from , Default 0x1
-pke     End range
-w       Set number of baby items 2^ (-w 22  mean 2^22 points)
-htsz    Set number of HashTable 2^ , Default 26
-infile  Set file with pubkey for searching in uncompressed/compressed  format (search sequential), one pubkey per line
-wl      Set recovery file from which the state will be loaded
-wt      Set timer for autosaving current state, Default every 180 seconds
```
### Colliding Speed: 
- RTX 3090 (24 GB) = 4.7 Ekeys/s
- RTX 3080 (10 GB) = 2.7 Ekeys/s
- RTX 2070 ( 8 GB) = 1.7 Ekeys/s
- GTX 1080 ( 8 GB) = 120 Pkeys/s
- 1 Ekeys = 1,000,000,000,000,000,000
- 1 Pkeys = 1,000,000,000,000,000,00

### Search [Puzzles 120-160](https://privatekeys.pw/puzzles/bitcoin-puzzle-tx)<br />
#120 17s2b9ksz5y7abUm92cHwG8jEPCzK3dLnT<br />
-pk 800000000000000000000000000000<br />
-pke FFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pb 02CEB6CBBCDBDF5EF7150682150F4CE2C6F4807B349827DCDBDD1F2EFA885A2630<br /><br />

#125 1PXAyUB8ZoH3WD8n5zoAthYjN15yN5CVq5<br />
-pk 10000000000000000000000000000000<br />
-pke 1FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pb 0233709EB11E0D4439A729F21C2C443DEDB727528229713F0065721BA8FA46F00E<br /><br />

#130 1Fo65aKq8s8iquMt6weF1rku1moWVEd5Ua <br />
-pk 200000000000000000000000000000000<br />
-pke 3FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pb 03633CBE3EC02B9401C5EFFA144C5B4D22F87940259634858FC7E59B1C09937852<br /><br />

#135 16RGFo6hjq9ym6Pj7N5H7L1NR1rVPJyw2v<br />
-pk 4000000000000000000000000000000000<br />
-pke 7FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pb 02145D2611C823A396EF6712CE0F712F09B9B4F3135E3E0AA3230FB9B6D08D1E16<br /><br />

#140 1QKBaU6WAeycb3DbKbLBkX7vJiaS8r42Xo<br />
-pk 80000000000000000000000000000000000<br />
-pke FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pb 031F6A332D3C5C4F2DE2378C012F429CD109BA07D69690C6C701B6BB87860D6640<br /><br />

#145 19GpszRNUej5yYqxXoLnbZWKew3KdVLkXg<br />
-pk 1000000000000000000000000000000000000<br />
-pke 1FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pb 03AFDDA497369E219A2C1C369954A930E4D3740968E5E4352475BCFFCE3140DAE5<br /><br />

#150 1MUJSJYtGPVGkBCTqGspnxyHahpt5Te8jy<br />
-pk 20000000000000000000000000000000000000<br />
-pke 3FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pb 03137807790EA7DC6E97901C2BC87411F45ED74A5629315C4E4B03A0A102250C49<br /><br />

#155 1AoeP37TmHdFh8uN72fu9AqgtLrUwcv2wJ<br />
-pk 400000000000000000000000000000000000000<br />
-pke 7FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pb 035CD1854CAE45391CA4EC428CC7E6C7D9984424B954209A8EEA197B9E364C05F6<br /><br />

#160 1NBC8uXJy1GiJ6drkiZa1WuKn51ps7EPTv<br />
-pk 8000000000000000000000000000000000000000<br />
-pke FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<br />
-pb 02E0A8B039282FAF6FE0FD769CFBC4B6B4CF8758BA68220EAC420E32B91DDFA673<br />

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

All arrays(Baby, Giant) and hashtable saved to the disk for fast spinup solver next time (if parameters will not changed). <br />
After you have the arrays saved, you will need less RAM to launch. <br />

## Building
- To compile Bitreverse you need [Purebasic v5.31](https://www.purebasic.com)
