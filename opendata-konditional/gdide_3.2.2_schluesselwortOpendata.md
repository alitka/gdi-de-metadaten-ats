**Ziel:** Prüfung auf Existenz des Eintrags "opendata" im Element keyword für die Verwendung der Metadaten bei Open Data.

**Beschreibung:** Metadaten zu Datensätzen und -serien, die über den Geodatenkatalog.de für GovData bereitgestellt werden sollen, müssen im Element keyword ([ISO 19115], B.2.2.3, No. 53) das Schlüsselwort „opendata“ enthalten. Das Schlüsselwort „opendata“ ist keinem Thesaurus entnommen und ist ohne Quellenangabe in den Metadaten zu führen.

**Testmethode:**
1. Prüfe, ob der Eintrag "opendata" in einem keyword-Element (Unterelement von MD_Metadata/identificationInfo/*/descriptiveKeywords) vorhanden ist.
2. Prüfe, ob im selben MD_Keywords-Element das Element thesaurusName belegt ist.

**Fehlermeldungen/Warnungen:**
* [F] Wenn Eintrag "opendata" nicht vorhanden ist [1]: "Fehler: Wenn der Metadatensatz eine Open Data-Ressource beschreibt und für GovData bereitgestellt werden soll, muss der Eintrag 'opendata' in einem keyword-Element vorhanden sein."
* [W] Wenn dem Eintrag "opendata" ein Thesaurus zugeordnet ist [2]: "Warnung: Das Schlüsselwort 'opendata' ist keinem Thesaurus entnommen und ist ohne Quellenangabe in den Metadaten zu führen."

**XPath:**
* `MD_Metadata/identificationInfo[1]/MD_DataIdentification/descriptiveKeywords/*/keyword`
* `MD_Metadata/identificationInfo/*/descriptiveKeywords/*/thesaurusName`

**Referenzen:**
* [AK MD] Abschnitt 3.2.2
* [ISO 19115] B.2.2.3 No. 53 

**Test type:** Automatisch

**Notizen:**
Beispiel
```
<gmd:descriptiveKeywords>
  <gmd:MD_Keywords>
    <gmd:keyword>
      <gco:CharacterString>opendata</gco:CharacterString>
    </gmd:keyword>
  </gmd:MD_Keywords>
</gmd:descriptiveKeywords>
```

**Konformitätsklasse:** OpenData (C - konditional)
