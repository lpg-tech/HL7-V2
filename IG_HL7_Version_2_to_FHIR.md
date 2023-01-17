# IG HL7 Version 2 to FHIR

Mit der Einführung von HL7(R) FHIR(R) würde ein von HL7 unterstütztes Mapping von HL7 v2-Komponenten auf FHIR-Komponenten, das als Ausgangspunkt für Implementierungen dienen kann, den konsistenten Übergang von Daten aus v2-Nachrichten in FHIR-basierte Ansätze (Nachrichten, Persistenz, RESTful APIs) unterstützen. Die aktuellen Mapping-Informationen in FHIR beschränken sich auf die Adressierung von FHIR-Komponenten und sind insofern unvollständig, als sie nicht bis auf die Ebene der Datentyp-Komponenten gehen und auch nicht alle häufig verwendeten v2-Datenelemente abdecken.
In diesem Projekt werden v2-to-FHIR-Maps für v2-Nachrichten, -Segmente und -Datentypen zu Standard-FHIR-Elementen entwickelt, sowie Erweiterungen vereinbart, wo FHIR eine Lücke aufweist. Der anfängliche Schwerpunkt des Projekts liegt auf den häufig verwendeten v2-Nachrichtenstrukturen und den Segment- und Datentyp-Bausteinen, die zur Erstellung dieser Nachrichten verwendet werden. Im Laufe der Zeit werden je nach Interesse und Nachfrage weitere v2-Nachrichtenstrukturen hinzukommen.
Um die v2-to-FHIR-Mappings zu entwerfen, zu dokumentieren und zu veröffentlichen und sie mit relevanten FHIR-Komponenten und zukünftigen v2+ Elementen zu verknüpfen, besteht auch Bedarf an einer Infrastruktur, die die FHIR-Publikationsinfrastruktur nutzen und Verknüpfungen zu den jeweiligen v2+ und FHIR-Standards ermöglichen kann.

## Geltungsbereich

### Source

v2.9 und neuere Versionen, wenn sie verfügbar werden. Abgelehnte (deprecated) Datenelemente werden weiter gemappt, um rückwärtskompatibel zu bleiben.

### Target

FHIR R4

### Nachrichten-Strukturen

Der anfängliche Schwerpunkt liegt auf den üblicherweise ausgetauschten v2-Nachrichtenstrukturen (z. B. ADT, Auftrag, Ergebnisse, Impfungen).
Die Umwandlung einer v2-Nachricht führt zu einem Bündel verwandter FHIR-Ressourcen, die möglicherweise MessageHeader-, Provenance- und Task-Ressourcen umfassen.
Beachten Sie, dass verschiedene FHIR-Workflows (z. B. Messaging, RESTFul Puts) verwendet werden können, sobald die Transformation von v2 nach FHIR erfolgt ist. Der anfängliche Projektumfang wird das FHIR-Messaging-Paradigma unterstützen, aber keinen bestimmten FHIR-Workflow vorschreiben.
Message Maps werden auf wiederverwendbare Segment Maps verweisen, die für das Mapping mehrerer Nachrichten wiederverwendet werden können.

### Felder/Segmente

* Typischerweise entspricht ein Segment einer FHIR-Ressource, kann aber auch einem FHIR-Datentyp zugeordnet werden.
* Die anfänglichen Segment-Maps konzentrieren sich auf die Segmente, die im anfänglichen Satz von v2-Nachrichten enthalten sind und die typischerweise vorhanden sind.
* Ein Segment kann eine andere Abbildung auf eine andere FHIR-Komponente erfordern, abhängig vom Kontext der Nachrichtenstruktur, in der es verwendet wird. Folglich werden Segment Map Flavors erstellt, um die Maps zu vereinfachen und gleichzeitig die Wiederverwendung zu maximieren, wo dies möglich ist.
* Für jedes Feld, von dem bekannt ist, dass es in der realen Welt der Nachrichtenübermittlung in einem gemappten Segment verwendet wird, wird das Projekt entweder identifizieren:
  * Das äquivalente FHIR-Kernressourcenelement oder,
  * eine FHIR-Erweiterung (entweder vorhanden oder vorgeschlagen), um eine konsistente Verwendung zu fördern, anstatt dass jede Implementierung ihre eigenen Erweiterungen definiert.
* Segmentkarten werden auf wiederverwendbare Datentypkarten verweisen, die für das Mapping mehrerer Segmente und Felder wiederverwendet werden können.

### Datentypen

* Erstellung von Mappings zwischen V2 und FHIR-Datentypen und Behebung fehlender Datentypkomponenten in FHIR für V2-Datentypkomponenten.
* Ein Datentyp kann eine andere Abbildung auf eine andere FHIR-Komponente erfordern, je nach Kontext des Segments oder eines anderen Datentyps, der verwendet wird. Folglich werden Flavors für Datentyp-Maps erstellt, um die Maps zu vereinfachen und gleichzeitig die Wiederverwendung zu maximieren, wo dies möglich ist.

### Vokabular

* Wenn ein kodierter v2-Datentyp auf einen FHIR-Datentyp abgebildet wird, der ein anderes Code ValueSet verwendet, wird eine anfängliche Vokabularabbildung bereitgestellt, indem entweder auf die anwendbare UTG-Abbildung verwiesen wird oder eine vorgeschlagene Abbildung erstellt wird, die die UTG übernehmen kann.
* Beachten Sie, dass nicht alle Elemente (weder in V2 noch in FHIR) vorgeschlagene oder erforderliche Wertesätze bereitstellen, so dass es nicht immer möglich ist, ein Vokabular-Mapping zu erstellen.
* Wenn eine V2-Tabelle verfügbar ist und der FHIR-Wertesatz nicht angegeben ist, können die V2-Codes im FHIR-Element verwendet werden.
* Innerhalb einer Abbildung kann es vorkommen, dass eine Untergruppe von v2-Codes keinen entsprechenden Code im FHIR-Wertesatz hat. Lokale Implementierungen müssen für diese Fälle eine Strategie entwickeln, bis die UTG den paradigmenübergreifenden Abgleich abgeschlossen hat.
