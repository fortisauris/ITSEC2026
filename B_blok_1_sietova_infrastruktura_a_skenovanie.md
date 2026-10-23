---
title: "Blok 1: Základy bezpečnej sieťovej infraštruktúry & skenovanie siete"
aliases:
  - "B1: Blok 1: Základy bezpečnej sieťovej infraštruktúry & skenovanie siete"
tags:
  - itsec
  - network-security
  - trojvrstvovy-model
  - dmz
  - vlan
  - 802-1q
  - port-security
  - dhcp-snooping
  - nmap
  - openvas
  - nessus
  - modul-b
target_audience: "Správcovia sietí a systémov (Administrátori)"
track: "Modul B: Pokročilá bezpečnosť pre administrátorov"
time: "08:00 – 09:30 (90 min)"
created: 2026-10-22
license: "CC-BY-4.0"
---

# Blok 1: Základy bezpečnej sieťovej infraštruktúry & skenovanie siete

> [!info] Informácie o bloku
> - **Cieľová skupina:** Správcovia sietí a systémov (Administrátori)
> - **Časový rozsah:** 08:00 – 09:30 (90 min)
> - **Okruh:** Modul B: Pokročilá bezpečnosť pre administrátorov
> - **Zdrojový súbor:** `B_Blok 1_ Sieťová infraštruktúra a skenovanie.pptx`

🏠 [[README|Obsah kurzu (MOC)]] | [[B_blok_2_perimetricka_ochrana_wifi_a_firewally.md|Blok 2: Perimetrická ochrana, Wi-Fi & moderné firewally]] ➡️

---

## ŠKOLENIE KYBERNETICKEJ BEZPEČNOSTI PRE ADMINISTRÁTOROV

![[static/B1_s01_školenie_kybernetickej_bezpečnosti_pre_a_8c9ba0.png]]

- **BLOK 1:** Základy bezpečnej sieťovej infraštruktúry & skenovanie siete
- **Časový rozsah:** 08:00 – 09:30 | Návrh hierarchie, DMZ, VLAN, ochrana switchov, DHCP Snooping a skenovanie portov

---

## Slide 1.1: Hierarchický trojvrstvový model podnikovej siete

![[static/B1_s02_11_hierarchický_trojvrstvový_model_podni_e875ac.png]]

- **Koniec chaotického zapájania:** Sieť rozdeľujeme do troch úrovní (Core, Distribution, Access) namiesto spájania switchov do reťaze.
- **Prístupová vrstva (Access):** Koncové zariadenia sa pripájajú len do prístupových switchov, nikdy priamo do jadra siete.
- **Distribúcia a Core:** Distribučná vrstva prepája poschodia a Core vrstva zabezpečuje vysokorýchlostný prenos k serverom.
- **Odolnosť voči výpadkom:** Kľúčové switche prepájame zdvojenými linkami (LACP) pre bezvýpadkový chod pri prerušení kábla.

---

## Slide 1.2: Demilitarizovaná zóna (DMZ)

![[static/B1_s03_12_demilitarizovaná_zóna_dmz_d9092a.png]]

- **Izolovaný ostrovček:** DMZ je vyhradená sieťová zóna pre servery vystavené do internetu (web, mail, VPN brána).
- **Jednosmerná dôvera:** Servery v DMZ nesmú nikdy samy od seba iniciovať nové spojenie do vnútornej LAN siete.
- **Ochrana pred nákazou:** Pri kompromitácii webového servera zostane útočník uväznený v DMZ a nedostane sa k LAN.
- **Oddelenie databáz:** V DMZ beží iba aplikácia, citlivá databáza zostáva vnútri v LAN prístupná len cez určený port.

---

## Slide 1.3: Virtuálne lokálne siete (VLAN - IEEE 802.1Q)

![[static/B1_s04_13_virtuálne_lokálne_siete_vlan_-_ieee_8_d7de67.png]]

- **Princíp virtuálnych sietí:** Na jednom fyzickom switchi vytvárame nezávislé siete (vedenie, účtovníctvo, hostia) bez novej kabeláže.
- **Značkovanie (802.1Q Tagging):** Switch pridáva do dátového rámca značku s číslom VLAN pre doručenie len oprávneným staniciam.
- **Zastavenie broadcastov:** Izoláciou zabránime tomu, aby nakazený počítač v jednej VLAN zahltil celú firemnú sieť.
- **Smerovanie cez firewall:** Komunikácia medzi rôznymi VLAN prebieha výhradne cez firewall podľa striktných pravidiel.

---

## Slide 1.4: Bezpečná správa sieťových prvkov

![[static/B1_s05_14_bezpečná_správa_sieťových_prvkov_ad9e45.jpg]]

- **Zákaz Telnetu a HTTP:** Nešifrované protokoly posielajú heslá v otvorenom texte a musia byť na switchoch vypnuté.
- **Povinné šifrovanie (SSH & HTTPS):** Správa prvkov prebieha výhradne cez SSH v2 (s kľúčmi) alebo zabezpečený HTTPS manažment.
- **Vyhradená Management VLAN:** Správa sieťových prvkov je dostupná len zo samostatnej privátnej VLAN určenej pre IT tím.
- **Zálohovanie konfigurácií:** Konfigurácie switchov a routrov automaticky zálohujeme pre rýchlu obnovu pri poruche hardvéru.

---

## Slide 1.5: Port Security na switchoch (Ochrana fyzických portov)

![[static/B1_s06_15_port_security_na_switchoch_ochrana_fy_5faf80.jpg]]

- **Ochrana zásuviek:** Bráni pripojeniu cudzích notebookov a neautorizovaných zariadení do kancelárskych zásuviek.
- **Viazanie na MAC adresu:** Switch si na konkrétnom porte zapamätá MAC adresu firemného PC a iné adresy odmietne.
- **Režim Shutdown (err-disable):** Pri zistení neznámej MAC adresy switch port okamžite vypne a pošle alert administrátorovi.
- **Prvá línia obrany:** Kedže MAC adresu možno naklonovať, Port Security slúži ako prvý filter dopĺňaný cez 802.1X.

---

## Slide 1.6: DHCP Snooping (Ochrana pred falošnými DHCP)

![[static/B1_s07_16_dhcp_snooping_ochrana_pred_falošnými__4745c4.png]]

- **Hrozba cudzieho DHCP:** Zapojený domáci Wi-Fi router v kancelárii začne rozdávať zlé IP adresy a vyradí sieť z prevádzky.
- **Riziko odpočúvania:** Útočník môže cez falošný DHCP server presmerovať internetovú prevádzku staníc cez svoj počítač.
- **Dôveryhodné porty (Trusted/Untrusted):** Switch povoľuje odpovede DHCP servera len z označených dôveryhodných portov.
- **Okamžitá blokácia:** Ak na klientskom porte odpovie nepovolený DHCP server, switch paket zahodí a port zablokuje.

---

## Slide 1.7: Princíp sieťového skenovania portov

![[static/B1_s08_17_princíp_sieťového_skenovania_portov_315bbf.jpg]]

- **Čo je sieťový port:** Číslovaný komunikačný kanál (0–65535) pre konkrétnu službu (HTTP:80, HTTPS:443, SSH:22, RDP:3389).
- **Účel skenovania:** Zistiť, ktoré porty sú otvorené, pripravené komunikovať a či na nich nebežia nebezpečné služby.
- **TCP Handshake (SYN / SYN-ACK):** Skener pošle požiadavku SYN; ak cieľ odpovie SYN-ACK, port je otvorený a služba beží.
- **Auditing pre správcu:** Pravidelné skenovanie odhalí zabudnuté služby skôr, než ich objavia útočníci na internete.

---

## Slide 1.8: Sieťový skener Nmap

![[static/B1_s09_18_sieťový_skener_nmap_7432a4.jpg]]

- **Nástroj Nmap:** Najpopulárnejší open-source skener na mapovanie aktívnych zariadení a otvorených portov v sieti.
- **Detekcia verzií (-sV):** Nmap zistí presný typ a verziu bežiacej služby (napr. Apache 2.4.41 namiesto len "port 80").
- **Rozpoznanie OS (-O):** Podľa reakcií v sieťovom stohu určí operačný systém (Windows, Linux, tlačiareň).
- **Nmap NSE Skripty:** Obsahuje knižnicu skriptov na overenie slabých hesiel a známych zraniteľností.

---

## Slide 1.9: Skener zraniteľností OpenVAS (Greenbone) alebo Nessus

![[static/B1_s10_19_skener_zraniteľností_openvas_greenbon_16ad44.png]]

- **Rozdiel Nmap vs OpenVAS:** Nmap zisťuje otvorené dvere; OpenVAS kontroluje, či sú poškodené a zneužiteľné.
- **Databáza CVE zraniteľností:** Kompletný skener, ktorý porovnáva systémy s celosvetovou databázou známych chyby.
- **Hodnotenie CVSS skóre:** Vygeneruje prehľadný report so zaradením rizík od nízkych až po kritické.
- **Návod na opravu:** Pre každú nájdenú chybu poskytne presné odporúčanie na patching alebo zmenu nastavení.

---

## Slide 1.10: Opakovanie 1. bloku: Kontrolné otázky

> [!question] Otázky na overenie vedomostí
>
> **1. Zmysel DMZ zóny:**
> - Prečo webové servery vystavené do internetu nesmú byť v rovnakej sieti ako kancelárske PC a prečo z DMZ nesmie ísť spojenie do LAN?
>
> **2. Výhoda VLAN sietí:**
> - Ako rozdelenie switcha na virtuálne siete (VLAN) zabráni tomu, aby útočník z napadnutej Wi-Fi pre hostí videl interné účtovníctvo?
>
> **3. Ochrana portov pred neznámymi zariadeniami:**
> - Ako kombinácia funkcií Port Security a DHCP Snooping ochráni sieť pred cudzími notebookmi a nesprávne zapojenými routrami?
>
> **4. Rozdiel medzi Nmapom a OpenVAS:**
> - V akej situácii použije správca rýchly sken portov cez Nmap a kedy naopak spustí hĺbkový skener zraniteľností cez OpenVAS?

---

## Image Sources

![[static/B1_s12_image_sources_862915.png]]

![[static/B1_s12_image_sources_ea362a.png]]

![[static/B1_s12_image_sources_953014.png]]

> [!note] Použité zdroje a diagramy
> - [https://creately.com/static/assets/guides/hierarchical-network-topology/campus-network-example-2B2gUiotuFa.svg](https://creately.com/static/assets/guides/hierarchical-network-topology/campus-network-example-2B2gUiotuFa.svg)
> - Source: creately.com
> - [https://media.geeksforgeeks.org/wp-content/uploads/20220808192523/DemiltarizedZoneDMZ.png](https://media.geeksforgeeks.org/wp-content/uploads/20220808192523/DemiltarizedZoneDMZ.png)
> - Source: www.geeksforgeeks.org
> - [https://images.ctfassets.net/aoyx73g9h2pg/3Bv0UJzi0ZOIpeIDn4SvEM/7f63324da001b246a7e263860cb9d89a/What-is-802-1Q-Port-Tagging-Diagram.jpg](https://images.ctfassets.net/aoyx73g9h2pg/3Bv0UJzi0ZOIpeIDn4SvEM/7f63324da001b246a7e263860cb9d89a/What-is-802-1Q-Port-Tagging-Diagram.jpg)
> - Source: www.cbtnuggets.com

---

## Navigácia v kurze

🏠 [[README|Obsah kurzu (MOC)]] | [[B_blok_2_perimetricka_ochrana_wifi_a_firewally.md|Blok 2: Perimetrická ochrana, Wi-Fi & moderné firewally]] ➡️
