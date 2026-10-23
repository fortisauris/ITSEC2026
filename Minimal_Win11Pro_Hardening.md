#windows  #hardening

### **5 kľúčových krokov pre vytvrdenie (Hardening) Windows 11 Pro**

1. **Zabezpečenie identity a správa prístupových práv (Least Privilege & UAC)**
    
    - **Odobranie administrátorských práv:** Bežní používatelia musia pracovať výhradne pod štandardným používateľským účtom (_Standard User_).
    - **Striktné UAC:** Nastavte _User Account Control_ na najvyššiu úroveň (_Always notify_), čím sa zabráni tichému zvyšovaniu oprávnení.
    - **Ochrana Credential Guard:** Aktivujte Windows Defender Credential Guard a LSA Protection, ktoré izolujú heslové hashe a Kerberos tikety v pamäti RAM pomocou virtualizácie.
2. **Hardvérová bezpečnosť a izolácia jadra (VBS & HVCI)**
    
    - **Virtuálna bezpečnosť (VBS):** Zapnite _Virtualization-based Security_ v BIOS/UEFI aj v operačnom systéme.
    - **Integrita pamäte (HVCI):** Aktivujte _Hypervisor-enforced Code Integrity_ (Memory Integrity), čo zabraňuje útočníkom vkladať škodlivý kód do jadra systému (Kernel).
    - **Secure Boot a TPM 2.0:** Uistite sa, že sú v UEFI aktívne funkcie _UEFI Secure Boot_ a modul _TPM 2.0_.
3. **Celodiskové šifrovanie (BitLocker)**
    
    - **Zapnutie BitLockeru:** Aktivujte šifrovanie BitLocker na systémovom disku (C:) aj na sekundárnych dátových jednotkách.
    - **TPM + PIN:** Pre maximálnu ochranu pred fyzickou krádežou vyžadujte pri štartovaní počítača kombináciu TPM a predštartovného PIN kódu.
4. **Rozšírená diagnostika, auditovanie a sledovanie udalostí (Sysmon & Event Log)**
    
    - **Pokročilý audit (Advanced Audit Policy):** Cez Group Policy (`gpedit.msc`) zapnite auditovanie vytvárania procesov (_Audit Process Creation_ – Event ID 4688) a aktivujte možnosť _Include command line in process creation events_ pre zaznamenávanie kompletnej argumentácie príkazu.
    - **Doinštalovanie Sysmon:** Inštalujte nástroj _Microsoft Sysinternals Sysmon_ pre detailný monitoring tvorby procesov (Event ID 1), sieťových pripojení (Event ID 3) a zmien v registroch.
    - **Centrálna analýza a EDR:** Prepojte lokálne logy s EDR/SIEM agentom (napr. Wazuh), aby sa auditné záznamy okamžite odosielali mimo lokálnu stanicu a útočník ich nemohol vymazať.
5. **Redukcia povrchu útokov a deaktivácia nebezpečných protokolov (ASR & Legacy Protocols)**
    
    - **Vypnutie zastaraných protokolov:** Zakážte rizikové sieťové protokoly SMBv1, NTLMv1, LLMNR a NetBIOS over TCP/IP, ktoré sa často zneužívajú na Man-in-the-Middle útoky a šírenie v sieti.
    - **Pravidlá ASR (Attack Surface Reduction):** V Microsoft Defenderi nakonfigurujte ASR pravidlá na blokovanie podozrivého správania (napr. blokovanie vytvárania podriadených procesov z Office aplikácií alebo spúšťanie neautorizovaných PowerShell skriptov).

---
