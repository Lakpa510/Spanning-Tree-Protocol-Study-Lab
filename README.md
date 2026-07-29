Learning by doing
# Spanning Tree Protocol (STP) Lab

**Layer 2 Loop Prevention | Cisco Packet Tracer | CCNA Level**  
**Author:** Lakpa Sherpa |

---

## Topology

```
 00D0:BC0C:208B                           0010:11A4:69CE
 Non-Root (Sw1)                           Root (Sw2)

      Sw1 ─────Fa0/1(RP)────────Fa0/1(DP)──── Sw2
       │   \                              /  Fa0/2(DP)
     Fa0/3   \                          /      
    (DP)       \                      /      
       │         \X----------------─X     
       │         / \                    
     Fa0/3   Fa0/2   \         
     (BLOCK)   /       \           
      Sw3 ----------- Fa0/5 Sw4
     Fa0/5(DP)         Block
 0030:A397:5A59               000C:8559:E168
 Non-Root (Sw3)               Non-Root (Sw4)
 
```

| Switch | Priority | Bridge-ID | Role |
|--------|----------|-----------|------|
| Sw1 | 32768 | 00D0:BC0C:208B | Non-root |
| Sw2 | 32768 | 0010:11A4:69CE | **Root** |
| Sw3 | 32768 | 0030:A397:5A59 | Non-root |

---

## Lab Objectives

| # | Topic | Key Concept |
|---|-------|-------------|
| 1 | STP Overview | Loop prevention, broadcast storm |
| 2 | Root/Non-root Election | Priority → Bridge-ID |
| 3 | Root/Designated Port Election | Path cost → Bridge-ID → Port-ID |
| 4 | Port States | Disabled → Blocking → Listening → Learning → Forwarding |
| 5 | Root Primary/Secondary Config | Manual root election per VLAN |

---


## Future Labs (Planned)
- RSTP (Rapid Spanning Tree) — 802.1w
- MSTP (Multiple Spanning Tree) — 802.1s
- STP with PortFast + BPDU Guard
- STP topology change simulation

---
*STP election logic लाई manually calculate गर्दै, diagram मा verify गर्दै सिकिएको lab।*
