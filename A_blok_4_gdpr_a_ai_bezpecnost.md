---
title: "Blok 4: Ochrana firemných údajov, GDPR & bezpečné používanie AI nástrojov"
aliases:
  - "A4: Blok 4: Ochrana firemných údajov, GDPR & bezpečné používanie AI nástrojov"
tags:
  - itsec
  - gdpr
  - klasifikacia-udajov
  - canarytokens
  - ai-bezpecnost
  - chatgpt-ochrana
  - halucinacie
  - anonymizacia
  - modul-a
target_audience: "Bežní korporátni používatelia"
track: "Modul A: Bezpečnosť pre korporátnych používateľov"
time: "14:00 – 15:30 (90 min)"
created: 2026-10-22
license: "CC-BY-4.0"
---

# Blok 4: Ochrana firemných údajov, GDPR & bezpečné používanie AI nástrojov

> [!info] Informácie o bloku
> - **Cieľová skupina:** Bežní korporátni používatelia
> - **Časový rozsah:** 14:00 – 15:30 (90 min)
> - **Okruh:** Modul A: Bezpečnosť pre korporátnych používateľov
> - **Zdrojový súbor:** `A_blok_4_gdpr_a_ai_bezpecnost.pptx`

⬅️ [[A_blok_3_sharepoint_a_spoluprac.md|Blok 3: OneDrive, SharePoint & tímová spolupráca]] | 🏠 [[README|Obsah kurzu (MOC)]]

---

## Slide 4.1: Ochrana osobných údajov (GDPR) v praxi

![[static/A4_s01_41_ochrana_osobných_údajov_gdpr_v_praxi_4b5ee7.jpg]]

- Osobné údaje sú informácie identifikujúce človeka: meno, rodné číslo, e-mail, plat.
- **Need to Know:** pracujte len s tými údajmi, ktoré nevyhnutne potrebujete.
- **Posielanie databáz:** nikdy neposielajte celý zoznam klientov kvôli jednému kontaktu.
- **Únik dát (Data Breach):** ak pošlete citlivý zoznam nesprávnemu, ihneď hláste IT.

---

## Slide 4.2: Klasifikácia informácií: Nie je dokument ako dokument

![[static/A4_s02_42_klasifikácia_informácií_nie_je_dokume_ef901e.jpg]]

- **Verejné (Public):** letáky, tlačové správy, verejné cenníky – môžu ísť von.
- **Interné (Internal):** bežné smernice, zápisnice – určené len pre zamestnancov.
- **Dôverné (Confidential):** zmluvy, finančné výsledky, osobné údaje – prísny prístup.
- **Prísne tajné (Restricted):** strategické plány, know-how – prístup má úzky okruh.

---

## Slide 4.3: Značky citlivosti a bezpečné narábanie

![[static/A4_s03_43_značky_citlivosti_a_bezpečné_narábani_9e549f.jpg]]

- **Štítky citlivosti (Sensitivity Labels):** jedným kliknutím označíte dokument.
- **Automatická ochrana:** označený dokument sa zašifruje a nepovolaný ho neotvorí.
- **Odpadkový kôš nie je skartovačka:** vytlačené papiere patria do skartovačky.
- **Zákaz fotenia:** nefoťte obrazovku s firemnými systémami na osobný mobil.

---

## Slide 4.4: Čo je to Canarytoken? (Tichý alarm)

- Špeciálne nastražený sledovací prvok vložený do dôležitého súboru.
- **Funguje ako alarm:** ak niekto nepovolaný otvorí súbor, pošle správu adminovi.
- Správca zistí presný čas, miesto a zariadenie, kde bol súbor otvorený.
- canarytokens.org

---

## Slide 4.5: Nástroje umelej inteligencije (AI): Riziká

![[static/A4_s05_45_nástroje_umelej_inteligencije_ai_rizi_f4307d.jpg]]

- Nástroje ako ChatGPT či Copilot šetria hodiny pri písaní a analýzach.
- **Ako fungujú:** učia sa zo všetkého textu, ktorý do nich používatelia vložia.
- **Obrovské riziko bezplatných verzií:** zadaný text sa stáva majetkom prevádzkovateľa.
- Čo vložíte do AI vy dnes, sa zajtra môže objaviť ako odpoveď konkurencii.

---

## Slide 4.6: Čo NIKDY nezadávať do verejnej AI?

- **Osobné údaje:** mená klientov, rodné čísla, adresy, životopisy (porušenie GDPR).
- **Obchodné tajomstvá:** interné finančné výkazy, marže, chystané projekty a zmluvy.
- **Prístupové údaje:** akékoľvek heslá, PIN kódy či konfiguračné nastavenia.
- Interné zdrojové kódy a citlivé právne analýzy tvoriace know-how firmy.
- !

---

## Slide 4.7: Rozdiel medzi ChatGPT a firemným Copilotom   WTF!!!

![[static/A4_s07_47_rozdiel_medzi_chatgpt_a_firemným_copi_043d4a.jpg]]

- **Verejný ChatGPT:** žiadna ochrana dát, informácie putujú na cudzie servery.
- **Firemný Microsoft Copilot:** dáta neopúšťajú firemné prostredie, Microsoft sa neučí.
- Aj pri firemnom Copilote však platí opatrnosť a dodržiavanie klasifikácie.
- Vždy používajte len tie AI nástroje, ktoré oficiálne schválilo IT oddelenie.

---

## Slide 4.8: Pozor na „halucinácie“ a pasce v AI

- AI generuje to, čo znie pravdepodobne, nie to, čo je zaručene pravda.
- **Halucinácie:** AI si s istotou vymyslí neexistujúce zákony, paragrafy či citácie.
- **Skrytý škodlivý text:** podvodný text na webe môže zmiasť AI asistenta.
- **Zlaté pravidlo:** za každý výstup z AI nesiete plnú osobnú zodpovednosť vy.

---

## Slide 4.9 [CVIČENIE]: Názorná ukážka Canarytoken alarmu

> [!example] Praktická úloha a ukážka
> - Cieľ: Pochopiť, ako bezpečnostné technológie odhalia únik informácií.
> - Ukážka: Lektor predvedie otvorenie testovacieho PDF s tokenom.
> - Efekt: O pár sekúnd pípne e-mailová notifikácia s IP adresou a časom.
> - Ponaučenie: Moderné formáty vedia upozorniť na neoprávnené šírenie.

---

## Slide 4.10 [CVIČENIE]: Ako bezpečne anonymizovať text?

![[static/A4_s10_410_cvičenie_ako_bezpečne_anonymizovať_t_393515.jpg]]

> [!example] Praktická úloha a ukážka
> - Cieľ: Využiť AI na úpravu textu bez odoslania citlivých firemných dát.
> - Zadanie: Máme e-mail pre klienta plný mien, čísiel zmlúv a súm.
> - Postup: Všetky konkrétne údaje nahradíme zástupnými značkami ([KLIENT], [SUMA]).
> - Výsledok: AI vylepší štylistiku, no žiadne citlivé tajomstvo neopustí firmu.

---

## Slide 4.11 [CVIČENIE]: Odhalenie halucinácie v AI

> [!example] Praktická úloha a ukážka
> - Cieľ: Otestovať kritické myslenie a neveriť slepo odpovediam AI.
> - Zadanie: Dáme AI otázku na vymyslené znenie slovenského predpisu.
> - Výsledok: AI vygeneruje presvedčivú, no úplne fiktívnu právnu odpoveď.
> - Ponaučenie: Každý fakt a paragraf vygenerovaný AI musíme sami overiť.

---

## Slide 4.12: Záverečné zhrnutie: 4 piliere bezpečnosti

- **Bezpečná pošta:** overujem odosielateľa, používam hover test, neotváram prílohy.
- **Ochrana počítača:** zamykám obrazovku, tvorím heslové frázy, neschvaľujem cudzie MFA.
- **Zodpovedná práca v cloude:** zdieľam s konkrétnymi ľuďmi, využívam verzionovanie.
- **Rozumná AI:** do verejnej AI nezadávam tajomstvá a výstupy vždy overujem.

---

## Navigácia v kurze

⬅️ [[A_blok_3_sharepoint_a_spoluprac.md|Blok 3: OneDrive, SharePoint & tímová spolupráca]] | 🏠 [[README|Obsah kurzu (MOC)]]
