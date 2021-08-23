**Ziel:**	Prüfung auf Existenz einer Verantwortlichen Stelle für die Metadaten im Element contact mit zugehöriger organisationName-, electronicMailAddress- und role-Angabe

**Beschreibung:** Ein Metadatensatz muss immer eine Information über die für Erstellung und Pflege der Metadaten zuständige Stelle beinhalten.

**Testmethode:**
1. Prüfe, ob das Element contact als Unterelement von MD_Metadata vorhanden ist.
2. Prüfe, ob im Element contact die Unterelemente organisationName, electronicMailAddress und role vorhanden sind.
3. Prüfe, ob die Elemente organisationName, electronicMailAddress und role nicht leer oder NULL sind.
4. Wenn [3] zutrifft:
   - a. Prüfe, ob das Element electronicMailAddress
     - i. vor dem @-Zeichen nach RFC 5322 (erlaubte Buchstaben und Zahlen für die Teil vor dem @-Zeichen: A-Za-z0-9.!#$%&'*+-/=?^_`{|}~) und
     - ii. nach dem @-Zeichen nach RFC 1034 und RFC 1035 (mindestens 3 Teile: Hostnamen, Punkt und Top-Level-Domain (häufig ein Ländercode); erlaubte Zeichen: reiner ASCII-Code sowie 92 Sonderzeichen) konform ist.
   - b. Prüfe, ob der Eintrag in role 
     - i. ein Wert aus der CodeList CI_RoleCode ist und
     - ii. den codeListValue-Wert "pointOfContact" hat.
   - c. Prüfe, ob im CI_RoleCode-Element das codeList-Attribut vorhanden ist und die URL "http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_RoleCode" enthält.

**Fehlermeldungen/Warnungen:**
* [F] Wenn Element contact nicht vorhanden ist [1]: "Fehler: Es muss ein contact-Element als Unterelement von MD_Metadata vorhanden sein."
* [F] Wenn Element organisationName, electronicMailAddressoder role nicht vorhanden sind [2]: "Fehler: Ein Metadatensatz muss immer eine Information über die Erstellung und Pflege der Metadaten zuständige Stelle beinhalten. Diese Information muss mindestens Folgendes beinhalten: einen Namen im Element organisationName; eine E-Mail-Adresse im Element electronicMailAddress und die Rolle „pointOfContact“ im Element role.
* [F] Wenn kein Eintrag in einem oder mehreren Elementen vorhanden ist [3]: "Fehler: Ein Metadatensatz muss immer eine Information über die für die Erstellung und Pflege der Metadaten zuständige Stelle beinhalten. Im Element organisationName muss ein Name, im Element electronicMailAddress eine E-Mail-Adresse und im Element role die Rolle „pointOfContact“ angegeben sein.
* [W] Wenn Eintrag nicht nach RFC 5322,RFC 1034 oder RFC 1035 konform ist [4a]: "Warnung: Die Angabe einer E-Mail-Adresse gemäß RFC 5322,RFC 1034 oder RFC 1035 wird empfohlen (z.B. verwaltungXY@deutschland.de).
* [F] Wenn der Eintrag nicht der CodeList CI_RoleCode entstammt [4bi]: "Fehler: Der Wert für das Element role muss der CodeList CI_RoleCode entstammen."
* [F] Wenn der Eintrag nicht "pointOfContact" ist [4bii]: ": Fehler: Der Wert für das Element role muss "pointOfContact" sein.
* [W] Wenn Eintrag unter CI_RoleCode im codeList-Attribut nicht "http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_RoleCode" oder das codeList-Attribut nicht vorhanden ist [4c]: "Warnung: Gemäß INSPIRE TG Metadata wird empfohlen, im CI_RoleCode-Element das codeList-Attribut mit der URL "http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_RoleCode" anzugeben."

**XPath:**
- `MD_Metadata/contact/CI_ResponsibleParty/organisationName`
- `MD_Metadata/contact/CI_ResponsibleParty/contactInfo/CI_Contact/address/CI_Address/electronicMailAddress`
- `MD_Metadata/contact/CI_ResponsibleParty/role/CI_RoleCode`

**Referenzen:**	
* [AK MD] Abschnitt 2.5
* [INS TG MD] 2.2.3
* [ISO 19115] B.3.2.1 No. 374

**Test type:** Automatisch

**Notizen:**
Beispiel

```
<gmd:contact>
  <gmd:CI_ResponsibleParty>
    <gmd:organisationName>
      <gco:CharacterString>Verwaltung XY</gco:CharacterString>
    </gmd:organisationName>
    ...
    <gmd:contactInfo>
      <gmd:CI_Contact>
        ...
        <gmd:address>
          <gmd:CI_Address>
            ...
            <gmd:electronicMailAddress>
              <gco:CharacterString>verwaltungXY@deutschland.de</gco:CharacterString>
            </gmd:electronicMailAddress>
          </gmd:CI_Address>
        </gmd:address>
        ...
      </gmd:CI_Contact>
    </gmd:contactInfo>
    <gmd:role>
      <gmd:CI_RoleCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_RoleCode" 
      codeListValue="pointOfContact"/>
    </gmd:role>
  </gmd:CI_ResponsibleParty>
</gmd:contact>
```

**Konformitätsklasse:** GDI-DE (M - verpflichtend)
