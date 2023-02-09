<h1 align="center"><strong>Tutorial Testnet Muon<strong></h1>

- [Website](https://muon.net/)
- [Discord](https://discord.gg/Q6Q5auhb49)
- [Doc offcial](https://docs.muon.net/muon-network/muon-nodes/joining-the-testnet-alice)
- [Dashbord Node](https://alice.muon.net/)

## Spesifikasi Minimum

| Komponen    | Requirements minimal                          |
| ----------- | --------------------------------------------- |
| sistem      | Ubuntu 18.04 atau lebih tinggi                |
| CPU         | 2 cores / 4 Cores                             |
| RAM         | 2 GB / 8 GB                                   |
| Penyimpanan | 20 GB HDD                                     |
| Koneksi     | 20 mbps / 50 mbps upload & bandwidth download |

<h2 align="center"><strong>Setup Wallet</strong></h2>

- disarangkan gunakan wallet baru!
- buka website [chainlist.org](https://chainlist.org/)
- add RPC BSC testnet 'pilih server RPC score dan privacy **aktif**'

[![addbsc.png](https://i.postimg.cc/W4Xqf4Qy/addbsc.png)](https://postimg.cc/JyHhsR73)

<h2 align="center"><strong>Setup Dashbord NODE</strong></h2>

- Buka [Dashbord Node](https://alice.muon.net/)
- Connect wallet
- Faucet BNB testnet juga [Faucet](https://testnet.bnbchain.org/faucet-smart)
- mint 1000 ALICE
- Klik **Next Step** | Klik **APPROVE**
- lanjut step SETUP NODE | untuk mendapatkan address Node & Peer id

[![muon2.png](https://i.postimg.cc/DyVxd21h/muon2.png)](https://postimg.cc/23wdCNH9)

<h2 align="center"><strong>Setup NODE</strong></h2>

### Install & Update

```
sudo apt update
```

```
sudo apt install curl tar wget tmux htop net-tools clang pkg-config libssl-dev jq build-essential git make ncdu docker-compose -y
```

```
systemctl restart docker
```

```
curl -SL https://github.com/docker/compose/releases/download/v2.5.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
```

```
chmod +x /usr/local/bin/docker-compose
```

```
ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

```
docker --version
```

```
apt-get install screen git
```

<h2 align="center"><strong>RUN NODE</strong></h2>

### clone & Run

```
git clone https://github.com/muon-protocol/muon-node-js.git --recurse-submodules --branch testnet
```

```
cd muon-node-js
```

```
docker-compose build
```

```
docker-compose up -d
```

```
screen -Rd moun-node
```

`ctrl A D` untuk Menyimpan Screen berJalan di Background.
Jika anda Ingin Kembali ke Screen Yang Sedang Jalan, Gunakan Perintah `screen -Rd moun-node`

```
docker compose logs -f
```

- Buka `http://IP-VPS:8000/status`
- Bagian IP-VPS ganti dengan Ip VPS anda
- Paste di browser
- Untuk mendapatkan Address NODE & Peer ID
- Copy dan Set di [Dashbord Node](https://alice.muon.net/) anda
- Next Klik Add NODE dan approve wallet

[![ip.png](https://i.postimg.cc/nrwT6DLS/ip.png)](https://postimg.cc/RJKctqKw)

- Buka lagi `http://IP-VPS:8000/status`
- Jika node berjalan dengan benar, akan menerima respons json yang `"isOnline":true`

[![ip.png](https://i.postimg.cc/6qbqndW0/ip.png)](https://postimg.cc/fSXMhS0t)

- Buka [Dashbord Node](https://alice.muon.net/) relog dan connect ulang untuk melihat reward dan status NODE!

<h2 align="center"><strong>Backup dan Save</strong></h2>

## Backup file Muon

```
cd muon-node-js
```

```
docker cp muon-node:/usr/src/muon-node-js/.env ./backup.env
```

- Download & simpan file backup.env

## Memindahkan NODE Ke VPS Baru
Noted: ini khusus jika ingin memindahkan NODE ke VPS baru!

- Ikuti Tutorial dibagian **Setup NODE** di VPS baru
- lanjut clone NODE Muon

```
git clone https://github.com/muon-protocol/muon-node-js.git --recurse-submodules --branch testnet
```

- setelah berhasil masuk ke folder

```
cd muon-node-js
```

- Upload file `backup.env` yang di simpan sebelumnya di VPS lama
- Install & Run File backup

```
docker cp backup.env muon-node:/usr/src/muon-node-js/.env
```

```
docker-compose restart
```

- Buka http://IP-VPS:8000/status
- Bagian IP-VPS ganti dengan Ip VPS anda
- Paste di browser

Jika proses backup berhasil, status node akan muncul `address` dan `peerId` dari node yang di backup sebelumya.

<h2 align="center"><strong>Perintah-perintah Berguna</strong></h2>

check list docker yang berjalan

```
docker ps
```

Stop NODE

```
docker stop [nama atau ID container]
```

Detele docker muon

```
docker rm muon-node
```

paska berhenti dan hapus

```
docker kill muon-node && docker rm muon-node
```

check log node gunakan di dalam `cd muon-node-js`

```
docker compose logs -f
```

[![Screenshot-2023-01-24-043510.png](https://i.postimg.cc/7L0dLYc6/Screenshot-2023-01-24-043510.png)](https://postimg.cc/94XJ8Vc5)

### Art-Team INFO

noted: **art team** here does not have any specific goals or intentions, they only collect data and share it with everyone.

untuk INFO Testnet lainya Silahkan join Discord 👇

[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/ArtSy5team)
[![Discord](https://img.shields.io/badge/discord-7289d9?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/EAKEdZU6c8)
[![Github](https://img.shields.io/badge/GitHub-171515?style=for-the-badge&logo=GitHub&logoColor=white)](https://github.com/Art-Sy5team)
[![trakteer](https://img.shields.io/badge/trakteer.id-e31e1e?style=for-the-badge&logo=ko-fi&logoColor=white)](https://trakteer.id/Art-Sy5team/tip)
