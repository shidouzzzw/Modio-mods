# Modio

**Temiz, hızlı ve sade Minecraft mod arşivi.**

Modio; Bedrock modları, Java client’lar, texturepack’ler, plugin’ler ve sunucuları tek bir arayüzde toplayan modern bir keşif sitesidir. Hesap gerektirmez, gereksiz animasyon yok, sadece aradığını bulman için tasarlandı.

---

## Özellikler

| Özellik | Açıklama |
|--------|----------|
| **Platform klasörleri** | Bedrock Modları · Java Clientler · Texturepack’ler · Plugin’ler · Sunucular |
| **Sunucu sıralaması** | Ana sayfada aktif oyuncu sayısına göre canlı sıralama |
| **Anında arama** | İsim, geliştirici veya anahtar kelime ile filtreleme |
| **Favoriler** | Beğendiğin içerikleri cihazda sakla (localStorage) |
| **Koyu / açık tema** | Tek tıkla geçiş, tercih hatırlanır |
| **Rehber** | Bedrock yükleme, client kurulumu, plugin ekleme ve yedekleme rehberleri |
| **Admin paneli** | GitHub token ile mod ve sunucu ekle / sil — site anında güncellenir |
| **Mobil öncelikli** | Alt navigasyon, sürükle-kapat modal, güvenli alan desteği |

---

## Ekran görüntüleri

> Buraya kendi ekran görüntülerini ekle (`docs/screenshots/` klasörü önerilir).

| Ana sayfa | Klasörler | Sunucu detayı |
|-----------|-----------|---------------|
| ![Home](docs/screenshots/home.png) | ![Folders](docs/screenshots/folders.png) | ![Server](docs/screenshots/server.png) |

---

## Teknoloji

- **Frontend:** Vanilla HTML · CSS · JavaScript (framework yok)
- **Veri:** GitHub raw JSON (`data/mods.json`, `data/servers.json`)
- **Depolama:** `localStorage` (favoriler + tema)
- **İkon / dosya host:** Aynı GitHub deposu (`icons/`, `mods/`)
- **Font:** Inter (Google Fonts)

Hiçbir backend, veritabanı veya üçüncü taraf analytics yoktur.

---

## Proje yapısı

```
├── index.html          # Ana site
├── admin.html          # Yönetim paneli
├── data/
│   ├── mods.json       # Mod listesi
│   └── servers.json    # Sunucu listesi
├── mods/               # İndirilebilir dosyalar (.mcpack, .jar, .zip …)
├── icons/              # Mod ve sunucu görselleri
└── README.md
```

### `mods.json` örneği

```json
[
  {
    "id": 1,
    "name": "Better on Bedrock",
    "desc": "Kısa açıklama",
    "platform": "bedrock",
    "color": "blue",
    "downloads": "1.2M",
    "rating": "4.8",
    "version": "1.21",
    "author": "Geliştirici",
    "url": "https://raw.githubusercontent.com/.../mods/better-on-bedrock.mcpack",
    "icon": "https://raw.githubusercontent.com/.../icons/better-on-bedrock.png",
    "iconSmall": "https://raw.githubusercontent.com/.../icons/better-on-bedrock-small.png"
  }
]
```

**platform değerleri:** `bedrock` · `javaclient` · `bedrocktexture` · `javaplugin`

### `servers.json` örneği

```json
[
  {
    "id": 1,
    "name": "Örnek SMP",
    "desc": "Survival + ekonomi. Detaylı sunucu açıklaması buraya.",
    "platform": "java",
    "version": "1.21.1",
    "players": 240,
    "color": "green",
    "ip": "play.ornek.net",
    "website": "https://ornek.net",
    "icon": "https://raw.githubusercontent.com/.../icons/server-ornek-smp.png"
  }
]
```

**platform değerleri:** `java` · `bedrock`  
`players` sayısal olmalıdır (sıralama buna göre yapılır).

---

## Kurulum

### 1. Depoyu çatalla veya klonla

```bash
git clone https://github.com/shidouzzzw/Modio-mods.git
cd Modio-mods
```

### 2. Siteyi yayınla

Statik hosting yeterlidir:

- **GitHub Pages** — Settings → Pages → branch `main`
- **Cloudflare Pages** / **Netlify** / **Vercel** — depo bağla, kök dizini seç
- Kendi sunucun — `index.html` ve `admin.html` dosyalarını yükle

`index.html` içindeki GitHub owner / repo / branch değerlerini kendi depona göre güncelle:

```js
const GITHUB_OWNER = "shidouzzzw";
const GITHUB_REPO  = "Modio-mods";
const GITHUB_BRANCH = "main";
```

### 3. Admin paneli

1. `admin.html` dosyasını tarayıcıda aç.
2. GitHub kullanıcı adı, repo adı, branch ve **Personal Access Token** gir.
3. Token oluştururken **classic** token seç ve `repo` yetkisini işaretle.
4. Token yalnızca tarayıcının `localStorage`’ında tutulur; hiçbir yere gönderilmez.

Bundan sonra:

- Mod ekle → dosya + ikon yüklenir, `mods.json` güncellenir  
- Sunucu ekle → `servers.json` güncellenir  
- Sil → listeden kaldırılır  

Site bir sonraki yenilemede yeni veriyi çeker (`cache: 'no-store'`).

---

## Admin kullanımı — kısa rehber

| Adım | Ne yapılır |
|------|------------|
| 1 | GitHub bilgilerini ve token’ı kaydet |
| 2 | Mod veya sunucu formunu doldur |
| 3 | Dosya / ikon seç (isteğe bağlı harici link de kabul edilir) |
| 4 | “Ekle” butonuna bas → commit otomatik oluşur |
| 5 | Siteyi yenile → içerik görünür |

**Silme notu:** Listeden silinen kayıt `mods.json` / `servers.json` dosyasından kaldırılır. Fiziksel dosyalar (`mods/`, `icons/`) GitHub’da kalır; istersen elle silebilirsin.

---

## Özelleştirme

- **Renkler:** CSS değişkenleri (`:root` ve `[data-theme="dark"]`)
- **Kategoriler:** `categories` dizisini `index.html` içinde düzenle
- **Rehber metinleri:** `footerInfo` objesi
- **Yasal / gizlilik:** Aynı `footerInfo` objesindeki ilgili anahtarlar

---

## SEO ve keşfedilebilirlik

Google’da çıkması için:

1. Siteyi bir domain’e bağla (GitHub Pages custom domain destekler).
2. `index.html` `<head>` içine anlamlı `title`, `meta description` ve Open Graph etiketleri ekle.
3. Google Search Console’a siteyi ekle ve sitemap gönder.
4. Düzenli içerik ekle (yeni mod / sunucu) — arama motorları taze içeriği sever.
5. Sosyal medya (Instagram / YouTube) linklerini footer’da tut; dışarıdan trafik SEO’ya da yardımcı olur.

---

## Yasal uyarı

Modio bir arşiv ve keşif arayüzüdür. Listelenen içeriklerin telif hakkı ilgili geliştiricilere aittir. Modio bu içeriklerin sahibi, resmi dağıtıcısı veya temsilcisi değildir. Kullanım, her projenin kendi lisans şartlarına tabidir.

---

## Katkı

Pull request’ler ve issue’lar açıktır. Büyük bir değişiklik planlıyorsan önce issue açman yeterli.

---

## Lisans

Bu arayüz kodu için dilediğin lisansı ekleyebilirsin. İçerik dosyaları (`mods/`, ikonlar) kendi orijinal lisanslarına tabidir.

---

**Modio** — Minecraft modları için temiz ve sade bir vitrin.
`)