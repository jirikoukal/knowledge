# Instrukce pro Claude Code

## Kontext

Claude Code (CC) je primární nástroj pro práci s kódem a GitHub repozitáři. Jiří nepracuje s terminálem přímo — CC je jeho rozhraní pro vše co se týká kódu, souborů a GitHubu.

## Repozitář knowledge

Hlavní repozitář: `/Users/jirikoukal/CLAUDE_PROJECTS/knowledge`

Struktura:
```
knowledge/
├── CLAUDE.md          ← routovací tabulka, čti vždy jako první
├── README.md
├── personal/
│   ├── brand/         ← brand.md, voice.md, templates/, icons/
│   ├── me/            ← about.md, techstack.md, working-style.md
│   └── services/      ← strategy.md, fractional-coo.md, ai-transformation.md, brand-marketing.md, due-diligence.md
├── clients/
│   └── viva-agency/   ← brand.md, templates/
├── prompts/           ← prompt-architect.md
└── instructions/      ← tento soubor a ostatní instrukce
```

## Pravidla pro každý úkol

1. **Vždy začni čtením `CLAUDE.md`** — tam je routovací tabulka která říká kde co najít
2. **Pro výstupy s brandem** — čti `personal/brand/brand.md` před generováním jakéhokoliv vizuálního výstupu
3. **Pro klientské projekty** — čti příslušný brand manuál v `clients/[klient]/brand.md`
4. **Pro konzultační výstupy** — čti příslušný soubor v `personal/services/`

## Git workflow

- **Commit message**: stručná, v angličtině, popisuje co se změnilo (ne proč)
- **Push**: vždy přes SSH (nastaveno), bez nutnosti hesla
- **Před pushnutím**: vždy `git pull --rebase` pokud mohly nastat změny z jiného zdroje
- **Větve**: zatím pracujeme na `main` přímo

## Typy úkolů pro CC

**Správa knowledge repo**
- Vytváření a úprava souborů v repo
- Commit a push změn na GitHub
- Reorganizace struktury

**Generování výstupů**
- HTML šablony a interaktivní dokumenty
- DOCX reporty (přes docx skill)
- React komponenty a weby

**Vibe coding workflow**
- Claude Chat jako architekt: navrhuje strukturu a kód
- CC jako exekutor: implementuje, commituje, pushuje
- Jiří jako stratég: určuje směr a schvaluje

## Jak zadávat úkoly CC

Jiří je teprve na začátku s CC — preferuje jasná, konkrétní zadání:

- Uveď vždy cestu k souboru nebo složce
- Popiš výsledný stav, ne postup ("chci aby soubor X obsahoval Y" místo "udělej A pak B pak C")
- Při nejasnosti se zeptej před akcí, ne po
- Při destructivních operacích (mazání, přepisování) vždy potvrď

## Aktuální projekty

- `knowledge` — personal OS, primární repo
- `viva-field-cc` — Viva Agency projekty (samostatné repo)

## Co CC nedělá

- Nepracuje s terminálem přímo (Jiří nemá zájem)
- Neotevírá prohlížeč
- Nezasahuje do jiných repo bez explicitního zadání
