**Ziel:**	Prüfung auf Belegung des Elements hierarchyLevel.

**Beschreibung:** Ein Metadatensatz muss immer eine Information über die Art der Ressource, die er beschreibt, beinhalten.

**Testmethode:**
1. Prüfe, ob das Element hierarchyLevel als Unterelement von MD_Metadata vorhanden ist.
2. Prüfe, ob das Element hierarchyLevel nicht leer oder NULL ist.
3. Wenn [2] zutrifft:
   - a. Prüfe, ob der Eintrag ein Wert aus der CodeList MD_ScopeCode ist.
   - b. Prüfe, ob im MD_ScopeCode-Element das codeList-Attribut vorhanden ist und die URL "http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#MD_ScopeCode" enthält".

Fehlermeldungen/Warnungen	
* [F] Wenn Element hierarchyLevel nicht vorhanden ist [1]: "Fehler: Es muss ein hierarchyLevel-Element vorhanden sein. Diese Regelung geht über die ISO 19115 für das Element hierarchyLevel hinaus und soll eine eindeutige Interpretierbarkeit des Metadatensatzes innerhalb der GDI-DE ermöglichen."
* [F] Wenn kein Eintrag vorhanden ist [2]: "Fehler: Ein Metadatensatz muss eine Information über die Art der Ressource, die er beschreibt, besitzen. Das Element hierarchyLevel darf nicht leer sein."
* [F] Wenn Eintrag nicht der CodeList MD_ScopeCode entstammt [3a]: "Fehler: Der Wert für das Element hierarchyLevel muss der CodeList MD_ScopeCode entstammen."
* [W] Wenn Eintrag im MD_ScopeCode-Element im codeList-Attribut nicht "http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#MD_ScopeCode" oder das codeList-Attribut nicht vorhanden ist [4b]: "Warnung: Gemäß INSPIRE TG Metadata wird empfohlen, im MD_ScopeCode-Element das codeList-Attribut mit der URL "http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#MD_ScopeCode" anzugeben."

**XPath:** `MD_Metadata/hierarchyLevel`

**Referenzen:**
* [AK MD] Abschnitt 2.3
* [INS TG MD] 3.1.1.1, 4.1.1.1
* [ISO 19115] B.2.1, No.6

**Test type:** Automatisch

**Notizen:**
Beispiel

```
<gmd:hierarchyLevel>
  <MD_ScopeCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#MD_ScopeCode" 
  codeListValue="dataset"/>
</gmd:hierarchyLevel>
```
