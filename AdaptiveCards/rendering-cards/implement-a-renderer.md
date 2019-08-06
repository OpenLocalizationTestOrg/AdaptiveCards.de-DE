---
title: Implementieren eines Renderers
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: 607ce40e70e0e54e61a572853a521d2dd70a5c23
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732612"
---
# <a name="adaptive-card-renderer-specification"></a>Spezifikation für adaptiver Karten-Renderer

In der folgenden Spezifikation wird beschrieben, wie ein adaptiver Karten-Renderer auf jeder UI-Plattform implementiert wird.

> [!IMPORTANT]
> 
> Dieser Inhalt ist noch nicht abgeschlossen. Überprüfen Sie es in Kürze.

## <a name="sdk-versioning"></a>SDK-Versionsverwaltung

1. Die Haupt-und neben Version des SDKs `schema` sollten der Version entsprechen. 
1. Patch/Build **sollte** für rendererupdates verwendet werden, die keine Schema Änderungen aufweisen.

## <a name="parsing-json"></a>JSON-JSON

### <a name="error-conditions"></a>Fehlerbedingungen
1. Ein Parser **muss** prüfen, ob es sich um gültige JSON-Inhalte handelt.
1. Ein Parser **muss** anhand des Schemas (erforderliche Eigenschaften usw.) überprüft werden.
1. Die obigen Fehler **müssen** der Host-app (Ausnahme oder Äquivalent) gemeldet werden.

### <a name="unknown-types"></a>Unbekannte Typen
1. Wenn Unbekannte "Typen" gefunden werden, müssen Sie aus dem Ergebnis **gelöscht werden** .
1. Alle Änderungen an der Nutzlast (wie oben) **sollten** als Warnungen an die Host-App gemeldet werden.

### <a name="unknown-properties"></a>Unbekannte Eigenschaften
1. Ein Parser **muss** **zusätzliche** Eigenschaften für Elemente enthalten.

### <a name="additional-considerations"></a>Weitere Überlegungen
1. Die `speak` -Eigenschaft kann SSML-Markup enthalten und **muss** wie angegeben an die Host-App zurückgegeben werden.

## <a name="parsing-host-config"></a>Die Host Konfiguration wird verarbeitet.
1. TODO

## <a name="versioning"></a>Versionskontrolle

1. Ein Renderer **muss** eine bestimmte Version des Schemas implementieren. 
1. Der `AdaptiveCard` Konstruktor **muss** der `version` Eigenschaft basierend auf der aktuellen Schema Version einen Standardwert zuordnen. 
1. Wenn ein Renderer auf eine `version` Eigenschaft in der `AdaptiveCard` trifft, die höher als die unterstützte Version ist, muss `fallbackText` er stattdessen den zurückgeben.

## <a name="rendering"></a>Rendern

Ein `AdaptiveCard` besteht aus einem `body` und `actions`. Der `body` ist eine Auflistung von `CardElement`s, die ein Renderer in der Reihenfolge aufzählt und renderert. 

1. Jedes Element **muss** sich auf die Breite seines übergeordneten Elements ( `display: block` in HTML-Code) ausdehnen.
1. Ein Renderer **muss** unbekannte Elementtypen ignorieren und das Rendering der restlichen Nutzlast fortsetzen.

### <a name="spacing-and-separators"></a>Abstände und Trennzeichen

1. Die `spacing` -Eigenschaft für jedes Element wirkt sich auf die Menge des Speicherplatzes zwischen dem aktuellen und dem **aktuellen** Element aus.
1. Der Abstand **darf nur** angewendet werden, wenn ein Element vorangestellt ist. (Z. b. gilt nicht für das erste Element in einem Array)
1. Ein Renderer **muss** den zu verwendenden Speicherplatz aus dem `hostConfig` Abstand für den Enumerationswert nachschlagen, der auf das aktuelle Element angewendet wird.
1. Wenn das-Element den `separator` `true`Wert hat, **muss** eine sichtbare Linie zwischen dem aktuellen Element und dem Element vor dem Element gezeichnet werden.
1. Die Trennlinie **muss** mit `container.style.default.foregroundColor`gezeichnet werden.
1. Ein Trennzeichen **darf nur** gezeichnet werden, wenn **es sich** bei dem Element nicht um das erste Element im Array handelt.

### <a name="columns"></a>Spalten

1. `Column`Muss durch "Auto", "Stretch" oder ein gewichtetes Verhältnis interpretiert werden. `width`

### <a name="textblock"></a>TextBlock

1. Ein TextBlock **muss** eine einzelne Zeile annehmen, es sei `wrap` denn, `true`die-Eigenschaft ist. 
1. Der TextBlock **muss** überzähligen Text mit Auslassungs Zeichen (...) kürzen.

#### <a name="markdown"></a>Markdown

1. Adaptive Karten ermöglichen eine Teilmenge von markdown und **sollten** in `TextBlock`unterstützt werden. 
1. Vollständige [markdown-Anforderungen](../authoring-cards/text-features.md)

#### <a name="formatting-functions"></a>Formatierungsfunktionen

1. `TextBlock`ermöglicht [Formatierungsfunktionen für Datum/Uhrzeit](../authoring-cards/text-features.md) , die für jeden Renderer unterstützt werden **müssen** .
1. **Alle Fehler müssen** die rohzeichenfolge in der Karte anzeigen. Es wurde keine benutzerfreundliche Nachricht versucht. (Das Ziel, den Entwickler sofort zu beachten, dass ein Problem vorliegt)

1. TODO: Regex einschließen

### <a name="images"></a>Bilder

1. Mit einem Renderer können Host-apps erkennen, wann alle http-Images heruntergeladen wurden und die Karte vollständig gerendert wird.
1. Ein Renderer **muss** beim Herunterladen von `maxImageSize` http-Images den Host Konfigurationsparameter überprüfen.
1. Ein Renderer **muss** und `.png` unterstützen.`.jpeg`
1. Ein Renderer **sollte** Bilder `.gif` unterstützen.

### <a name="host-config"></a>Host Konfiguration

* TODO: Wie lauten die Standardwerte? Sollten Sie alle diese freigeben? Sollte eine gängige hostconfig. JSON-Datei in die Binärdateien eingebettet werden?
* TODO: Ich denke, die hostconfig muss mit Versions Angabe versehen werden, um die Verarbeitung zu übernehmen?

[`HostConfig`](host-config.md)ein frei gegebenes Konfigurationsobjekt, das angibt, wie ein adaptiver Karten-Renderer eine Benutzeroberfläche generiert.  

Dadurch können Eigenschaften, die plattformunabhängig sind, von rendererarbeitern auf verschiedenen Plattformen und Geräten gemeinsam genutzt werden. Außerdem können Tools erstellt werden, die Ihnen eine Vorstellung davon vermitteln, dass diese Karte für eine bestimmte Umgebung vorhanden wäre.

1. Renderer **müssen** einen **Host Konfigurations** Parameter zum Hosten von apps verfügbar machen.
1. Alle Elemente **müssen** entsprechend ihren jeweiligen Host Konfigurationseinstellungen formatiert werden.

### <a name="native-platform-styling"></a>Native Platt Form Formatierung

1. Jeder Elementtyp **sollte** mit dem generierten UI-Element einen nativen Platt Form Stil anfügen. Beispiel: in HTML haben wir den Elementtypen eine CSS-Klasse hinzugefügt, und in XAML weisen wir einen bestimmten Stil zu.

## <a name="extensibility"></a>Erweiterungen 

1. Ein Renderer **muss** zulassen, dass Host-apps standardmäßige Element-Renderer überschreiben. Ersetzen `TextBlock` Sie z. b. Rendering durch ihre eigene Logik.
1. Ein Renderer **muss** es Host-apps ermöglichen, benutzerdefinierte Elementtypen zu registrieren. Fügen Sie beispielsweise Unterstützung für ein `Rating` benutzerdefiniertes Element hinzu.
1. Ein Renderer **muss** es Host-apps ermöglichen, die Unterstützung für ein Standardelement zu entfernen. Entfernen `Action.Submit` Sie z. b., wenn diese nicht unterstützt werden sollen.

## <a name="actions"></a>Aktionen

1. Wenn hostconfig `supportsInteractivity` ist `false`, **darf** ein Renderer keine Aktionen Renren.
1. Die `actions` -Eigenschaft **muss** als Schaltflächen in einer Aktionsleiste gerendert werden, normalerweise am unteren Rand der Karte. 
1. Wenn eine Schaltfläche getippt wird, **muss** die Host-APP das Ereignis verarbeiten können. 
1. Das Ereignis **muss** alle zugeordneten Eigenschaften mit der Aktion übergeben.
1. Das Ereignis **muss** an der `AdaptiveCard` übergeben werden, die ausgeführt wurde.

Aktion | Verhalten
--- | ---
**Action.OpenUrl** | Öffnen einer externen URL zum Anzeigen
**Action.ShowCard** | Fordert an, dass dem Benutzer eine unter Karte angezeigt wird.
**Action.Submit** | Bitten Sie, alle Eingabeelemente in einem Objekt zu erfassen, das dann über eine Methode, die von der Host Anwendung definiert wird, an Sie gesendet wird.

### <a name="actionopenurl"></a>Action.OpenUrl
1. `Action.OpenUrl`Eine URL **muss** mithilfe des nativen Platt Form Mechanismus geöffnet werden.
1. Wenn dies nicht möglich ist, **muss** es ein Ereignis für die Host-App zum Verarbeiten des Öffnens der URL ausführen. Dieses Ereignis **muss** der Host-App ermöglichen, das Standardverhalten zu überschreiben. Beispielsweise können Sie die URL in ihrer eigenen APP öffnen.

### <a name="actionshowcard"></a>Action.ShowCard

1. `Action.ShowCard`**Muss** auf irgendeine Weise unterstützt werden, basierend auf der hostconfig-Einstellung. Es gibt zwei Modi: Inline und Popup. Inline Karten **sollten** die Karten Sichtbarkeit automatisch umschalten. Im Popup Modus **sollte** ein Ereignis für die Host-App ausgelöst werden, um die Karte auf irgendeine Weise anzuzeigen.

### <a name="actionsubmit"></a>Action.Submit

Die Submit-Aktion verhält sich wie ein HTML-Formular, mit dem Unterschied, dass der HTML-Code in der Regel eine HTTP Post-Methode auslöst 

1. Wenn dadurch ein Ereignis ausgelöst werden **muss** , tippt der Benutzer auf die aufgerufene Aktion.  
1. Die `data` -Eigenschaft **muss** in der Rückruf Nutzlast enthalten sein.
1. Für `Action.Submit` **muss** ein Renderer alle Eingaben auf der Karte erfassen und seine Werte abrufen. 

### <a name="selectaction"></a>selectAction

1. Wenn die Host `supportedInteractivity` Konfiguration `false` ist `selectAction` , **darf nicht** als Berührungs Ziel dargestellt werden.
1. `Image`, `ColumnSet`und `Column` bieten eine`selectAction` Eigenschaft, die ausgeführt werden **soll** , wenn der Benutzer Sie aufruft, z. b. durch Tippen auf das-Element.

## <a name="inputs"></a>Eingaben

1. Wenn hostconfig `supportsInteractivity` ein `false` Renderer ist, **darf** keine Eingaben gerbt werden.
2. Eingaben **sollten** mit der höchsten Genauigkeit gerbt werden. Beispielsweise `Input.Date` würde eine Datumsauswahl idealerweise einem Benutzer anbieten, aber wenn dies auf dem UI-Stapel nicht möglich ist, **muss** der Renderer auf das Rendern eines Standard Textfelds zurückgreifen.
3. Ein Renderer **sollte** nach Möglichkeit `placeholderText` die Anzeige anzeigen.
4. Ein Renderer muss die Überprüfung der Eingabe **nicht** implementieren. Benutzer von adaptiven Karten müssen planen, beliebige empfangene Daten auf Ihrem Ende zu validieren.
5. Eingabe Wert Bindung **muss** ordnungsgemäß mit Escapezeichen versehen werden

6. Das Objekt **muss** wie folgt an die Host-App zurückgegeben werden:

   Wir machen keine Zusagen der Eingabe Überprüfung in adaptiven Karten. Daher liegt es an der empfangenden Partei, die Antwort ordnungsgemäß zu analysieren. Beispielsweise kann eine Eingabe. Number "Hello" zurückgeben, und Sie müssen darauf vorbereitet werden.


## <a name="events"></a>Ereignisse

1. Ein Renderer **sollte** ein Ereignis auslösen, wenn sich die Sichtbarkeit eines Elements geändert hat, sodass die Host-APP einen Bildlauf zur Position durchführen kann.
