# 🌱 Yaşayan Okullar

> *"İş içinde, iş aracılığıyla, iş için eğitim."* — Köy Enstitüleri Felsefesi

**Yaşayan Okullar**, Köy Enstitüleri'nin kolektif üretim ve "iş içinde eğitim" felsefesini 21. yüzyılın dijital dünyasına taşıyan hibrit bir öğrenme ekosistemidir. Gençlerin teoriye boğulup asosyalleşmesi, el becerilerinden yoksun kalması ve eleştirel düşünme yetisini kaybetmesi sorununa; Sokratik tartışma, pratik yaşam becerileri ve vicdanlı teknoloji kullanımı ile çözüm üretir.

---
 Problem

Türkiye'deki kırsal bölgelerde yaşayan çocuklar, kaliteli eğitime erişimde ciddi imkansızlıklar ve fırsat eşitsizliği ile karşı karşıyadır. Mevcut eğitim sistemi çocukların günlük hayatından kopuk kalırken; yerel bilgiler, el becerileri ve geleneksel zanaatlar teknoloji çağında kaybolma tehlikesiyle karşı karşıya kalmaktadır.

🟢 Çözüm

Uygulama, öğrenmeyi gerçek hayatla buluşturur: tohumdan ağaca büyüyen bir köy metaforu üzerinden çocuklar zanaat atölyesi, tarla, mutfak gibi alanlardan görevler seçer ve bunları tamamlayarak kolektif bir **"Hayat Ağacı"**nı büyütürler.

Yücel (🦉) isimli AI rehber, bu süreçte şu rolleri üstlenir:

Sokratik Rehberlik: Cevap vermek yerine soru sorarak çocukları düşünmeye sevk eder ve tartışmaları canlı tutar.

Multimodal Doğrulama: Gemini API kullanarak, çocukların tamamladığı fiziksel görevlerin (dikiş, tamirat, tarım vb.) fotoğraflarını analiz eder ve görevleri doğrular.

Proaktif Motivasyon: Kullanıcı pasif kaldığında veya bir noktada tıkandığında durumu tespit ederek kişiselleştirilmiş motivasyon mesajları gönderir.

## 🗺️ Proje Özü

| Konu | Açıklama |
|------|----------|
| **Proje Adı** |Yaşayan Okullar|
| **Durum** | MVP Geliştirme |
| **Tema** | Toprak Tonları · Gök Mavisi · Doğa Yeşili |
| **Karakter** | Bilge · Sokratik · Üretken |
| **SKH Hedefleri** | Hedef 4 (Nitelikli Eğitim) · Hedef 10 (Eşitsizliklerin Azaltılması) |

---

## 🏘️ 6 Ada, 1 Köy

| Ada | Simge | Ruh | İşlev |
|-----|-------|-----|--------|
| **Sokratik Amfi** | 🏛️ | Sessiz kütüphane, ama zihinlerin çarpıştığı meydan | Klasik eserler ve güncel konuların Sokratik tartışması |
| **Zanaat Atölyesi** | 🛠️ | Dağınık ama üretken, ahşap kokulu | Dikiş, yemek, tamirat — kız/erkek işi ayrımı yok |
| **Gelecek Tarlası** | 🌾 | Tohumların (kodların) atıldığı modern sera | AI araçları etik ve yaratıcı kullanım rehberleri |
| **Radyo Köy** | 🎶 | Plak cızırtısı ile dijital tınıların buluşması | Müzik, kültür, kolektif beste, podcast |
| **Gönül Köprüsü** | 🤝 | Ağaç gölgesinde derin sohbet | Kuşaklar arası mentörlük, tersine mentörlük |
| **Köy Meydanı** | 🌿 | Herkesin birbirini gördüğü ana meydan | İmece takibi, Hayat Ağacı, kolektif puan |

---

## 🦉 Yücel AI — Sokratik Rehber

- **Rolü:** Cevap veren ansiklopedi değil, soru sordurtan Sokratik rehber
- **Müdahale:** Tartışma 5 dakikadan fazla durursa ateşi harlar
- **Felsefesi:** Yanlışı "öğrenme fırsatı" olarak kutlar
- **Motoru:** Anthropic Claude API

---

## 🌿 İmece & Hayat Ağacı

- Biri dikiş diktiğinde ağaç bir **yaprak** açar
- Biri Amfi'de çözüm ürettiğinde ağaç **meyve** verir
- Toplam puan köyün görsel kalitesini artırır (yollar düzelir, çiçekler açar)
- Puanlar **kolektiftir** — bireysel değil

---




🛠️ Kullanılan Teknolojiler

Frontend: HTML5, CSS3, Vanilla JavaScript ve React.

AI/Zeka: Gemini 2.0 Flash API (Google AI Studio) ve Anthropic Claude API.

Depolama: LocalStorage (Kullanıcı ilerlemesi ve oturum yönetimi için).

Tasarım: Google Fonts (Playfair Display, Crimson Pro, DM Sans).


## 🚀 Nasıl Çalıştırılır

```bash
# Repoyu klonla
git clone https://github.com/kullanici-adi/dijital-imece.git
cd dijital-imece

# HTML prototipi — doğrudan tarayıcıda aç
open features/index.html

# React versiyonu
cd dijital-imece-react
npm install
npm run dev
```

`.env` dosyasına API anahtarını ekle:

```env
VITE_ANTHROPIC_API_KEY=sk-ant-...
```

---

## 📁 Proje Yapısı

```
dijital-imece/
├── README.md
├── idea.md
├── user-flow.md
├── tech-stack.md
└── features/
    ├── index.html
    ├── amfi/
    ├── zanaat/
    ├── gelecek/
    ├── muzik/
    ├── gonul/
    └── meydan/
```

---

## 🔗 Yayın Linki

Yayın Linki (Replit): https://ai-buildathon--busranurkaya290.replit.app

Demo Video (YouTube): https://youtu.be/R0LAUvD661s

Her katkı, köyün bir yaprağını açar. 🌳
