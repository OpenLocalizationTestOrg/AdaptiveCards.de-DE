---
title: Text Features
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: f7ea40b80df4d976c0a8a86b15254018fdf2fac6
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732672"
---
# <a name="text-features"></a>Text Features

`TextBlock`bietet einige erweiterte Funktionen zum Formatieren und Lokalisieren des Texts.

## <a name="markdown"></a>Markdown
Um Inline Markup zu unterstützen, unterstützen Adaptive Karten eine **Teilmenge** der markdownsyntax.

_Unterstützt_

| Textstil      | Markdown |
|-----------------|-----|
| **Fett**        | ```**Bold**``` |
| _Kursiv_        | ```_Italic_``` |
| Aufzählungs Liste     | ```- Item 1\r- Item 2\r- Item 3``` | 
| Nummerierte Liste   | ```1. Green\r2. Orange\r3. Blue``` |
| Links      | ```[Title](url)``` |

_Nicht unterstützt_

* Header
* Tabellen
* Bilder
* Alles, was nicht in der obigen Tabelle angegeben ist

### <a name="markdown-example"></a>Markdown-Beispiel

Die folgende Nutzlast würde etwa wie folgt aussehen:

![markdown-Bildschirmfoto](media/text-features/markdown.png)

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a>Datums-/Uhrzeitformatierung und Lokalisierung

Manchmal wissen Sie nicht, dass die Zeitzone des Benutzers, der die Karte empfängt, angezeigt wird `DATE()` , `TIME()` daher bieten Adaptive Kartenfunktionen und Formatierungsfunktionen zum automatischen lokalisieren der Zeit auf dem Zielgerät.

### <a name="datetime-example"></a>Datums-/Uhrzeit-Beispiel

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Your package will arrive on {{DATE(2017-02-14T06:00:00Z, SHORT)}} at {{TIME(2017-02-14T06:00:00Z)}}",
            "wrap": true
        }
    ]
}
```

Die obige Karte wird angezeigt: 

> **Ihr Paket wird am Dienstag, 14. Februar, 2017 um 6:00 Uhr eintreffen.**

### <a name="datetime-function-rules"></a>Datums-/uhrzeitfunktionsregeln

Es gibt einige Regeln, mit denen die Datums-/Uhrzeitfunktionen auf allen Plattformen ordnungsgemäß interpretiert werden können. Wenn die Regeln nicht erfüllt sind, wird die unformatierte Zeichenfolge für den Benutzer angezeigt, und niemand möchte dies.

1. beachten Sie (muss alle Caps sein)
1. Es sind **keine Leerzeichen** zwischen den `{{`Klammern, `}}`oder enthalten.
1. **Strikte [RFC 3389](https://tools.ietf.org/html/rfc3339) -Formatierung** (Siehe Beispiele unten)
1. **Muss** ein gültiges Datum und eine gültige Uhrzeit sein

### <a name="valid-formats"></a>Gültige Formate

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a>Datums Formatierungs Parameter

Für Datumsangaben kann ein optionaler Parameter angegeben werden, um die Ausgabe zu formatieren.


|       Format        |            Beispiel            |
|---------------------|-------------------------------|
| `COMPACT`Vorgegebene |          "2/13/2017"          |
|       `SHORT`       |     "Mon, 13. Feb, 2017"     |
|       `LONG`        | "Montag, 13. Februar, 2017" |

