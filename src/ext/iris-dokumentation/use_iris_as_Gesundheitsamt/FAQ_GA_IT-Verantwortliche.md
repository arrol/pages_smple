# FAQ für TechnikerInnen in den Gesundheitsämtern zu Funktionsweise, Einrichtung und Betrieb

## Funktionsweise

### Wo wird verschlüsselt? Wo liegen die Daten?

Die Verschlüsselung der personenbezogenen Daten findet direkt in der jeweiligen Anwendung statt. Die Entschlüsselung erfolgt im IRIS-Client-Backend, also quasi im Gesundheitsamt. Hinzu kommt Transportverschlüsselung mittels tls/https.    

Im IRIS-Client liegen die Daten dann unverschlüsselt. Vor der Datenabfrage durch ein Gesundheitsamt liegen diese ausschließlich bei der App und nicht im IRIS-System. Die Verschlüsselung und Entschlüsselung entnehmen Sie auch der Grafik am Anfang des Dokuments.

### Welche Daten werden übertragen?
Hier ist zwischen Kontakttagebüchern und Gästelisten zu unterschieden.

| Bei Gästelisten                                         | Bei Kontakttagebüchern und Gästelisten   |
| :-------------------------------------------------------| :----------------------------------------|
| `vom Gesundheitsamt zur Location`                       | `von der Location zum Gesundheitsamt`    |
| Anfragezeitraum                                         | Gästeliste                               |
| Angefragter Bereich innerhalb der Location (z.B. Raum)  | Name                                     |
| Kommentarfeld                                           | Vorname                                  |
|                                                         | Geburtsdatum (optional)                  |  
|                                                         | Geschlecht (optional)                    |  
|                                                         | E-Mail-Adresse (optional)                |  
|                                                         | Telefonnummer (optional)                 |  
|                                                         | Adresse (optional)                       |  
|                                                         | Straße                                   |  
|                                                         | Hausnummer                               |  
|                                                         | PLZ                                      |  
|                                                         | Ort                                      |  
|                                                         | Von (Zeitpunkt Check-In)                 |  
|                                                         | Bis (Zeitpunkt Check-Out)                |  
|                                                         | Zusätzliche Informationen zur Location   |  


### Werden die abgerufenen Daten der Apps durch IRIS überprüft/gecheckt/validiert?

Eine »input validation« und »input sanitation« sollen vorgenommen werden. Hier ist Vorsicht mit den Begrifflichkeiten geboten. Input validation heißt hier nur, dass drin ist, was drauf steht. Es kann geprüft werden ob die formalen Kriterien einer Telefonnummer erfüllt sind. Automatisiert kann nicht bestätigt werden, ob die Nummer stimmt. (Anmerkung: Das ist technisch kaum machbar in der Zeit und mit den Ressourcen - Unternehmen der Größenordnung Google oder Facebook könnten das).

### Wie kann sichergestellt werde, dass reale Daten und keine fake Daten übertragen werden?

Die Plausibilitätsprüfung liegt nicht im Fokus von IRIS, sondern muss durch andere Prozesse dargestellt werden, da IRIS die Daten selbst nicht einsieht. Eine Plausibilitätsprüfung erfolgt über die Gesundheitsamt Mitarbeiter:in im IRIS Client. Darüber hinaus gilt für die Locations eine Sorgfaltspflicht bei der Erfassung der Gästelisten entsprechend der gültigen Verordnungen. 

### Was ist wenn sich jemand nicht ausloggt aus dem Gästebuch - können Einrichtungs-Betreibende das manuell machen? Sprich: ist das durch Dritte manipulierbar?
Dies obliegt der App und muss im entsprechenden Hygienekonzept der Veranstaltung berücksichtigt werden.

### Werden Daten zwischengespeichert?

Es findet keine Vorratsspeicherung statt. Die Daten werden nur im Bedarfsfall angefragt. Dann wird eine dezentrale Verbindung mit dem Client 
des jeweiligen Gesundheitsamts aufgebaut.

### Wie sieht die Backup Strategie für IRIS aus?

Die zentralen Strukturen werden redundant betrieben, dort werden keine Daten vorgehalten. Daten, die im Gesundheitsamt ankommen unterliegen der 
dortigen Datenhaltung.

###Ist IRIS 3-Tier fähig?
Aus Applikations-Sicht spricht nichts dagegen. 

Wie findet die Orchestrierung statt?
Über Kubernetes.


## Welchen Kundenservice bieten Sie an? Nur per E-Mail oder geht es auch telefonisch?

Es wird ein Kundenservice über die Dienstleistungs-GmbH der Björn Steiger Stiftung angeboten. Dieser beinhaltet ein Ticket-System und eine Hotline.


## Nutzendenverwaltung
### Wie findet die Anmeldung für die Anwendung statt?


Es gibt eine »klassische« Nutzerverwaltung, d.h. NutzerInnenkonten können in IRIS angelegt werden und sich über ein Login in der Anwendung anmelden. 
### Wie sieht das Rollen- und Rechtekonzept aus?
Siehe Rechtevergabe. Grundsätzlich dürfen angemeldete Nutzende Anfragen stellen und die erhaltenen Daten verarbeiten.

### Wie ist die Rechtevergabe für Mitarbeiter?

'Link zu Dokumentation der Nutzendenverwaltung folgt'

### Welche Schutzmechanismen nutzt IRIS?
Schutzmechanismen werden im Rahmen eines Open Development Prozesses implementiert. Unter anderem  werden wir voraussichtlich den OWASP Katalog abarbeiten (s. Injection Prevention Cheat Sheet). Weiteres ist auch im IT-Sicherheitskonzept ausgeführt.

## Bedienung
### Wie intuitiv ist die Bedienung von IRIS?
Ziel ist es, die Bedienung so intuitiv wie möglich zu gestalten. Das Feedback im Rahmen von Tests in Gesundheitsämtern war allgemein sehr positiv.

### Wie wird die Usability auf Seiten der Gesundheitsämter sichergestellt? Können z.B. Feature-Wünsche, bzw. Änderungswünsche zurückgespielt werden?
Grundsätzlich besteht ein hohes Interesse an einer bestmöglichen Nutzbarkeit. Dazu wurden bereits mehrere Gespräche und Tests mit Gesundheitsämtern durchgeführt. IRIS wird im sogenannten Open-Development-Prozess entwickelt. Es können also direkt Feature-Requests gestellt und innerhalb der Community diskutiert werden. Falls weitere Features gewünscht werden, können diese auch extern beauftragt werden. Diese Module werden dann ebenfalls Open-Source bereitgestellt und können von allen genutzt werden. 

### Gibt es einen Barrierefreiheits-Test nach BITV (Standard nach welchen Kriterien Barrierefreiheits-Tests erfolgen soll)?
Zunächst nicht. Ziel ist es, im Zuge der Pandemie zunächst schnell eine Lösung bereitzustellen. Im weiteren Verlauf der Entwicklung wird dies natürlich berücksichtigt werden.

## Einrichtung

### Kann ein Gesundheitsamt die IRIS Anwendung käuflich erwerben oder geht dies über das Land?
Die Software wird Open Source betrieben, d.h. es fallen keine Lizenzkosten an. Für den Produktivbetrieb im Gesundheitsamt ist ein Zertifikat der Bundesdruckerei notwendig. Die Björn Steiger Dienstleistungs GmbH bietet Zertifikate, welche jeweils eine Gültigkeit von 12 Monaten haben, zusammen mit Support- und Pflegeleistungen an. Sofern keine Vereinbarung mit dem jeweiligen Bundesland getroffen wurde, können diese Leistungen direkt über die Dienstleistungs-GmbH erworben werden. Empfohlen wird jedoch ein Ankauf über die Länder.

### Wie wird der Client installiert?
Die Installationsanleitung für den Client wird im öffentlichen Repositorium einsehbar sein.
(Link zur Ìnstallationsanleitung folgt)

### Muss für jedes Gesundheitsamt ein Client im Rechenzentrum betrieben werden oder liegt die Clientbereitstellung bei den GAs und diese nutzen die zentralen Strukturen?

Der Client kann durch die verantwortlichen kommunalen Stellen betrieben werden. Ausschlaggebend ist das bestehen von Zugriff auf den Internal-Reverse-Proxy und die SORMAS-Instanz des Gesundheitsamtes.

### Was für Protokolle machen Sinn und werden allgemein gesprochen?
Bei allen Schnittstellen handelt es sich um REST-Schnittstellen. Diese nutzen tls/https. Die Kommunikation mit externen Diensten erfolgt über einen Ende-zu-Ende Tunnel. Die Dienste im GA kommunizieren mit den App Providern und der Location Suche per gRPC über eine mTLS-Verbindung.

### Welche Betriebssysteme werden unterstützt?
Nur relevant für Betriebsmodus »Java«. Jedes System das Open JDK unterstützt ist geeignet. Die aktuelle IRIS Staging Umgebung läuft auf Ubuntu LTS.

### Welches Java wird für die Lizenzerklärung verwendet?
OpenJDK. Corretto wäre alternativ auch möglich.

### Wie groß sollte die Datenbank für singuläre Strukturen und die Clients der Gesundheitsämter sein?
200 GB für ganz Deutschland für die singulären Strukturen auf die länderübergreifend zugegriffen werden kann. Hinzu kommen die Datenbanken für die Clients der Gesundheitsämter von je ca. 50 GB.

### Wie viele VMs bzw. Server werden benötigt? Ist ein Loadbalancing geplant?
Betriebsmodus Java: Die singulären Strukturen können problemlos auf VMs betrieben werden. Beispiel: 4 VMs, 2 Core, 16 GB RAM. 

### Welcher Unterbau wird präferiert?
Wir präferieren ein Container Deployment, Betriebsmodus Java ist möglich.

### Wie bekommte ich das entsprechende Zertifikat für die Registrierung eines Gesundheitsamtes?
Es gibt einen gesonderten Prozeß, der die Bestellung und Einrichtung des Zertifikats von der Bundesdruckerei (Public-Key-Infrastruktur, PKI) beschreibt. Der Prozess ist in der Installationsanleitung beschrieben.

### Wird für die Pilotierung Java oder Container System genutzt?
In der Pilotierung werden Container für das Staging System genutzt, wir sind aber offen für andere Vorschläge.

### Wer stellt das »IRIS Onboarding Team« zur Unterstützung bei der Einrichtung eines neuen Gesundheitsamtes?
Das »IRIS Onboarding Team« wird aktuell aus einem Teil des Kern-Teams des IRIS Projekts gebildet. Wir stehen mit weiteren Partnern in Kontakt, die entsprechende Personalkapazitäten aufbauen bzw. vorhalten.

### Mit der Vorgabe vom BSI "Nur eine Applikation pro Server" müssten für den GA Client mindestens zwei Server plus DB Server genutzt werden – oder?

Nein, das IRIS-Client-Frontend und IRIS-Client-Backend können zu einer Applikation zusammengezogen werden. Ob gleiches auch für die Datenbank gilt, hängt von der genauen Ausgestaltung der Vorgabe ab. 


## Betrieb

### Wie wird IRIS betrieben?
Bestimmte Teile der Infrastruktur müssen nur einmal betrieben werden. Eine länderübergreifende Bereitstellung dieser Teile ist jedoch abhängig von politischen Entscheidung und muss im Rahmen der Vertragserstellung diskutiert werden. Die singulären Strukturen für den Pilot sind redundant bei der AKDB gehostet und von dort aus bereitgestellt.

### Welche Auslastung mit welchen Leistungsspitzen sind zu erwarten?
Dies hängt vom Infektionsgeschehen und der Intensität des öffentlichen Lebens ab. Bei hoher Inzidenz und Kontaktbeschränkungen sind von 3–5 Kontaktpersonen pro Indexfall auszugehen. Das bedeutet bei einer 7-Tage-Inzidenz von 200 Fällen/100.000&#8239;EW ca. 33.000 Anfragen bzw. 170.000 Kontaktdatensätze pro Wochenarbeitstag. Bei mehr sozialem Leben (50 Kontaktpersonen pro Fall) und eher niedriger 7-Tage-Inzidenz (10/100.000&#8239;EW) sind es 1.660 Anfragen pro Wochenarbeitstag und 83.000 Kontaktdatensätze.

### Wer übernimmt den Support für die lokalen Gesundheitsämter?
Das Betriebsmodell muss noch final geklärt werden. Die Dienstleistungs-GmbH der Björn Steiger Stiftung kann entsprechende Strukturen für den Support der kommunalen verantwortlichen IT-Stelle bereitstellen. Gleiches gilt für die Betreuung von Rollout und Installation.

### Woher kennt IRIS die verschiebenden Apps/Anbieter?
Apps/Anbieter sind über Client Zertifikate eindeutig zuordenbar. Es gibt einen Onboarding Prozess, der die Bereitstellung verschiedener relevanter Dokumente erfordert. Außerdem werden entsprechende zu integrierende Komponente zur Verfügung gestellt. Das Prozedere ist im Repositorium beschrieben.

### Wie wird mit Updates umgegangen? Wie funktioniert der Prozess?
Zuständigkeiten und Vorgehen sind aktuell noch in der Klärung. Dies ist außerdem unterschiedlich von der Betreiberstruktur in den jeweiligen Kommunen abhängig.

### Wie werden Images bereitgestellt?
Über ein öffentliches Docker-Repository. Alternativ können sie auch direkt aus dem Source-Code erstellt werden.

### Wie werden die Zertifikate des IRIS Client verwaltet?
Die Verwaltung der Zertifikate ist aktuell noch in Klärung, diese werden aber durch einen Dienstleister zur Verfügung gestellt. Hier ist aktuell vorgesehen, diese alle 12 Monate zu erneuern. Weitere Fragen zum Prozess werden beim Onboarding geklärt.

### Was für Proxies werden für den Zugriff auf die singulären Komponentenverwendet?
`wird nachgereicht`

### Was für Proxies werden für den Zugriff auf den Client verwendet?
Das Gateway stellt keine Verbindung zum Client her. Der Client stellt Verbindung zum Client her.

###Wo liegt der Internal Reverse-Proxy, hat er eine öffentlich IP oder besteht dort eine Anbindung an private Netze?
Der Internal Reverse-Proxy muss von allen IRIS-Clients aus zugänglich sein. Da sich die Clients per Client-Zertifikat gegenüber dem Internal Reverse-Proxy authentifizieren, kann der Internal Reverse-Proxy öffentlich aus dem Internet zugänglich sein. Ein zusätzlicher Schutz per Firewall/VPN kann aber auch hinzugefügt werden.
 
### Besteht die Gefahr, dass durch die IRIS-Plattform SORMAS infiltriert werden kann?
Grundsätzlich besteht diese Gefahr immer (auch Microsoft Exchange Server hatten Lücken). Wir können allerdings nach Best Practices arbeiten um die Wahrscheinlichkeit durch diverse Maßnahmen (s. oben) zu senken. Zudem wird für den Import zunächst noch eine .csv-Datei verwendet, die nicht Ende-zu-Ende durchgereicht, sondern erst innerhalb des IRIS Client generiert wird. Sollten die Daten eines Anbieters infiltriert werden, dann wird das beim Entpacken vom IRIS Client geblockt.

### Sind „Injections” möglich?
Grundsätzlich besteht diese Gefahr immer. Es gibt Best Practice Gegenmaßnahmen die vermutlich eingebaut werden können (s. erste Frage). Auch im erweiterten toolkit. package size checkes etc. Durch die innerhalb IRIS stattfindende Generierung der csv-Datei vor dem Durchreichen in die Fachanwendung ist eine Art Firewall implementiert.

### Gibt es ein Datenbankmodell oder ERM?
`Wird nachgereicht und offen in der Dokumentation dargestellt`

### Wie sieht es mit der Redundanz aus?
Das sollte bei Kubernetes kein Problem darstellen. Diese Art der Architektur ist inhärent eben sehr robust konzipiert.

### Gibt es ein HELM chart oder ein docker-compose manifest?
Ja, es gibt ein docker manifest, dieses wird im öffentlichen Repositorium bereitgestellt.
`Link zu HELM chart folgt`

### Ergänzung zur PKI: Wird eine Certificate Revokation List (CRL) gepflegt/genutzt, um die Nutzung kompromittierter Zertifikate zu unterbinden?
Ja.

### Wird SORMAS mit Keycloak eingesetzt?
SORMAS wird idR mit Keycloak eingesetzt. Diese Infrastruktur kann auch von IRIS mitgenutzt werden. 
