# Workflow — osobní návod

## Které AI nástroje používám a kdy

### Claude Chat (primární)
Strategie, metodiky, složité projekty, vizualizace nástrojů a webů, texty, dlouhé dokumenty, iterativní práce. Nejvíce času.

Použij když:
- Řešíš strategii, framework nebo vlastní metodiku
- Potřebuješ výstup v konkrétním formátu (report, HTML, DOCX)
- Projekt vyžaduje kontext z více zdrojů (brand, services, klient)
- Iteruješ výstup opakovaně

### Claude Code (exekutor)
Práce s GitHub repo, generování a editace souborů, commit a push, implementace kódu.

Použij když:
- Chceš zapsat výstup přímo do repo
- Implementuješ co Chat navrhl
- Reorganizuješ nebo upravuješ soubory v knowledge repo
- Spouštíš vibe coding projekt

### Gemini (stínový LLM)
Rychlé a kreativní věci, Google ekosystém, fotky/video, research, cross-check výsledků.

Použij když:
- Chceš stejný úkol dát dvěma LLM pro srovnání
- Pracuješ s Google Drive, Gmail, Google Docs nativně
- Analyzuješ fotky nebo video
- Děláš rychlý research bez nutnosti hlubokého kontextu
- Došel kredit na Claudu pro daný den

### Cowork
Spolupráce na dokumentech v reálném čase s klientem nebo kolegou.

Použij když:
- Pracuješ na dokumentu s klientem živě
- Chceš sdílet výstup a iterovat společně
- Prezentace nebo report který klient vidí v reálném čase

## Jak zvládnout dlouhé konverzace v Chatu

Největší riziko: ztráta kontextu při iteraci a vkládání screenshotů.

**Pravidla:**
- Na začátku komplexního tématu jasně formuluj cíl: "Cílem této části je X"
- Každých ~20 zpráv zkontroluj: jsme stále na cestě k cíli?
- Pokud Claude upozorní na ztrátu kontextu — okamžitě shrň kde jste a co zbývá
- Nové téma = nové vlákno (nebo alespoň explicitní "přecházíme k tématu X")
- Při screenshotech přidej vždy jednu větu co chceš vědět nebo udělat

**Kdy začít nové vlákno:**
- Téma se kompletně mění
- Konverzace je dlouhá a výstupy se komplikují
- Začínáš nový projekt nebo engagement
- Potřebuješ čistý kontext

## Vibe coding workflow

1. **Chat** — popiš co chceš postavit, jaký je účel, kdo to bude používat
2. **Chat** — požádej o návrh architektury, struktury souborů, tech stack
3. **Chat** — iteruj architekturu dokud ti nedává smysl
4. **CC** — předej hotový plán, CC implementuje
5. **Chat** — review výstupu, návrh úprav
6. **CC** — implementuje úpravy, commituje, pushuje

## Knowledge repo — kdy co aktualizovat

| Událost | Co aktualizovat |
|---------|----------------|
| Nový klient | `clients/[klient]/brand.md` + templates |
| Nová služba nebo změna přístupu | `personal/services/[služba].md` |
| Změna brandu | `personal/brand/brand.md` |
| Nový prompt nebo metodika | `prompts/` |
| Změna tech stacku | `personal/me/techstack.md` |
| Nové instrukce pro AI | `instructions/` |

## Kredity a limity

- Claude Pro: denní limit může být dosažen při intenzivní práci
- Při dosažení limitu: přepnout na Gemini pro méně kritické úkoly
- Kritické a komplexní úkoly vždy na Claudu — počkat na reset nebo použít jiný den

## Brno a okolí — kontext pro výstupy

Primární trh: Jihomoravský kraj, Brno a okolí. Pro klientské engagementy mimo Brno: cestovné nad 50 km účtováno zvlášť. Remote možné pro část kapacity.
