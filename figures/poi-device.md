~~~~ ascii-art
                  |---------------|
                  |   P-PNC(s),   |
                  |   O-PNC(s),   |
                  |   MDSC        |
                  |---------------|
                          ^
                          |  (A)
      +-------------------|-------------------+
      |                   |                   |  Packet Device
      |                   V                   |  Vendor X
      |        |---------------------|        |  (i.e, Host)
      |        |                     |        |
      |        v                     v        |
      |  |-----------|          |----------|  |
      |  | Packet    |          | Coherent |  |
      |  | Function  |..........| Plug     |  |
      |  | Data      |          | Data     |  |
      |  |-----------|          |----------|  |
      |        .                      .       |
      |        .                      . (B)   |
      |        .                      .       |
      |  |--------------|   (C)   |------------------|  (D)
      |  |Packet Device |<------->| Coherent Plug #1 |=======
      |  |Function      |<---|    | Vendor X         |
      |  |--------------|    |    |------------------|
      |                      |                |
      |                      |    |------------------|
      |                      |--->| Coherent Plug #2 |=======
      |                           | Vendor Y         |
      |                           |------------------|
      |                                       |
      +---------------------------------------+

  Legend
    (A) Packet device management interfaces (e.g., YANG, NETCONF, gNMI, etc.)
    (B) CMIS interface between Optical pluggable and Host
    (C) Host side of the optical pluggable (towards the Host)
    (D) Media side of the optical pluggable (towards Optical/Photonic network)
~~~~
