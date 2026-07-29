५) Root Switch बनाउने Primary/Secondary Config.
```
Default मा Bridge-ID को आधारमा root switch election हुन्छ, तर production network मा हामीले manually root switch तोक्नु पर्छ नभए कुनै पनि switch root बन्न सक्छ। मैले यहाँ vlan config. गरेको छैन त्यसकारणले default vlan 1 को आधारमा lab गर्ने छु ।

Method 1 — Priority manually set गर्ने
Sw2(config)# spanning-tree vlan 1 priority 28672

Priority value 4096 को multiple मा मात्र हुन सक्छ: 0, 4096, 8192, 12288, 16384, 20480, 24576, 28672, 32768 (default)

सानो priority = Root switch बन्ने probability बढी।

Method 2 — Macro command (सजिलो तरिका)
sw1(config)# spanning-tree vlan 1 root primary
sw1(config)# spanning-tree vlan 1 root secondary

root primary ले automatically priority 24576 सेट गर्छ। root secondary ले automatically priority 28672 सेट गर्छ।

Primary root fail भएमा secondary automatically root बन्छ।

VLAN अनुसार root बाँड्ने (Load balancing):
Sw2(config)# spanning-tree vlan 1 root primary

sw1(config)# spanning-tree vlan 1 root secondary
sw1 मा root secondary बनाउने वित्तिकै sw3 को fa0/3 block state मा पुग्छ र sw1 को DP बन्छ ।
```
