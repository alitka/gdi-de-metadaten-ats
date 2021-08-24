**Ziel:** Lizenzinformationen zu Open Data sind einheitlich in den Metadaten der GDI-DE hinterlegt, um im GovData-Portal weiterverarbeitet werden zu können.

**Beschreibung:** Sofern die zu beschreibende Ressource unter Open Data fällt, sind die Lizenzinformationen in einem zusätzlichen otherConstraints-Element (im selben MD_LegalConstraints) im Datenformat JSON (JavaScript Object Notation) strukturiert anzugeben.

**Testmethode:**
1. Prüfe, ob der Test "gdide_2.9.1_bedingungenGDIde" ODER "gdide_2.9.2_bedingungenINSPIRE" bestanden wurde.
2. Wenn [1] zutrifft:
   - a. Prüfe, ob einer der MD_LegalConstraints/useConstraints/MD_RestrictionCode-Einträge den Begriff otherRestrictions enthält.
   - b. Prüfe, ob im selben MD_LegalConstraints genau ein otherConstraints-Element vorhanden ist, dessen Freitext "{ }" enthält.
3. Wenn [2b] zutrifft:
   - a. Prüfe, ob das otherConstraints-Element in der JSON-Notation einen Eintrag für "id": enthält, der der Spalte „Lizenzcode“ unter https://www.dcat-ap.de/def/licenses/ entspricht.
   - b. Prüfe, ob das otherConstraints-Element in der JSON-Notation Einträge für "name": und "url": und "quelle": enthält.

**Fehlermeldungen/Warnungen:**
* [F] Wenn der Test "gdide_2.9.1_bedingungenGDIde" ODER "gdide_2.9.2_bedingungenINSPIRE" nicht bestanden wurde [1]: „Fehler: Der Test „Nutzungs- und Zugriffsbedingungen in der GDI-DE (ohne INSPIRE)“ bzw. „Nutzungs- und Zugriffsbedingungen in der GDI-DE (mit INSPIRE)“ wurde nicht bestanden. Die Bedingungen für den Zugang und die Nutzung sind innerhalb eines gemeinsamen MD_LegalConstraints-Objekts anzugeben. Dadurch wird sichergestellt, dass textliche Erläuterungen zweifelsfrei der ggf. dokumentierten Beschränkungsart zugeordnet werden können.“
* [F] Wenn es keine Ausprägung von otherRestrictions gibt [2a & 2b]: „Fehler: Im Rahmen der GDI-DE sind die Nutzungsbedingungen bzw. Lizenzinformationen zu Open Data in einem zusätzlichen otherConstraints-Element im Datenformat JSON (JavaScript Object Notation) anzugeben.“
* [F] Wenn im otherConstraints-Element kein Freitext „{}“ vorhanden ist [2b]: „Fehler: Im Rahmen der GDI-DE sind die Nutzungsbedingungen bzw. Lizenzinformationen zu Open Data in einem zusätzlichen otherConstraints-Element im Datenformat JSON (JavaScript Object Notation) strukturiert in „{}“ anzugeben. Mischformen aus JSON und Freitext innerhalb eines otherConstraints-Element müssen zur Vermeidung von Fehlinterpretationen verhindert werden. “
* [F] Wenn mehrere otherConstraints-Elemente mit Freitext „{}“ vorhanden sind [2b]: „Fehler: Im Rahmen der GDI-DE sind die Nutzungsbedingungen bzw. Lizenzinformationen zu Open Data in genau einem zusätzlichen otherConstraints-Element im Datenformat JSON (JavaScript Object Notation) strukturiert in „{}“ anzugeben.“
* [F] Wenn im otherConstraints-Element mit der Notation "{ }" kein Eintrag für "id" vorhanden ist [3a]: „Fehler: Im Rahmen der GDI-DE sind die Nutzungsbedingungen bzw. Lizenzinformationen zu Open Data in einem zusätzlichen otherConstraints-Element im Datenformat JSON (JavaScript Object Notation) strukturiert in „{}“ anzugeben. Mindestens der Parameter „id“ soll bei der Lizenzbeschreibung gesetzt werden und der Spalte „Lizenzcode“ unter https://www.dcat-ap.de/def/licenses/ entsprechen.“
* [W] Wenn im otherConstraints-Element mit der Notation "{ }" keine Eintrag Einträge für "name": und "url": und "quelle" vorhanden sind [3b]: „Warnung: Im Rahmen der GDI-DE sind die Nutzungsbedingungen bzw. Lizenzinformationen zu Open Data in einem zusätzlichen otherConstraints-Element im Datenformat JSON (JavaScript Object Notation) strukturiert in „{}“ anzugeben. Zusätzlich zum „id“-Parameter sollten mindestens die Parameter „name“ (Name der Lizenz); „ur“ (URL, unter welcher der Lizenztext bezogen werden kann) und „quelle“ (Text der Namensnennung, unter welcher die Datenquelle bei einer Weiternutzung zitiert werden soll) angegeben sein.“

**XPath:** `MD_Metadata/identificationInfo[1]/MD_DataIdentification/resourceConstraints/MD_LegalConstraints/useConstraints`

**Referenzen:**
* [AK MD] Abschnitt 3.6

**Test type:** Automatisch

**Notizen:**
Beispiel

```
<gmd:resourceConstraints>
  <gmd:MD_LegalConstraints>
    <gmd:useConstraints>
      <gmd:MD_RestrictionCode codeList="http://...l#MD_RestrictionCode" codeListValue="otherRestrictions"/>
    </gmd:useConstraints>
    <gmd:otherConstraints>
      < gco:CharacterString>Dieser Datensatz kann gemäß der „Nutzungsbestimmungen für die Bereitstellung von 
      Geodaten des Bundes“ (http://www.geodatenzentrum.de/docpdf/geonutzv.pdf) genutzt werden.</gco:CharacterString>
    </gmd:otherConstraints>
    <gmd:otherConstraints>
      < gco:CharacterString>
{
"id": "geoNutz/20130319",
"name": "Nutzungsbestimmungen für die Bereitstellung von Geodaten des Bundes",
"url": "http://www.geodatenzentrum.de/docpdf/geonutzv.pdf",
"quelle": "Quelle: © GeoBasis-DE / BKG <Jahr des letzten Datenbezugs>"
}
</gco:CharacterString>
    </gmd:otherConstraints>
  </gmd:MD_LegalConstraints>
</gmd:resourceConstraints>
```

**Konformitätsklasse:** OpenData (C - konditional)
