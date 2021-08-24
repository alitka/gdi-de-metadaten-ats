**Ziel:** Prüfung auf Existenz eines eindeutigen Identifikators im Element fileIdentifier.

**Beschreibung:** Ein Metadatensatz besitzt immer einen eindeutigen Identifikator. Die Verwendung einer UUID gemäß RFC 4122 wird empfohlen.

**Testmethode:**
1. Prüfe, ob das Element fileIdentifier als Unterelement von MD_Metadata vorhanden ist.
2. Prüfe, ob das Element fileIdentifier nicht leer und nicht NULL ist.
3. Wenn [2] zutrifft: Prüfe, ob der Eintrag eine UUID gemäß RFC 4122 ist:
   * 16-Byte-Zahl
   * hexadezimal notiert
   * in fünf Gruppen unterteilt

**Fehlermeldungen/Warnungen:**
* [F] Wenn Element fileIdentifier nicht vorhanden ist [1]: "Fehler: Es muss ein fileIdentifier-Element vorhanden sein."
* [F] Wenn kein Eintrag vorhanden ist [2]: "Fehler: Ein Metadatensatz muss immer einen eindeutigen Identifikator besitzen. Das Element fileIdentifier darf nicht leer sein. Die Verwendung einer UUID gemäß RFC 4122 wird empfohlen (z. B. 550e8400-e29b-11d4-a716-446655440000)."
* [W] Wenn Eintrag keine UUID gemäß RFC 4122 ist [3]: "Warnung: In der GDI-DE wird die Verwendung einer UUID gemäß RFC4122 empfohlen (z. B. 550e8400-e29b-11d4-a716-446655440000). Sollte der bisher verwendete Metadatensatzidentifikator historisch bedingt nicht den Regeln einer UUID gemäß RFC 4122 entsprechen, so ist dieser im Sinne des Bestandsschutzes weiterhin zulässig. Darüber hinaus sind gemäß der INSPIRE TG Metadata auch Identifikatoren nach landesspezifischem Schema mit entsprechendem Präfix zulässig (z. B. nach folgendem Muster DE_<producer>_<product>_<version>_<theme>). Hierzu gibt es aber in der GDI-DE bislang noch keine Regelungen."

**XPath:** `MD_Metadata/fileIdentifier`

**Referenzen:**
* [AK MD] Abschnitt 2.2
* [INS TG MD], 2.2.1
* [ISO 19115], B.2.1, No.2

**Test type:** Automatisch

**Notizen:** 

  Beispiel
  
```
<gmd:fileIdentifier>
  <gco:CharacterString>550e8400-e29b-11d4-a716-446655440000</gco:CharacterString>  
</gmd:fileIdentifier>
```

**Konformitätsklasse:**	Metadaten: GDI-DE (M - verpflichtend)
