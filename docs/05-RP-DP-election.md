३)	Root/Designated port Election
```
हामिलाई थाहा छ, Root/Designated port Election हुदाँ पहिला path cost हेर्छ, यो बराबर भयो भने bridge-id  हेर्छ । bridge-id  पनि बराबर भएको खण्डमा switch ले port value हेरेर election गर्छ । Ethernet प्रविधिमा path cost यसप्रकार छः
Interface			Path Cost
Ethernet			    100
FastEthernet			19
GBEthernet 		  	4

Topology मा मैले सबै तार FastEthernet भएकोले path cost 19

पहिला Root switch (sw2) को port सधै Designated Port हुन्छ । यो सधै Forwarding state मा बसेर BPDU पठाउने र traffic receive गर्ने काम गर्छ । 
```
Sw1:
```
mac address: 00D0:BC0C:208B
Non-Root switch        Fa0/1
                | SW1 | ---------->
            Fa0/3   |
                    |
        Fig 2: Non-root switch (sw1)

Sw1 को Fa0/1 → Root switch (Sw2) मा सिधै जोडिएको → Root Port (RP)
Root Port भनेको Non-root switch को त्यो port हो जुन Root switch सम्म पुग्ने सबैभन्दा कम cost को path मा हुन्छ। प्रत्येक Non-root switch मा एउटा मात्र Root Port हुन्छ।
```
sw3:
```
0030:A397:5A59
Non-Root switch    /
            |    /
     Fa0/3  |   /Fa0/2
         | sw3 |
    Fig 3: Non-root switch (sw3)

Sw3 को Fa0/2 → Root switch (Sw2) मा सिधै जोडिएको → Root Port (RP)
```
```
mac address: 00D0:BC0C:208B
Non-Root switch        Fa0/1
                | SW1 | ---------->
            Fa0/3   |
                    |       /     
                    |     /
             Fa0/3  |   /Fa0/2
                 | sw3 |   
         0030:A397:5A59
        Non-Root switch
Fig 4: Non-Root switch (sw1-sw3)

Sw1 Fa0/3 ↔ Sw3 Fa0/3 को बीचमा election यसरी हुन्छ:
Path cost calculation:
Sw1 को Fa0/3 बाट Root (Sw2) सम्म:
  Sw1 → Sw3 → Sw2 = 19 + 19 = 38

Sw3 को Fa0/3 बाट Root (Sw2) सम्म:
  Sw3 → Sw2 = 19 (Fa0/2 = Root Port)
  तर यो link Sw1-Sw3 को बीचको हो,
  दुवैतर्फबाट cost बराबर = 38
Path cost बराबर भएकोले Bridge-ID हेर्छ:
Sw1: 00D0:BC0C:208B
Sw3: 0030:A397:5A59  ← सानो = Designated Port
Sw3 को Bridge-ID सानो भएकोले Sw3 को Fa0/3 = Designated Port (DP) Sw1 को Fa0/3 = Blocking state
```
