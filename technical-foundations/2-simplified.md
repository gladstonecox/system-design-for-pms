# 2. Simplified version

The original draft with the review applied, at the same level of detail. Steps 1–6: a clerk adds one line and gets results right away. Steps A–D: a supplier sends a full invoice, gets a receipt, and it's processed in the background.

```mermaid
flowchart LR
    client["Client<br>AP clerk, Workday UI"]
    supplier["Supplier system<br>sends whole invoices"]
    gw["API gateway<br>• checks who is calling<br>• rate limits suppliers"]
    server["Server<br>• check fields allowed for item<br>(taxability, supplier)<br>• validate the line<br>• calculate line, tax, totals<br>• ignore duplicate requests<br>(idempotency key)"]
    queue[["Invoice queue<br>supplier invoices"]]
    db[("Database<br>invoices, line items, audit log")]

    client -->|"1: POST line item"| gw
    gw -->|"2: forward"| server
    server -->|"3: get fields + rules"| db
    db -->|"4: fields + rules"| server
    server -->|"5: save line + new totals"| db
    server -.->|"6: calculated fields, or errors"| client

    supplier -->|"A: send invoice"| gw
    gw -->|"B: add to queue"| queue
    gw -.->|"C: received (202)"| supplier
    queue -->|"D: process like steps 3–5"| server
```

Solid arrows are requests. Dashed arrows are responses.
