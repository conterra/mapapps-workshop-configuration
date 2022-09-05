[:point_left: zurük zur Übersicht](README.md)

Aufgabe 5 - Suche hinzufügen
===============================================

Created by con terra GmbH

In dieser Übung lernen Sie, wie eine ArcGIS Server Suche der App hinzugefügt wird. Danach können Sie nach den Namen der Krankenhäuser suchen.

1.  Fügen Sie, falls noch nicht vorhanden, das Bundle agssearch zur neuen App in der `app.json` hinzu.

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    {
       "load": {
          "allowedBundles": [
              "agssearch",
    ...
    ```

2.  Fügen Sie im Abschnitt "bundles" der **`app.json`** folgenden Code in die Konfiguration ein.

    **agssearch**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    "agssearch": {
        "AGSStore": [{
            "id": "krankenhaus",
            "layerId": "krankenhaeuser",
            "fetchIdProperty": true,
            "title": "Krankenhäuser",
            "useIn": ["omnisearch", "selection"],
            "description": "Suche nach Krankenhäusern",
            "omniSearchDefaultLabel": "Krankenhaus suchen...",
            "omniSearchLabelAttr": "${name}",
            "omniSearchSearchAttr": "name"
        }],
    ...
    },
    ```

    Anschließend sieht die `app.json` wie folgt aus:

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    ...
       
    "bundles": {
          "agssearch": {
            "AGSStore": [
                {
                   "id": "krankenhaus",
                   "layerId": "krankenhaeuser",
                   "fetchIdProperty": true,
                   "title": "Krankenhäuser",
                   "useIn": [
                      "omnisearch",
                      "selection"
                   ],
                   "description": "Suche nach Krankenhäusern",
                   "omniSearchDefaultLabel": "Krankenhaus suchen...",
                   "omniSearchLabelAttr": "${name}",
                   "omniSearchSearchAttr": "name"
                }
             ],
            "AutoStoreRegistration": {
                "componentEnabled": true,
                "useIn": [
                    "selection"
                ]
            }
        },


    ...
    ```

3.  Speichern Sie die Konfiguration und laden Sie die App neu. Die Suche steht nun zur Verfügung.

Ergebnis
--------

Sie können nun in der App nach Krankenhäusern im Suchfeld suchen.


