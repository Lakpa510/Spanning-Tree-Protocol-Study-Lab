२)	Root/Non-root switch Election
```
हामिलाई थाहा छ, Root/Non-root switch Election हुँदा सबैभन्दा पहिला priority value हेर्छ, त्यसपछि Bridge-ID (MAC address) हेर्छ। सानो value भएको switch Root switch बन्छ।
यहाँ सबै switch को priority value 32768 (default) समान भएकोले Bridge-ID को आधारमा election हुन्छ:

Sw1: 00D0:BC0C:208B
Sw2: 0010:11A4:69CE  ← सबैभन्दा सानो = ROOT SWITCH
Sw3: 0030:A397:5A59

Sw2 को Bridge-ID सबैभन्दा सानो भएकोले Root switch बन्छ। Sw1 र Sw3 Non-root switch बन्छन्।

Root switch ले के काम गर्छ ?
Root switch STP topology को reference point (anchor) हो — अन्य सबै switch ले Root switch सम्म पुग्ने best path calculate गर्छन्। Root switch ले:

सबै switch मा BPDU (Bridge Protocol Data Unit) पठाउँछ
Topology Change Notification (TCN) manage गर्छ
आफ्नो सबै port लाई Designated Port बनाउँछ
```
