```bash
sudo apt install aria2 -y
# -x, --max-connection-per-server=<NUM>; -s, --split=<N>; -c, --continue [true|false]; -o, --out=<FILE>
aria2c -x 16 -s 16 -c --min-split-size=1M -o <FILENAME> [<URI><MAGNET>]
```

```bash
# -c, --continue; open follow redirect link optional by default, save to local file rather than stdout by default
wget -c [URL]
wget -qO- [URL] | dd of=/dev/vda bs=4M status=progress && sync
```

```
# -L, --location; transfer to stdout rather than local file by default
curl -fsSL [URL] | dd of=/dev/vda bs=4M status=progress && sync  # without an option `o` will not save to local, just print stream
curl -L -C - -O <URL>  # name saved same as link provided default
curl -L -C - -o <FILENAME> <URL>  # save as a customized name
```

Check hash, all ways should be same
```
sha256sum [FILENAME]
dd if=/dev/vdb bs=4M count=$(( (822083584 + 4194304 - 1) / 4194304 )) status=progress | sha256sum
dd if=/dev/vdb1 bs=4M status=progress | sha256sum
dd if=/dev/vdb bs=4M status=progress | sha256sum
```
