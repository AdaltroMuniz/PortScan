#!/usr/bin/env python3

import sys
from scapy.all import *

conf.verb = 0

if len(sys.argv) != 2:
    print(f"Uso: {sys.argv[0]} <IP>")
    sys.exit(1)

portas = [21, 22, 23, 25, 80, 443, 110, 3389, 161, 139, 445]

pacote = IP(dst=sys.argv[1]) / TCP(dport=portas, flags="S")

resp, noresp = sr(pacote, timeout=3)

for resposta in resp:
    if TCP in resposta[1]:
        porta = resposta[1][TCP].sport
        flag = resposta[1][TCP].flags

        if flag == "SA":
            print(f"Porta {porta} ABERTA")
