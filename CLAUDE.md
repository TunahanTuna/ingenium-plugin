# Ingenium — Claude Code Plugin Marketplace

Tek plugin'li marketplace repo'su. Plugin: `plugins/ingenium/`, skill'ler: `plugins/ingenium/skills/<skill-adi>/SKILL.md`.

## Komutlar

- Doğrulama: `claude plugin validate .` (marketplace) ve `claude plugin validate plugins/ingenium` (plugin)
- Kurulumsuz test: `claude --plugin-dir plugins/ingenium` → oturumda `/reload-plugins`
- Marketplace testi: `/plugin marketplace add <repo-yolu>` → `/plugin install ingenium@ingenium`
- Skill düzenledikten sonra kurulu kopyayı tazeleme: marketplace GitHub kaynaklı (TunahanTuna/ingenium-plugin), sürüm commit SHA'sından türer — **commit + push** gerekir; sonra `claude plugin marketplace update ingenium`. Push'lamadan hızlı deneme: `claude --plugin-dir plugins/ingenium`

## Yapı

- `.claude-plugin/marketplace.json` — plugin listesi; `source` yolları plugin köklerine işaret eder
- `plugins/ingenium/.claude-plugin/plugin.json` — plugin manifest'i. `version` alanı bilinçli olarak YOK (her commit SHA bazlı yeni sürüm sayılır); ekleme
- Bileşenler (`skills/` vb.) asla `.claude-plugin/` içine konmaz; plugin kökünde durur

## Skill yazım kuralları

- Frontmatter: `name` (klasör adıyla aynı, kebab-case) + `description` zorunlu
- `description` formatı: İngilizce "ne yapar + ne zaman kullanılır (Use when...)" + sonda `Türkçe tetikleyiciler - "ifade1", "ifade2"` listesi. Claude tetikleme kararını YALNIZCA bu alandan verir; `when_to_use` ile birlikte 1536 karakter sınırı var
- Description içinde iki nokta üst üste (`:`) YAML'ı bozar — tire kullan veya tırnakla
- Gövde: İngilizce, emir kipi, fazlı yapı (Phase 1..N) + Rules bölümü; başta "Always communicate with the user in their own language." satırı bulunur
- Destek dosyaları skill klasörüne: `reference.md`, `scripts/` — SKILL.md'den `[reference.md](reference.md)` diye link ver; büyük içerik gövdeye değil referansa
