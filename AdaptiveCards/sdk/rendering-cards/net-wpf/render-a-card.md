---
title: 'Rendering einer Karte: .net WPF SDK'
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 1445754d968ee531dc1e2b1816df1189c286d479
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732717"
---
# <a name="render-a-card---net-wpf"></a><span data-ttu-id="85a2f-102">Rendering einer Karte: .net WPF</span><span class="sxs-lookup"><span data-stu-id="85a2f-102">Render a card - .NET WPF</span></span>

<span data-ttu-id="85a2f-103">Im folgenden wird beschrieben, wie Sie eine Karte mithilfe des .net WPF SDK Rendering.</span><span class="sxs-lookup"><span data-stu-id="85a2f-103">Here's how to render a card using the .NET WPF SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="85a2f-104">**`Media`mit HTTPS-URLs können nicht in WPF verwendet werden.**</span><span class="sxs-lookup"><span data-stu-id="85a2f-104">**`Media` with HTTPS URLs will not work in WPF**</span></span>
> 
> <span data-ttu-id="85a2f-105">Aufgrund eines [Fehlers im WPF Media Element-Steuerelement](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) können wir keine Medien renderingmedien Renten, die über HTTPS bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="85a2f-105">Due to a [bug in the WPF MediaElement control](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) we aren't able to render media that is served via HTTPS.</span></span> <span data-ttu-id="85a2f-106">Sie sollten HTTP-URLs im `Media` -Element verwenden, bis dies behoben wird.</span><span class="sxs-lookup"><span data-stu-id="85a2f-106">You should use HTTP URLs in the `Media` element until this is addressed.</span></span>  

## <a name="instantiate-a-renderer"></a><span data-ttu-id="85a2f-107">Instanziieren eines Renderers</span><span class="sxs-lookup"><span data-stu-id="85a2f-107">Instantiate a renderer</span></span>

<span data-ttu-id="85a2f-108">Erstellen Sie eine Instanz der rendererbibliothek.</span><span class="sxs-lookup"><span data-stu-id="85a2f-108">Create an instance of the renderer library.</span></span> 

```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Wpf;
// ...

// Create a card renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// If using the Xceed package, enable the enhanced input
renderer.UseXceedElementRenderers();

// For fun, check the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion;
```

## <a name="render-a-card-to-xaml"></a><span data-ttu-id="85a2f-109">Rendering einer Karte in XAML</span><span class="sxs-lookup"><span data-stu-id="85a2f-109">Render a card to XAML</span></span>

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard("1.0")
{
    Body = { new AdaptiveTextBlock() { Text = "Hello World" } }
};

try
{
    // Render the card
    RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

    // Get the FrameworkElement
    // Add this to your app's UI somewhere
    FrameworkElement fe = renderedCard.FrameworkElement;

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

