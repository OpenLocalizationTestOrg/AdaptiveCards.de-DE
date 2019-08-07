---
title: JavaScript-SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 55360658d74ca384b0e6090631a7f5db463e968a
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732907"
---
# <a name="getting-started---javascript"></a>Getting Started (JavaScript)

Wie auf der Seite [Getting Started](../../../authoring-cards/getting-started.md) mit den ersten Schritten beschrieben, handelt es sich bei einer adaptiven Karte um ein JSON-serialisiertes Karten Objektmodell. Dies ist ein JavaScript-SDK zum Erstellen von Client seitigem HTML im Browser.

> [!IMPORTANT]
> **Wichtige Änderungen von v 0,5**
> 
> 1. Paket umbenannt von `microsoft-adaptivecards` in`adaptivecards`
> 1. Der statische `AdaptiveCards.setHostConfig()` wurde zu einem Instanzmember von `AdaptiveCard`verschoben. E.g., `myCard.hostConfig = {}` 
> 1. `HostConfig`Es sind jedoch verschiedene Umbenennungen und Verschiebungen aufgetreten. Siehe " [Sample. JSON](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) Host config" für die aktuelle Struktur
> 1. Es gibt auch einige Schema Änderungen aus der v 0.5-Vorschau, die [hier beschrieben](https://github.com/Microsoft/AdaptiveCards/pull/633) werden.
> 1. Die statische `renderCard()` Funktion wurde entfernt, da Sie mit den Klassen Methoden redundant war. Verwenden `adaptiveCard.render()` Sie, wie unten beschrieben. 


## <a name="install"></a>Installieren

### <a name="node"></a>Knoten

[![NPM-Installation](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)

```console
npm install adaptivecards --save
```

### <a name="cdn"></a>CDN

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a>Verwendung

### <a name="import-the-module"></a>Importieren des Moduls

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a>Nächste Schritte

Die nächsten Schritte finden Sie unter [Rendering a Card](render-a-card.md) !
