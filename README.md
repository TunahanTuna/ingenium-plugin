# Ingenium

Bir developer'ın İsviçre çakısı — Claude Code için katman katman gelen workflow, web ve oyun geliştirme skill'leri. Amaç: yapay zeka destekli geliştirmeyi her projede en güvenli, en optimum ve en verimli hale getirmek.

Tek plugin, tüm skill'ler: `ingenium`'u kurduğunda her şey birlikte gelir. Tüm skill'ler hem Türkçe hem İngilizce komutlarla tetiklenir.

## Kurulum

```
/plugin marketplace add <github-kullanici>/ingenium
/plugin install ingenium@ingenium
```

Lokal kurulum (geliştirme için):

```
/plugin marketplace add F:\development\Tunahan\tuna\ingenium
/plugin install ingenium@ingenium
```

## Skill'ler

### Workflow

| Skill | Ne yapar | Örnek komut |
|---|---|---|
| `safe-merge` | Kayıpsız, release kalitesinde branch merge: divergence analizi, her konfliktte iki tarafın niyetini anlayarak çözüm, build+test doğrulaması, onaysız push yok | "dev'i uat'a al, çakışmaları güvenli çöz" |
| `refactor-safe` | Davranış koruyarak refactor: önce characterization test, mikro adımlar, seam'ler, strangler-fig, sonda "hiçbir şey değişmedi" kanıtı | "bu god component'i böl ama hiçbir şeyi bozma" |
| `debug-detective` | Sistematik kök neden analizi: önce reproduce, bisect, kanıtla, sonra düzelt + regresyon testi | "bu bug'ın kök nedenini bul, bazen çalışıyor bazen çalışmıyor" |
| `release-prep` | Son tag'den bu yana commitleri analiz eder, semver kararı, changelog, sürüm güncelleme, tag + release | "release hazırla" |

### Proje

| Skill | Ne yapar | Örnek komut |
|---|---|---|
| `project-onboard` | Projeyi derinlemesine analiz edip doğrulanmış CLAUDE.md üretir — projeyi AI'a hazırlar | "projeyi tanı ve claude'a hazırla" |
| `docs-sync` | Proje dokümanlarını kodun güncel haliyle kanıta dayalı eşitler, drift raporu çıkarır | "dokümanları projenin son haliyle senkronize et" |
| `web-kickoff` | Yeni web projesini production kalitesinde temelle kurar: stack seçimi, strict TS, lint/test/CI, CLAUDE.md | "yeni bir web projesi kur" |

### Frontend craft

| Skill | Ne yapar | Örnek komut |
|---|---|---|
| `frontend-craft` | Framework'ten bağımsız frontend temelleri: semantik HTML, formlar, modern CSS, URL-as-state, üç-durum kuralı, platform-first bağımlılık disiplini + AI ile token-verimli kod tabanı | "frontend'de en doğru yöntem hangisi", "kodu ai için optimize et" |
| `perf-audit` | Ölçüm öncelikli web performans denetimi: Core Web Vitals teşhisi, bundle diyeti, asset/caching stratejisi, runtime jank avı | "site yavaş, performans denetimi yap" |
| `motion-craft` | Animasyon ve micro-interaction mühendisliği: doğru araç seçimi, süre/easing, FLIP, koreografi, 60fps disiplini, reduced-motion | "bu geçişleri yumuşat, animasyon takılıyor" |
| `design-system` | Design system inşası: semantik token'lar, tema (dark mode token swap), primitive-first mimari, variant API'ları, headless a11y | "design system kur, dark mode altyapısı ekle" |
| `human-made-design` | AI-görünümlü tasarımı törpüler: "tell" kataloğu (mor gradyanlar, glassmorphism, emoji ikonlar, şablon hero), referans-öncelikli süreç, tipografi/renk/layout karakteri, de-AI review geçişi | "bu tasarım çok yapay zeka işi görünüyor, insanileştir" |
| `pwa-offline` | PWA ve offline-first: manifest/kurulabilirlik, kaynak tipine göre SW cache stratejisi, güncelleme problemi çözümü, IndexedDB + outbox, oyunlar için offline | "uygulama offline çalışsın", "kullanıcılar eski sürümü görüyor" |

### Game dev

| Skill | Ne yapar | Örnek komut |
|---|---|---|
| `game-design` | Koddan önce oyun tasarımı: core loop, tek sayfalık GDD, acımasız MVP kapsamı, zorluk/ilerleme eğrileri, ekonomi, playtest | "oyun fikrim var, tasarlayalım" |
| `pixel-game-dev` | Web teknolojileriyle 2D pixel art oyun geliştirme: framework seçimi, pixel-perfect render, asset pipeline, juice, yayınlama | "phaser ile bir platformer yapalım" |
| `pixel-art-assets` | İnsan eli değmiş gibi duran pixel art asset üretimi: style bible, hue-shift'li ramp'ler, üç üretim rotası (el/script/diffusion-kurtarma), gömülü px.py aracı (palet kilidi, denetim, contact sheet) | "ai ile asset üret ama insan çizmiş gibi dursun" |
| `godot-dev` | Godot 4 geliştirme: sahne kompozisyonu, signals-up/calls-down, typed GDScript, Resource'lar, fizik/input, export; Godot MCP entegrasyonu | "godot'ta envanter sistemi kur" |
| `tauri-game-dev` | React + Tailwind + Tauri v2 ile masaüstü (ve mobil) oyun: üç katmanlı mimari, React↔canvas köprüsü, IPC/plugin'ler, platform-bazlı webview performans gerçekleri, Steam/itch dağıtımı | "tauri ile masaüstü oyunu yapalım" |
| `multiplayer-netcode` | Web oyunları için multiplayer: türe göre model seçimi (snapshot interpolation, prediction/reconciliation, rollback), transport, authoritative server, determinizm tuzakları | "oyuna multiplayer ekle", "desync oluyor" |
| `shader-vfx` | Shader ve görsel efektler: GLSL araç seti (SDF, smoothstep, noise), hazır VFX tarifleri (dissolve, outline, su, CRT), pixel-art-güvenli efektler, üç.js/Pixi/Phaser/Godot eşlemeleri | "hit flash ve dissolve efekti ekle" |
| `game-audio` | Oyun sesi mühendisliği: Web Audio bus mimarisi, ilk-dokunuş kilidi, SFX varyasyonu, lookahead scheduler, adaptif müzik (yatay/dikey), ducking ve miks | "oyuna ses ekle, mobilde ses gelmiyor" |

Skill'ler iki şekilde çalışır:

- **Otomatik**: Doğal dilde isteğini yaz ("dev branch'ını qa'ya merge et, hiçbir geliştirme ezilmesin") — Claude ilgili skill'i kendisi yükler.
- **Elle**: `/ingenium:safe-merge dev uat` gibi doğrudan çağır (çakışma yoksa `/safe-merge` kısayolu da çalışır).

## Geliştirme

Yeni skill eklemek:

1. `plugins/ingenium/skills/<skill-adi>/SKILL.md` oluştur — frontmatter'da `name` ve `description` zorunlu.
2. `description` alanına İngilizce tanımın sonuna `Türkçe tetikleyiciler - "..."` listesini ekle; Claude'un tetikleme kararı yalnızca bu alana bakar.
3. Doğrula: `claude plugin validate .`
4. Kurulu kopyayı tazele: sürümleme commit SHA'sına bağlı olduğu için önce **commit'le**, sonra `/plugin marketplace update ingenium` çalıştır (yeni oturumda etkinleşir). Commit'lemeden denemek istersen: `claude plugin uninstall ingenium@ingenium && claude plugin install ingenium@ingenium`.
5. Alternatif — kurulum yapmadan hızlı deneme: `claude --plugin-dir plugins/ingenium` (`/reload-plugins` ile anında yenile).

## Sürümleme

`plugin.json`'da bilinçli olarak `version` alanı yok: her commit otomatik olarak yeni sürüm sayılır (commit SHA bazlı). Push'ladığın her değişiklik, marketplace'i ekleyen kullanıcılara otomatik güncellemeyle ulaşır. Kararlı sürümler yayınlamak istersen `version` alanı ekleyip semver ile artırman yeterli — o durumda kullanıcılar yalnızca versiyon değişince güncelleme alır.

## Deka plugin'leriyle birlikte kullanım

Ingenium, Deka marketplace'indeki review/pattern odaklı skill'lerle çakışmayacak şekilde workflow odaklı tasarlandı. İkisi birlikte kurulu olabilir: örneğin React component review'u `deka-engineering-react` yapar, branch merge ve release akışını `ingenium` yönetir.
