---
title: JavaScript SDK für Adaptive Karten
author: matthidinger
ms.author: mahiding
ms.date: 07/26/2019
ms.topic: article
ms.openlocfilehash: 4ddff841ec073c60a8aa6184f309e94052cb002d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732552"
---
# <a name="javascript-sdk-for-creating-cards"></a>JavaScript SDK zum Erstellen von Karten

> [!IMPORTANT]
> Die Bibliothek für die Serialisierung von JSON befindet sich noch in der Entwicklung, und ihre miterlage kann variieren.

Wie in den ersten Schritten [Getting Started](../../authoring-cards/getting-started.md)beschrieben, ist eine Adaptive Karte nichts anderes als ein serialisiertes JSON-Objekt eines Karten Objektmodells.  Um das Bearbeiten des Objektmodells zu vereinfachen, haben wir einige Bibliotheken definiert, die eine stark typisierte Klassenhierarchie definieren, die einfach serialisieren/deserialisieren von JSON-Code ist.

Sie können ein beliebiges Tool verwenden, mit dem Sie den JSON-Code für die Adaptive Karte erstellen möchten.

Das `adaptivecards` NPM-Paket definiert eine Bibliothek zum Arbeiten mit adaptiven Karten in JavaScript.

## <a name="to-install"></a>So installieren Sie
```console
npm install adaptivecards
```

## <a name="example"></a>Beispiel

Die folgende API zeigt, wie Sie eine Adaptive Karte mithilfe des Objektmodells erstellen und in JSON Serialisieren.

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);

let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";

card.addItem(textBlock);

let json = card.toJSON();
```
