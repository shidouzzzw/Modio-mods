# ⛏ Modio

### Temiz · Hızlı · Sade — Minecraft mod ve sunucu arşivi

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Web-007aff.svg)](#)
[![No Backend](https://img.shields.io/badge/backend-none-success.svg)](#)
[![Turkish](https://img.shields.io/badge/lang-Türkçe-red.svg)](#)

> Hesap yok. Reklam yok. Sadece aradığın mod, client, texturepack, plugin ve sunucu — tek ekranda.

**[▶ Siteyi aç](https://shidouzzzw.github.io/Modio-mods/)** 

---

## Neden Modio?

Çoğu mod sitesi ya da Discord sunucusu dağınık, yavaş veya reklam dolu.  
Modio bunun tersi:

| | |
|---|---|
| ⚡ **Anında yüklenir** | Framework yok, sadece HTML + CSS + JS |
| 📁 **Klasör mantığı** | Platforma göre ayrılmış, numaralı listeler |
| 🖥️ **Sunucu sıralaması** | Aktif oyuncu sayısına göre canlı ranking |
| ❤️ **Favoriler** | Cihazında saklanır, hesap istemez |
| 🌙 **Koyu tema** | Göz yormayan arayüz |
| 🛠️ **Tek tık admin** | GitHub token ile mod/sunucu ekle, site anında güncellenir |

---

## Ne var içinde?

- **Bedrock Modları** — `.mcpack` / `.mcaddon`
- **Java Clientler** — Lunar, Badlion, LabyMod tarzı istemciler
- **Texturepack’ler** — Bedrock doku paketleri
- **Plugin’ler** — Paper / Spigot `.jar`
- **Sunucular** — Java & Bedrock, IP, sürüm, oyuncu sayısı, detaylı açıklama
- **Rehber** — Yükleme, kurulum, yedekleme ve sorun giderme

---

## Ekran görüntüleri

> `docs/screenshots/` klasörüne kendi görsellerini koy.

| Ana sayfa | Klasörler | Sunucu detayı | Admin |
|-----------|-----------|---------------|--------|
| ![home](docs/screenshots/home.png) | ![folders](docs/screenshots/folders.png) | ![server](docs/screenshots/server.png) | ![admin](docs/screenshots/admin.png) |

---

## Nasıl çalışıyor?

```
Kullanıcı → index.html
                ↓
         GitHub raw JSON
         (mods.json + servers.json)
                ↓
         Kartlar / sıralama / arama
```

- Veri **GitHub**’da tutulur
- Admin paneli token ile dosya yükler ve JSON’u günceller
- Site her açılışta taze veriyi çeker (`cache: no-store`)
- Favoriler ve tema **localStorage**’da kalır — sunucuya gitmez

---

## Hızlı başlangıç

### 1. Fork / clone

```bash
git clone https://github.com/shidouzzzw/Modio-mods.git
cd Modio-mods
```

### 2. Kendi deponu bağla

`index.html` içinde:

```js
const GITHUB_OWNER  = "SENIN_KULLANICI_ADIN";
const GITHUB_REPO   = "Modio-mods";
const GITHUB_BRANCH = "main";
```

### 3. Yayınla

| Platform | Not |
|----------|-----|
| **GitHub Pages** | Settings → Pages → `main` branch |
| **Cloudflare Pages** | Depoyu bağla, root dizin |
| **Netlify / Vercel** | Aynı şekilde tek tık |

### 4. Admin’i aç

1. `admin.html` dosyasını tarayıcıda aç  
2. GitHub kullanıcı adı + repo + **Personal Access Token** (`repo` yetkisi)  
3. Mod veya sunucu ekle → commit otomatik gider → site güncellenir  

Token sadece tarayıcında saklanır.

---

## Veri formatı

### Mod (`data/mods.json`)

```json
{
  "id": 1,
  "name": "Better on Bedrock",
  "desc": "Kısa açıklama",
  "platform": "bedrock",
  "color": "blue",
  "downloads": "1.2M",
  "rating": "4.8",
  "version": "1.21",
  "author": "Yapımcı",
  "url": "https://raw.githubusercontent.com/.../mods/dosya.mcpack",
  "icon": "https://raw.githubusercontent.com/.../icons/dosya.png"
}
```

`platform`: `bedrock` · `javaclient` · `bedrocktexture` · `javaplugin`

### Sunucu (`data/servers.json`)

```json
{
  "id": 1,
  "name": "Örnek SMP",
  "desc": "Detaylı sunucu açıklaması",
  "platform": "java",
  "version": "1.21.1",
  "players": 240,
  "color": "green",
  "ip": "play.ornek.net",
  "website": "https://ornek.net",
  "icon": "https://raw.githubusercontent.com/.../icons/server-ornek.png"
}
```

`players` **sayı** olmalı (sıralama buna göre).

---

## Proje yapısı

```
├── index.html       # Ana site
├── admin.html       # Yönetim paneli
├── data/
│   ├── mods.json
│   └── servers.json
├── mods/            # İndirme dosyaları
├── icons/           # Görseller
└── README.md
```

---

## SEO — Google’da çıksın diye

1. Custom domain bağla (GitHub Pages destekler)  
2. `<title>` + `meta description` + Open Graph ekle  
3. [Google Search Console](https://search.google.com/search-console) → site ekle  
4. Düzenli içerik ekle (yeni mod / sunucu)  
5. Sosyal medya linklerini footer’da tut  

---

## Yasal

Modio bir arşiv arayüzüdür. Listelenen içeriklerin hakları geliştiricilerine aittir.  
Modio sahibi, resmi dağıtıcı veya temsilci değildir. Kullanım ilgili projenin lisansına tabidir.

---

## Katkı

Issue ve PR açık. Büyük değişiklik için önce issue açman yeterli.

⭐ Faydalı bulduysan star at — görünürlük artar.

---

**Modio** — Minecraft için gereksiz şişkinlik olmadan, sadece aradığını bul.
