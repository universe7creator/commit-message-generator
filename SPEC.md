# commit-message-generator — SPEC.md

## 1. Concept & Vision
Git diff'leri analiz ederek anlamlı conventional commit mesajları üreten AI destekli tool. 
Developer'ların commit message yazma sürecini 5 saniyeye indirir. 
CLI + Web arayüzü, stateless, no DB, Vercel serverless.

## 2. Design Language
- Aesthetic: Terminal/monokromatik — developer tool estetiği
- Colors: #0D1117 bg, #58A6FF accent, #F0F6FC text
- Font: JetBrains Mono (monospace)
- Motion: Minimal — sonuç fade-in 200ms

## 3. Layout & Structure  
Single page:
- Sol: diff/mesaj input alanı (textarea, monospace)
- Sağ: AI commit message output
- Alt: Copy butonu + format seçici (conventional/emoji/concise)

## 4. Features & Interactions
- **Input:** Git diff metni yapıştır
- **Output:** Conventional commit formatında: type(scope): description
- **Types:** feat, fix, docs, style, refactor, test, chore, perf, ci, build
- **Scope detection:** Dosya yollarından otomatik scope çıkarımı
- **Body/footer:** Uzun diff'ler için body ekle
- **Copy:** Tek tıkla copy, feedback toast
- **Format seçici:** conventional / emoji / concise

## 5. Technical Approach
- Single HTML file, vanilla JS
- Client-side LLM call (kullanıcı kendi API key girer)
- Anthropic Claude API kullan
- API key gizli tutulur — server-side key YOK
