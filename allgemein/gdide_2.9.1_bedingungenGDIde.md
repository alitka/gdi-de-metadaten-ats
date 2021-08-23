**Ziel:** Prüfung auf Belegung des Elements MD_LegalConstraints/useConstraints

**Beschreibung:** Ein Metadatensatz muss immer eine Angabe über die Nutzungsbedingungen enthalten. Ggf. umfassen diese auch Zugangsbedingungen. Die Angaben werden als freie Texte erwartet. Für die Aussage, dass es keine Bedingungen gibt, ist ein Textmuster einzuhalten.

**Testmethode:**
1. Prüfe, ob die Sprache der Metadaten Deutsch ist (vergl. gdide_2.4_spracheMetadaten)
2. Wenn [1] zutrifft: Prüfe, ob genau ein Objekt MD_LegalConstraints existiert, das useConstraints-Elemente enthält.
3. Wenn [2] zutrifft: Prüfe, ob jedes useConstraints-Element ein Attribut codeListValue enthält, in dem ein Wert der MD_RestrictionCode ([ISO 19115], B.5.24) angegeben ist.
4. Wenn [3] zutrifft: Prüfe, ob innerhalb der Gruppe von useConstraints-Elementen im MD_LegalConstraints-Element genau einmal der Eintrag „otherRestrictions“ als codeListValue verwendet wurde.
5. Wenn [4] zutrifft: Prüfe, ob innerhalb des gleichen MD_LegalConstraints-Objekts dem Element useConstraints mit Codewert „otherRestrictions“ mindestens ein Element otherConstraints folgt, dessen Inhalt (als CharacterString oder in einem gmx:Anchor-Element) ungleich dem OpenData-Eintrag (umschlossen von {  } Zeichen, siehe 3.6 Nutzungsbedingungen und Lizenzinformationen für Open Data) ist.
6. Wenn [5] zutrifft: Prüfe, ob innerhalb des gleichen MD_LegalConstraints-Objekts dem Element useConstraints mit Codewert „otherRestrictions“ mehr als ein Element otherConstraints folgt, dessen Inhalt (als CharacterString oder in einem gmx:Anchor-Element) ungleich einem optional vorkommenden otherConstraints mit OpenData-Eintrag (umschlossen von {  } Zeichen, siehe 3.6 Nutzungsbedingungen und Lizenzinformationen für Open Data) ist.
7. Wenn [5] zutrifft: Prüfe für jedes gefundene Element otherConstraints [7a] bis [8] einzeln:
   - a. Prüfe, ob im otherConstraints-Elemente ein Eintrag existiert (bzw. nicht leer und nicht NULL ist.)
8. Wenn [7a] zutrifft: Prüfe, ob der Eintrag (als CharacterString oder in einem gmx:Anchor-Element) dem Text „Bedingungen unbekannt“ entspricht

**Fehlermeldungen/Warnungen:**
* [W] Wenn die Sprache der Metadaten nicht Deutsch ist [1]: "Warnung: Die Prüfung von konkreten Textinhalten kann nur auf Basis der Metadaten-Sprache „Deutsch“ erfolgreich durchgeführt werden. Beim vorliegenden Metadatensatz ist dies nicht gegeben, sodass daher die Prüfung zu diesem Abschnitt komplett ausgelassen wird. Die Erfüllung der Anforderungen ist somit nicht gewährleistet!"
* [F] Wenn kein MD_LegalConstraints-Objekt mit useConstraints-Elementen existiert [2]: "Fehler: Es muss genau ein MD_LegalConstraints-Objekt mit mindestens einem useConstraints-Element vorhanden sein. Das Element MD_LegalConstraints darf nicht leer sein. Sollten keine Bedingungen vorliegen, so ist dies mit "Es gelten keine Bedingungen" anzugeben."
* [F] Wenn mehr als ein MD_LegalConstraints-Objekt existiert, das useConstraints-Elemente beinhaltet [2]: „Fehler: Es wurden mehr als ein MD_LegalConstraints-Objekt mit useConstraints-Elementen gefunden. Die Angaben zu den Nutzungs- und ggf. Zugriffsbedingungen sind in genau einem MD_LegalConstraints-Objekt anzugeben.“
* [F] Wenn useConstraints-Elemente vorkommen, die keinen Codelisten-Wert aus MD_RestrictionCode enthalten [3]: "Fehler: In dem Element MD_LegalConstraints/useConstraints muss das Attribut codeListValue einen Wert aus der MD_RestrictionCode-Liste enthalten."
* [W] Wenn kein Codewert „otherRestrictions“ existiert [4]: "Warnung: Es wird empfohlen, die Nutzungs- und ggf. Zugriffsbedingungen als Freitext oder als Verweis (URL) zu dokumentieren. Dazu ist im useConstraints-Element der Codewert „otherRestrictions“ anzugeben und in dem nachfolgenden otherConstraints-Element diese Angabe einzutragen. Sollten keine Bedingungen vorliegen, so ist dies mit "Es gelten keine Bedingungen" anzugeben."
* [W] Wenn mehr als einmal der Codewert „otherRestrictions“ existiert [4]: "Warnung: Das useConstraints-Element mit dem Codewert „otherRestrictions“ kommt mehrfach vor.“
* [F] Wenn kein Element otherConstraints folgt [5]: "Fehler: Das Element otherConstraints existiert nicht. Sollten keine Bedingungen vorliegen, so ist dies mit "Es gelten keine Bedingungen" anzugeben."
* [F] Wenn außer dem OpenData-Eintrag kein Element otherConstraints folgt [5]: "Fehler: Das Element otherConstraints, das einen Eintrag ungleich dem OpenData-Eintrag enthält, existiert nicht."
* [W] Wenn zusätzlich zum OpenData-Eintrag mehr als ein Element otherConstraints folgt [6]: "Warnung: Das Element otherConstraints kommt zusätzlich zum OpenData-Eintrag mehrfach vor."
* [F] Wenn keines der otherConstraints-Elemente, die nicht JSON enthalten, einen Text enthält [7a]: "Fehler: Es fehlen Einträge im otherConstraints-Element. Sollten keine Bedingungen vorliegen, so ist dies mit "Es gelten keine Bedingungen" anzugeben."
* [W] Wenn der Freitext "Bedingungen unbekannt" existiert [8]: "Warnung: Die Angabe "Bedingungen unbekannt" sollte vermieden werden. Die Angaben zu den Nutzungs- und ggf. Zugriffsbedingungen sollten konkret sein. Liegen keine Nutzungsbedingungen vor, sollte "Es gelten keine Bedingungen" angegeben werden."

**XPath:** `MD_Metadata/identificationInfo[1]//resourceConstraints/MD_LegalConstraints/useConstraints`

**Referenzen:**
* [AK MD] Abschnitt 2.9.1
* [ISO 19115] B.5.24

**Test type:** Automatisch

**Notizen:**

Beispiel1

```
<gmd:resourceConstraints>
  <gmd:MD_LegalConstraints>
    <gmd:useConstraints>
      <gmd:MD_RestrictionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#MD_RestrictionCode" 
      codeListValue="otherRestrictions"/>
    </gmd:useConstraints>
    <gmd:otherConstraints>
      < gco:CharacterString>Es gelten die Lizenzbedingungen „Datenlizenz Deutschland - Namensnennung - Version 2.0“ bzw. 
      „dl-de/by-2-0” (https://www.govdata.de/dl-de/by-2-0) mit den dort geforderten Angaben zum Quellenvermerk. Als 
      Rechteinhaber und Bereitsteller ist „Land NRW“, sowie das Jahr des Datenbezugs in Klammern anzugeben. Beispiel für 
      Quellenvermerk: Land NRW (2017) Datenlizenz Deutschland - Namensnennung - Version 2.0 (www.govdata.de/dl-de/by-2-0).
      </gco:CharacterString>
    </gmd:otherConstraints>
  </gmd:MD_LegalConstraints>
</gmd:resourceConstraints>

```

Beispiel2

```
<gmd:resourceConstraints>
  <gmd:MD_LegalConstraints>
    <gmd:useConstraints>
      <gmd:MD_RestrictionCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#MD_RestrictionCode" 
      codeListValue="otherRestrictions"/>
    </gmd:useConstraints>
    <gmd:otherConstraints>
      < gco:CharacterString>Es gelten keine Bedingungen</gco:CharacterString>
    </gmd:otherConstraints>
  </gmd:MD_LegalConstraints>
</gmd:resourceConstraints>
```

**Konformitätsklasse:** GDI-DE (M - verpflichtend)
