```
               +-----------------------------+
               |   Bus Controller (FCC)      |
               |      [BC Address 0x00]      |
               +-------------+---------------+
                             |
            =========================================
            ||       MIL-STD-1553 Dual Redundant Bus      ||
            =========================================
           /     |         |           |         |       \
          /      |         |           |         |        \
         v       v         v           v         v         v
+--------+  +--------+  +--------+  +--------+  +--------+  +--------+
|  RT1   |  |  RT2   |  |  RT3   |  |  RT4   |  |  RT5   |  | Future |
|  INS   |  | Radar  |  |Weapons |  |Engine  |  | Data   |  | Device |
|0x01    |  |0x02    |  |Mgmt    |  |Monitor |  |Logger  |  |(Spare) |
+--------+  +--------+  +--------+  +--------+  +--------+  +--------+
```


```
docker compose build
docker compose up -d
docker exec -it tool python network_tool.py
```


Target	IP Address	Command	Expected Response
rt1	172.28.1.11	BC -> RT1: Request Position	RT1: Position: LAT123...
rt2	172.28.1.12	BC -> RT2: Request Radar Scan	RT2: Radar: Target ...
rt3	172.28.1.13	BC -> RT3: Arm Weapons	RT3: Weapons: System Armed