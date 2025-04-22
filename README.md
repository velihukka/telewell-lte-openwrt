# telewell-lte-openwrt

![TeleWell TW-LTE/4G/3G Reititin](https://telewell.fi/wp-content/uploads/2024/12/tw_lte_reititin-1-1.jpg)

Otsikon mukainen reititin tuli käsiini, ja fiksumman firmiksen saaminen kiinnostaa. 

Tuntomerkit: **TeleWell TW-LTE/4G/3G Reititin**, valmistajan firmissivu: [Lataukset - TeleWell 2.0](https://www.telewell.fi/)

Vastaavaa rautaa löytyy muistakin reitittimistä, jotka jo tuettuna
[https://openwrt.org/toh/lb-link/bl-w1200](https://openwrt.org/toh/lb-link/bl-w1200)

Telewellin webbipäivityssysteemi haluaa tiedoston oikeanlaisella headerillä. Onneksi sen toiminta oli todella helppo keksiä; headeri on seuraavanlainen ja 100 tavun pituinen:

```
52616C696E6B000000000000000000000000000000000000ABCD1234AA19955F000000004E523231323000000000000000000000000000000000000054656C6577656C6C0000000000000000000000000000000000000000000000000000000000000000
```

**AA19955F** (4 tavua 29-32) on lopputiedoston `crc32`-summa, tuossa `ABCD1234` jälkeen.

LB-Link -reitittimen initramfs tiedostoa muuttamalla sai reitittimen boottaamaan OpenWRT:hen, mutta sysupgrade flash teki laitteesta tiiliskiven. Pelastuu onneksi valmistajan ohjeilla : [Emergency flash](https://telewell.fi/wp-content/uploads/2024/12/tw-lte-reititin_emergency.pdf). K.o. initramfs tiedosto löytyy tästä reposta. 
