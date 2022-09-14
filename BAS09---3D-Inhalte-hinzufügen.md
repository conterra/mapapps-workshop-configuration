[:point_left: zurük zur Übersicht](README.md)

Aufgabe 10 - 3D Inhalte hinzufügen
====================================================

Created by con terra GmbH

In dieser Übung soll ein Scene Layer zur App hinzugefügt werden, um in der 3D-Ansicht Gebäude in Hamburg darzustellen.

1.  Ergänzen Sie folgende Layer-Konfiguration in der App im Abschnitt map-init → layers:

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    {
        "id": "hh3d",
        "title": "3D-Gebäude (nur in 3D-Ansicht sichtbar)",
        "url": "https://tiles.arcgis.com/tiles/P3ePLMYs2RVChkJx/arcgis/rest/services/Buildings_Hamburg/SceneServer",
        "type": "AGS_SCENE"
    }
    ```

    Sobald ein Gebäude ein Krankenhaus- oder Schulen-Symbol überdeckt, wird das Symbol ausgeblendet. Dies führt zu einem unschönen Auftauchen und Verschwinden der Objekte, wenn man sich in der 3D-Szene bewegt. Um die Auffindbarkeit der Objekte zu verbessern, können diese mit einem Versatz zu den Gebäuden dargestellt werden.

2.  Ergänzen Sie folgende Informationen an den beiden Layern "krankenhaeuser" und "schulen":

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    ...
       "elevationInfo": {
            "mode": "relative-to-scene",
            "offset": 20
        }
    
    ...
    ```

    Hinweis

    Die Objekte werden nun immer relativ zur Szene, d.h. auf den Gebäuden dargestellt. Außerdem wird zusätzlich ein Versatz von 20 Metern eingefügt. Eine Übersicht zu den verfügbaren Parametern finden Sie hier: [https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-FeatureLayer.html\#elevationInfo](https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-FeatureLayer.html#elevationInfo)

3.  [In 3D-Szenen mit sehr vielen Objekten kann es vorkommen, dass sich die Symbole je nach Betrachtungswinkel stark überlagern und die Ansicht unübersichtlich und unaufgeräumt wirkt. Dies ist in unserem Beispiel nicht stark ausgeprägt, aber es soll dennoch gezeigt werden, wie dies verhindert werden kann. Fügen Sie dazu die folgende Konfiguration zum Krankenhäuser  und Notunterkünfte - Layer hinzu:
    ](https://developers.arcgis.com/javascript/latest/api-reference/esri-layers-FeatureLayer.html#elevationInfo)

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    ...
    "featureReduction": {
        "type": "selection"
    },
    ...
    ```

4.  Prüfen Sie ob das Attribut "ground": "world-elevation" innerhalb der map Definition in der app.json eingefügt ist. Dies sorgt für die Höhenunterschiede des Untergrunds.

    Die gesamte Kartenkonfiguration sollte nun wie folgt aussehen:

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    "map-init": {
        "Config": {
            "basemaps": [{
                "id": "topo",
                "title": "Topographisch",
                "basemap": "topo-vector"
            }, {
                "id": "gray",
                "title": "Hellgrauer Hintergrund",
                "basemap": "gray-vector",
                "selected": true
            }, {
                "id": "streets",
                "title": "Straßenkarte",
                "basemap": "streets-relief-vector"
            }],
            "map": {
                "layers": [{
                    "id": "krankenhaeuser",
                    "url": "https://services2.arcgis.com/jUpNdisbWqRpMo35/ArcGIS/rest/services/HH_Krankenh%c3%a4user_2016/FeatureServer/0",
                    "type": "AGS_FEATURE",
                    "title": "Krankenhäuser",
                    "outFields": ["*"],
                    "popupTemplate": {
                        "title": "{name}",
                        "content": [{
                            "type": "text",
                            "text": "Dieses Krankenhaus verfügt über {anzahl_planbetten} Betten und {anzahl_plaetze_teilstationaer} teilstationäre Behandlungsplätze."
                        }, {
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
                        }, {
                            "type": "attachments"
                        }]
                    },
                    "elevationInfo": {
                        "mode": "relative-to-scene",
                        "offset": 20
                    },
                    "featureReduction": {
                        "type": "selection"
                    }
                }, {
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
                    "featureReduction": {
                        "type": "selection"
                    }
                }, {
                    "id": "hh3d",
                    "title": "3D-Gebäude (nur in 3D-Ansicht sichtbar)",
                    "url": "https://tiles.arcgis.com/tiles/P3ePLMYs2RVChkJx/arcgis/rest/services/Buildings_Hamburg/SceneServer",
                    "type": "AGS_SCENE"
                }],
                "ground": "world-elevation"
            },
            "view": {
                "viewmode": "3D",
                "extent": {
                    "xmin": 1043064.5974291301,
                    "xmax": 1189823.691736472,
                    "ymin": 7062770.136241392,
                    "ymax": 7130493.343301968,
                    "spatialReference": 3857
                }
            }
        }
    },
    ```

5.  Um die Ansicht von 2D auf 3D umstellen zu können, muss hierfür das entsprechende Werkzeug in der App eingefügt werden.

    Fügen Sie, falls nicht vorhanden, das folgende Bundle zur App hinzu:

    **app.json**

    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    {
       "load": {
          "allowedBundles": [
             "viewmodeswitcher",
             ...
    ```

6.  Navigieren Sie nun durch die Szene und beobachten Sie, wie sich die Darstellung der Punkt-Symbole dynamisch verändert.

