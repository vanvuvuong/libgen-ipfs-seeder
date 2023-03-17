## This is a fully-decentralized application to query Library Genesis database hosted on IPFS.

---

Removing any dependency on central entities makes Library Genesis incredibly resilient to censorship attempts, and presents a chance to its users to support their website by helping host it if they wish.

- Latency, especially on first use, can be greater than normal; this is expected.
- Successive searches might fail due to rate-limiting by gateways.
- You may require or prefer an IPFS-to-HTTP(S) gateway due to lack of native IPFS support in mainstream browsers. Those gateways are a central component that nullify the aims of decentralization, and can be censored just as easily by your school/workplace, ISP, or your government.
  - For a browser with built-in IPFS support, try Brave or Opera. Alternatively, you can also add IPFS Companion extension to Firefox or Chrome (and Chrome derivatives, such as Edge or Vivaldi) and install IPFS Desktop.
- To resolve our dWeb domain names (see the footer), you may use Brave or Opera, both which have first-class support, or install PeerName browser extension in your browser.

---

## Fast local use

You can download this page to search locally without constant internet access:

1. Download recursively using wget (requires less than a GB of space):
   ```
   wget -m -nH -np -P libgen https://ipfs.io/ipns/libgen.crypto/
   ```
2. Start the HTTP server redbean:

```
# On Windows:

.\libgen\redbean-1.3.com -s -D . -l 127.0.0.1 -p 7671

# On Linux, macOS, and \*BSD:

bash -c './libgen/redbean-1.3.com -s -D . -l 127.0.0.1 -p 7671'
```

3. Visit http://127.0.0.1:7671/ and voilà!
   You may also copy the libgen folder to a USB drive or burn a CD for your friends and colleagues. :)

---

## How does this work?

[SQLite](https://sqlite.org/) compiled into [WebAssembly](https://webassembly.org/) fetches pages of the database hosted on IPFS through [HTTP range requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Range_requests) using [sql.js-httpvfs](https://github.com/phiresky/sql.js-httpvfs) layer, and then evaluates your query in your browser.
