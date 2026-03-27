# 🗺️ user-flow.md — Kullanıcı Akışı

---

## Ana Akış (Happy Path)

```
┌────────────────────────────────────────────────────────┐
│                    KULLANICI GİRİŞİ                    │
└────────────────────────┬───────────────────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────────────────┐
│  1. KARŞILAMA — Köy Haritası (Köy Meydanı)            │
│                                                        │
│  • Toprak tonlarında interaktif köy haritası açılır   │
│  • 5 ada + Köy Meydanı birbirine yollarla bağlı       │
│  • Hayat Ağacı mevcut kolektif puanı yansıtır         │
│  • İmece Puanı sayacı sticky bar'da görünür           │
│  • Yücel AI kısa bir Sokratik selamlama yapar         │
└────────────────────────┬───────────────────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────────────────┐
│  2. KEŞİF — Ada Seçimi                                │
│                                                        │
│  🏛️ Sokratik Amfi  → Aktif tartışmaları görür        │
│  🛠️ Zanaat Atölyesi→ 5 görevi ve rehberleri inceler  │
│  🌾 Gelecek Tarlası→ 7 tekno-rehberi keşfeder        │
│  🎶 Radyo Köy      → Playlist ve bestelere göz atar  │
│  🤝 Gönül Köprüsü → Aktif ustaları ve gençleri listeler│
└────────────────────────┬───────────────────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────────────────┐
│  3. ETKİLEŞİM — Göreve Başlama                        │
│                                                        │
│  a) İçerik tüketir → Rehber okur, video izler        │
│  b) Tartışmaya katılır → Amfi'de fikir yazar          │
│  c) Göreve başlar → "Bu görevi yapacağım" butonuna basar│
│                                                        │
│  ┌────────────────────────────────────────────────┐   │
│  │  YÜCEL AI DEVREYEGİRER                         │   │
│  │  Tartışma 5 dk durursa:                        │   │
│  │  "Peki, bu durumun zıttını düşünürsek          │   │
│  │   toplumsal adalet nasıl etkilenirdi?"         │   │
│  └────────────────────────────────────────────────┘   │
└────────────────────────┬───────────────────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────────────────┐
│  4. ONAY — Fiziksel / Dijital Kanıt                   │
│                                                        │
│  [FİZİKSEL GÖREV]           [DİJİTAL GÖREV]          │
│  Fotoğraf yükle              Yazılı analiz gönder     │
│  "Gerçek hayata taştı" onayla Tartışmaya katkı ekle  │
│         │                           │                  │
│         └──────────┬────────────────┘                  │
│                    ▼                                   │
│           Yücel AI onaylar + Sokratik soru sorar      │
└────────────────────────┬───────────────────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────────────────┐
│  5. İMECE — Köy Meydanı'nda Kolektif Büyüme          │
│                                                        │
│  • İmece Puanı artar (kolektif, bireysel değil)       │
│  • Hayat Ağacı'nda değişim görünür:                   │
│    - Dikiş → Yaprak açar                              │
│    - Amfi katkısı → Meyve verir                       │
│    - Müzik → Yeni dal uzar                            │
│    - Usta buluşması → Çiçek açar                     │
│  • Yeni içerik/görev seviyeleri açılır               │
└────────────────────────────────────────────────────────┘
```

---

## Alt Akışlar

### 🏛️ A. Sokratik Amfi — Tartışma Akışı

```
Kullanıcı aktif tartışmayı açar
        │
        ▼
Mevcut yorumları okur
        │
        ▼
Kendi fikrini yazar (min. 3 paragraf)
        │
        ▼
[5 dakika sessizlik kalır mı?]
        │
   Evet ▼                Hayır ▼
        │                      │
Yücel AI müdahil olur    Diğer kullanıcılar
"Bu durumun zıttını      yanıt verir
düşünürsek..."                │
        │                     │
        └──────────┬──────────┘
                   ▼
         Tartışma derinleşir
                   │
                   ▼
         +5 İmece Puanı → Ağaç meyve verir 🍎
```

---

### 🛠️ B. Zanaat Atölyesi — Fiziksel Kanıt Akışı

```
Kullanıcı 5 görevden birini seçer
(Örn: "Temel Menemen Yapımı")
        │
        ▼
Adım adım rehber + video açılır
        │
        ▼
Yücel AI Sokratik soru sorar:
"Neden önce soğan/biber koyuyoruz,
 bunu hiç düşündün mü?"
        │
        ▼
Kullanıcı görevi fiziksel dünyada tamamlar
        │
        ▼
Fotoğraf yükleme ekranı açılır
        │
        ▼
"Fiziksel Dünyada Tamamladım" onay butonu
        │
        ▼
Yücel AI onaylar + değerlendirme sorusu sorar
        │
        ▼
+15 İmece Puanı → Ağaç yaprak açar 🍃
```

---

### 🌾 C. Gelecek Tarlası — Teknoloji Rehberi Akışı

```
Kullanıcı 7 rehberden birini seçer
(Örn: "Dijital Dedektif")
        │
        ▼
Adım adım rehber açılır
"WhatsApp haberi 30 saniyede nasıl doğrularsın?"
        │
        ▼
Pratik uygulama alanı:
Gerçek bir haber bağlantısı yapıştır → AI analiz eder
        │
        ▼
Yücel AI sorar:
"Peki bu tekniği öğrenmeden önce
 kaç yanlış haberi paylaşmış olabilirsin?"
        │
        ▼
Kullanıcı öğrendiklerini yazar
        │
        ▼
+8–18 İmece Puanı
```

---

### 🎶 D. Radyo Köy — Kolektif Beste Akışı

```
Kullanıcı "Haftanın Bestesi" projesini görür
        │
        ▼
Aylık tema açıklanır (Örn: "Toprak ve Kod")
        │
        ▼
Katkı türü seçer:
┌─────────────┬──────────────┬──────────────┐
│  Melodi     │    Söz       │  Ses Kaydı   │
│  (nota)     │   (güfte)    │  (mikrofon)  │
└──────┬──────┴──────┬───────┴──────┬───────┘
       └─────────────┴──────────────┘
                    │
                    ▼
       Katkı yüklenir → Kolektif albüme eklenir
                    │
                    ▼
       Radyo Köy'de yayınlanır → +25 İmece Puanı
```

---

### 🤝 E. Gönül Köprüsü — İki Yönlü Akış

```
ATADON TOPRAĞA (Usta → Genç)        TERSINE MENTORLUK (Genç → Usta)
        │                                       │
        ▼                                       ▼
Usta profili incelenir              Genç, "Usta Ol" butonuna basar
        │                                       │
        ▼                                       ▼
Randevu alınır                      Öğretecek konu girilir
(canlı sohbet / Bilgelik Postası)   (Örn: "Akıllı telefon kullanımı")
        │                                       │
        ▼                                       ▼
Görüşme gerçekleşir                 Eşleşme yapılır (uygun usta)
        │                                       │
        ▼                                       ▼
Genç, öğrendiklerini yazar          Görüntülü görüşme (15 dk)
        │                                       │
        └────────────────┬──────────────────────┘
                         ▼
              +10–30 İmece Puanı → Köyde çiçek açar 🌸
```

---

### 🌿 F. Köy Meydanı — Hayat Ağacı Akışı

```
Herhangi bir görev tamamlanır
        │
        ▼
İmece Puanı sisteme işlenir
        │
        ▼
[Puan eşiği kontrol edilir]
        │
   ┌────┴──────────────────────────────────┐
   │ 0–50 puan    │ 51–150   │ 151–300     │
   │ Filiz köy    │ Büyüyen  │ Çiçek açan  │
   │              │ köy      │ olgun köy   │
   └────┬─────────┴──────────┴─────────────┘
        │
        ▼
Köy görselinde anlık değişim:
  Dikiş dikme    → 🍃 Yaprak açar
  Amfi katkısı   → 🍎 Meyve verir
  Müzik katkısı  → 🌿 Dal uzar
  Usta buluşması → 🌸 Çiçek açar
  Eşik geçilince → 🏘️ Yollar düzelir, binalar yenilenir
```

---

## Kullanıcı Durumları

| Durum | Tetikleyici | Kazanım |
|-------|-------------|---------|
| **Filiz** | İlk ziyaret | Yücel selamlama sorusu sorar |
| **Öğrenci** | 10+ puan | Yeni içerikler açılır |
| **Üretici** | Fiziksel görev tamamlama | "Köy Üreticisi" rozeti |
| **Usta Adayı** | 50+ puan | Kendi alanında usta profili açma hakkı |
| **Köy Ustası** | 100+ puan | Yeni tartışma konusu açabilir |

---

## Hata Akışları

```
API Hatası (Yücel AI)
→ Önceden yazılmış Sokratik sorulardan biri sunulur
→ Kullanıcı deneyimi kesintisiz devam eder

Fotoğraf Yüklenemedi
→ "Tekrar dene" + alternatif: yazılı tanım ile görev tamamlama

Tartışma Kuralı İhlali
→ Yücel nazikçe uyarır: "Bunu Sokratik yöntemle söylesek nasıl olurdu?"
→ Tekrar ihlalde moderatöre otomatik bildirim

Usta Müsait Değil
→ "Bilgelik Postası"na yazılı soru bırakma seçeneği sunulur
```

---

*Teknik implementasyon için → `tech-stack.md` | Modül kaynak kodları için → `features/`*
