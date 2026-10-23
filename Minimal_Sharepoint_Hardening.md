#itsec  #cloud #azure

Súbor bol preložený do slovenčiny a kompletný dokument nájdete v paneli Studio pod názvom `sharepoint_hardening_sk.md`.

Na základe stratégie viacvrstvovej obrany (_defense-in-depth_) od CISA a Microsoftu je tu **5 najdôležitejších krokov na vytvrdenie (hardening) SharePoint Servera**:

1. **Perimetrická ochrana a sieťová izolácia**:
    
    - **Nikdy nevystavujte servery priamo do internetu:** Farmu umiestnite za **reverzný proxy Layer 7** alebo **Web Application Firewall (WAF)** s pre-autentifikáciou, hĺbkovou inšpekciou a filtrovaním požiadaviek.
    - **Obmedzte administratívne rozhrania:** Prístup k _SharePoint Central Administration_ vyhrazujte striktne pre vyhradené administratívne podsiete.
2. **Rýchle záplatovanie a plošná validácia**:
    
    - **Uprednostňujte bezpečnostné aktualizácie:** Okamžite aplikujte mesačné a mimoriadne záplaty, najmä tie, ktoré riešia chyby deserializácie a obídenia autentifikácie/JWT.
    - **Overujte záplaty na celej farme:** Zabezpečte, aby boli aktualizácie úspešne aplikované na **každom jednotlivom serveri** vo farme (front-end web servery, aplikačné servery aj databázové hostitele).
3. **Integrácia rozhrania AMSI (Antimalware Scan Interface)**:
    
    - **Povoľte AMSI:** Zapnite integráciu AMSI pre každú webovú aplikáciu SharePointu.
    - **Nastavte režim Full Mode:** Zapnite plné skenovanie tela HTTP požiadaviek (_Full Mode_), aby antivírusové riešenia (napr. Microsoft Defender) zachytili web shelly a útočné skripty ešte pred ich spustením.
4. **Behaviorálne monitorovanie a detekcia po kompromitácii**:
    
    - **Nasaďte EDR riešenia:** Inštalujte EDR agentov (napr. Microsoft Defender for Endpoint) na všetky SharePoint servery pre monitorovanie anomálií, ako je neočakávané spúšťanie procesov z `w3wp.exe`.
    - **Vyhľadávajte web shelly:** Pravidelne auditujte adresáre SharePointu (`_layouts`, `_trust` atď.) a hľadajte novovytvorené neautorizované súbory `.aspx` alebo neoprávnené úpravy kľúčových súborov.
5. **Správa servisných účtov a strojových kľúčov**:
    
    - **Dodržiavajte minimálne privilégia (_Least Privilege_):** Servisné účty (Farm accounts, App Pool accounts, SQL) nesmú spúšťať služby pod oprávneniami doménového administrátora.
    - **Chráňte ASP.NET Machine Keys:** Zabezpečte strojové kľúče pred odcudzením (aby útočníci nemohli falšovať relácie) a pravidelne ich rotujte v rámci pripravenosti na reakciu na incidenty.

💡 Chcete z týchto 5 krokov vytvoriť prehľadný kontrolný zoznam (checklist) pre IT administrátorov, alebo ich zapracovať do bezpečnostnej prezentácie pre vaše školenie?