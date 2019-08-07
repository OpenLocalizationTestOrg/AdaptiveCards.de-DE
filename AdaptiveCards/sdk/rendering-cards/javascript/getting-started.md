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
# <a name="getting-started---javascript"></a><span data-ttu-id="2b54d-102">Getting Started (JavaScript)</span><span class="sxs-lookup"><span data-stu-id="2b54d-102">Getting started - JavaScript</span></span>

<span data-ttu-id="2b54d-103">Wie auf der Seite [Getting Started](../../../authoring-cards/getting-started.md) mit den ersten Schritten beschrieben, handelt es sich bei einer adaptiven Karte um ein JSON-serialisiertes Karten Objektmodell.</span><span class="sxs-lookup"><span data-stu-id="2b54d-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="2b54d-104">Dies ist ein JavaScript-SDK zum Erstellen von Client seitigem HTML im Browser.</span><span class="sxs-lookup"><span data-stu-id="2b54d-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b54d-105">**Wichtige Änderungen von v 0,5**</span><span class="sxs-lookup"><span data-stu-id="2b54d-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="2b54d-106">Paket umbenannt von `microsoft-adaptivecards` in`adaptivecards`</span><span class="sxs-lookup"><span data-stu-id="2b54d-106">Package renamed from `microsoft-adaptivecards` to `adaptivecards`</span></span>
> 1. <span data-ttu-id="2b54d-107">Der statische `AdaptiveCards.setHostConfig()` wurde zu einem Instanzmember von `AdaptiveCard`verschoben.</span><span class="sxs-lookup"><span data-stu-id="2b54d-107">The static `AdaptiveCards.setHostConfig()` has been moved to an instance member of `AdaptiveCard`.</span></span> <span data-ttu-id="2b54d-108">E.g., `myCard.hostConfig = {}`</span><span class="sxs-lookup"><span data-stu-id="2b54d-108">E.g., `myCard.hostConfig = {}`</span></span> 
> 1. <span data-ttu-id="2b54d-109">`HostConfig`Es sind jedoch verschiedene Umbenennungen und Verschiebungen aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="2b54d-109">`HostConfig` has gone though various renames and moves.</span></span> <span data-ttu-id="2b54d-110">Siehe " [Sample. JSON](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) Host config" für die aktuelle Struktur</span><span class="sxs-lookup"><span data-stu-id="2b54d-110">See the [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) Host Config for current structure</span></span>
> 1. <span data-ttu-id="2b54d-111">Es gibt auch einige Schema Änderungen aus der v 0.5-Vorschau, die [hier beschrieben](https://github.com/Microsoft/AdaptiveCards/pull/633) werden.</span><span class="sxs-lookup"><span data-stu-id="2b54d-111">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>
> 1. <span data-ttu-id="2b54d-112">Die statische `renderCard()` Funktion wurde entfernt, da Sie mit den Klassen Methoden redundant war.</span><span class="sxs-lookup"><span data-stu-id="2b54d-112">The static `renderCard()` function was removed as it was redundant with the class methods.</span></span> <span data-ttu-id="2b54d-113">Verwenden `adaptiveCard.render()` Sie, wie unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2b54d-113">Use `adaptiveCard.render()` as described below.</span></span> 


## <a name="install"></a><span data-ttu-id="2b54d-114">Installieren</span><span class="sxs-lookup"><span data-stu-id="2b54d-114">Install</span></span>

### <a name="node"></a><span data-ttu-id="2b54d-115">Knoten</span><span class="sxs-lookup"><span data-stu-id="2b54d-115">Node</span></span>

<span data-ttu-id="2b54d-116">[![NPM-Installation](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="2b54d-116">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards --save
```

### <a name="cdn"></a><span data-ttu-id="2b54d-117">CDN</span><span class="sxs-lookup"><span data-stu-id="2b54d-117">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="2b54d-118">Verwendung</span><span class="sxs-lookup"><span data-stu-id="2b54d-118">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="2b54d-119">Importieren des Moduls</span><span class="sxs-lookup"><span data-stu-id="2b54d-119">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="2b54d-120">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="2b54d-120">Next steps</span></span>

<span data-ttu-id="2b54d-121">Die nächsten Schritte finden Sie unter [Rendering a Card](render-a-card.md) !</span><span class="sxs-lookup"><span data-stu-id="2b54d-121">See [Render a card](render-a-card.md) for the next steps!</span></span>
