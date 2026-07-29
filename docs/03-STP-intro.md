१)	Spanning Tree Protocol बारे छोटो जानकारी
```
STP (Spanning Tree Protocol) OSI Layer 2 मा काम गर्ने protocol हो। Switch network मा redundant path हुँदा broadcast storm र MAC table instability को समस्या आउँछ एउटा frame network भरि loop भएर घुम्दै रहन्छ र network नै ठप्प हुन्छ। STP ले redundant link मध्ये एउटालाई logic रूपमा block गरेर loop-free topology बनाउँछ, तर त्यो link fail भएमा backup को रूपमा automatically activate गर्छ।STP नभएको भए data पठाउन त सकिन्थ्यो तर broadcast storm ले network मै flood भएर सबै traffic ठप्प हुने थियो।
```
