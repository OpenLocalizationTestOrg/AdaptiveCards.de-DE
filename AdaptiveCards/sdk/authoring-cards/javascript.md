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
# <a name="javascript-sdk-for-creating-cards"></a><span data-ttu-id="36ef0-102">JavaScript SDK zum Erstellen von Karten</span><span class="sxs-lookup"><span data-stu-id="36ef0-102">JavaScript SDK for creating cards</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36ef0-103">Die Bibliothek für die Serialisierung von JSON befindet sich noch in der Entwicklung, und ihre miterlage kann variieren.</span><span class="sxs-lookup"><span data-stu-id="36ef0-103">The library for serializing JSON is still in development and your milage may vary.</span></span>

<span data-ttu-id="36ef0-104">Wie in den ersten Schritten [Getting Started](../../authoring-cards/getting-started.md)beschrieben, ist eine Adaptive Karte nichts anderes als ein serialisiertes JSON-Objekt eines Karten Objektmodells.</span><span class="sxs-lookup"><span data-stu-id="36ef0-104">As we described in the [Getting Started](../../authoring-cards/getting-started.md), an Adaptive Card is nothing more than a serialized JSON object of a card object model.</span></span>  <span data-ttu-id="36ef0-105">Um das Bearbeiten des Objektmodells zu vereinfachen, haben wir einige Bibliotheken definiert, die eine stark typisierte Klassenhierarchie definieren, die einfach serialisieren/deserialisieren von JSON-Code ist.</span><span class="sxs-lookup"><span data-stu-id="36ef0-105">To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.</span></span>

<span data-ttu-id="36ef0-106">Sie können ein beliebiges Tool verwenden, mit dem Sie den JSON-Code für die Adaptive Karte erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="36ef0-106">You can use any tooling that you want to create the adaptive card json.</span></span>

<span data-ttu-id="36ef0-107">Das `adaptivecards` NPM-Paket definiert eine Bibliothek zum Arbeiten mit adaptiven Karten in JavaScript.</span><span class="sxs-lookup"><span data-stu-id="36ef0-107">The `adaptivecards` npm package defines a library for working with adaptive cards in javascript</span></span>

## <a name="to-install"></a><span data-ttu-id="36ef0-108">So installieren Sie</span><span class="sxs-lookup"><span data-stu-id="36ef0-108">To install</span></span>
```console
npm install adaptivecards
```

## <a name="example"></a><span data-ttu-id="36ef0-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="36ef0-109">Example</span></span>

<span data-ttu-id="36ef0-110">Die folgende API zeigt, wie Sie eine Adaptive Karte mithilfe des Objektmodells erstellen und in JSON Serialisieren.</span><span class="sxs-lookup"><span data-stu-id="36ef0-110">The following API shows how to construct an Adaptive Card using the object model and serialize it to JSON.</span></span>

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);

let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";

card.addItem(textBlock);

let json = card.toJSON();
```
