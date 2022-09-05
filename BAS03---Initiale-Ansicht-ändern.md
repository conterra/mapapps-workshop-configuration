[:point_left: zurük zur Übersicht](README.md)

Aufgabe 3 - Initiale Ansicht ändern
======================================================

Created by con terra GmbH

In den folgenden Schritten wird ihnen gezeigt, wie Sie die Initiale Kartenansicht der App ändern.

1.  Öffnen Sie den App-Editor der App "Krankenhäuser in Hamburg". Dazu wählen Sie zuerst die App aus der App Liste im map.apps Manger per Mausklick aus.
2.  Im Dialog nachfolgenden Dialog wählen Sie den "App-Editor"-Button aus.
3.  Ein Editor geöffnet, der die Datei app.json vorausgewählt hat.
4.  Ändern Sie im map-init Bundle unter view den extent, sodass die Karte initial einen Ausschnitt aus Hamburg zeigt. 
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
"view": {
           "viewmode": "2D",
           "extent": {
                 "xmin": 1085568.0513,
                 "ymin": 7057509.4268,
                 "xmax": 1143305.2772,
                 "ymax": 7114167.7032,
                 "spatialReference": 102100
                 }
           }
```

3.  Speichern Sie den festgelegten Raumausschnitt im Dialog über den "Speichern"-Button ab.
4.  Klicken Sie erneut auf "App-Vorschau".

