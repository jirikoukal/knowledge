# Viva Agency — UI rulebook interních aplikací
*Poslední aktualizace: 24. července 2026*

**Platí pro:** VIVA Promoter Hub, VIVA Event Monitor a další interní aplikace.
**Neplatí pro:** vivaagency.cz — veřejný web se řídí `brand.md`.

**Vztah k ostatním souborům:**
`brand.md` říká, jak značka vypadá navenek. `voice.md`, jak mluví.
Tenhle soubor říká, jak se chová aplikace uvnitř. Barvy a typografii přebírá
z `brand.md` a nepředefinovává je — přidává jen pravidla, která web nepotřebuje.

Blok z kapitoly 7 se vkládá do každého Lovable promptu, který sahá na UI.

---

## 0. K čemu to je

Aplikace nemá vadu vkusu, má vadu původu: každý panel vznikl zvlášť a dostal
vlastní anatomii. Rozdílné velikosti písma jsou důsledek, ne příčina. Tenhle
soubor definuje primitiva, aby se rozhodnutí nedělalo znovu při každém promptu.

Pravidlo pro budoucnost: **co není v tomhle souboru, se do promptu nepíše.**
Když prompt potřebuje hodnotu, která tu není, doplní se sem nejdřív.

---

## 1. Typografická škála

Šest stupňů. Víc jich nebude.

| Název | Velikost | Váha | Barva | Kde |
|---|---|---|---|---|
| `title` | 21 px | 700, −0.01em | `#0F1724` | název stránky — výhradně PageHeader |
| `heading` | 15 px | 700 | `#0F1724` | nadpis karty nebo panelu |
| `strong` | 13.5 px | 600 | `#0F1724` | primární text v řádku — název akce, firma |
| `body` | 13 px | 400 | `#374151` | běžný text, hodnoty v tabulce |
| `meta` | 12 px | 400 | `#6B7280` | doplněk — klient, místo, datum, podtitulek |
| `label` | 10 px | 700, +0.08em, uppercase | `#9CA3AF` | hlavičky tabulek, nadpisy skupin, popisky |

**Jediná dokumentovaná výjimka:** `metric` — 26 px / 700 / `tabular-nums` /
`#0F1724` pro číslo v KPI dlaždici. Není to text, je to údaj; proto stojí mimo
škálu. Další výjimky se nezavádějí bez zápisu sem.

Řádkování: `title` a `metric` 1.2, ostatní 1.45.

Co z toho plyne pro dnešek: názvy akcí na Přehledu jsou dnes zhruba o dva
stupně nad `strong` a spadnou na 13.5 px. Pravý panel Neobsazené pozice je už
teď blízko cíli a skoro se nezmění. Sidebar zůstane, jak je — 13 px / 500 je
záměrně mimo obsahovou škálu, protože navigace není obsah.

---

## 2. Barvy a jejich práce

### Růžová #E91E8C

Má **tři** práce a žádnou další:

1. primární akce (tlačítko, které stránku posouvá dál)
2. aktivní položka navigace
3. odkaz v textu

Dokumentovaná výjimka: akcentní proužek 34 × 3 px v `PageHeader`.

**Kde růžová být nesmí:** zebra řádků tabulky, dekorativní ikony v seznamech,
nadpisy, pozadí neutrálních panelů, orámování karet bez významu.

Důvod: barva, která znamená pět věcí, neznamená nic. Zvýrazněný řádek, který
není nijak zvláštní, naučí oko barvu ignorovat — a pak přehlédne i tlačítko.

**Kontrast:** růžová na bílé má poměr kolem 4.2:1. Pro `title`, `heading` a
tlačítka stačí. Pro `meta` a `label` ne — drobný růžový text se v hale nebo
venku nepřečte. Drobné odkazy proto `#C2185B` (poměr 5.9:1), ne `#E91E8C`.

### Neutrály

| Token | Hodnota | Použití |
|---|---|---|
| `ink` | `#0F1724` | nadpisy, primární text, sidebar |
| `body` | `#374151` | běžný text |
| `muted` | `#6B7280` | sekundární text |
| `faint` | `#9CA3AF` | popisky, disabled |
| `line` | `#E9EBEF` | oddělovače, okraje karet |
| `surface` | `#F9FAFB` | hover řádku, zebra hustých tabulek |
| `canvas` | `#F5F6F8` | pozadí sekcí, ikonové čtverce |

### Funkční barvy

| Význam | Text | Pozadí |
|---|---|---|
| Hotovo / OK | `#065F46` | `#D1FAE5` |
| Čeká / pozor | `#92400E` | `#FEF3C7` |
| Problém | `#991B1B` | `#FEE2E2` |
| Informace | `#1E40AF` | `#DBEAFE` |
| Neutrální stav | `#374151` | `#F1F3F5` |

Funkční barva nikdy neoznačuje typ nebo kategorii — jen stav a naléhavost.

Dokumentovaná výjimka: kalendářní kategorie nepřítomnosti (dovolená,
nemoc, osobní volno, meeting) mají vlastní barevnou sadu mimo funkční
paletu. Barva tam označuje kategorii záměrně a jinde se to neopakuje.

**Výjimka — peněžní evidence.** V modulech, které sčítají pohyby peněz
(Interní evidence, výkazy s částkami), nese částka barvu podle znaménka
pohybu: příjem `#065F46`, výdej `#991B1B`. Barva je zde redundantní ke
znaménku, ne jeho náhrada — informace nezávisí jen na barvě.

Neplatí pro odznak směru. Ten zůstává obrysová pilulka bez výplně, protože
směr je kategorie, a kategorie se barvou neoznačuje ani tady.

---

## 3. Odznaky

Čtyři tvary, čtyři významy. Tvar nese informaci sám o sobě.

| Tvar | Význam | Provedení | Příklad |
|---|---|---|---|
| **Plná pilulka** | stav záznamu | funkční barva, 11 px / 700, radius 999 px, padding 4/10, min-height 22 px | Aktivní, Zaúčtováno, Obsazeno |
| **Obrysová pilulka** | typ nebo kategorie | 1px `line`, text `muted`, bez výplně, stejná metrika jako plná | Event, Sampling, Výroba, Výdaj |
| **Číslo v kolečku** | počet vyžadující pozornost | `#FEE2E2` / `#991B1B`, 20 × 20 px, 11 px / 700, `tabular-nums` | 6 chybí, 28 |
| **Pastelový chip** | filtr — klikací | funkční pozadí, 12 px / 600, padding 5/12, min-height 26 px, kurzor pointer, aktivní stav rámečkem | Celkem 19, Volných 5 |

Pravidla:

- Jeden odznak nese jeden význam. Nikdy nekombinuje stav s typem.
- Na řádku seznamu **maximálně dva** odznaky. Třetí informace patří do `meta`.
- Chip, na který se nedá kliknout, není chip — je to plná pilulka.
- Chip s počtem 0 se vykreslí neaktivní — text a rámeček `faint`, kurzor
  default, bez hoveru, neklikací. Filtr, který nic nevrátí, není akce.
- Počet v kolečku vždy znamená „tolik položek čeká na akci". Nikdy celkový
  počet záznamů; ten patří do `meta` jako text.
- Odznak, který otevírá výběr, je ovládací prvek. Dostane chevron 12 px
  za text, jinak vypadá jako statický údaj a nikdo na něj neklikne.
- Prázdná hodnota není chybový stav. Chybějící údaj je pomlčka v barvě
  `faint`, ne červený křížek. Červená patří tomu, co čeká na akci.
- Metrika odznaku se mění jen tady a propíše se komponentami
  `StatusPill`, `TypePill`, `CountCircle` a `FilterChip`. Do promptu se
  nikdy nepíše jiná velikost, než která stojí v téhle tabulce.

To poslední mění dnešní stav: odznak u Akcí v menu ukazuje 38 jako celkový
počet, u Směn 5 jako počet volných. Stejný slot, dva významy. Sjednotit na
„čeká na akci" — u Akcí tedy počet akcí s neobsazenými pozicemi, ne všech.

---

## 4. Řádek seznamu

Jedna komponenta `ListRow`, jedna anatomie. Použije ji každý seznam v aplikaci.

```
┌────────────────────────────────────────────────────────────┐
│ [ikona]  Název akce                      [stav] [typ]  ›   │  56 px
│  32px    12. 6. · Praha · Coca-Cola                        │  (64 px dvouřádkový)
└────────────────────────────────────────────────────────────┘
```

- **Ikona:** volitelná, 32 × 32 px, radius 8 px, pozadí `canvas`, ikona
  `muted` 16 px. Nikdy růžová — růžový čtverec na každém řádku je dekorace,
  ne informace.
- **Název:** `strong`, jeden řádek, `truncate`.
- **Meta:** `meta`, jeden řádek, položky spojené ` · `. Když se nevejde,
  zkracuje se zprava, ne že se zalomí.
- **Vpravo:** max dva odznaky, pak volitelný chevron `faint` 16 px.
- **Hover:** pozadí `surface`, celý řádek klikací, kurzor pointer.
- **Oddělení:** spodní linka `line`. **Bez zebry.** Zebra patří jen do hustých
  datových tabulek nad 10 sloupců, a to v `surface`, nikdy v růžové.
- **Focus:** viditelný ring, 2 px `#E91E8C`, offset 2 px.
- Levý blok 32 px je v řádku vždy, i když ikona chybí. Bez něj se
  vedle sebe postavené seznamy rozejdou o šířku ikony.
- Ikona smí nést kategorii pomocí odlišného glyfu, nikdy barvou.
  Když glyf nese typ, obrysová pilulka s typem se z řádku odstraňuje.

---

## 4b. Záhlaví tabulek a panelů

Referenční provedení je záhlaví na stránce Doklady.

Pozadí `ink` #0F1724, výška 48 px, horní rohy 8 px, bez svislých linek
mezi sloupci a bez spodní linky. Text 13 px / 600 / bílá, font Montserrat
nastavený explicitně, ne děděný ze stylu tabulky.

Popisky se píší větným tvarem — velké písmeno na začátku, zbytek malými.
Žádné verzálky, žádné rozpalování písmen. Verzálky patří jen `label`
uvnitř obsahu, ne do záhlaví.

Popisek se nikdy nezalamuje na dva řádky — dlouhý název se zkrátí.
Text svisle na střed řádku. První sloupec začíná na stejné svislé ose
jako obsah pod ním. Záhlaví se zarovnává stejně jako obsah svého sloupce.

Řazený sloupec zůstává bílý a jeho šipka také, nikdy růžová.
Ikony řazení #8B95A5, 16 px.

Platí bez výjimky pro všechny datové tabulky i pro hlavičky panelů
na Přehledu.

Sticky záhlaví se zastavuje pod komponentou `PageHeader` a má nižší
z-index než ona. Tmavý pruh nesmí hlavičku stránky nikdy překrýt.

---

## 4c. Sumární patička tabulky

Tabulka, která sčítá částky, končí patičkovým řádkem na pozadí `surface`.

- vlevo `meta` „Zobrazeno X z Y záznamů"
- vpravo hodnoty **v jednom řádku vedle sebe**, mezera 32 px, nikdy pod
  sebou — sloupec čísel bez řádků tabulky se čte jako seznam, ne jako součet
- každá hodnota je dvojice: popisek `label` nad hodnotou 15 px / 600
  `tabular-nums`
- barva podle pravidla peněžní evidence z kapitoly 2
- pod 900 px se skupina zalomí pod text o počtu a zarovná doleva

Součet napříč směry se nezobrazuje. Příjmy a výdeje jsou dvě veličiny;
jedno číslo, které je slučuje, je vždy chyba — buď rozdíl, nebo nic.

---

## 5. Rozestupy

Základ 4 px. Povolené hodnoty: 4, 8, 12, 16, 20, 24, 32. Nic mezi tím.

- vnitřek karty: 20 px
- mezera mezi kartami: 16 px
- mezera mezi sekcemi stránky: 24 px
- vnitřní okraj stránky pod hlavičkou: 22 px, pod 640 px 16 px

---

## 6. Tlačítka

| Typ | Provedení | Kdy |
|---|---|---|
| Primární | pozadí `#E91E8C`, bílý text, 600, radius 8 px | jedna akce na stránku, ne víc |
| Sekundární | 1px `line`, text `body`, bílé pozadí | vedlejší akce |
| Tichá | bez rámečku, text `muted`, hover `surface` | akce v řádku |
| Destruktivní | text `#991B1B`, bez výplně | mazání, archivace |

Destruktivní akce **není v klidovém stavu vidět plnou barvou**. Odhalí se při
hoveru řádku, nebo bydlí v menu pod třemi tečkami. Dnešní červený koš u každé
karty v Q&A má stejnou vizuální váhu jako čtení obsahu, což je špatně.

Mazání záznamu, který mění vypočtenou hodnotu na stránce — saldo, součet,
stav fondu — potvrzuje dialog, který ten dopad uvádí číslem. „Záznam bude
odstraněn" je málo; uživatel maže řádek, ale mění ukazatel, podle kterého
se rozhoduje.

Segmentový přepínač pohledu není primární akce. Aktivní segment je
bílá karta na dráze `canvas`, nikdy růžová výplň.

Výška tlačítek 36 px, v řádcích tabulky 30 px.

---

## 7. Blok DESIGN do promptů

Kopírovat do každého Lovable promptu, který sahá na UI:

```
=== DESIGN ===
Řiď se rulebookem aplikace:
- Typografie: title 21/700, heading 15/700, strong 13.5/600, body 13/400,
  meta 12/400 #6B7280, label 10/700 uppercase +0.08em #9CA3AF.
  Metrika v KPI dlaždici 26/700 tabular-nums. Jiné velikosti nezaváděj.
- Růžová #E91E8C jen pro primární tlačítko, aktivní navigaci a odkaz.
  Nikdy zebra, dekorativní ikony, nadpisy ani orámování bez významu.
  Drobný růžový text #C2185B kvůli kontrastu.
- Odznaky: plná pilulka = stav, obrysová = typ, číslo v kolečku = počet
  čekající na akci, pastelový chip = klikací filtr. Max dva na řádek.
  Chip s počtem 0 je neaktivní a neklikací.
- V peněžních evidencích má částka barvu podle znaménka (příjem #065F46,
  výdej #991B1B), odznak směru zůstává obrysový. Sumární patička staví
  hodnoty vedle sebe, ne pod sebe.
- Seznamy staví na komponentě ListRow, tabulky na sdíleném tmavém záhlaví.
  Novou anatomii řádku ani hlavičky nevymýšlej.
- Rozestupy jen 4, 8, 12, 16, 20, 24, 32.
- Destruktivní akce se odhalí až při hoveru nebo bydlí v menu.
- Montserrat, shadcn/ui a lucide-react. Žádná nová knihovna.
```

---

## 8. PROMPT Č. 1 — tokeny a Přehled jako referenční stránka

*Archiv provedeného kroku. Ponecháno jako doklad, jak vznikly tokeny —
hodnoty v něm nejsou kanonické, kanonická je kapitola 1.*

Jedna stránka udělaná úplně správně se stane vzorem pro ostatní. Přehled proto,
že je nejnavštěvovanější a rozdíl mezi jeho dvěma panely je nejkřiklavější.

```
Zaveď designové tokeny a přepiš na ně stránku Přehled.

ROZSAH: pracuj v src/index.css, tailwind.config.ts, nové komponentě
src/components/ui/ListRow.tsx a ve stránkách Dashboard (všechny tři
role-varianty). Žádnou jinou stránku neupravuj.

=== KROK 1: tokeny ===
Do index.css a tailwind.config.ts doplň:
- barvy: ink #0F1724, body #374151, muted #6B7280, faint #9CA3AF,
  line #E9EBEF, surface #F9FAFB, canvas #F5F6F8, pink #E91E8C,
  pink-text #C2185B
- funkční dvojice: ok #065F46/#D1FAE5, warn #92400E/#FEF3C7,
  bad #991B1B/#FEE2E2, info #1E40AF/#DBEAFE, neutral #374151/#F1F3F5
- textové utility: text-title 21px/700, text-heading 15px/600,
  text-strong 13.5px/600, text-body 13px/400, text-meta 12px/400,
  text-label 10px/700 uppercase letter-spacing .08em,
  text-metric 26px/700 tabular-nums
Existující tokeny nepřepisuj ani nemaž, jen doplň.

=== KROK 2: ListRow ===
Vytvoř src/components/ui/ListRow.tsx.
Props: icon (volitelná), title, meta (pole stringů), badges (max 2),
onClick (volitelný), chevron (bool).
- výška 56 px jednořádkový, 64 px když je meta
- ikona 32x32, radius 8, pozadí canvas, ikona muted 16px — NIKDY růžová
- title text-strong, truncate
- meta text-meta, položky spojené " · ", truncate
- vpravo badge sloty, pak chevron faint 16px
- hover pozadí surface, celý řádek klikací, focus ring 2px #E91E8C offset 2
- spodní linka line, žádná zebra

=== KROK 3: Přehled ===
Přepiš oba seznamy na Přehledu na ListRow:
- panel Akce: ikonu ponech, ale v canvas/muted provedení místo růžové;
  název text-strong; meta "datum · místo"; badge stav (plná pilulka)
  a typ akce (obrysová pilulka)
- panel Neobsazené pozice: bez ikony; název text-strong; meta klient;
  badge počet chybějících jako číslo v kolečku bad
Nadpisy obou panelů text-heading, jejich podtitulky text-meta.
KPI dlaždice: číslo text-metric, popisek text-label, ikona muted.

Odkaz "5 volných směn tento týden" zařaď do mřížky dlaždic jako plnohodnotnou
buňku, ne pod ně. Barva textu pink-text.

Panel "Dnešní akce" odstraň — dlaždice "Dnes" nese tutéž informaci a duplicita
mate. Prostor po něm zabere panel Neobsazené pozice.

=== KROK 4: kontrola ===
Žádnou datovou logiku, dotaz ani route neměň. Jde čistě o vzhled a jednu
odstraněnou duplicitu.

NEMĚŇ: src/App.tsx, Sidebar, AppLayout, PageHeader, navigation.ts, ostatní
stránky v src/pages, databázi, RLS, edge functions.
```

**Ověření:** Přehled na 1440 px a na 375 px, všechny tři role. Dlouhý název
akce se ořízne a nezalomí. Focus ring je vidět při průchodu tabulátorem.

---

## 9. Další v pořadí

**Prompt č. 2 — odznaky napříč aplikací.** Sjednocení na čtyři tvary, včetně
opravy významu počtu u Akcí v menu. Až po ověření Přehledu.

**Prompt č. 3 — ListRow do zbylých seznamů.** Akce, Směny, Klienti, Tým, Q&A.
Po jednom, ne najednou.

**Prompt č. 4 — drobné vady.** Uříznuté popisky filtrů na Směnách, čas 00:00
u akcí bez zadaného času (zobrazit pomlčku, ne půlnoc), destruktivní koš v Q&A
až na hover, zebra na Směnách z růžové na surface.

**Ověřit v kódu:** token `text-heading`. Kapitola 1 i blok DESIGN říkají
15 px / 700, prompt č. 1 ho ale zaváděl jako 600. Zjistit, co je v
`tailwind.config.ts`, a srovnat s rulebookem — ne naopak.

**Provozní rozhodnutí, ne designové:** tab Výkazy uvnitř Směn versus položka
Výkazy v menu. Buď je to tentýž pohled na dvou místech, nebo dvě věci se
stejným názvem. Rozhodnout s Radimem, pak se to promítne do menu.
