---
title: "Blok 2: Perimetrická ochrana, Wi-Fi & moderné firewally"
aliases:
  - "B2: Blok 2: Perimetrická ochrana, Wi-Fi & moderné firewally"
tags:
  - itsec
  - wifi-security
  - wpa3
  - wpa-enterprise
  - 802-1x
  - freeradius
  - evil-twin
  - ngfw
  - dpi
  - wireguard
  - vpn
  - modul-b
target_audience: "Správcovia sietí a systémov (Administrátori)"
track: "Modul B: Pokročilá bezpečnosť pre administrátorov"
time: "09:45 – 11:15 (90 min)"
created: 2026-10-22
license: "CC-BY-4.0"
---

# Blok 2: Perimetrická ochrana, Wi-Fi & moderné firewally

> [!info] Informácie o bloku
> - **Cieľová skupina:** Správcovia sietí a systémov (Administrátori)
> - **Časový rozsah:** 09:45 – 11:15 (90 min)
> - **Okruh:** Modul B: Pokročilá bezpečnosť pre administrátorov
> - **Zdrojový súbor:** `B_Blok 2_ Perimetrická ochrana, Wi-Fi & Firewally.pptx`

⬅️ [[B_blok_1_sietova_infrastruktura_a_skenovanie.md|Blok 1: Základy bezpečnej sieťovej infraštruktúry & skenovanie siete]] | 🏠 [[README|Obsah kurzu (MOC)]] | [[B_blok_3_sledovanie_prevadzky_logy_a_wazuh.md|Blok 3: Sledovanie prevádzky (NIDS), centrálne logovanie & Wazuh]] ➡️

---

## ŠKOLENIE KYBERNETICKEJ BEZPEČNOSTI PRE ADMINISTRÁTOROV

![[static/B1_s01_školenie_kybernetickej_bezpečnosti_pre_a_8c9ba0.png]]

- **BLOK 2:** Perimetrická ochrana, bezpečná Wi-Fi & moderné firewally s DPI
- **Časový rozsah:** 09:45 – 11:15 | WPA Enterprise (802.1X), RADIUS, Evil Twin, Next-Gen Firewall, DPI & WireGuard VPN

---

## Slide 2.1: Základy bezpečnosti korporátnej Wi-Fi siete

![[static/B2_s02_21_základy_bezpečnosti_korporátnej_wi-fi_9bdd7d.png]]

- **Signál nepozná steny:** Rádiový signál presahuje steny budovy a umožňuje útočníkovi pokusy o pripojenie z ulice.
- **Riziko zdieľaného hesla:** Heslo (PSK) pozná celá firma aj návštevy, a pri odchode zamestnanca sa málokedy mení.
- **Oddelenie sietí (SSID):** Zriaďujeme minimálne dve nezávislé siete – jednu pre firemné stanice a druhá pre hostí.
- **Guest VLAN:** Wi-Fi pre hostí smerujeme výhradne do izolovanej VLAN bez prístupu k vnútorným serverom.

---

## Slide 2.2: Zabezpečenie WPA2-Personal vs. moderné WPA3

![[static/B2_s03_22_zabezpečenie_wpa2-personal_vs_moderné_fa5507.png]]

- **WPA2 Handshake:** Overenie prebieha výmenou 4 správ, ktoré si overia znalosť hesla bez jeho priameho odoslania.
- **Slabina offline lúštenia:** Zachytený WPA2 handshake umožňuje útočníkovi offline slovníkový útok na GPU.
- **WPA3 a SAE protokol:** Moderný štandard WPA3 používa protokol SAE, ktorý offline slovníkové útoky znemožňuje.
- **Odporúčanie správcovi:** Voliť unikátne heslá (min. 16 znakov) a pri nákupe hardvéru vyžadovať podporu WPA3.

---

## Slide 2.3: Mýtus skrytého SSID (Non-discoverable Wi-Fi)

![[static/B2_s04_23_mýtus_skrytého_ssid_non-discoverable__ee7c51.png]]

- **Čo robí skrytie SSID:** AP iba prestane vysielať svoj názov v Beacon rámcoch; sieť však naďalej normálne beží.
- **Okamžité odhalenie:** Pri pripojení akéhokoľvek zariadenia sa názov prenesie vzduchom a nástroje ho ihneď zobrazia.
- **Nevýhoda pre batérie:** Zariadenia neustále vysielajú dotazy do okolia, čím vybíjajú batériu a odhaľujú históriu.
- **Reálna bezpečnosť:** Skutočnú ochranu tvorí silné šifrovanie a individuálne prihlasovanie, nie skrytie názvu.

---

## Slide 2.4: Podnikové overovanie WPA Enterprise (802.1X)

![[static/B2_s05_24_podnikové_overovanie_wpa_enterprise_8_74cc37.png]]

- **Individuálne účty:** Každý zamestnanec sa prihlasuje vlastným menom a heslom alebo osobným certifikátom.
- **Rýchle zrušenie prístupu:** Pri odchode zamestnanca stačí zablokovať jeho účet v AD/LDAP bez zmeny hesiel na staniciach.
- **3 piliere 802.1X:** Supplicant (klient), Authenticator (Wi-Fi AP/Switch) a RADIUS Server (overovacie centrum).
- **Ochrana certifikátom:** Zariadenie si overuje pravosť servera, čím bráni pripojeniu k podvrhnutej sieti útočníka.

---

## Slide 2.5: FreeRADIUS Server (Centrálne overovanie prístupu)

![[static/B1_s07_16_dhcp_snooping_ochrana_pred_falošnými__4745c4.png]]

- **Úloha RADIUS servera:** Centrálna vrátnica riadiaca prístup používateľov do bezdrôtovej aj káblovej siete.
- **Princíp AAA:** Autentifikácia (kto si?), Autorizácia (kam môžeš?) a Accounting (audit pripojenia).
- **Prepojenie s Active Directory:** Používatelia využívajú rovnaké prihlasovacie údaje ako do svojho doménového PC.
- **Dynamické priradenie VLAN:** Po prihlásení RADIUS server automaty priradí zariadenie do VLAN podľa oddelenia.

---

## Slide 2.6: Útok Evil Twin (Falošný prístupový bod)

![[static/B2_s07_26_útok_evil_twin_falošný_prístupový_bod_25da2f.png]]

- **Princíp Evil Twin:** Útočník vysiela falošnú Wi-Fi s rovnakým názvom (SSID), aký má legitímna firemná sieť.
- **Deautentifikácia klientov:** Útočník pošle deauth rámce, ktoré odpoja stanice od pravej Wi-Fi a prinútia ich prepojiť sa.
- **Zachytenie údajov:** Klient sa pripojí na silnejší signál útočníka, kde mu je podstrčená falošná prihlasovacia stránka.
- **Účinná obrana:** Zapnutie ochrany PMF (802.11w), nasadenie WPA Enterprise a validácia serverových certifikátov.

---

## Slide 2.7: Next-Generation Firewall (NGFW)

![[static/B2_s08_27_next-generation_firewall_ngfw_83afe0.png]]

- **Limity starých firewallov:** Tradičné filtre riešia len IP a porty, čo nestačí pri prevádzke cez port 80/443.
- **Rozpoznávanie aplikácií:** NGFW rozozná skutočnú aplikáciu (web vs torrent vs C2 komunikácia škodlivého kódu).
- **Dynamic Threat Feeds:** Sťahuje aktuálne zoznamy nebezpečných IP adresa podvodných domén pre blokovanie.
- **Automatická blokácia:** Opakované neúspešné pokusy o prihlásenie vedú k okamžitému zablokovaniu útočníka.

---

## Slide 2.8: Hĺbková inšpekcia paketov (Deep Packet Inspection)

![[static/B2_s09_28_hĺbková_inšpekcia_paketov_deep_packet_bd3fb0.png]]

- **Princíp DPI:** Bežný firewall číta iba obálku paketu; DPI obálku otvorí a kontroluje samotný obsah správ.
- **Odhalenie malvéru:** Zachytí pokusy o zneužitie zraniteľností a škodlivý kód maskovaný za bežný webový prevádzku.
- **Inšpekcia HTTPS:** Firewall prevádzku bezpečne dešifruje, skontroluje na vírusy a opäť zašifruje.
- **Prevencia úniku dát (DLP):** Zabraňuje odosielaniu citlivých firemných databáz a hesiel smerom do internetu.

---

## Slide 2.9: WireGuard (Moderná a bezpečná VPN)

![[static/B2_s10_29_wireguard_moderná_a_bezpečná_vpn_15540e.png]]

- **Účel VPN:** Vytvára šifrovaný tunel cez internet pre bezpečný prístup zamestnancov z domu do LAN.
- **Výhody WireGuard:** Extrémne rýchly, čistý kód, nízka záťaž procesora a vysoká bezpečnosť oproti OpenVPN.
- **Kryptografické kľúče:** Funguje na princípe páru verejného a súkromného kľúča bez zložitej CA infraštruktúry.
- **Restrikcia prístupu:** VPN používateľom povoľujeme prístup len k pracovným serverom, nie do celej LAN siete.
- **ALTERNATIVY:** TAILSCALE, CLOUDFLARE TUNNEL, NEBULA, NETBIRD

---

## Slide 2.10: Opakovanie 2. bloku: Kontrolné otázky

> [!question] Otázky na overenie vedomostí
>
> **1. Riziko spoločného hesla na Wi-Fi:**
> - Prečo je používanie jedného hesla (WPA2-Personal) pre celú firmu nebezpečné a ako tento problém rieši WPA Enterprise?
>
> **2. Pravda o skrytých sieťach:**
> - Prečo vypnutie vysielania názvu Wi-Fi siete (skryté SSID) neposkytuje reálnu ochranu pred odchytením signálu?
>
> **3. Prínos hĺbkovej inšpekcie paketov (DPI):**
> - V čom spočíva hlavná výhoda DPI kontroly oproti klasickému filtrovaniu sieťových tokov len podľa IP adries a portov?
>
> **4. Bezpečné vzdialené pripojenie cez VPN:**
> - Prečo je dôležité obmedziť prístup používateľov pripojených cez VPN a nenechávať im voľný prístup do celej vnútornej LAN?

---

## Image Sources

![[static/B2_s12_image_sources_64d897.png]]

![[static/B2_s12_image_sources_66946b.png]]

> [!note] Použité zdroje a diagramy
> - [https://wifi-settings.com/wp-content/uploads/2020/09/configure-WPA3-only-for-5-GHz-Network-on-TP-Link-router.png](https://wifi-settings.com/wp-content/uploads/2020/09/configure-WPA3-only-for-5-GHz-Network-on-TP-Link-router.png)
> - Source: wifi-settings.com
> - [https://cyberartspro.com/wp-content/uploads/2023/02/deep-packet-inspection-firewall.png](https://cyberartspro.com/wp-content/uploads/2023/02/deep-packet-inspection-firewall.png)
> - Source: www.cyberartspro.com

---

## Navigácia v kurze

⬅️ [[B_blok_1_sietova_infrastruktura_a_skenovanie.md|Blok 1: Základy bezpečnej sieťovej infraštruktúry & skenovanie siete]] | 🏠 [[README|Obsah kurzu (MOC)]] | [[B_blok_3_sledovanie_prevadzky_logy_a_wazuh.md|Blok 3: Sledovanie prevádzky (NIDS), centrálne logovanie & Wazuh]] ➡️
