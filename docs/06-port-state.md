४)	Port state
```
State	    BPDU/TCN पढ्छ?	MAC सिक्छ?  	Traffic Forward गर्छ?	  Duration
Disabled	  X	                X	          X	                  Administratively shutdown
Blocking	  	                X	          X	                  20 sec (Max Age)
Listening	  	                X	          X	                  15 sec (Forward Delay)
Learning	  	                	          X	                  15 sec (Forward Delay)
Forwarding	  	                	          	                  Normal operation

कुल convergence time: 20 + 15 + 15 = 50 seconds
यही कारणले गर्दा Voice VLAN को port मा PortFast राख्नुपर्छ — 50 second को delay IP phone को लागि अनावश्यक हो।
```
