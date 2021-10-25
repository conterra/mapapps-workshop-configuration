[:point_left: zurük zur Übersicht](README.md)

Augabe 11 - Arcade Expressions nutzen
========================================================

Created by con terra GmbH

In dieser Übung erfahren Sie, wie Sie mit Hilfe von Arcade Expressions Sachdaten am Client für die Ausgabe von Popups anpassen können.

In dem in unserer App genutzten Layer für die Darstellung der Krankenhäuser ([https://services2.arcgis.com/jUpNdisbWqRpMo35/ArcGIS/rest/services/HH_Krankenh%c3%a4user_2016/FeatureServer/0](https://services2.arcgis.com/jUpNdisbWqRpMo35/ArcGIS/rest/services/HH_Krankenh%c3%a4user_2016/FeatureServer/0)) gibt es zwei Attribute, die Detail-Auskünfte zu den Angeboten der Krankenhäuser liefern:

-   **`teilnahme_ `** (Informiert darüber, ob das KKH an der Herzinfarktversorgung teilnimmt)
-   **`geburtskli`**(Informiert darüber, ob dieses KKH eine Geburtshilfe-Station hat)

Die Felder sind jedoch nur mit numerischen Werten belegt, die der Anwender der App nicht verstehen kann. (1 bedeutet "ja").

Mit Hilfe von Arcade Expressions können die Werte entsprechend in verständliche Texte umgewandelt werden.

1.  Ergänzen Sie dazu folgende Konfiguration in Ihrer App:

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: js; gutter: false; theme: Confluence" data-theme="Confluence"}
    {
        "id": "krankenhaeuser",
        "url": "https://services2.arcgis.com/jUpNdisbWqRpMo35/ArcGIS/rest/services/HH_Krankenh%c3%a4user_2016/FeatureServer/0",
        "type": "AGS_FEATURE",
        "title": "Krankenhäuser",
        "outFields": ["*"],
        "elevationInfo": {
            "mode": "relative-to-scene",
            "offset": 20
        },
        "popupTemplate": {
            "title": "{name}",
            "content": [{
                "type": "text",
                  "text": "Dieses Krankenhaus verfügt über {anzahl_pla} Betten und {anzahl_p_1} teilstationäre Behandlungsplätze."
            }, {
                "type": "fields",
                "fieldInfos": [{
                    "fieldName": "adresse",
                    "label": "Adresse"
                }, {
                    "fieldName": "ort",
                    "label": "Ort"
                }, {
                    "fieldName": "telefon",
                    "label": "Telefon"
                }, {
                    "fieldName": "homepage",
                    "label": "Homepage"
                }, {
                    "fieldName": "link_einze",
                    "label": "Details im Krankenhausverzeichnis"
                }, {
                    "fieldName": "expression/herz"
                }, {
                    "fieldName": "expression/geburt"
                }]
            }, {
                "type": "attachments"
            }],
            "expressionInfos": [{
                "name": "herz",
                "expression": "IIf($feature.teilnahme_ == \"ja\", \"Wir versorgen Herzinfarkte\", \"Hier keine Herzinfarktversorgung\")",
                "title": "Teilnahme an der Herzinfarktversorgung"
            }, {
                "name": "geburt",
                "expression": "IIf($feature.geburtskli == \"ja\", \"Hier können Sie ihr Kind bekommen\", \"Wir haben keine Geburtenstation\")",
                "title": "Geburtshilfe"
            }]
        }
    }
    ```

