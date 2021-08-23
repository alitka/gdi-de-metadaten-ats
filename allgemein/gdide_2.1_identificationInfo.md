**Ziel:** Prüfung auf Existenz genau eines identificationInfo-Elements.

**Beschreibung:** Alle relevanten Informationen sind im ersten identificationInfo-Element anzugeben. Gemäß ISO 19115 kann das identificationInfo-Element innerhalb eines Metadatensatzes mehrfach verwendet werden. Im Rahmen von INSPIRE wird jedoch nur das erste identificationInfo-Element ausgewertet (siehe [INS TG MD], 2.3). Auch im Geoportal.de finden nur Informationen Berücksichtigung, die im ersten identificationInfo-Element angegeben sind.

**Testmethode:**
1. Prüfe, ob das Element identificationInfo als Unterelement von MD_Metadata vorhanden ist.
2. Prüfe, ob das Element identificationInfo als Unterelement von MD_Metadata mehrfach vorhanden ist.

**Fehlermeldungen/Warnungen:**
* [F] Wenn Element identificationInfo nicht vorhanden ist [1]: "Fehler: Der Metadatensatz enthält kein identificationInfo-Element als Unterelement von MD_Metadata."
* [W] Wenn mehr als ein identificationInfo Element vorhanden ist [2]: "Warnung: Es sind mehrere identificationInfo-Elemente vorhanden. Im Rahmen der GDI-DE sowie für INSPIRE-relevante Daten- und Dienst-Metadatensätze wird nur das erste identificationInfo-Element ausgewertet."

**XPath:** `MD_Metadata/identificationInfo`

**Referenzen:**
* [AK MD] Abschnitt 2.1
* [INS TG MD] 2.3

**Test type:** Automatisch

**Notizen:** -	

**Konformitätsklasse:** Metadaten: GDI-DE (M - verpflichtend)
