[:point_left: zurük zur Übersicht](README.md)

Aufgabe 2 - Kartenlayer hinzufügen
=====================================================

Created by con terra GmbH

In den folgenden Schritten lernen Sie, wie Sie einen neuen Kartenlayer der App hinzufügen.

1.  Öffnen Sie den App-Editor der App "Krankenhäuser in Hamburg". Dazu wählen Sie zuerst die App aus der App Liste im map.apps Manger per Mausklick aus.
2.  Im Dialog nachfolgenden Dialog wählen Sie den "App-Editor"-Button aus.
3.  Ein Editor geöffnet, der die Datei app.json vorausgewählt hat.
4.  Scrollen Sie nun zu dem Abschnitt "map-init".
5.  Fügen Sie nun das unten stehende Code-Sniplet unter Layer ein
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
"map": {
    "layers": [
            {
               "id": "krankenhaeuser",
                "url": "https://services2.arcgis.com/jUpNdisbWqRpMo35/ArcGIS/rest/services/HH_Krankenh%c3%a4user_2016/FeatureServer/0",
                "title": "Krankenhäuser",
                "type": "AGS_FEATURE"
            },
```
6.  Klicken Sie auf den "Vorschau anzeigen"-Button. Die Anwendung wird gestarten und die Krankenhäuser von Hamburg erscheinen auf der Karte.

