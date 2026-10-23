---
title: "Blok 4: Ochrana EDR, Threat Hunting, Honeypoty & Legislatíva"
aliases:
  - "B4: Blok 4: Ochrana EDR, Threat Hunting, Honeypoty & Legislatíva"
tags:
  - itsec
  - edr
  - threat-hunting
  - velociraptor
  - sigma-rules
  - honeypot
  - chameleon
  - zakon-69-2018
  - vyhlaska-nbu-362-2018
  - csirt
  - sk-cert
  - modul-b
target_audience: "Správcovia sietí a systémov (Administrátori)"
track: "Modul B: Pokročilá bezpečnosť pre administrátorov"
time: "14:00 – 16:00 (120 min)"
created: 2026-10-22
license: "CC-BY-4.0"
---

# Blok 4: Ochrana EDR, Threat Hunting, Honeypoty & Legislatíva

> [!info] Informácie o bloku
> - **Cieľová skupina:** Správcovia sietí a systémov (Administrátori)
> - **Časový rozsah:** 14:00 – 16:00 (120 min)
> - **Okruh:** Modul B: Pokročilá bezpečnosť pre administrátorov
> - **Zdrojový súbor:** `B_Blok 4_ Ochrana EDR, Threat Hunting & Legislatíva.pptx`

⬅️ [[B_blok_3_sledovanie_prevadzky_logy_a_wazuh.md|Blok 3: Sledovanie prevádzky (NIDS), centrálne logovanie & Wazuh]] | 🏠 [[README|Obsah kurzu (MOC)]]

---

## ŠKOLENIE KYBERNETICKEJ BEZPEČNOSTI PRE ADMINISTRÁTOROV

![[static/B1_s01_školenie_kybernetickej_bezpečnosti_pre_a_8c9ba0.png]]

- **BLOK 4:** Ochrana PC (EDR), Threat Hunting, Honeypot & Zákon o KB
- **Časový rozsah:** 14:00 – 16:00 | EDR, Velociraptor, Sigma pravidlá, Chameleon Honeypot, Zákon 69/2018 Z.z. & Vyhláška NBÚ

---

## Slide 4.1: Moderná ochrana koncových bodov (Antivírus vs. EDR)

![[static/B4_s02_41_moderná_ochrana_koncových_bodov_antiv_502b0d.jpg]]

- **Limity antivírusu:** Klasický antivírus hľadá iba známe vzory súborov; nové a modifikované vírusy nespozná.
- **Fileless útoky:** Útočníci neukladajú súbory na disk, ale zneužívajú dôveryhodné nástroje (PowerShell) v RAM.
- **EDR technológia:** Sleduje chovanie programov, sieťové spojenia a spúšťané procesy nepretržite v reálnom čase.
- **Detekcia anomálií:** Odhalí útok podľa správania (napr. Word spúšťajúci príkazový riadok a sťahujúci kód).

---

## Slide 4.2: Forenzná analýza EDR: Strom procesov & Izolácia

![[static/B4_s03_42_forenzná_analýza_edr_strom_procesov_i_290de9.png]]

- **Strom procesov (Process Tree):** EDR zobrazuje rodokmeň procesov – presne vidíte, čo ktorý program spustil.
- **Ochrana pamäte LSASS:** Stráži pokusy útočníkov o vytiahnutie doménových hesiel z pamäte systému Windows.
- **Izolácia stanice:** Správca dokáže jedným kliknutím odpojiť podozrivý PC od siete a zastaviť šírenie nákazy.
- **Riadiaci kanál:** Aj počas izolácie zostáva funkčné šifrované spojenie pre vzdialenú opravu a analýzu.

---

## Slide 4.3: Úvod do Threat Huntingu (Proaktívny lov hrozieb)

![[static/B4_s04_43_úvod_do_threat_huntingu_proaktívny_lo_7557c4.png]]

- **Predpokladajme prienik:** Správca nečaká na poplach antivírusu, ale predpokladá, že útočník už je v sieti prítomný.
- **Proaktívne hľadanie:** Cielené pátranie po skrytých anomáliách, ktoré automatické nástroje nemusia vyhodnotiť ako útok.
- **MITRE ATT&CK:** Globálna znalostná databáza techník hackerov, ktorá slúži ako sprievodca pri vyhľadávaní.
- **Pátracie otázky:** Admin si kladie otázky typu "Bežia v noci neobvyklé skripty?" a preveruje stanice.

---

## Slide 4.4: Velociraptor (Digitálne vyšetrovanie staníc)

![[static/B4_s05_44_velociraptor_digitálne_vyšetrovanie_s_f6d53c.jpg]]

- **Nástroj Velociraptor:** Špičkový open-source nástroj na bleskový zber digitálnych dôkazov zo stoviek PC.
- **Jednoduchá architektúra:** Centrálny webový server (Docker) a ľahký klientsky agent pre Windows a Linux.
- **Dopytovací jazyk VQL:** K počítačom pristupuje ako k databáze; otázkou podobnou SQL získa odpovede do pár sekúnd.
- **Hromadná kontrola:** Umožňuje zistiť výskyt konkrétneho podozrivého súboru na všetkých staniciach vo firme.

---

## Slide 4.5: Sigma pravidlá (Univerzálny formát detekcie)

![[static/B4_s06_45_sigma_pravidlá_univerzálny_formát_det_824431.png]]

- **Problém rozdrobenosti:** Rôzne SIEM nástroje (Wazuh, Graylog) používajú vlastný vyhodnocovací syntax.
- **Štandard Sigma:** Univerzálny textový formát (YAML), ktorý popisuje vzor kybernetického útoku v logoch.
- **Konverzia pravidiel:** Prekladače korigujú jedno Sigma pravidlo priamo do vyhľadávacieho dotazu pre akýkoľvek SIEM.
- **Komunitná sila:** Pri výskyte novej hrozby experti okamžite zverejnia Sigma pravidlo voľne na stiahnutie.

---

## Slide 4.6: Koncept Honeypot (Klamná pasca v sieti)

![[static/B4_s07_46_koncept_honeypot_klamná_pasca_v_sieti_607508.png]]

- **Čo je Honeypot:** Zámerne vytvorený zdanlivo zraniteľný server, ktorý slúži ako návnada na útočníka.
- **Nulová bežná prevádzka:** Na honeypote nebeží produkcia, preto bežní zamestnanci s ním nikdy nekomunikujú.
- **Nulové False Positives:** Akýkoľvek pokus o kontakt alebo skenovanie znamená takmer 100 % istotu útočníka v sieti.
- **Včasné varovanie:** Odhalí IP útočníka a jeho postupy skôr, než nájde skutočné produkčné servery.

---

## Slide 4.7: Chameleon Honeypot (Open-source pasca)

![[static/B4_s08_47_chameleon_honeypot_open-source_pasca_35ba84.jpg]]

- **Nástroj Chameleon:** Ľahký modulárny honeypot nasaditeľný v Docker kontajneri priamo v interných VLAN.
- **Imitácia služieb:** Vierohodne simuluje služby ako SSH, HTTP web, FTP súbory či databázové porty.
- **Záznam aktivity:** Zaznamenáva pokusy o heslo, spojenia a spúšťané príkazy útočníka do logov.
- **Grafana vizualizácia:** Prepojenie na prehľadný dashboard zobrazuje útoky v reálnom čase na mapách a grafoch.

---

## Slide 4.8: Slovenská legislatíva: Zákon č. 69/2018 Z.z.

![[static/B4_s09_48_slovenská_legislatíva_zákon_č_692018__fca76d.png]]

- **Zákon 69/2018 Z.z.:** Základný právny rámec KB na Slovensku preberajúci európske smernice NIS a NIS2.
- **Pôsobnosť zákona:** Vzťahuje sa na prevádzkovateľov základných služieb (zdravotníctvo, doprava, energetika, úrady).
- **Vyhláška NBÚ č. 362/2018 Z.z.:** Vykonávací predpis definujúci konkrétne bezpečnostné opatrenia v 16 oblastiach.
- **Systematický riadenie:** Vyžaduje poriadok v IT, pravidelné riadenie rizík, testovanie záloh a auditovanie.

---

## Slide 4.9: Technické požiadavky Vyhlášky NBÚ na IT

![[static/B4_s10_49_technické_požiadavky_vyhlášky_nbú_na__4aa52b.png]]

- **Segmentácia sietí:** Dôsledné rozdelenie siete (VLAN), umiestnenie webov do DMZ a ochrana perimetra firewallom.
- **Centrálne logovanie:** Povinnosť centrálne zbierať a uchovávať auditné záznamy bez možnosti ich manipulácie.
- **Skenovanie zraniteľností:** Pravidelná kontrola systémov skenermi a aplikovanie bezpečnostných záplat.
- **Ochrana pred malvérom:** Nasadenie a aktualizácia antivírusových/EDR nástrojov na všetkých zariadeniach.

---

## Slide 4.10: Rola Manažéra KB a hlásenie incidentov

![[static/B4_s11_410_rola_manažéra_kb_a_hlásenie_incident_6da37b.png]]

- **Nezávislosť Manažéra KB:** Zákonom vyžadovaná rola nezávislá od IT prevádzky (admin nemôže kontrolovať sám seba).
- **Skúška na NBÚ:** Manažér kybernetickej bezpečnosti musí úspešne absolvovať odbornú skúšku pred NBÚ.
- **Hlásenie incidentov:** Zákonná povinnosť bezodkladne hlásiť závažné incidenty na SK-CERT alebo CSIRT.SK.
- **Disaster Recovery:** Vopred spísané a otestované postupy na obnovu dát a serverov zo záloh po havárii.

---

## Slide 4.11: Funkcie tímov CERT / CSIRT (SK-CERT & CSIRT.SK)

![[static/B4_s12_411_funkcie_tímov_cert_csirt_sk-cert_csi_7cabfb.png]]

- **Reakcia a riešenie incidentov:** Prijímanie hlásení o útokoch, koordinácia riešenia (triage), zmierňovanie následkov a technická pomoc subjektom.
- **Včasné varovanie a Threat Intel:** Nepretržité monitorovanie hrozieb, vydávanie bezpečnostných varovaní, bulletinov o zraniteľnostiach a zdieľanie IoC.
- **Proaktívne služby a audit (Achilles):** Preventívne skenovanie systémov a hľadanie slabín – bezplatná služba Achilles od CSIRT.SK pre audit verejných IP a domén.
- **Forenzná expertíza a spolupráca:** Hĺbková analýza malvéru a útokov, metodické usmernenia a výmena informácií v medzinárodných sieťach (CSIRTs Network, FIRST).

---

## Slide 4.12: Opakovanie 4. bloku: Kontrolné otázky

> [!question] Otázky na overenie vedomostí
>
> **1. Rozdiel medzi AV a EDR:**
> - V čom spočíva hlavná výhoda EDR technológie pri odhaľovaní moderných útokov, ktoré neukladajú súbory na disk (fileless)?
>
> **2. Rýchla kontrola cez Velociraptor:**
> - Ako dokáže administrátor cez Velociraptor preveriť výskyt neznámeho procesu na stovkách firemných počítačov do pár minút?
>
> **3. Prínos Chameleon honeypotu:**
> - Prečo je nasadenie jednoduchej pasce v sieti mimoriadne efektívnym spôsobom, ako okamžite odhaliť cudzieho človeka v sieti?
>
> **4. Zákonné požiadavky na správcu:**
> - Ktoré 4 základné technické oblasti (segmentácia, logy, skenovanie zraniteľností, EDR) vyžaduje Vyhláška NBÚ?

---

## Slide 5.1: Komplexný pohľad, certifikácie a diskusia

![[static/B1_s01_školenie_kybernetickej_bezpečnosti_pre_a_8c9ba0.png]]

- **Viacvrstvová obrana (Defense in Depth):** Spojenie segmentácie, firewallu, centrálnych logov, EDR a pascí.
- **Nepretržitý proces:** Bezpečnosť je každodenná rutina – pravidelný patching, zálohovanie a kontrola logov.
- **Certifikačné cesty:** Medzinárodné skúšky CompTIA Security+, Network+, Cisco CyberOps a certifikát Manažéra KB pod NBÚ.
- **Otázky a odpovede (Q&A):** Priestor na vašu diskusiu, riešenie praktických scenárov a odovzdanie certifikátov.
- Ďakujeme za pozornosť!

---

## Image Sources

![[static/B4_s15_image_sources_9103eb.png]]

![[static/B4_s15_image_sources_39adc4.png]]

> [!note] Použité zdroje a diagramy
> - [https://www.businessbroadbandhub.co.uk/wp-content/uploads/2025/12/EDR-detection-and-response-summary.webp](https://www.businessbroadbandhub.co.uk/wp-content/uploads/2025/12/EDR-detection-and-response-summary.webp)
> - Source: www.businessbroadbandhub.co.uk
> - [https://www.techtarget.com/rms/onlineimages/security-honeypot_place_in_network-f_mobile.png](https://www.techtarget.com/rms/onlineimages/security-honeypot_place_in_network-f_mobile.png)
> - Source: www.techtarget.com

---

## Navigácia v kurze

⬅️ [[B_blok_3_sledovanie_prevadzky_logy_a_wazuh.md|Blok 3: Sledovanie prevádzky (NIDS), centrálne logovanie & Wazuh]] | 🏠 [[README|Obsah kurzu (MOC)]]
