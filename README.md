#  Atividade 4 — Ambiente Hierárquico de Rede Local

###  Informações do Atividade

**Curso:** Tecnologia em Redes de Computadores
**Disciplina:** Comutação de Redes Locais
**Ferramenta:** Cisco Packet Tracer 8.2.2

---

##  Sobre o projeto

Este projeto apresenta uma simulação de um **ambiente hierárquico de rede local**, utilizando uma estrutura de **3 camadas: Núcleo, Distribuição e Acesso**, com um roteador de borda no topo da rede.

A atividade foi desenvolvida no **Cisco Packet Tracer 8.2.2**.

---

##  Topologia da rede
<img width="1361" height="717" alt="image" src="https://github.com/user-attachments/assets/7ebbd6d4-eb37-4934-8646-32964cb0996f" />


 ##  Equipamentos da rede

| Camada           | Quantidade | Modelo                      | Nome            |
| ---------------- | ---------: | --------------------------- | --------------- |
| Borda/Roteamento |          1 | Router 2811                 | Router1         |
| Núcleo           |          2 | Multilayer Switch 3650-24PS | CORE0, CORE1    |
| Distribuição     |          2 | Multilayer Switch 3650-24PS | DIST0, DIST1    |
| Acesso           |          4 | Switch 2960-24TT            | acesso0–acesso3 |
| Desktops         |          4 | PC-PT                       | PC0–PC3         |
| Laptop           |          4 | Laptop-PT                   | Laptop0–Laptop3 |
| Servidor         |          1 | Server-PT                   | Server0         |

---

##  Cabeamento

###  Roteador → Núcleo

* `Router1 Fa0/0` ↔ `CORE0`
* `Router1 Fa0/1` ↔ `CORE1`
* Cabo: **Copper Straight-Through**

###  Núcleo → Núcleo

Foram utilizados **4 links GigabitEthernet em paralelo**, preparados para uma futura configuração de EtherChannel.

* `CORE0 Gi1/0/2` ↔ `CORE1 Gi1/0/2`
* `CORE0 Gi1/0/3` ↔ `CORE1 Gi1/0/3`
* `CORE0 Gi1/0/4` ↔ `CORE1 Gi1/0/4`
* `CORE0 Gi1/0/5` ↔ `CORE1 Gi1/0/5`

**Capacidade:** 4 × 1 Gbps = **4 Gbps agregados** quando o EtherChannel for ativado.

###  Núcleo → Distribuição

Foram utilizados módulos ópticos **GLC-LH-SMD** nas portas de uplink.

* `CORE0 Gi1/1/1` ↔ `DIST0 Gi1/1/1`
* `CORE0 Gi1/1/2` ↔ `DIST0 Gi1/1/2`
* `CORE1 Gi1/1/1` ↔ `DIST1 Gi1/1/1`
* `CORE1 Gi1/1/2` ↔ `DIST1 Gi1/1/2`

**Meio físico:** Fibra óptica
**Capacidade:** 2 × 1 Gbps = **2 Gbps agregados** quando o EtherChannel for ativado.

###  Distribuição → Acesso

* `DIST0` ↔ `acesso0`
* `DIST0` ↔ `acesso1`
* `DIST1` ↔ `acesso2`
* `DIST1` ↔ `acesso3`

Todos utilizando **Copper Straight-Through**.

###  Acesso → Hosts

* `acesso0` → PC0 e Laptop0
* `acesso1` → PC1 e Laptop1
* `acesso2` → PC2 e Laptop2
* `acesso3` → PC3, Laptop3 e Server0

---

##  Configurações realizadas

A atividade foi realizada principalmente na parte física da rede.

Não foram aplicadas configurações de:

* VLAN
* Roteamento
* EtherChannel

As interfaces conectadas foram habilitadas utilizando `no shutdown`.
<img width="643" height="664" alt="image" src="https://github.com/user-attachments/assets/e0e38c29-bd8b-4d96-8ac8-0c1f25f8a96c" />


Também foram inseridos os módulos de fibra **GLC-LH-SMD** nos equipamentos correspondentes.

###  Salvamento da configuração

<img width="1362" height="722" alt="image" src="https://github.com/user-attachments/assets/a1ff3d44-bae8-47c5-8b7d-6ece8a49925e" />



---

##  Endereçamento IP — Configuração Extra

Para testar a comunicação entre os dispositivos, foi utilizada a rede **192.168.1.0/24**.

| Dispositivo | Endereço IP  | Máscara       |
| ----------- | ------------ | ------------- |
| PC0         | 192.168.0.1 | 255.255.255.0 |
| Laptop0     | 192.168.0.2 | 255.255.255.0 |
| PC1         | 192.168.0.3 | 255.255.255.0 |
| Laptop1     | 192.168.0.4 | 255.255.255.0 |
| PC2         | 192.168.0.5 | 255.255.255.0 |
| Laptop2     | 192.168.0.6 | 255.255.255.0 |
| PC3         | 192.168.0.7 | 255.255.255.0 |
| Laptop3     | 192.168.0.8 | 255.255.255.0 |
| Server0     | 192.168.0.9 | 255.255.255.0 |

A comunicação foi validada utilizando **ping entre hosts de diferentes switches de acesso**.

<img width="693" height="706" alt="image" src="https://github.com/user-attachments/assets/f1190dac-6ce4-48a2-9065-1dfc285bd3b7" />
<img width="692" height="706" alt="image" src="https://github.com/user-attachments/assets/41690dac-2cef-4ec6-b5ea-11bc99973f68" />
<img width="691" height="703" alt="image" src="https://github.com/user-attachments/assets/02b01eb0-1b1c-42ff-a0a8-88fbcbc657b3" />
<img width="691" height="708" alt="image" src="https://github.com/user-attachments/assets/036329c4-577a-41bc-878f-354f9a33ac81" />
<img width="679" height="719" alt="image" src="https://github.com/user-attachments/assets/828c9758-b53b-4192-beec-1d3c3d04fdaf" />



Desenvolvido para a disciplina de **Comutação de Redes Locais**.
