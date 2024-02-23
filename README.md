# GDI+
Eine Sammlung von Tipps und Tricks zum Thema Grafikprogrammierung mit GDI+.

## Klassen / Ereignisse
### Timer
Ein Timer führt in regelmäßigen Abständen ein `Tick`-Event aus. Der [`System.Windows.Forms`.`Timer`](https://learn.microsoft.com/de-de/dotnet/api/system.windows.forms.timer?view=windowsdesktop-8.0&viewFallbackFrom=net-6.0) kann über die Toolbox auf die GUI gezogen werden. 

Anschließend können wir 
- die Zeit zwischen jedem `Tick`-Event einstellen (`+ Interval { get; set; }: int`) und
- den Timer starten (`+ Start():void`) oder
- stoppen (`+ Stop():void`) oder
- den Zustand abfragen. (`+ Enabled{ get; set; }: bool`) (Standard ist ausgeschaltet: `enabled = false`)



## Tipps und Tricks
Ergänzen Sie hier die notwendigen Code-Ausschnitte, um zu zeigen, wie man es macht. 
- Sie können [CodeBlöcke mit Syntax-Highlighting](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks#syntax-highlighting) einsetzen
- Wird es zu unübersichtlich? Sie können auch Unterordner mit Beispiel-Code anlegen und auf die entsprechenden Dateien verlinken. [Inspiration](https://github.com/gsoTH/flaskShowcase/tree/master/datenbanken).
- Die folgende Liste kann gerne ergänzt werden :)

### Bewegung animieren
Die Methode tmrGameTick_Tick ausgeführt. Der Spieler wird in einem If erstellt, wo gesagt wird, dass der GameTick noch nicht ausgeführt wurden ist. Das heißt der Spieler kann nur einmal erstellt werden.
Mit FillEllipse zeichnen wir den Spieler.

### Objekte mit Tasten steuern
Wir haben eine Methode für, wenn Tasten gedrückt werden. 
In der Methode checkt der welche Taste genau gedrückt wird.
Wenn die genaue Taste ausgeführt wird addiert oder subtrahiert man die Position des Spielers
```csharp
if (e.KeyCode == Keys.Down)
{
    if (currentline != 0)
    {
        spieler.Y = spieler.Y + hoeheJeBereich;
        currentline--;
    }
}
```

### Verhindern, dass ein Spieler aus dem Bild läuft
Um zu verhinder, dass der SPieler oberhalb oder unterhalbe des Spielfeld ist, benutzt man ein int currentline.
currentline zählt immer mit hoch oder runter, wenn der Spieler sich nach oben oder unten bewegt.
wenn currentline != 0 , dann kann der sich nach unten bewegen.
Das gleiche auch für oben.
wenn currentline != 4 (oberste Zeile im Spiel ist die fünfte Zeile), dann bewegt er sich nach oben

Damit der Spieler nicht seitwärts aus dem Bild läuft, habe ich statt wie im obrigen Text ein int, sondern die Koordinaten des Spielers benutzt.
Wenn die X-Position vom Spieler kleiner als 0 ist, dann kann er nicht weiter nach links laufen.
Wenn die Y-Position vom Spieler mehr ist als die vom Fenster, dann kann er nicht weiter nach rechts laufen.

### Spiel pausieren
Da das ganze Spiel auf einer Tickrate spielt, können wir die Tickrate auf 0 stellen.
Die alle Objekte brauchen einen Tick, um sich zu bewegen.
Der Spieler kann sich auch nicht bewegen, indem man noch eine Anforderung bei der Bewegen hinzufügt.
Wenn das Spiel zuende geht, soll ein boolean gameover auf true setzen.
Der If für nach oben bewegen wäre dann, wenn currentline !=4 && !gameover.
So kann man den Spieler nicht mehr bewegen lassen.

### Ihr schönstes Ergebnis





