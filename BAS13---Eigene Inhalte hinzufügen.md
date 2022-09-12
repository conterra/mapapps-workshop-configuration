[:point_left: zurük zur Übersicht](README.md)


Augabe 14 - Eigene Inhalte hinzufügen
========================================================

Created by con terra GmbH

Die folgenden Schritte beschreiben wie sie eigene Inhalte einer App hinzufügen.

1.  Starten Sie den "App Editor.
      
    
2.  Fügen Sie in der app.json im Abschnitt allowedBundles das "custominfo" Bundle hinzu und speichern die app.json mit dem "Speichern"- Button.
    
    **app.json**
    
    {
       "load": {
          "allowedBundles": \[
             "domains-system",
             "domain-basemaps",
             "custominfo",
    ....
    
3.  Fügen Sie nun im "bundles"-Abschnitt eine Konfiguration für das "custominfo" Bundle hinzu. 
4. Welche Möglichkeiten es für die Konfiguration gibt kann in der [Dokumentation](https://demos.conterra.de/mapapps/resources/jsregistry/root/custominfo/4.13.1/README.md#b%3Dcustominfo%3Bv%3D4.13.1%3Bf%3Dcustom%3B) zu diesem Bundle nachgelesen werden.
    
5.  Erstellen Sie einen Inhalt vom Typ "Copyright". Wählen Sie für den Typ des Fensters "Link" und fügen folgenden Link ein: **`https://www.conterra.de/`** . 
6. Klicken Sie Abschließend den "Speichern"-Button. 
7. Laden Sie die App-Vorschau neu.

