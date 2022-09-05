[:point_left: zurük zur Übersicht](README.md)

Aufgabe 7 - Karteninhalte hinzufügen
=======================================================

Created by con terra GmbH

In dieser Übung ändern sie die Darstellung des zuletzt hinzugefügten ArcGIS Feature Service.

1. Fügen Sie dem Layer das "renderer" Attribut hinzu. Dokumentationen, welche Möglichkeiten zur Darstellung es gibt finden Sie hier: 
* [Dokumentation Feature Layer](https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-FeatureLayer.html#renderer) 
* [Dokumentation Symbole](https://developers.arcgis.com/javascript/latest/api-reference/esri-symbols-Symbol.html)

**app.json**

``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
"map": {
    "layers": [
            {
                            "id": "krankenhuser",
                            ...
                        },
                        {
                            "id": "schulen",
                            "url": "https://services2.arcgis.com/jUpNdisbWqRpMo35/ArcGIS/rest/services/Hamburg_Schulen/FeatureServer/0",
                            "type": "AGS_FEATURE",
                            "title": "Schulen",
                            "outFields": [
                                "*"
                            ],
                            "renderer": {
                                "type": "simple",
                                "symbol": {
                                    "type": "simple-marker",
                                    "size": 6,
                                    "color": "green",
                                    "outline": {
                                        "width": 0.5,
                                        "color": "white"
                                    }
                                }
                            }
                        }
```

Hinweis

Die Reihenfolge der Layer-Konfiguration bestimmt auch die Zeichenreihenfolge in der Karte (unten stehende Layer werden unter anderen Layern in der Karte dargestellt).

