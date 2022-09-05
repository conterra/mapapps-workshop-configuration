[:point_left: zurük zur Übersicht](README.md)

Aufgabe 9 - Räumliche Auswahl / Selektion aktivieren
=======================================================================

Created by con terra GmbH

In dieser Übung lernen Sie eine räumliche Selektion auf alle ArcGIS Feature Layer (Rechteck, Punkt, Polygon)  zu konfigurieren.
Um automatisch alle Layer, die in einer App verwendet werden zur räumlichen Auswahl zur Verfügung zu stellen, kann die sog. **`AutoStoreRegistrierung`**verwendet werden.

1.  Ergänzen Sie dazu in der Konfiguration folgende Option:

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    "agssearch": {
        "AutoStoreRegistration": {
            "componentEnabled": true,
            "useIn": ["selection"]
        },
        "AGSStore": [
        ...
    ```

2.  Um eine doppelte Auflistung der Krankenhäuser zu vermeiden, entfernen Sie außerdem den Eintrag "`selection`" aus der AGSStore Registrierung der Krankenhäuser. Die fertige Konfiguration sollte wie folgt aussehen:

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    "agssearch": {
        "AutoStoreRegistration": {
            "componentEnabled": true,
            "useIn": ["selection"]
        },
        "AGSStore": [{
            "id": "kkh",
            "layerId": "krankenhaeuser",
            "fetchIdProperty": true,
            "title": "Krankenhäuser",
            "useIn": ["omnisearch"],
            "description": "Suche nach Krankenhäusern",
            "omniSearchDefaultLabel": "Krankenhaus suchen...",
            "omniSearchLabelAttr": "${name}",
            "omniSearchSearchAttr": "name"
        }]
    }
    ```

3.  Ergänzen Sie folgende zwei Bundles, um die Auswahl-Funktion zur Verfügung zu stellen:

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    {
       "load": {
          "allowedBundles": [
             "selection-resultcenter",
             "selection-ui",
            ...
    ```

4.  Nun müssen sie noch das passende Selektionswerkzeug in der App bereit stellen. Dazu fügen Sie im Abschnitt `tools `der "`drawer_left`" Werkzeugleiste das "`selection-ui-tool`" hinzu. Das Werkzeug ist nun im Drawer Menu verstandortet.

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
     "toolset": {
             "ToolsetManager": {
                "toolsets": [
    ...


            {
                      "id": "drawer_left",
                      "title": "Werkzeuge",
                      "cssClass": "ct-main-app-menu",
                      "registerWidget": {
                         "widgetRole": "drawer_button"
                      },
                      "container": "ignore",
                      "windowType": "drawer_left",
                      "window": {
                         "closable": false
                      },
                      "__isDirty": true,
                      "position": {
                         "rel_l": 0,
                         "rel_t": 0
                      },
                      "tools": [
                         "printingToggleTool",
                         "sharelinkTool",
                         "selection-ui-tool"
                      ]
                   }
    ]
    },


    ...
    ```

5.  Speichern Sie die Konfiguration und starten Sie die App neu.

