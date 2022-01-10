[:point_left: zurük zur Übersicht](README.md)

Aufgabe 6 - Popups gestalten
===============================================

Created by con terra GmbH

In dieser Übung lernen Sie, wie sie Informationen zu einem Objekt in Popups anpassen können.

1. Fügen Sie eine "popupTemplate" Definition zur Layer-Konfiguration hinzu, wie im folgenden Beispiel dargestellt:

   **app.json**

   ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
   ...

   "layers": [
     {
        "id": "krankenhaeuser",
        "url": "https://services2.arcgis.com/jUpNdisbWqRpMo35/ArcGIS/rest/services/HH_Krankenh%c3%a4user_2016/FeatureServer/0",
        "type": "AGS_FEATURE",
        "title": "Krankenhäuser",
        "description": "Krankenhäuser_Points",
        "visible": true,
        "popupTemplate": {
           "title": "{name}",
           "content": [
              {
                 "type": "text",
                 "text": "Dieses Krankenhaus verfügt über {anzahl_pla} Betten und {anzahl_p_1} teilstationäre Behandlungsplätze."
              }
           ]
        }
     }
   ],

   ...
   ```

   Hinweis:

   Wie im Beispiel zu sehen, können Attribute des jeweiligen Layers referenziert werden, indem Sie in geschweiften
   Klammern aufgerufen werden.

2. Fügen Sie nun eine Tabelle in Ihr Popup ein, indem Sie folgende Konfiguration wählen:

   **app.json**

   ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
   ...

   "layers": [
     {
        "id": "krankenhaeuser",
        "url": "https://services2.arcgis.com/jUpNdisbWqRpMo35/ArcGIS/rest/services/HH_Krankenh%c3%a4user_2016/FeatureServer/0",
        "type": "AGS_FEATURE",
        "title": "Krankenhäuser",
        "description": "Krankenhäuser_Points",
        "visible": true,
        "popupTemplate": {
           "title": "{name}",
           "content": [
              {
                 "type": "text",
                 "text": "Dieses Krankenhaus verfügt über {anzahl_pla} Betten und {anzahl_p_1} teilstationäre Behandlungsplätze."
              },
              {
                 "type": "fields",
                 "fieldInfos": [{
                               "fieldName": "strasse",
                               "label": "Straße"
                           }, {
                               "fieldName": "ort",
                               "label": "Ort"
                           }, {
                               "fieldName": "homepage",
                               "label": "Homepage"
                           }, {
                               "fieldName": "krankenhau",
                               "label": "Details im Krankenhausverzeichnis"
                           }]
              }
           ]
        }
     }
   ],

   ...
   ```

   Die verschiedenen Content-Typen können beliebig oft und in beliebiger Reihenfolge verwendet werden. Abschließend
   möchten wir noch die Darstellung der Attachments hinzufügen.

3. Fügen Sie ein Objekt vom Typ "attachments" zu Ihrer Konfiguration hinzu. Die fertige Konfiguration sollte so
   aussehen:

   **app.json**

   ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
   ...

   "layers": [
     {
        "id": "krankenhaeuser",
        "url": "https://services2.arcgis.com/jUpNdisbWqRpMo35/ArcGIS/rest/services/HH_Krankenh%c3%a4user_2016/FeatureServer",
        "type": "AGS_FEATURE",
        "title": "Krankenhäuser",
        "description": "Krankenhäuser_Points",
        "visible": true,
        "popupTemplate": {
           "title": "{name}",
           "content": [
              {
                 "type": "text",
                 "text": "Dieses Krankenhaus verfügt über {anzahl_pla} Betten und {anzahl_p_1} teilstationäre Behandlungsplätze."
              },
              {
                 "type": "fields",
                 "fieldInfos": [
                    {
                       "fieldName": "adresse",
                       "label": "Adresse"
                    },
                    {
                       "fieldName": "ort",
                       "label": "Ort"
                    },
                    {
                       "fieldName": "telefon",
                       "label": "Telefon"
                    },
                    {
                       "fieldName": "homepage",
                       "label": "Homepage"
                    },
                    {
                       "fieldName": "link_einze",
                       "label": "Details im Krankenhausverzeichnis"
                    }
                 ]
              },
              {
                 "type": "attachments"
              }
           ]
        }
     }
   ],

   ...
   ```

Ergebnis
--------

Es wird ein angepasstes Popup dargestellt mit individuellen und ausgewählten Attributnamen sowie der Darstellung von
Dateianhängen.


