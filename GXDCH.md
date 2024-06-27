# 2. Sprint - Neuster Stand GXDCH

*Clearing house → it “clears” who can participate*

---

<aside>
💡 **Tl;DR der Gaia-X Digital Clearing House (GXDCH)**

Die Gaia-X Digital Clearing Houses (GXDCH) dienen als zentrale Anlaufstellen in der Gaia-X-Infrastruktur. Sie überprüfen die Einhaltung der Mindestanforderungen für die Teilnahme an Gaia-X und stellen sicher, dass die unterschiedlichen Gaia-X-Datenräume miteinander kompatibel sind. Ihre Hauptaufgabe ist die Zertifizierung der Gaia-X-Konformität, basierend auf den Vorgaben des Gaia-X Trust Frameworks.

**Kernkomponenten der GXDCHs:**

- **Gaia-X Compliance:** Überprüft die Aussagen der Teilnehmenden und stellt Gaia-X Verifiable Credentials (VC) aus.
- **Gaia-X Registry:** Verwaltet eine Liste der vertrauenswürdigen Ausstellungsstellen (Trust Anchors) und definiert, wie Credentials aussehen müssen.
- **Notarisierungsservice:** Überprüft Firmennummern und stellt entsprechende Verifiable Credentials (VC) aus.

**Optionale Komponenten:**

- UIs für das Erstellen und Speichern von VCs, sowie Kataloge, die Gaia-X-konforme Dienste listen.

**Konformitätsprüfung:**
Die Konformität wird durch eine Compliance Engine gewährleistet, die die Einhaltung von Vorgaben überprüft und bei positiver Bewertung ein Gaia-X Credential nach den 4 Konformitäts-Leveln (konform, 1-3) ausstellt. Wichtig ist, dass die Aussage selbst nicht überprüft wird, sondern nur z.B. syntaktische Korrektheit. Die Aussage selbst ist bereits von einem Trust Anchor überprüft worden ist. 

**Zukunft der GXDCHs:**
Die kommende Software-Version LOIRE v2 wird neue verpflichtende Komponenten einführen. Diese konzentrieren sich auf Police Enforcement beim Anbieten und Nutzen von Diensten. Nutzenden können so z.B. im Katalog nach Diensten filtern, die in Deutschland angeboten werden.
**Operable GXDCHS**

Es gibt 3 operable GXDCHs (T-System, Arbua, Aire Networks), die die Basisfunktionen kostenlos und weiter Services kostenpflichtig zur Verfügung stellen.

</aside>

## Begriffsklärungen

- Verifiable Credential
    
    Verifiable Credentials (VCs) sind digitale Nachweise, die auf Standards der World Wide Web Consortium (W3C) basieren. Sie bieten eine sichere Methode, um Identitätsmerkmale oder Qualifikationen einer Person, Organisation zu verifizieren. VCs verwenden kryptografische Mechanismen, um die Echtheit und Manipulationsfreiheit (digitale Signatur) der in ihnen enthaltenen Angaben zu gewährleisten.
    
    **Beispiel**: 
    
    VCs sind wie digitale Pässe. Genau wie ein Reisepass Ihre Identität und Nationalität bestätigt, bestätigen VCs online Ihre Daten oder Berechtigungen. Sie nutzen kryptographische Verfahren, um sicherzustellen, dass die Informationen echt und unverändert sind, ähnlich den Sicherheitsmerkmalen in einem physischen Pass.
    
- Trust Anchors - **WER** kann **WAS** bescheinigen
    
    TAs sind 3rd Parties die im Ökosystem als Nachweis akzeptiert werden. Diese werden immer nur für einen bestimmten Anwendungsbereich akzeptiert und in der Registry gespeichert. Z.b. kann ein eIDAS Provider als Nachweis für die Identität einer natürlichen Person als Nachweis definiert werden. 
    
    Akzeptiert werden: 
    
    - Trust Service Providers (TSP), die von Staaten validiert oder Ausgeber von EV SSL Zertifikaten sind
    - eIDAS Ausgeber von  Qualified Certificate for Electronic Signatures ([Website](https://esignature.ec.europa.eu/efda/tl-browser/#/screen/home), [Selben Infos wie Website aber Machine-redable](https://ec.europa.eu/tools/lotl/eu-lotl.xml))
    
    Mehr Infos [hier](https://docs.gaia-x.eu/policy-rules-committee/policy-rules-conformity-document/23.10/Gaia-X_Trust_Anchors/) und [hier](https://gaia-x.gitlab.io/policy-rules-committee/trust-framework/trust_anchors/)
    

## Gaia-X Digital Clearing House (GXDCH)

Die Clearing Houses (GXDCH) sind der Einstiegspunkt in der Gaia-X Welt. Sie stellen sicher, dass die minimalen Anforderung zur Partizipation in der Gaia-X Welt von allen Akteuren eingehalten werden und dass verschieden Gaia-X Ökosystem kompatibel zueinander sind. I**hre Hauptaufgabe ist die Ausstellung von Gaia-X Konformität.**  

Sie übersetzen somit die Anforderung, die im [Trust Framework](https://docs.gaia-x.eu/policy-rules-committee/trust-framework/22.10/), niedergeschrieben sind in die Praxis. 

<aside>
💡 ⇒ GXDCH ermöglichen Akteuren Gaia-X zu nutzen.

</aside>

## Komponenten der GXDCHs

GXDCHs müssen verschieden Aufgaben kostenlos zur Verfügung stellen um als GXDCH akkreditiert zu werden. Zusätzlich können diese weiter Funktionen bereitstellen, die den Zugang und Nutzung von Gaia-X vereinfachen. Die verpflichtenden Komponenten werden von der AISBL definiert und kontrolliert. Die optionalen Services können vom Betreiber selbst definiert und verkauft werden. 

Die aktuellste gültige technische Definitionen, wie diese Komponenten implementiert werden müssen, ist **TAGUS V1.1** (implementiert Version 22.10 des Trust Frameworks). Versionen sind immer für 2 weiter Version gültig und sind dann veraltet (*deprecated).* Somit ist TAGUS bis zur Version DANUBE gültig. Eine Beispiel Implementation findet sich auf [Git](https://gitlab.com/gaia-x/lab/compliance/gx-compliance). 

### Verpflichtende Komponenten

**Gaia-X Compliance**

- Überprüft die Verifiable Presentation von einem Teilnehmenden auf Konsistenz (z.B. von einer gültigen Stelle ausgegeben) und stellt bei positiver Prüfung ein Verifiable Credential (VC) aka *Gaia-X Credential* aus. Den Wahrheitsgehalt wird nicht geprüft, sondern ist bereits von einem Trust Anchor wie [Conformance Assessment Body](https://eidas.ec.europa.eu/efda/tl-browser/#/screen/home) (CAB) geprüft.

**Gaia-X Registry**

- Diese enthält die Liste der Trust Anchors (inkl. kryptographischen Schlüssel, Widerruf etc.) und wie die VCs “*geschrieben”* sein müssen (Ontologie).

**Gaia-X Notarization service for the registration number**

- Überprüft ob eine gegebene Firmen-Nummer (z.B. Handelsregisternummer) valide ist und stellt ein entsprechendes VC aus.

### Optionale Komponenten

Die hier aufgeführten Komponenten sind explizit von der AISBL definiert. Es wird also nahegelegt, diese zu implementieren. Dies ergibt zusätzlich Sinn, da teilweise als optional gekennzeichnete Komponenten in folgenden Version verpflichtend werden. Über diese Komponenten hinaus können Anbieter von GXDCHs weiter Services anbieten, die den Zugang und den Komfort zur Nutzung von Gaia-X erhöhen wie z.B. VCs oder Catalogue as a Service bei Aruba.  

**Wizard & Wallet**

- Eine graphische Oberfläche (UI) um eine VC zu erhalten und (lokal) zu speichern.

**Katalog**

- Ein Katalog in dem Nutzende relevante Gaia-X konforme Services finden können und Anbieter ihre Services potentiellen Nutzenden bekannt zu machen.

Erklärende Details und weiter optionale Komponenten, finden sich [hier](https://docs.gaia-x.eu/technical-committee/architecture-document/latest/annex/).

Ausführliche technische Details finden sich [hier](https://gitlab.com/gaia-x/lab/gxdch/-/tree/main/architecture?ref_type=heads). 

<aside>
💡 **Kostenlos** werden in der aktuellen Version das Ausstellen von Gaia-X Credentials (Compliance), eine Auflistung von TAs, die Ontologie von VCs (Registry) und das validieren von Firmen-Nummer angeboten.
**Optional** (eventuell kostenpflichtig) wird u.a. ein UI zur Ausstellung und Speicherung von VCs und ein Katalog mit Gaia-X konformen Angeboten bereitgestellt.

</aside>

### Gaia-X Konformität

**Wie und wo ist Gaia-X Konformität definiert?**

Zunächst gibt es *high-level objectives* der Gaia-X Initiative, die durch die AISBL in den **Policy Rules** ([Conformity](https://docs.gaia-x.eu/policy-rules-committee/policy-rules-conformity-document/23.10/Executive_Summary/), [Rules and Labelling](https://docs.gaia-x.eu/policy-rules-committee/policy-rules-labelling/22.11/policy_rules_labeling_document/)) definiert werden. Daraus leiten sich im [Trust Framework](https://docs.gaia-x.eu/policy-rules-committee/trust-framework/latest/) die *low-level requirements* ab, die diesen abstrakte Ziele und Werte wie Transparenz und Datenschutz in praktisch umsetzbare Anforderung übersetzt und definiert **WAS und WIE** es nachgewiesen werden kann. Diese Anforderung werden von GXDCHs *Compliance Engine* in Software umgesetzt und somit für Teilnehmende tatsächlich nutzbar. Somit garantiert diese Engine, dass die Anforderung an eine Gaia-X Konformität erfüllt worden sind und bescheinigt dieses mit einem VC. 

- Übersicht über die verschieden Dokumente und ihrem Scope
    
    ![[https://docs.gaia-x.eu/framework/?tab=specifications](https://docs.gaia-x.eu/framework/?tab=specifications)](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/Untitled.png)
    
    [https://docs.gaia-x.eu/framework/?tab=specifications](https://docs.gaia-x.eu/framework/?tab=specifications)
    

**Wie läuft die Prüfung der Konformität in GXDCHs ab?**

Vorbedingung: Ein Ökosystem (Dataspace) hat beschlossen Gaia-X konform zu werden, da es das Vertrauen in einen fairen, sicher und interoperablen Datenaustausch ermöglicht.  

1. Ein Akteur (z.B. eine natürliche Person) möchte diesem Ökosystem beitreten und braucht somit ein VC um Gaia-X konform z.B. seine Identität zu belegen. 
    1. Aussage = Ich bin Person xyz. (Declaration)
2. Der Akteur erhält über eine Trust Anchor (TA) einen Nachweis über die zu belegende Aussage.
    1. Mittels z.B. einem eIDAS Zertifikat wird Aussage nachgewiesen (z.B. eID)
3. Die Aussage, Nachweis und weiter Parameter werden an ein GXDCH geschickt (API oder Wizard) 
4. Das GXDCH validiert und verifiziert den Nachweis des TA aber nicht den Wahrheitsgehalt der Aussaag selber selber, da diese bereits von der TA bestätigt worden ist. Folgendes wird überprüft: 
    1. Ist es syntaktisch korrekt?
    2. Ist das Schema valide und die VP konsistent?
    3. Ist die kryptographische Kette valide (public key etc. überprüfen)?
    4. Ist die Ausstellende 3rd Party akzeptiert? 
    - Schema für VC Prüfung
        
        ![Untitled](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/Untitled%201.png)
        
5. Nach einer positiven Prüfung wird ein Gaia-X VC ausgestellt. 

Details des Ablaufes [hier](https://docs.gaia-x.eu/policy-rules-committee/policy-rules-conformity-document/23.10/Process/). 

- Diagram
    
    ![Untitled](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/Untitled%202.png)
    

<aside>
💡 GXDCHs stellen **Gaia-X Konformitäts-Zertifikat** aus. Dazu wird eine Aussage eines Teilnehmenden durch eine extern Trust Anchor bestätigt. Anschließend schickt dieser das  Zertifikat mit weiteren Infos an ein GXDCH. Diese prüft alle Infos (u.a. ist TP berechtigt dies zu bescheinigen, syntaktisch korrekt, Kryptographie korrekt) und stellt bei positiver Prüfung ein Gaia-X VC in den vers. Levels aus.

</aside>

**Konformitäts-Levels** 

Die drei Level existieren, um unterschiedliche Sicherheits-, Datenschutz- und Transparenzanforderungen für verschiedene Einsatzszenarien und Bedürfnisse von Konsumenten in verschiedenen Ländern und Branchen zu berücksichtigen. Sie ermöglichen eine flexible Anpassung an die spezifischen Anforderungen und Ziele der Nutzer, indem sie von grundlegenden bis zu höchsten Standards reichen.

- Gaia-X Conformity: Basisanforderung im Hinblick auf Transparenz, Sicherheit, Interoperabilität, Portabilität und Nachhaltigkeit sind gegeben
- Label Level 1: Erfüllt zusätzlich zur Konformität Anforderungen zum Datenschutz und Sicherheit, gemäß den minimalen Anforderung im Trust Framework, mit Cybersecurity auf dem Basisniveau des ENISA-Europäischen Cybersicherheitsschemas.
- Label Level 2: Erweitert die Anforderungen von Level 1 um höhere Sicherheits- und Transparenzstandards sowie die obligatorische Bereitstellung eines Dienststandorts in Europa. Cybersecurity muss das substanzielle Niveau des ENISA-Europäischen Cybersicherheitsschemas erfüllen.
- Label Level 3: Setzt die höchsten Standards für Datenschutz, Sicherheit, Transparenz, Portabilität und Flexibilität sowie europäische Kontrolle um. Ein Dienststandort in Europa ist obligatorisch, Daten müssen ausschließlich in Europa verarbeitet und geteilt werden können und Cybersecurity muss das hohe Niveau des ENISA-Europäischen Cybersicherheitsschemas erreichen.
- Schaubilder
    
    ![Präsentation CTO Gaia-X Label, S. 2](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/Untitled%203.png)
    
    Präsentation CTO Gaia-X Label, S. 2
    
    ![Präsentation CTO Gaia-X Label, S. 6](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/Untitled%204.png)
    
    Präsentation CTO Gaia-X Label, S. 6
    

Ausführliche Infos [hier](https://docs.gaia-x.eu/policy-rules-committee/policy-rules-conformity-document/23.10/criterions/) und [hier](https://docs.gaia-x.eu/policy-rules-committee/policy-rules-labelling/22.11/) und in kurz im [PDF](https://gaia-x.eu/wp-content/uploads/files/2021-11/Gaia-X%20Labelling%20Framework_0.pdf).

<aside>
💡 Es gibt 3 Gaia-X Konformitäts-Level, die verschiedene Sicherheits- Datenschutz- und Transparenzanforderungen fordern.

</aside>

## Wie werde ich GXDCH, welche gibt es aktuell und wie nutze ich diese?

Die AISBL erstellt und verwaltet die Richtlinien (Architektur, Policy Rules Conformity Dokumente und Trust Framework), die GXDCHs technisch umsetzen müssen. 

Jeder Service Provider kann GXDCH werden, der diese Gaia-X Richtlinien einhält, die obligatorischen Dienste wie Gaia-X Konformität für jeden frei zur Verfügung bereitstellen und von der AISBL akkreditiert worden sind. Die Funktionsfähigkeit der verpflichtenden Komponenten wird durch das [*Gaia-X Testbed](https://gitlab.com/gaia-x/lab/gxdch/-/tree/main/gxdch_test?ref_type=heads)* sichergestellt. Die AISBL betreibt selber keine GXDCHs.

Als Geschäftsmodell werden die Anbieter wahrscheinlich eine Art [*Freemium Model](https://en.wikipedia.org/wiki/Freemium)* anbieten. Die verpflichteten Komponenten werden gratis zur Verfügung gestellt und weiter Services wie ein graphische Oberfläche zur Erstellung von Zertifikaten oder die Speicherung von Zertifikaten (Wizard, Wallet) und weiterer Support werden kostenpflichtig angeboten. (s. auch Angebot von [Aruba](https://www.aruba.it/gxdch.aspx))

[Hier](https://gitlab.com/gaia-x/lab/gxdch/-/tree/main) finden sich technische Infos zum Aufbau eines GXDCH. 

### GXDCH nutzen

Jedes GXDCH bietet APIs für die obligatorischen Dienste an. Diese kann man auf einer [Übersichtsseite](http://docs.gaia-x.eu/framework/?tab=clearing-house) der AISBL finden. Außerdem betreibt die AISBL einen *Loadbalancer,* der Anfragen an die GXDCHs gleichmäßig zwischen diesen aufteilt. Das aktuelle (technische) Skript zur Aufteilung findet sich [hier](https://gitlab.com/gaia-x/lab/gxdch/-/blob/main/loadbalancer/haproxy.cfg). Falls Aktuere nur die kostenlose Dienste nutzen möchten, ist dierser Loadbalancer optimal, da nur eine gleichbleibende URl genutzt werden muss und bei sich nicht auf ein GXDCH Instanz verlassen werden. Somit liefert dies eine gewisse Redunanz. Es ist möglich in der erhaltenden Antwort des *Loadbalancers* zu überprüfen, welches konkrete GXDCH verantwortlich für die Erfüllung der Antwort war *(Proof Section).* Weiter Infos [hier](https://gitlab.com/gaia-x/lab/gxdch/-/tree/main#using-the-gxdch). 

- Loadbalancer URLs
    - [https://registrationnumber.notary.gaia-x.eu/v1/docs/](https://registrationnumber.notary.gaia-x.eu/v1/docs/)
    - [https://compliance.gaia-x.eu/v1/docs/](https://compliance.gaia-x.eu/v1/docs/)
    - [https://registry.gaia-x.eu/v1/docs/](https://registry.gaia-x.eu/v1/docs/)

### Welche GXDCHs gibt es?

**Stand April 2024**

Operabel sind T-Systems, Aruba (Italien) und Aire Networks (Spanischer Telekomunikations-Provider). 

**Stand Gaia-X Summit November 23, Alicante.** 

![[https://gaia-x.eu/summit-2023/wp-content/uploads/2023/11/1.3-Creating-value-through-GXDCH-Gaia-X-Digital-Clearing-House.pdf](https://gaia-x.eu/summit-2023/wp-content/uploads/2023/11/1.3-Creating-value-through-GXDCH-Gaia-X-Digital-Clearing-House.pdf) (p.19)](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/Untitled%205.png)

[https://gaia-x.eu/summit-2023/wp-content/uploads/2023/11/1.3-Creating-value-through-GXDCH-Gaia-X-Digital-Clearing-House.pdf](https://gaia-x.eu/summit-2023/wp-content/uploads/2023/11/1.3-Creating-value-through-GXDCH-Gaia-X-Digital-Clearing-House.pdf) (p.19)

**Beispiel T-System** 

- Bei T-Systems werden eine kostenfreie Community-Version und eine kostenpflichtige Enterprise-Version (mit Support und zusätzlichen Services) angeboten
- Enthaltene Komponenten
    - SD-Wizard von T-Systems (vergleiche mit dem Gaia-X Wizard: [https://wizard.lab.gaia-x.eu/](https://wizard.lab.gaia-x.eu/)
    - Registrierung über den Data Intelligence Hub, über API können die verschiedenen Dienste abgerufen werden, bspw. Credential Management & SD-Wizard
    - Erstellung einer digitalen Signatur nach Überprüfung der legal entity über staatliche Register durch den internen Partner Telekom Security

 **Quelle: C. Weiss - T-System Workshop Michael**

<aside>
💡 Es gibt 3 akkreditierte und funktionsfähige GXDCHs (T-System, Arbua, Aire Networks), die die Basisfunktionen kostenlos und weiter Services kostenpflichtig zur Verfügung stellen. Weiter Kandidaten werden in 2024 folgen (z.B. Orange, TIM).

</aside>

## Zukunft der GXDCHs

Die nächste Software Version für GXDCHs **LOIRE v2 23.xx** soll im 3. Quartal 2024 von allen GXDCHs genutzt werden (General Availability - GA). 

**Roadmap**

![[https://gaia-x.eu/wp-content/uploads/2024/01/Gaia-X-Brochure_2024_Online_Spread.pdf](https://gaia-x.eu/wp-content/uploads/2024/01/Gaia-X-Brochure_2024_Online_Spread.pdf)](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/Untitled%206.png)

[https://gaia-x.eu/wp-content/uploads/2024/01/Gaia-X-Brochure_2024_Online_Spread.pdf](https://gaia-x.eu/wp-content/uploads/2024/01/Gaia-X-Brochure_2024_Online_Spread.pdf)

<aside>
⚠️ Welche Komponenten final in TAGUS einziehen ist nicht klar und kann sich in der Entwicklung noch ändern. Die hier aufgelisteten Komponenten beruhen auf Informationen aus der Präsentation vom CTO der AISBL. Die Präsentation findet sich unten.
Die Komponenten-Beschreibung stammen aber aus weiteren Quellen und sind belastbar.

</aside>

### **Neue Komponenten**

**Credential Event Service ***

Ein verteilter Speicher von Gaia-X konformen VCs. Somit sind bei jedem GXDCH alle VCs und Gaia-X konforme Dienste abrufbar und überprüfbar.  

**Trust Indexes ***

Trust Indexes in Gaia-X dienen als Gradmesser, um das Vertrauen in Services zu bewerten. Diese Indizes bieten eine quantifizierte Bewertung der Zuverlässigkeit und Transparenz von Services, die in den Katalogen von Gaia-X aufgeführt sind, und unterstützen so die Auswahlentscheidung der Nutzer. Ausführliche Infos [hier](https://gaia-x.eu/news-press/gaia-x-and-trust-indexes/). 

**Registry Service erweitert um Policy Reasoning Engine**

In Gaia-X sollen Verträge zur Nutzung von Diensten digital und rechtssicher geschlossen werden können. Diese können Regeln zur Nutzung, wie das Kunden oder Anbieter nur in speziellen Ländern ihren Sitz haben müssen, enthalten (eng. Policies). Technisch werden diese Regeln in der [Open Digital Rights Language](https://www.w3.org/TR/odrl-model/) verfasst. 
Nutzende könnten dann in der Registry nach passenden Service Angeboten filtern und Anbietende könnten sicherstellen, dass ihre Dienste nur von ihnen gewollten Nutzenden genutzt werden. Z.B. lässt sich somit verhindern, dass Dienste oder Daten von Wettbewerbern genutzt werden können. 

Mehr Infos [hier](https://gaia-x.eu/news-press/gaia-x-and-the-policy-reasoning-engine/) und in der Präsentation vom CTO ab Seite 32. 

** bereits optional in der aktuellen Version verfügbar* 

**Optional Data Exchange Services** 

Der Data Exchange Service von Gaia-X bietet ein Set an Dienstleistungen, die den Austausch von Daten zwischen verschiedenen Teilnehmern, wie Datenproduzenten, -konsumenten und -anbietern, ermöglichen. Diese Dienstleistungen umfassen Funktionen wie Zugangskontrolle durch Richtlinienverhandlung, Nachverfolgbarkeit des Datenaustauschs, Dienstprotokollverhandlung und Datennutzungskontrolle. Ziel ist es, einen sicheren und vertrauenswürdigen Rahmen für den Austausch von Daten zu schaffen, der den Wert der Daten maximiert und gleichzeitig Compliance und Vertrauen gewährleistet. [Link](https://docs.gaia-x.eu/technical-committee/data-exchange/23.11/dewg/) zu weiteren Infos. 

Neben dieser erweiterten Liste an verpflichteten und optionalen Liste an Services wird sich auch die darunterliegenden technische Standards ändern. Dies betrifft auch schon jetzt verpflichtende Komponenten wie die Compliance Engine. 

- **Vergleich TAGUS vs. LORIE**
    
    
    | TAGUS v1 (22.10) | LOIRE v2 (23.xx) |
    | --- | --- |
    | Verpflichtende Komponenten
    - Compliance & Notary Service
    - Registry Service
     | Verpflichtende Komponenten
    - Compliance & Notary Service
    - Registry Service
    - Credential Event Service
    - Trust Indexes |
    | Optionale Komponenten
    - Wallet & Wizard | Optionale Komponenten
    - Wallet & Wizard
    - Policy Decision & Enforcement Point
    - Data Exchange Service |
    | Basiert auf Trust Framework 22.10 (low level requirements) &
     Policy Rules 23.10 (high level criteria) | Basiert auf Trust Framework 23.xx & 
    Policy Rules 24.04 |
    | GXDCHs replizieren die verpflichtenden Komponenten vom offiziellen Gaia-X Github Repository. 
    ⇒ Manuelle Updates der Providers → event. vers. Versionen  | GXDCHs replizieren die verpflichtenden Komponenten vom offiziellen Gaia-X Github Repository und synchronisieren sich über das Internet 
    ⇒  Automatische Updates → keine Versionsunterschiede |
    | Gaia-X Compliance nach Level 1 und Selbstauskunft | Gaia-X Compliance nach Level 1 und validiert durch GXDCHs
    - in weiteren Releases auch Compliance nach Level 2, 3 |
    | Stabile TAGUS Version verfügbar unter:
    https://compliance.lab.gaia-x.eu/v1/docs/ | Aktuelle LOIRE Version (Dev) abrufbar unter: 
    https://compliance.lab.gaia-x.eu/v2/docs/ |
    
    - Technische Änderungen der genutzten Standards
        
        ![S. 29](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/Untitled%207.png)
        
        S. 29
        

<aside>
💡 Es wird ab ca. August 2024 eine neue Software Version (LOIRE) für die GXDCHs geben. Diese wird neue verplichtende Softwarekomponenten enthalten, die sich auf Police Enforcement beim Anbieten und Nutzen von Diensten konzentrieren wird. Nutzenden können so z.B. im Katalog nach Diensten filtern, die in Deutschland angeboten werden.

</aside>

## Anhang 1 - Vergleich GXDCH und Building Blocks des DSSC

![[https://dssc.eu/space/BBE/178421761/Building+Blocks+|+Version+0.5+|+September+2023?attachment=/download/attachments/178421761/image-20230928-141101.png&type=image&filename=image-20230928-141101.png](https://dssc.eu/space/BBE/178421761/Building+Blocks+%7C+Version+0.5+%7C+September+2023?attachment=/download/attachments/178421761/image-20230928-141101.png&type=image&filename=image-20230928-141101.png)](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/Untitled%208.png)

[https://dssc.eu/space/BBE/178421761/Building+Blocks+|+Version+0.5+|+September+2023?attachment=/download/attachments/178421761/image-20230928-141101.png&type=image&filename=image-20230928-141101.png](https://dssc.eu/space/BBE/178421761/Building+Blocks+%7C+Version+0.5+%7C+September+2023?attachment=/download/attachments/178421761/image-20230928-141101.png&type=image&filename=image-20230928-141101.png)

GXDCHs implementieren die [*Building Blocks*](https://dssc.eu/space/BBE/178421761/Building+Blocks+%7C+Version+0.5+%7C+September+2023?attachment=/download/attachments/178421761/image-20230928-141101.png&type=image&filename=image-20230928-141101.png) des DSSC. In der aktuellen Version werden folgende Building Blocks umgesetzt: 

- Building Blocks v1
    - Data Products, Services, Participants and Offerings descriptions
    - Publication and discovery (registry)
    - Trust Framework with Conformity & Label
    - Identity & Attestation management

![Untitled](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/Untitled%209.png)

In der folgenden Version werden folgenden Blocks umgesetzt: 

![Untitled](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/Untitled%2010.png)

- Building Blocks v2
    - Access & Usage policy and enforcement
    - Contractual Framework
    - Data Sharing Governance
    - Trust Indexes*
    - Identity for workloads*
    - Service Composition and workload roaming
    - * Not (yet?) covered by the DSSC

## Anhang 2 - Weiterführende technische Infos

### Terms and Conditions

Um GXDCHs nutzen zu können, müssen die T&C akzeptiert werden. Diese finden sich [hier](https://registry.gaia-x.eu/v1/docs/#/TermsAndConditions/TermsAndConditionsController_getTermsAndConditions). (*Try it out Button drücken*). 

### Akzeptierte Zertifikate

<aside>
⚠️ Quelle: Aussage vom CTO im AISBL Call 10.4.24, mitgeschrieben von Dennis

</aside>

Um die Endpoints der GXDCHs nutzen zu können sind bestimmte Zertifikate bei der Request zu nutzen. Normale Zertifikate wie LetsEncrypt sind nur auf Development Endpoints erlaubt (staging, dev). Die folgenden Zertifikate werden akzeptiert. 

- [eIDAS qualified electronic signatures/seal](https://eidas.ec.europa.eu/efda/home)
- [eIDAS qualified website authentication certificate (QWAC)](https://www.europarl.europa.eu/RegData/etudes/ATAG/2023/739285/EPRS_ATA(2023)739285_EN.pdf)
- [SSL Extended Validation Certificate](https://www.ssl.com/certificates/ev-code-signing/)

### Technischer Workshop

Hier finden sich weiter Infos zum technischen Zugriff auf die Endpoints inkl. Erklärung der verwendeten Standards wie JSON-LD oder DID. 

[PDF des Workshops](https://gitlab.com/gaia-x/lab/workshops/gaia-x-101/-/blob/master/Gaia-X_101_-_Tech-stage_Market-X.pdf)

[Video des Workshops](https://www.youtube.com/watch?v=xHaBM-T2--k)

[Quellcode des Workshops](https://gitlab.com/gaia-x/lab/workshops/gaia-x-101/-/blob/master/gaia-x-101.ipynb)

[Link zur Gaia-X Entwicklungs-Bibliotheken](https://www.npmjs.com/search?q=%40gaia-x) 

## Quellen:

Komponenten von GXDCHs [https://docs.gaia-x.eu/technical-committee/architecture-document/latest/gx_services/](https://docs.gaia-x.eu/technical-committee/architecture-document/latest/gx_services/)

Architecture document 23.10 [https://docs.gaia-x.eu/technical-committee/architecture-document/latest/](https://docs.gaia-x.eu/technical-committee/architecture-document/latest/)

Präsentation CTO AISBL: 

[CTO+resources_231121+Gaia-X+conformity+scheme(1) 1.pptx](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/CTOresources_231121Gaia-Xconformityscheme(1)_1.pptx)

Policy Rules Conformity (high level objectives) [https://docs.gaia-x.eu/policy-rules-committee/policy-rules-conformity-document/23.10/Executive_Summary/](https://docs.gaia-x.eu/policy-rules-committee/policy-rules-conformity-document/23.10/Executive_Summary/)

Gaia-X Policy Rules and Labelling Document: [https://docs.gaia-x.eu/policy-rules-committee/policy-rules-labelling/22.11/policy_rules_labeling_document/](https://docs.gaia-x.eu/policy-rules-committee/policy-rules-labelling/22.11/policy_rules_labeling_document/)

GXDCHs: [https://gaia-x.eu/gxdch/](https://gaia-x.eu/gxdch/)

Trust Indexes: [https://gaia-x.eu/news-press/gaia-x-and-trust-indexes/](https://gaia-x.eu/news-press/gaia-x-and-trust-indexes/), [https://docs.gaia-x.eu/technical-committee/architecture-document/latest/enabling_services/#veracity](https://docs.gaia-x.eu/technical-committee/architecture-document/latest/enabling_services/#veracity)

Gaia-X Exchange Services: [https://docs.gaia-x.eu/technical-committee/data-exchange/23.11/dewg/](https://docs.gaia-x.eu/technical-committee/data-exchange/23.11/dewg/)

Präsentation CTO Gaia-X Label: 

[CTO+resources_240404+Gaia-X+Compliance+-+Label.pptx](2%20Sprint%20-%20Neuster%20Stand%20GXDCH%20065af5b7bb6e4cadba36a59d42965261/CTOresources_240404Gaia-XCompliance-Label.pptx)

GXDCH Gitlab: [https://gitlab.com/gaia-x/lab/gxdch/-/tree/main](https://gitlab.com/gaia-x/lab/gxdch/-/tree/main)

Generelle Infos zu GXDCHs: [https://gaia-x.eu/gxdch/](https://gaia-x.eu/gxdch/)

Übersicht GXDCHs: [http://docs.gaia-x.eu/framework/?tab=clearing-house](http://docs.gaia-x.eu/framework/?tab=clearing-house)

Trust Framework: [https://docs.gaia-x.eu/policy-rules-committee/trust-framework/latest/](https://docs.gaia-x.eu/policy-rules-committee/trust-framework/latest/)
