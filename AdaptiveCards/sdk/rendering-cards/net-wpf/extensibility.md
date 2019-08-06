---
title: 'Erweiterbarkeit: .net WPF SDK'
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 3e5bb9239d4b4200262648350d67d6494eed9724
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732477"
---
# <a name="extensibility---net-wpf"></a>Erweiterbarkeit: .net WPF

## <a name="custom-element-rendering"></a>Benutzerdefiniertes Element Rendering

Um die vollständige Kontrolle über den Renderer zu erhalten `ElementRenderers` , können Sie die-Eigenschaft zum **Hinzufügen**, **Entfernen**oder **außer Kraft setzen** von Standard Renderers verwenden.

Im folgenden Beispiel wird gezeigt, wie Sie ein Benutzer `"type": "Rating"` definiertes Element definieren und es wiedergeben können.

```csharp
// Register the new type with the JSON parser
AdaptiveTypedElementConverter.RegisterTypedElement<MyCustomRating>();

// Add the new type to the element renderer registry
renderer.ElementRenderers.Set<MyCustomRating>(MyCustomRating.Render);

// Define a custom Rating element type
public class MyCustomRating : AdaptiveElement
{
    public MyCustomRating() { Type = "Rating"; }

    public override string Type { get; set; }

    public AdaptiveTextSize Size { get; set; }

    public AdaptiveTextColor Color { get; set; }

    public static FrameworkElement Render(MyCustomRating rating, AdaptiveRenderContext context)
    {
        var textBlock = new AdaptiveTextBlock
        {
            Size = rating.Size,
            Color = rating.Color
        };
        for (int i = 0; i < rating.Rating; i++)
        {
            textBlock.Text += "\u2605";
        }
        textBlock.Text += $" ({rating.Rating})";
        return context.Render(textBlock);
    }
}
```
