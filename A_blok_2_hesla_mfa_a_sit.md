---
title: "Blok 2: Ochrana počítača, heslá (čo je hash), MFA & bezpečný internet"
aliases:
  - "A2: Blok 2: Ochrana počítača, heslá (čo je hash), MFA & bezpečný internet"
tags:
  - itsec
  - hesla
  - hash
  - sha256
  - mfa
  - spravca-hesiel
  - vpn
  - verejna-wifi
  - haveibeenpwned
  - modul-a
target_audience: "Bežní korporátni používatelia"
track: "Modul A: Bezpečnosť pre korporátnych používateľov"
time: "09:45 – 11:15 (90 min)"
created: 2026-10-22
license: "CC-BY-4.0"
---

# Blok 2: Ochrana počítača, heslá (čo je hash), MFA & bezpečný internet

> [!info] Informácie o bloku
> - **Cieľová skupina:** Bežní korporátni používatelia
> - **Časový rozsah:** 09:45 – 11:15 (90 min)
> - **Okruh:** Modul A: Bezpečnosť pre korporátnych používateľov
> - **Zdrojový súbor:** `A_blok_2_hesla_mfa_a_sit.pptx`

⬅️ [[A_blok_1_hrozby_a_phishing.md|Blok 1: Kybernetické hrozby, sociálne inžinierstvo & bezpečný e-mail]] | 🏠 [[README|Obsah kurzu (MOC)]] | [[A_blok_3_sharepoint_a_spoluprac.md|Blok 3: OneDrive, SharePoint & tímová spolupráca]] ➡️

---

## Slide 2.1: Ako chrániť svoj počítač každý deň?

![[static/A2_s01_21_ako_chrániť_svoj_počítač_každý_deň_14e989.jpg]]

- SILNÉ HESLO, KTORÉ NIKTO NEVIE OKREM VÁS.
- **Zamykanie obrazovky:** pri každom odchode použiť skratku Windows + L.
- **Politika čistého stola:** nenechávať na stole papieriky s heslami ani citlivé zmluvy.
- **Pravidelné reštarty a aktualizácie:** záplaty chránia systém pred novými dierami.
- **Cudzie USB kľúče:** nikdy nezapájať do firemného PC neznáme pamäťové médiá a kable

---

## Slide 2.2: Bezpecne Prihlasovanie

![[static/A2_s02_22_bezpecne_prihlasovanie_2b40c2.jpg]]

- Heslá sa neukladajú ako bežný text, ale ako zašifrovaný odtlačok – HASH.
- **Analógia s mletým mäsom:** z mäsa spravíte mleté, no naspäť ho už nezložíte.
- **Unikátny odtlačok:** ak zmeníte jediné písmeno, výsledný hash je úplne iný.
- Systém neporovnáva heslo, ale len to, či zadaný odtlačok sedí s uloženým.
- UKAŽKA VYPOČTU HASHU

**Powershell:**
```powershell
Get-FileHash -Path "C:\cesta\k\suboru.txt" -Algorithm SHA256
```

**Linux Shell:**
```bash
sha256sum \cesta\k\suboru.txt
```

---

## Slide 2.3: Prečo hackeri kradnú hashe?

![[static/A2_s03_23_prečo_hackeri_kradnú_hashe_2f6d40.jpg]]

- Pri úniku dát útočníci ukradnú milióny hashov namiesto hesiel.
- Útočník pomocou rýchlych počítačov skúša miliardy slov a porovnáva odtlačky.
- Jednoduché heslá ako 123456 či heslo majú dávno známy odtlačok.
- Dlhé a originálne heslo má odtlačok, ktorý útočník v žiadnom zozname nenájde.

**HASHCAT DEMO:**

---

## Slide 2.9 [CVIČENIE]: Názorná ukážka: Ako funguje HASH?

> [!example] Praktická úloha a ukážka
> - Cieľ: Vidieť na vlastné oči, ako zmena jedného písmena zmení celý odtlačok.
> - Ukážka: Lektor zadá slovo „heslo“, ukáže odtlačok, potom zmení „h“ na „H“.
> - Čo vidíme: Výsledný odtlačok sa kompletne zmení na nepoznanie.
> - Ponaučenie: Systém overuje zhodu bez toho, aby poznal vaše skutočné slovo.

---

## Slide 2.4: Mýtus o zložitých heslách: Dĺžka víťazí!

- Krátke zložité heslo (P@s!1) je ťažké na pamäť, no pre počítač ľahké na prelomenie.
- **Riešenie:** Heslová fráza – spojenie 3-4 bežných slov do vety (traktor-pecie-kolace).
- Takáto fráza má 25+ znakov, perfektne sa pamätá a jej prelomenie trvá stáročia.
- **Zákaz recyklácie:** nikdy nepoužívajte rovnaké heslo všade.

**HASHCAT DEMO:**

---

## Slide 2.5: Použite Správcu hesiel: Pamätajte si len jedno heslo

![[static/A2_s06_25_použite_správcu_hesiel_pamätajte_si_l_66f372.jpg]]

- Ľudský mozog si nedokáže pamätať desiatky rôznych silných hesiel.
- Správca hesiel bezpečne uchováva všetky prihlasovacie údaje v trezore.
- Vám stačí jediné hlavné heslo (Master Password), ostatné vygeneruje správca.
- **Chráni pred phishingom:** na podvodnej stránke správca heslo nevypíše.
- KEEPASS DEMO

---

## Slide 2.6: Viacfaktorové overenie (MFA): Druhý zámok

![[static/A2_s07_26_viacfaktorové_overenie_mfa_druhý_zámo_b2281f.jpg]]

- Ani silné heslo nestačí, ak ho útočník vyláka; preto potrebujeme MFA.
- **Dva nezávislé kroky:** niečo čo viem (heslo) + niečo čo mám (mobil v aplikácii).
- Bez potvrdenia na vašom telefóne sa útočník do účtu nedostane.
- **Zlaté pravidlo:** ak sa neprihlasujete a vyskočí notifikácia, okamžite ju zamietnite!

---

## Slide 2.7: Bezpečná práca na internete a verejné Wi-Fi

![[static/A2_s08_27_bezpečná_práca_na_internete_a_verejné_06e593.png]]

- Verejné Wi-Fi siete sú otvorené a ktokoľvek môže odpočúvať sieťový traffic.
- **EVIL TWIN:** útočník vytvorí sieť s názvom kaviarne a sleduje prevádzku.
- **Firemná VPN:** pri práci mimo kancelárie vždy zapínajte bezpečný šifrovaný tunel.
- **Kontrola ikony zámku:** vždy si všímajte protokol HTTPS a symbol zámku.
- UKAŽKA WIRESHARK-TERMSHARK

---

## Slide 2.8: VPN šifrovaný tunel odkialkoľvek ?

![[static/A2_s09_28_vpn_šifrovaný_tunel_odkialkoľvek_7c8f2b.jpg]]

- HOME OFFICE ODKIALKOLVEK?
- Je to naozaj take jednoduche?
- CO TO ZNAMENA PRE CYBERSECURITY?
- ZERO-TRUST NETWORKS

---

## Slide 2.10 [CVIČENIE]: Overenie úniku na HaveIBeenPwned

> [!example] Praktická úloha a ukážka
> - Cieľ: Zistiť, či vaša adresa alebo staré heslá neunikli pri incidentoch.
> - Nástroj: Bezplatná bezpečnostná služba haveibeenpwned.com od Troya Hunta.
> - Postup: Zadáme ukážkový e-mail a pozrieme databázy únikov.
> - Ponaučenie: Pochopenie nutnosti používať uniknuté heslá pre každú službu.
> - https://haveibeenpwned.com

---

## Slide 2.11: Zhrnutie 2. bloku: Bezpečný používateľ

- Odchádzam od počítača = automaticky stláčam Windows + L.
- Heslá tvorím ako dlhé slovné vety (heslové frázy), ktoré si ľahko pamätám.
- Na každú službu mám iné heslo, s čím mi pomáha správca hesiel.
- Mimo kancelárie sa pripájam cez VPN a potvrdzujem len svoje vlastné MFA.

---

## Navigácia v kurze

⬅️ [[A_blok_1_hrozby_a_phishing.md|Blok 1: Kybernetické hrozby, sociálne inžinierstvo & bezpečný e-mail]] | 🏠 [[README|Obsah kurzu (MOC)]] | [[A_blok_3_sharepoint_a_spoluprac.md|Blok 3: OneDrive, SharePoint & tímová spolupráca]] ➡️
