---
title: 'Rendering einer Karte: .net html SDK'
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 0280e37506e1034572f518b1f596e8f1a3bb30be
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732812"
---
# <a name="render-a-card---net-html"></a><span data-ttu-id="e9e75-102">Rendering einer Karte: .net-html</span><span class="sxs-lookup"><span data-stu-id="e9e75-102">Render a card - .NET HTML</span></span>

<span data-ttu-id="e9e75-103">Im folgenden wird beschrieben, wie Sie eine Karte mithilfe des .net html SDK Rendering.</span><span class="sxs-lookup"><span data-stu-id="e9e75-103">Here's how to render a card using the .NET HTML SDK.</span></span>

## <a name="instantiate-a-renderer"></a><span data-ttu-id="e9e75-104">Instanziieren eines Renderers</span><span class="sxs-lookup"><span data-stu-id="e9e75-104">Instantiate a renderer</span></span>

<span data-ttu-id="e9e75-105">Der nächste Schritt ist das Erstellen einer Instanz des Renderers.</span><span class="sxs-lookup"><span data-stu-id="e9e75-105">The next step is to create an instance of the renderer.</span></span> 

```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Html;
// ... 

// Create a card renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// For fun, check the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion; // 1.0
```

## <a name="render-a-card-to-html"></a><span data-ttu-id="e9e75-106">Eine Karte in HTML-Code darstellen</span><span class="sxs-lookup"><span data-stu-id="e9e75-106">Render a card to HTML</span></span>

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard()
{
    Body = { new AdaptiveTextBlock() { Text = "Hello World" } }
};

try
{
    // Render the card
    RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

    // Get the output HTML 
    HtmlTag html = renderedCard.Html;

    // (Optional) Check for any renderer warnings
    // This includes things like an unknown element type found in the card
    // Or the card exceeded the maximum number of supported actions, etc
    IList<AdaptiveWarning> warnings = renderedCard.Warnings;
}
catch(AdaptiveException ex)
{
    // Failed rendering
}
```
