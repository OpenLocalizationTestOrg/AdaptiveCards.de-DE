---
title: Erste Schritte
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: c9a0ad07ba5fefbcdc35239591c02fe0720b5b66
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732652"
---
# <a name="getting-started"></a>Erste Schritte 

Eine Adaptive Karte ist ein JSON-serialisiertes Karten Objektmodell.

## <a name="adaptive-card-structure"></a>Adaptive Karten Struktur

Die grundlegende Struktur einer Karte lautet wie folgt:

* `AdaptiveCard`-Das Stamm Objekt beschreibt die adaptivecard selbst, einschließlich der Element Umgebung, ihrer Aktionen, der Art und Weise, wie Sie gesprochen werden soll, und der Schema Version, die zum Rendering erforderlich ist.
* `body`-Der Hauptteil der Karte besteht aus Bausteinen, die als `elements`bezeichnet werden. Elemente können in nahezu unendlichen Anordnungen zusammengesetzt werden, um viele Kartentypen zu erstellen. 
* `actions`-Viele Karten verfügen über eine Reihe von Aktionen, die ein Benutzer ausführen kann. Diese Eigenschaft beschreibt die Aktionen, die in der Regel in einer "Aktionsleiste" am unteren Rand gerendert werden.

### <a name="example-card"></a>Beispiel Karte

Diese Beispiel Karte enthält eine einzelne Textzeile, gefolgt von einem Bild.

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png"
        }
    ]
}
```

## <a name="type-property"></a>`Type` -Eigenschaft

Jedes-Element verfügt `type` über eine-Eigenschaft, die angibt, welche Art von Objekt es ist. Wenn Sie sich die obige Karte ansehen, sehen Sie, dass zwei Elemente vorhanden `TextBlock` sind: `Image`a und.

Alle adaptiven Kartenelemente werden **vertikal gestapelt** und **auf die Breite der übergeordneten** Elemente `display: block` (in HTML) erweitert. Sie können jedoch einen `ColumnSet` verwenden, um parallele Container Spalten zu erstellen.

## <a name="adaptive-elements"></a>Adaptive Elemente

Die grundlegendsten Elemente sind:

* **TextBlock** -fügt einen TextBlock mit Eigenschaften hinzu, um zu steuern, wie der Text aussieht.
* **Image** : Fügt ein Bild mit Eigenschaften hinzu, um zu steuern, wie das Bild aussieht.

## <a name="container-elements"></a>Container Elemente

Karten können auch Container enthalten, die eine Auflistung von untergeordneten Elementen anordnen.

* **Container** : definiert eine Auflistung von Elementen.
* **ColumnSet/Column** : definiert eine Auflistung von Spalten, wobei jede Spalte ein Container ist.
* **FactSet** -Container von Fakten
* **ImageSet** -Container von Bildern, damit die Benutzeroberfläche für eine Auflistung von Bildern die passende Fotogalerie Darstellung anzeigen kann.

## <a name="input-elements"></a>Eingabeelemente

Eingabeelemente ermöglichen es Ihnen, eine native Benutzeroberfläche zum Erstellen von einfachen Formularen anzufordern:

* **Input. Text** : Text Inhalt vom Benutzer erhalten
* **Input. Date** : ein Datum vom Benutzer erhalten.
* **Eingabe. Zeit** zum Zeitpunkt der Benutzereingabe
* **Input. Number** : eine Zahl vom Benutzer erhalten.
* **Input. choiceset** : Geben Sie dem Benutzer einen Satz von Optionen, und lassen Sie ihn auswählen.
* **Eingabe.** umschalten: Hiermit wird dem Benutzer eine einzige Auswahl zwischen zwei Elementen gewährt.

## <a name="actions"></a>Aktionen

Aktionen fügen der Karte Schaltflächen hinzu. Diese können eine Reihe von Aktionen durchführen, z. b. das Öffnen einer URL oder das Senden von Daten.

* **Action. OpenURL** : die Schaltfläche öffnet eine externe URL für die Anzeige.
* **Action. showcard** : fordert an, dass dem Benutzer eine unter Karte angezeigt wird.
* **Action. Submit** : bitten Sie, alle Eingabeelemente in einem Objekt zu erfassen, das dann über eine Methode, die von der Host Anwendung definiert wird, an Sie gesendet wird.

> **Beispiel für Action. Submit**: Mit Skype sendet eine Aktion. Submit eine bot Framework-bot-Aktivität zurück an den bot mit der **value** -Eigenschaft, die ein Objekt mit allen Eingabedaten enthält.

## <a name="learn-more"></a>Weitere Informationen

* [Beispiel Karten zur Inspiration durchsuchen](http://adaptivecards.io/samples/)
* Verwenden des [Schema-Explorers](http://adaptivecards.io/explorer) zum Durchsuchen der verfügbaren Elemente
* Erstellen einer Karte mithilfe der [interaktiven](http://adaptivecards.io/visualizer/) Schnellansicht
* Feedback zu Feedback [erhalten](http://adaptivecards.io/connect)
