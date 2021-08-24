**Ziel:** Prüfung auf Belegung des Elements language

**Beschreibung:** Ein Metadatensatz muss immer eine Information über die in den Metadaten verwendete Sprache beinhalten.

**Testmethode:**
1. Prüfe, ob das Element language als Unterelement von MD_Metadata vorhanden ist.
2. Wenn [1] zutrifft:
  - a. Prüfe, ob im Element language der Wert in codeListValue im LanguageCode-Element nicht leer oder NULL ist.
3. Wenn [2] zutrifft:
  - a. Prüfe, ob der Eintrag in codeListValue (im LanguageCode-Element) gemäß ISO 639-2 ein gültiger 3-Buchstaben-Sprachcode und "ger" ist.
  - b. Prüfe, ob im LanguageCode-Element das codeList-Attribut vorhanden ist und die URL "http://www.loc.gov/standards/iso639-2/" enthält.

**Fehlermeldungen/Warnungen:**
* [F] Wenn Element language nicht vorhanden ist [1]: "Fehler: Es muss ein language-Element vorhanden sein."
* [F] Wenn kein Eintrag vorhanden ist [2]: "Fehler: Ein Metadatensatz muss eine Information über die in den Metadaten verwendete Sprache beinhalten. Das Element codeListValue im LanguageCode-Element darf nicht leer sein."
* [F] Wenn Eintrag nicht ein gültiger 3-Buchstaben-Sprachcode ist [3]: "Fehler: Der Wert ist gemäß ISO 693-2 (https://www.loc.gov/standards/iso639-2/php/code_list.php) kein gültiger 3-Buchstaben-Sprachcode."
* [W] Wenn Eintrag in codeListValue nicht "ger" ist [3a]: "Warnung: Die Festlegungen im Dokument "Konventionen zu Metadaten" sind für die Metadaten-Sprache „Deutsch“ getroffen, sofern durch ISO oder INSPIRE keine anderen Forderungen bestehen."
* [W] Wenn Eintrag unter LanguageCode im codeList-Attribut nicht "http://www.loc.gov/standards/iso639-2/" oder das codeList-Attribut nicht vorhanden ist [3b]: "Warnung: Gemäß INSPIRE TG Metadata wird empfohlen, im LanguageCode-Element das codeList-Attribut mit der URL "http://www.loc.gov/standards/iso639-2/" anzugeben."

**XPath:** `MD_Metadata/language`

**Referenzen:**
* [AK MD] Abschnitt 1.4, 2.4
* [INS TG MD] 2.2.2
* [ISO 19115] B.2.1 No. 3

**Test type:** Automatisch

**Notizen:**
Beispiel

```
<gmd:language>
  <LanguageCode codeList="http://www.loc.gov/standards/iso639-2/" codeListValue="ger"/>
</gmd:language>
```

**Konformitätsklasse:** Metadaten: GDI-DE (M - verpflichtend)
