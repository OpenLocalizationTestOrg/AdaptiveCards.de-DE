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
# <a name="render-a-card---net-wpf"></a>Rendering einer Karte: .net WPF

Im folgenden wird beschrieben, wie Sie eine Karte mithilfe des .net WPF SDK Rendering.

> [!NOTE]
> **`Media`mit HTTPS-URLs können nicht in WPF verwendet werden.**
> 
> Aufgrund eines [Fehlers im WPF Media Element-Steuerelement](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) können wir keine Medien renderingmedien Renten, die über HTTPS bereitgestellt werden. Sie sollten HTTP-URLs im `Media` -Element verwenden, bis dies behoben wird.  

## <a name="instantiate-a-renderer"></a>Instanziieren eines Renderers

Erstellen Sie eine Instanz der rendererbibliothek. 

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

## <a name="render-a-card-to-xaml"></a>Rendering einer Karte in XAML

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

