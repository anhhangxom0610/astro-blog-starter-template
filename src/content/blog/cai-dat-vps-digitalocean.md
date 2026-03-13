---
title: "Cach cai dat VPS tren DigitalOcean tu A-Z"
description: "Huong dan tao Droplet, ket noi SSH va cau hinh bao mat co ban cho VPS DigitalOcean."
pubDate: "Mar 13 2026"
heroImage: "/blog-placeholder-1.jpg"
---

## Buoc 1: Tao Droplet trong Control Panel

Sau khi dang nhap DigitalOcean, bam **Create** va chon **Droplets** de mo trang tao VPS.

![Mo menu Create va chon Droplets](https://docs.digitalocean.com/screenshots/create.88f76a2e0fbab47d46467cfdb31a9a9396d289032523120cfbdf1b695f0aac34.png)

## Buoc 2: Chon region phu hop

Uu tien chon datacenter gan nguoi dung cua ban de giam do tre.

![Chon region trong trang tao Droplet](https://docs.digitalocean.com/screenshots/droplets/create/choose-region.d011879df45e3e0181f08f93d19a25e0315f8f16dc777a028424d58f86327995.png)

## Buoc 3: Chon cau hinh (size)

Voi website nho hoac tu hoc, co the bat dau tu goi Basic 1GB RAM va nang cap sau.

![Chon size cho Droplet](https://docs.digitalocean.com/screenshots/droplets/create/choose-size.1e141505aa37ca99c65e3c4139b8621301f8097de0a6c1afe97a4c55bc7747bd.png)

## Buoc 4: Them SSH key va tao Droplet

Neu co SSH key, hay them key de dang nhap an toan. Neu chua co, ban co the tao key moi:

```bash
ssh-keygen -t ed25519 -C "email@example.com"
cat ~/.ssh/id_ed25519.pub
```

Sau do dan public key vao DigitalOcean, dat ten Droplet, chon so luong va bam **Create Droplet**.

## Buoc 5: Dang nhap VPS qua SSH

Sau khi VPS khoi tao xong, ban se thay dia chi IP. Dang nhap nhu sau:

```bash
ssh root@your_server_ip
```

Neu ban su dung key, he thong se tu dong nhan key tren may.

## Buoc 6: Tao user moi va cau hinh co ban

Khong nen dung `root` de lam viec hang ngay. Hay tao user moi va cap quyen sudo:

```bash
adduser deploy
usermod -aG sudo deploy
```

## Buoc 7: Bat firewall (UFW)

Mo cac cong can thiet:

```bash
ufw allow OpenSSH
ufw enable
ufw status
```

## Buoc 8: Cap nhat he thong

```bash
apt update && apt upgrade -y
```

## Goi y nhanh ve stack phu hop

- **Web tĩnh / blog**: Nginx + SSL (Lets Encrypt)
- **Node.js**: Nginx reverse proxy + PM2
- **WordPress**: LEMP (Nginx + MySQL + PHP)

## Tong ket

Chi can 10-15 phut, ban da co mot VPS DigitalOcean san sang. Sau khi hoan tat cac buoc co ban,
ban co the cai them domain, SSL va he thong backup de van hanh on dinh hon.
