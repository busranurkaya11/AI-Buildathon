# ⚙️ tech-stack.md — Kullanılan Teknolojiler & Seçim Gerekçeleri

---

## Genel Mimari

```
┌──────────────────────────────────────────────────────────┐
│                       KULLANICI                          │
│                 (Tarayıcı / Mobil)                       │
└─────────────────────────┬────────────────────────────────┘
                          │
                          ▼
┌──────────────────────────────────────────────────────────┐
│                  FRONTEND KATMANI                        │
│   React.js + Vite · Tailwind CSS · Framer Motion        │
│   SVG Köy Haritası · Hayat Ağacı · Modal Sistemi        │
└──────────┬───────────────────────────────┬───────────────┘
           │                               │
           ▼                               ▼
┌────────────────────┐       ┌─────────────────────────────┐
│    AI MOTORU       │       │        VERİ KATMANI          │
│  Anthropic Claude  │       │  LocalStorage (MVP)          │
│  claude-sonnet-4   │       │  → Firebase / Supabase (v2) │
│  (Yücel AI beyni) │       │  Kullanıcı · Puan · İçerik  │
└────────────────────┘       └─────────────────────────────┘
```

---

## 1. Frontend

### React.js + Vite

**Neden?**
- Hızlı geliştirme ortamı — `npm run dev` ile anında çalışır
- Her ada ayrı bir React component olarak modüler yapılabilir
- Cursor ile AI destekli kod yazımına en uygun framework
- Büyük ekosistem: ihtiyaç duyulacak her kütüphane mevcut

```bash
npm create vite@latest dijital-imece -- --template react
cd dijital-imece && npm install
```

---

### Tailwind CSS

**Neden?**
- Utility-first: toprak, gök, yeşil paletini saniyeler içinde tanımla
- Cursor ile yazarken sınıflar otomatik tamamlanır
- Responsive tasarım için hazır breakpoint sistemi

**Renk Paleti:**

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        toprak:        '#8B4513',
        'toprak-light':'#C4793A',
        'toprak-pale': '#F2E8DA',
        gok:           '#4A7FA5',
        'gok-light':   '#87CEEB',
        yesil:         '#3A6B35',
        'yesil-light': '#5A9E52',
        bej:           '#F5F0E8',
        kahve:         '#6B4C2A',
      }
    }
  }
}
```

---

### Framer Motion

**Neden?**
- Ada tıklama → modal açılış animasyonu
- Hayat Ağacı büyüme efektleri (yaprak, meyve, dal animasyonları)
- Köy görselinde puan geçişleri

```bash
npm install framer-motion
```

---

## 2. Köy Haritası & Hayat Ağacı

### SVG Tabanlı İnteraktif Harita

**Neden SVG?**
- Vektörel: Her ekran boyutunda keskin görünür
- `onClick`, `hover` state'leri doğrudan uygulanır
- CSS animasyonları ile yapraqlar, çiçekler canlandırılır

**Hayat Ağacı Mantığı (SVG + JS):**

```jsx
// components/LifeTree.jsx
const LifeTree = ({ score }) => {
  const leaves   = Math.floor(score / 5);   // Her 5 puan = 1 yaprak
  const fruits   = Math.floor(score / 20);  // Her 20 puan = 1 meyve
  const flowers  = Math.floor(score / 10);  // Her 10 puan = 1 çiçek

  return (
    <svg viewBox="0 0 400 500">
      {/* Gövde */}
      <rect x="190" y="300" width="20" height="150"
            fill="#5A3A15" rx="4"/>
      {/* Yapraklar — score'a göre render edilir */}
      {Array.from({ length: leaves }).map((_, i) => (
        <motion.ellipse
          key={i}
          cx={200 + Math.cos(i) * 60}
          cy={280 - i * 8}
          rx="18" ry="12"
          fill="#3A7A30"
          initial={{ scale: 0 }}
          animate={{ scale: 1 }}
          transition={{ delay: i * 0.1 }}
        />
      ))}
    </svg>
  );
};
```

---

## 3. AI Motoru — Yücel AI

### Anthropic Claude (claude-sonnet-4-20250514)

**Neden?**
- Sokratik yöntem için derin muhakeme kapasitesi
- Türkçe desteği güçlü
- Sistem komutu ile karakter tutarlılığı kolayca sağlanır

**Sistem Komutu:**

```
Sen Yücel'sin — bilge bir Köy Enstitüsü öğretmeni ve Sokratik bir filozofsun.

KURALLAR:
1. Kullanıcıya ASLA doğrudan cevap vermezsin.
2. Her yanıtın mutlaka bir soruyla bitmesi gerekir.
3. Tartışma 5 dakikadan fazla durursa müdahil olursun:
   "Peki, bu durumun zıttını düşünürsek toplumsal adalet nasıl etkilenirdi?"
4. Yanlış cevapları öğrenme fırsatı olarak kutlarsın.
5. Zanaat görevlerinde pratik Sokratik sorular sorarsın:
   "Neden önce soğan/biber koyuyoruz? Bunu hiç düşündün mü?"
6. Türkçe konuş. Kısa ve öz ol (2–4 cümle).

FELSEFE: "Bilmemek utanç değil, bilmekten korkmak utançtır."
```

**Temel Kullanım:**

```js
const yucelChat = async (messages) => {
  const response = await fetch("https://api.anthropic.com/v1/messages", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      model: "claude-sonnet-4-20250514",
      max_tokens: 1000,
      system: YUCEL_SYSTEM_PROMPT,
      messages: messages  // Tüm konuşma geçmişi
    })
  });
  const data = await response.json();
  return data.content[0].text;
};
```

**Amfi Moderasyon (5 dk Kuralı):**

```js
// hooks/useAmfiTimer.js
const useAmfiTimer = (onSilence) => {
  useEffect(() => {
    const timer = setTimeout(() => {
      onSilence(); // Yücel devreye girer
    }, 5 * 60 * 1000); // 5 dakika
    return () => clearTimeout(timer);
  }, [lastMessageTime]);
};
```

---

## 4. Veri Katmanı

### MVP: LocalStorage

**Neden (şimdilik)?**
- Sıfır kurulum — hemen çalışır
- Cursor ile prototiplemede sürtünme minimuma iner

```js
// utils/imece.js
const defaultState = {
  score: 0,
  completedTasks: [],
  villageLevel: 0,
  treeState: { leaves: 0, fruits: 0, flowers: 0 }
};

export const addScore = (points, reason) => {
  const state = loadState();
  state.score += points;
  state.treeState.leaves = Math.floor(state.score / 5);
  state.treeState.fruits  = Math.floor(state.score / 20);
  state.treeState.flowers = Math.floor(state.score / 10);
  saveState(state);
};
```

### v2: Firebase (Üretim)

**Neden?**
- Gerçek zamanlı: Köy güzellik seviyesi tüm kullanıcılarda eş zamanlı güncellenir
- Fotoğraf yükleme (Zanaat kanıtları için Firebase Storage)
- Google Auth ile tek tıkla giriş

```
Firebase Servisleri:
├── Firestore   → Kullanıcı, puan, tartışma verileri
├── Storage     → Zanaat görevi fotoğrafları
├── Auth        → Google / e-posta girişi
└── Hosting     → Ücretsiz yayın
```

---

## 5. Ada Bazlı Component Yapısı

```
src/
├── components/
│   ├── VillageMap.jsx         ← SVG harita, tüm adalar
│   ├── LifeTree.jsx           ← Hayat Ağacı (puana göre büyür)
│   ├── YucelChat.jsx          ← AI sohbet bileşeni
│   └── ImeceBar.jsx           ← Sticky puan çubuğu
├── features/
│   ├── amfi/
│   │   ├── Amfi.jsx           ← Tartışma arayüzü
│   │   └── useAmfiTimer.js    ← 5 dk Yücel tetikleyici
│   ├── zanaat/
│   │   ├── Zanaat.jsx         ← 5 görev + fotoğraf yükleme
│   │   └── tasks.js           ← Görev tanımları ve puan değerleri
│   ├── gelecek/
│   │   ├── Gelecek.jsx        ← 7 rehber
│   │   └── guides.js          ← Rehber içerikleri
│   ├── muzik/
│   │   ├── Muzik.jsx          ← Playlist + kolektif beste
│   │   └── CollaborationBoard.jsx
│   ├── gonul/
│   │   ├── Gonul.jsx          ← Usta profilleri + randevu
│   │   └── Reversementor.jsx  ← Tersine mentörlük akışı
│   └── meydan/
│       └── Meydan.jsx         ← Köy meydanı + Hayat Ağacı
└── utils/
    ├── imece.js               ← Puan sistemi
    ├── yucel.js               ← Claude API wrapper
    └── storage.js             ← LocalStorage / Firebase
```

---

## 6. Deployment

### Vercel (Önerilen)

```bash
npm install -g vercel
vercel --prod
```

```env
# .env
VITE_ANTHROPIC_API_KEY=sk-ant-...
VITE_FIREBASE_API_KEY=...
VITE_FIREBASE_PROJECT_ID=dijital-imece
```

---

## 7. Cursor ile Geliştirme — Prompt Şablonları

```
"Bana React ve Tailwind CSS kullanarak bir köy haritası yap.
 Ortada Köy Meydanı, etrafında 5 tıklanabilir ada olsun.
 Renkler: bej #F5F0E8, toprak #8B4513, gök #4A7FA5.
 Her adaya tıklayınca Framer Motion ile modal açılsın."

"Köy Meydanı'nda büyüyen bir Hayat Ağacı SVG bileşeni yaz.
 score prop'una göre yaprak (her 5 puan), meyve (her 20 puan),
 çiçek (her 10 puan) eklensin. Animasyonlar Framer Motion ile."

"Sokratik yöntemle konuşan Yücel AI chat bileşeni yaz.
 Anthropic Claude API kullan. 5 dakika sessizlikte otomatik
 müdahale etsin. Sistem komutu: [YUCEL_SYSTEM_PROMPT]"

"Zanaat Atölyesi için fotoğraf yükleme bileşeni yaz.
 Yükleme olmadan 'Görevi Tamamla' butonu aktif olmasın.
 Başarılı yüklemede +15 İmece Puanı eklensin."
```

---

## Özet Tablo

| Katman | Teknoloji | Gerekçe |
|--------|-----------|---------|
| **Framework** | React.js + Vite | Hız, modüler yapı, Cursor uyumu |
| **Stil** | Tailwind CSS | Toprak paleti, responsive |
| **Animasyon** | Framer Motion | Hayat Ağacı, ada geçişleri |
| **Harita & Ağaç** | SVG (inline) | Vektörel, interaktif, puana duyarlı |
| **AI** | Anthropic Claude Sonnet | Sokratik derin muhakeme, Türkçe |
| **Veri (MVP)** | LocalStorage | Sıfır kurulum, hızlı prototip |
| **Veri (v2)** | Firebase | Gerçek zamanlı, fotoğraf, auth |
| **Deploy** | Vercel | Otomatik CI/CD, ücretsiz |

---

*Kullanıcı akışı için → `user-flow.md` | Kaynak kodlar için → `features/`*
