---
title: "Blok 3: OneDrive, SharePoint & tímová spolupráca"
aliases:
  - "A3: Blok 3: OneDrive, SharePoint & tímová spolupráca"
tags:
  - itsec
  - sharepoint
  - onedrive
  - cloud
  - prava-ugo-acl
  - snapshoty
  - verzionovanie
  - ransomware-obnova
  - modul-a
target_audience: "Bežní korporátni používatelia"
track: "Modul A: Bezpečnosť pre korporátnych používateľov"
time: "12:15 – 13:45 (90 min)"
created: 2026-10-22
license: "CC-BY-4.0"
---

# Blok 3: OneDrive, SharePoint & tímová spolupráca

> [!info] Informácie o bloku
> - **Cieľová skupina:** Bežní korporátni používatelia
> - **Časový rozsah:** 12:15 – 13:45 (90 min)
> - **Okruh:** Modul A: Bezpečnosť pre korporátnych používateľov
> - **Zdrojový súbor:** `A_blok_3_sharepoint_a_spoluprac.pptx`

⬅️ [[A_blok_2_hesla_mfa_a_sit.md|Blok 2: Ochrana počítača, heslá, MFA & bezpečný internet]] | 🏠 [[README|Obsah kurzu (MOC)]] | [[A_blok_4_gdpr_a_ai_bezpecnost.md|Blok 4: Ochrana firemných údajov, GDPR & AI nástroje]] ➡️

---

## Slide 3.1: OLD SCHOOL VERSUS  CLOUD

![[static/A3_s01_31_old_school_versus_cloud_b8dfe0.jpg]]

- **OneDrive:** Váš osobný pracovný stôl; koncepty, poznámky a rozpracované dokumenty.
- **SharePoint:** Spoločná firemná knižnica; hotové projekty, zmluvy a tímové dáta.
- >NextCloud, ProtonDrive
- **Automatická synchronizácia:** súbory dostupné z počítača, mobilu aj webu.
- **Už žiadne stratené dáta:** pri poruche notebooku sú cloudové súbory v bezpečí.
- Security Included

---

## Slide 3.2: NAJČASTEJŠIE CHYBY PRI POUZIVANÍ CLOUDOVYCH ULOŽÍSK

- 1. Architektúra a štruktúra dát
- Prenášanie starých štruktúr (File Server Mentality): Kopírovanie hlbokých štruktúr priečinkov z lokálnych diskov do cloudu. SharePoint je primárne vyhľadávací systém; hlboké vnorenie sťažuje orientáciu a naráža na systémové limity dĺžky cesty k súborom.
- **Zanedbanie metadát:** Spoliehanie sa výhradne na adresárove priečinky namiesto využívania vlastných stĺpcov, tagov a typov obsahu, čo výrazne spomaľuje vyhľadávanie a filtrovanie dokumentov.

---

## Slide 3.3: NAJČASTEJŠIE CHYBY PRI POUŽÍVANÍ CLOUDOVYCH ULOZISK

- 2. Bezpečnosť a správa oprávnení
- **Nebezpečné odkazy na zdieľanie:** Predvolené vytváranie odkazov typu „Každý, kto má odkaz, môže upravovať“, ktoré sa ľahko dostanú mimo firemný perimeter.
- **Rozbitá dedičnosť oprávnení:** Nadmerné udeľovanie výnimiek a špecifických práv na úrovni jednotlivých súborov či vnorených priečinkov namiesto čistého riadenia prístupu na úrovni celých lokalít (sites) či knižníc.

---

## Slide 3.4: NAJČASTEJŠIE CHYBY PRI POUŽÍVANÍ CLOUDOVYCH ULOŽÍSK

- 3. Používateľské návyky a správa verzií
- **Ignorovanie vstavaného verzovania:** Ručné premenovávanie súborov (napr. zmluva_final_v2_opravené.docx) namiesto spoliehania sa na automatickú históriu verzií v SharePointe.
- **Nadmerná lokálna synchronizácia:** Synchronizácia celých obrovských firemných knižníc do lokálneho počítača bez zapnutia funkcie Files On-Demand (Súbory na požiadanie), čo zbytočne zaťažuje disky a spomaľuje systém.

---

## Slide 3.5: NAJČASTEJŠIE CHYBY PRI POUŽÍVANÍ CLOUDOVYCH ULOŽÍSK

- 4. Governance a životný cyklus dát
- **Mýtus „Cloud je automaticky zálohovaný“:** Neoboznámenie sa so zdieľaným modelom zodpovednosti (Shared Responsibility Model). Microsoft garantuje dostupnosť infraštruktúry, ale ochrana dát pred ransomvérom, omylným zmazaním či internou chybou je na strane používateľa.
- **Chýbajúce pravidlá archivácie:** Absencia politík uchovávania dát (Retention Policies), čo v priebehu rokov vedie k obrovskému množstvu duplicitných a zastaraných súborov.

---

## Slide 3.6: Poriadok v priečinkoch a organizácia

- **Zmysluplná štruktúra:** vyhnite sa ukladaniu stoviek súborov na plochu.
- **Prehľadné názvy:** používajte zrozumiteľné pomenovania s dátumom (2025_Zmluva).
- **Jeden zdroj pravdy:** namiesto posielania kópií pracujte na jednom odkaze.
- **Preč s lokálnym diskom:** súbory len na disku C nie sú chránené zálohovaním.

---

## Slide 3.7: Ako bezpečne zdieľať: Voľba odkazu

- **Konkrétni ľudia (Najbezpečnejšie):** odkaz otvorí len ten, koho e-mail zadáte.
- **Ľudia v našej organizácii:** súbor otvorí ktokoľvek z firmy, kto má odkaz.
- **Ľudia s existujúcim prístupom:** pošle odkaz kolegom, ktorí už prístup majú.
- **POZOR na „Ktokoľvek s odkazom“:** funguje ako verejný leták na ulici!

---

## Slide 3.8: Pokročilé ochranné prvky pri zdieľaní

- **Expirácia odkazu:** odkaz po niekoľkých dňoch automaticky prestane fungovať.
- **Blokovanie sťahovania:** príjemca si dokument prečíta online, nemôže ho stiahnuť.
- **Heslo na odkaz:** dodatočný bezpečnostný kód oznámený iným kanálom (SMS ???).
- **Pravidelné upratovanie:** po skončení projektu zrušte prístup externistom.

---

## Slide 3.9: Permissions: UGO a ACL

![[static/A3_s09_39_permissions_ugo_a_acl_17328c.png]]

- Rozdiel medzi Môže zobrazovať (Read) a Môže upravovať (Edit).
- **Ochrana pred prepísaním:** externým partnerom posielajte materiály len na čítanie.
- **Oprávnenia priečinka:** čokoľvek vložíte do priečinka, získa rovnaké práva.
- **Kontrola prístupov:** cez položku Manage Access môžete kedykoľvek práva odobrať.
- USER
- GROUP
- OTHERS

---

## Slide 3.10: Verzionovanie pomocou Snapshotov

![[static/A3_s10_310_verzionovanie_pomocou_snapshotov_79277a.jpg]]

- OneDrive a SharePoint automaticky ukladajú históriu každej úpravy.
- **Koniec paniky:** ak omylom vymažete časť tabuľky, nič nie je stratené.
- **Jednoduchý návrat v čase:** pozrite sa, ako dokument vyzeral včera či pred týždňom.
- **Sledovanie zmien:** presne vidíte, kto a kedy urobil konkrétnu úpravu.

---

## Slide 3.11: Obnova verzií a ochrana pred ransomvérom

- **Ako vrátiť verziu:** kliknúť pravým tlačidlom -> História verzií -> Obnoviť.
- **Celkový rollback:** ak ransomvér zašifruje súbory, OneDrive umožňuje vrátiť stav.
- **Kôš s poistkou:** vymazaný súbor zostáva v koši 93 dní, IT ho vie obnoviť.
- **Žiadne platenie výkupného:** cloudové verzie sú najlepšou zbraňou.
- NEZABUDNÚŤ NA BACKUP SÚBOROV

---

## Slide 3.12: Zhrnutie 3. bloku: Zlaté pravidlá cloudu

- Koncepty patria na OneDrive, tímové projekty na SharePoint; na plochu nič.
- Neposielame súbory v prílohe mailu, ale zdieľame odkaz na centrálny súbor.
- Pri externom zdieľaní volíme Konkrétni ľudia a zákaz sťahovania.
- Pri prepísaní dát pamätáme na záchrannú funkciu História verzií.

---

## Slide 3.8: Najcastejsie zranitelnosti SHAREPOINT

- . Software Vulnerabilities & Remote Code Execution (RCE)
- Authentication Bypasses & Deserialization Flaws: Attackers target unpatched on-premises servers using exploit chains (such as those leveraging forged security tokens or unsafe .NET object deserialization) to bypass authentication entirely.
- **Web Shell Deployment:** Once attackers achieve code execution through vulnerabilities (like critical flaws in endpoints such as ToolPane.aspx or _trust/default.aspx), they drop malicious ASPX web shells (e.g., spinstall0.aspx) into the SharePoint layout directories. This grants them persistent, remote command-line access via IIS (w3wp.exe).
- **Machine Key Theft:** Threat actors actively target SharePoint farm ASP.NET machine keys. Stealing these keys allows them to forge valid session tokens and execute arbitrary code repeatedly, even if initial entry points are patched.

---

## Slide 3.9 Najcastejsie vektory utokov na Sharepoint

- Misconfigurations and Excessive Permissions
- **Over-sharing and "Anyone" Links:** The most frequent human-error vector involves users generating anonymous or broad "Anyone with the link can edit/view" sharing links, exposing confidential corporate data to the public internet.
- **Broken Permission Inheritance:** Manual breaking of permission inheritance on sensitive sub-sites, document libraries, or individual files creates hidden islands of unsecured data that bypass broader compliance tracking.

---

## Slide 3.10 Najcastejsie vektory utokov na Sharepoint

- Credential Theft & Lateral Movement
- **LSASS Dumping & Token Theft:** Attackers using SharePoint as an initial foothold deploy credential-harvesting tools (like Mimikatz) to scrape local memory and LSASS, extracting plaintext credentials or tokens to move laterally across the internal domain.
- **Living off the Land (LotL):** Post-compromise, actors leverage built-in administrative tools, legitimate cloud storage services for staging payloads, and signed vulnerable drivers to disable endpoint detection before launching ransomware.

---

## Navigácia v kurze

⬅️ [[A_blok_2_hesla_mfa_a_sit.md|Blok 2: Ochrana počítača, heslá, MFA & bezpečný internet]] | 🏠 [[README|Obsah kurzu (MOC)]] | [[A_blok_4_gdpr_a_ai_bezpecnost.md|Blok 4: Ochrana firemných údajov, GDPR & AI nástroje]] ➡️
