### In order to contribute to the genesis library, a free search engine that could help you find free ebooks to engage your knowledges in free way, this is an simple guild for self-hosting for distributed storage backend for the engine.

Here are the IPFS UI address for the Libgen:

- https://libgen.crypto/
- https://ipfs.io/ipns/libgen.crypto/
  If you can't go to that address, please refer to [here](Guide.md) (open with a browser) to see the detail guide.

# I.Requirements

- Install Docker: https://www.docker.com/
- At least 100 GB Disk Capacity
- Moderate Network Bandwidth

# II.Get started:

## 1. Create docker container:

```
docker run -d \
--name go-ipfs \
-v $HOME/ipfs/export:/export \
-v $HOME/ipfs/data:/data/ipfs \
-p 4001:4001 \
-p 127.0.0.1:8080:8080 \
-p 127.0.0.1:5001:5001 \
ipfs/go-ipfs:latest
```

## 2. Start container:

```
docker start go-ipfs
```

## 3. Download the merkle tree of all the ebooks and pin all the ebooks:

```
docker exec -it go-ipfs sh
```

Run these script inside the container

```
wget https://pastebin.com/raw/4KBmyC9v
tail -n $(($(wc -l /4KBmyC9v | awk '{print $1}')-1)) /4KBmyC9v | awk -F"," ' {print $3}' | ipfs pin add --progress
```

### ALL THINGS ARE DONE, JUST WAIT FOR THE EBOOKS ARE DOWNLOADED TO YOUR STORAGE DEVICES. IT MAY TAKE SEVERAL WEEKS IF YOU RUN IT 24/7.

---

# III. Use the IPFS UI:

## 1. Access to this address to view the IPFS status http://127.0.0.1:5001/webui/

## 2. Discovery the book that you pin:

If you pin books in address, for example: `bafykbzaceaeofefgje22l7rhgtcgs22m32f4ysw5nqa3ty5zawfovqam7pj2c` (second line in the pin address: [PIN_ADDRESS](PIN_ADDRESS)), you could access through:

[`http://127.0.0.1:8080/ipfs/bafykbzaceaeofefgje22l7rhgtcgs22m32f4ysw5nqa3ty5zawfovqam7pj2c`](http://127.0.0.1:8080/ipfs/bafykbzaceaeofefgje22l7rhgtcgs22m32f4ysw5nqa3ty5zawfovqam7pj2c)

## References:

- #### [Free Read](!https://freeread.org/ipfs.html)
- #### [Awesome Genesis Library Repository](!https://github.com/freereadorg/awesome-libgen)
