[:point_left: zurük zur Übersicht](README.md)

Aufgabe 7 - Karteninhalte hinzufügen
=======================================================

Created by con terra GmbH

In dieser Übung fügen Sie einen weiteren ArcGIS Feature Service der Anwendung hinzu.

1.  Fügen Sie einen weiteren Karten-Layer in der **`app.json`** zur App hinzu.

**app.json**

``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
"map": {
    "layers": [
            {
                "id": "krankenhuser"
                ...
            },
            {
                "id": "not",
                "url": "https://services2.arcgis.com/jUpNdisbWqRpMo35/ArcGIS/rest/services/HH_Notunterk%c3%bcnfte_2016/FeatureServer/0",
                "type": "AGS_FEATURE",
                "title": "Notunterkünfte",
                "outFields": ["*"]
            }
```

Hinweis

Die Reihenfolge der Layer-Konfiguration bestimmt auch die Zeichenreihenfolge in der Karte (unten stehende Layer werden unter anderen Layern in der Karte dargestellt).

