---
title: "Blok 3: Sledovanie prevádzky (NIDS), centrálne logovanie & Wazuh"
aliases:
  - "B3: Blok 3: Sledovanie prevádzky (NIDS), centrálne logovanie & Wazuh"
tags:
  - itsec
  - ids-ips
  - suricata
  - eve-json
  - jq
  - syslog-ng
  - graylog
  - wazuh
  - siem
  - xdr
  - fim
  - modul-b
target_audience: "Správcovia sietí a systémov (Administrátori)"
track: "Modul B: Pokročilá bezpečnosť pre administrátorov"
time: "12:15 – 13:45 (90 min)"
created: 2026-10-22
license: "CC-BY-4.0"
---

# Blok 3: Sledovanie prevádzky (NIDS), centrálne logovanie & Wazuh

> [!info] Informácie o bloku
> - **Cieľová skupina:** Správcovia sietí a systémov (Administrátori)
> - **Časový rozsah:** 12:15 – 13:45 (90 min)
> - **Okruh:** Modul B: Pokročilá bezpečnosť pre administrátorov
> - **Zdrojový súbor:** `B_Blok 3_ Sledovanie prevádzky, Logy & Wazuh.pptx`

⬅️ [[B_blok_2_perimetricka_ochrana_wifi_a_firewally.md|Blok 2: Perimetrická ochrana, Wi-Fi & moderné firewally]] | 🏠 [[README|Obsah kurzu (MOC)]] | [[B_blok_4_ochrana_edr_threat_hunting_a_legislativa.md|Blok 4: Ochrana EDR, Threat Hunting, Honeypoty & Legislatíva]] ➡️

---

## ŠKOLENIE KYBERNETICKEJ BEZPEČNOSTI PRE ADMINISTRÁTOROV

![[static/B1_s01_školenie_kybernetickej_bezpečnosti_pre_a_8c9ba0.png]]

- **BLOK 3:** Sledovanie prevádzky, centrálny zber logov & SIEM
- **Časový rozsah:** 12:15 – 13:45 | IDS/IPS Suricata, Syslog-ng, Graylog, SIEM/XDR platforma Wazuh & FIM

---

## Slide 3.1: Systémy detekcie a prevencie prienikov (IDS vs. IPS)

![[static/B3_s02_31_systémy_detekcie_a_prevencie_prieniko_d0598f.png]]

- **IDS (Požiarny hlásič):** Pasívne sleduje kópiu sieťovej prevádzky a pri zistení útoku zalarmuje správcu.
- **IPS (Hasiaci prístroj):** Je zaradený priamo v ceste komunikácie a zistené škodlivé pakety okamžite blokuje (DROP).
- **Pripojenie cez SPAN port:** IDS využíva zrkadlenie portov na switchi bez akéhokoľvek spomalenia siete.
- **Riziko False Positive:** Zle nastavené IPS môže omylom zablokovať legitímnu firemnú komunikáciu.

---

## Slide 3.2: Suricata (Moderný open-source IDS/IPS)

![[static/B3_s03_32_suricata_moderný_open-source_idsips_294632.jpg]]

- **Nástroj Suricata:** Špičkový open-source systém, ktorý v reálnom čase analyzuje sieťové toky a hľadá útoky.
- **Multi-threading:** Využíva všetky jadrá procesora súčasne, vďaka čomu stíha aj gigabitové firemné siete.
- **Porozumenie protokolom:** Rozpoznáva HTTP, DNS, TLS, SMB a vytahuje názvy súborov aj nebezpečné domény.
- **Emerging Threats pravidlá:** Pracuje s pravidelne aktualizovanou databázou vzorov najnovších útokov.

> [!tip] Poznámka lektora / doplňujúci kontext
> Security Information and Event Management

---

## Slide 3.3: Štruktúrovaný protokol Suricata (eve.json & jq)

![[static/B3_s04_33_štruktúrovaný_protokol_suricata_evejs_ab2189.jpg]]

- **Súbor eve.json:** Všetky události, alerty a certifikáty ukládá Suricata do štruktúrovaného JSON formátu.
- **Presné polia:** Záznamy obsahujú presný čas, zdrojovú/cieľovú IP a typ udalosti pre rýchly export do SIEM.
- **Filtrovanie cez jq:** Nástroj jq umožňuje správcovi v Linux konzole bleskovo filtrovať dôležité výstrahy.
- **Live monitoring:** Príkaz tail -f eve.json | jq zobrazuje len bezpečnostné alerty v reálnom čase.

---

## Slide 3.4: Architektúra centrálneho zberu logov

![[static/B3_s05_34_architektúra_centrálneho_zberu_logov_067ca7.png]]

- **Hrozba mazania stôp:** Prvým krokom útočníka po prieniku je zmazanie lokálnych logov pre zahladenie stôp.
- **Okamžité odosielanie:** Každá udalosť sa v reálnom čase odosiela po sieti na centrálny zabezpečený server.
- **Nemennosť a integrita:** Centrálny server ukladá logy tak, aby ich nebolo možné spätne upraviť ani vymazať.
- **Zákonná povinnosť:** Centrálny zber vyžadujú normy ISO 27001 aj Vyhláška NBÚ č. 362/2018 Z.z.

---

## Slide 3.5: Syslog-ng (Bezpečný transport logov)

![[static/B3_s06_35_syslog-ng_bezpečný_transport_logov_9932ee.png]]

- **Úloha Syslog-ng:** Výkonný démon na serveroch, ktorý zhromažďuje správy a smeruje ich na centrálne úložisko.
- **Stavebné bloky:** Konfigurácia definuje zdroj (source), cieľ (destination), filter a logovacie pravidlo.
- **Šifrovanie TLS:** Nahradzuje nešifrovaný Syslog za bezpečný TLS tunel s klientskymi certifikátmi.
- **Lokálna vyrovnávacia pamäť:** Pri výpadku siete ukladá logy do pamäte a doručí ich po obnovení spojenia.

---

## Slide 3.6: Graylog (Centrálne vyhľadávanie a vizualizácia)

![[static/B3_s07_36_graylog_centrálne_vyhľadávanie_a_vizu_f0992e.png]]

- **Platforma Graylog:** Open-source systém, ktorý indexuje logy zo všetkých serverov do vyhľadávacej databázy.
- **Bleskové vyhľadávanie:** Správca vyhľadáva meno používateľa alebo IP adresu v miliónoch logov do 1 sekundy.
- **Grafické dashboardy:** Zobrazujú neúspešné prihlásenia, vyťaženie firewallu a sieťové anomálie v grafoch.
- **Automatické alerty:** Posiela upozornenia (e-mail, Teams) pri prekročení stanovených prahových hodnôt.

---

## Slide 3.7: Wazuh (Architektúra SIEM/XDR platformy)

![[static/B3_s08_37_wazuh_architektúra_siemxdr_platformy_80d4ff.png]]

- **Čo je SIEM:** Spája logy zo všetkých zdrojov, koreluje ich a automaticky odhaľuje komplexné útoky.
- **Wazuh Platforma:** Špičkové open-source riešenie pre SIEM a priamy dohľad nad bezpečnosťou koncových bodov.
- **3 komponenty:** Wazuh Agent (stanice), Wazuh Server (analytika) a Wazuh Dashboard (web rozhranie).
- **Minimálna záťaž:** Agent komunikuje po šifrovanom porte (1514/TCP) a spotrebúva pod 1 % CPU.

---

## Slide 3.8: Wazuh File Integrity Monitoring (FIM)

![[static/B3_s09_38_wazuh_file_integrity_monitoring_fim_806bb8.png]]

- **Princíp FIM:** Wazuh kontinuálne porovnáva digitálne odtlačky (hashe) dôležitých súborov a registrov.
- **Detekcia zmien:** Pri úprave konfiguračného súboru alebo pridaní nového administrátora okamžite spustí alarm.
- **Detailný audit:** Správca presne vidí, ktorý používateľ a proces súbor zmenil a aký bol pôvodný obsah.
- **Aktívna odozva (Active Response):** Dokáže automaticky zablokovať IP útočníka alebo zabiť podozrivý proces.

---

## Slide 3.9: Opakovanie 3. bloku: Kontrolné otázky

> [!question] Otázky na overenie vedomostí
>
> **1. Rozdiel medzi IDS a IPS:**
> - Prečo je v praxi bezpečnejšie najprv nasadiť Suricatu v pasívnom režime IDS a až po overení pravidiel uvažovať o IPS?
>
> **2. Dôležitosť centrálneho logovania:**
> - Aký je hlavný bezpečnostný dôvod na to, aby sme logy neuchovávali iba lokálne na diskoch jednotlivých serverov?
>
> **3. Prínos systému Graylog pre správcu:**
> - Ako platforma Graylog pomôže administrátorovi pri rýchlom hľadaní príčiny výpadku siete alebo bezpečnostného incidentu?
>
> **4. Funkcia Wazuh FIM:**
> - Akým spôsobom dokáže modul kontroly integrity súborov (FIM) odhaliť útočníka, ktorý sa do systému dostal cez novú zraniteľnosť?

---

## Image Sources

![[static/B3_s11_image_sources_68915c.png]]

![[static/B3_s11_image_sources_01cf32.png]]

![[static/B3_s11_image_sources_c4c32b.png]]

> [!note] Použité zdroje a diagramy
> - [https://canada1.discourse-cdn.com/flex030/uploads/suricata/original/1X/b7724d3d0fef0b395f6605488ca54e277af4beee.jpeg](https://canada1.discourse-cdn.com/flex030/uploads/suricata/original/1X/b7724d3d0fef0b395f6605488ca54e277af4beee.jpeg)
> - Source: forum.suricata.io
> - [https://raw.githubusercontent.com/O-X-L/logserver-graylog/refs/heads/main/Overview.svg](https://raw.githubusercontent.com/O-X-L/logserver-graylog/refs/heads/main/Overview.svg)
> - Source: github.com
> - [https://wazuh.com/wp-content/themes/wazuh-v3/assets/images/home/siem-dashboard.png?ver=1790971975750](https://wazuh.com/wp-content/themes/wazuh-v3/assets/images/home/siem-dashboard.png?ver=1790971975750)
> - Source: wazuh.com

---

## Navigácia v kurze

⬅️ [[B_blok_2_perimetricka_ochrana_wifi_a_firewally.md|Blok 2: Perimetrická ochrana, Wi-Fi & moderné firewally]] | 🏠 [[README|Obsah kurzu (MOC)]] | [[B_blok_4_ochrana_edr_threat_hunting_a_legislativa.md|Blok 4: Ochrana EDR, Threat Hunting, Honeypoty & Legislatíva]] ➡️
