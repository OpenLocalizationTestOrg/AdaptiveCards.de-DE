---
title: Rendering eines Card-UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d7e101bbabfccf162797a3a8e154028f29bdc84b
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732547"
---
# <a name="render-a-card---uwp"></a>Rendering einer Karte (UWP)

Im folgenden wird beschrieben, wie Sie eine Karte mithilfe des UWP SDK Rendering.

## <a name="create-an-instance-of-your-renderer"></a>Erstellen einer Instanz des Renderers

Erstellen Sie eine Instanz der rendererbibliothek. 

```csharp
using AdaptiveCards.Rendering.Uwp;
// ...

var renderer = new AdaptiveCardRenderer();
```

## <a name="create-a-card-from-a-json-string"></a>Erstellen einer Karte aus einer JSON-Zeichenfolge

```csharp
var card = AdaptiveCard.FromJsonString(jsonString);
```

## <a name="create-a-card-from-a-json-object"></a>Erstellen einer Karte aus einem JSON-Objekt

```csharp
var card = AdaptiveCard.FromJson(jsonObject);
```

## <a name="render-a-card"></a>Rendering einer Karte

Erwerben Sie eine Karte aus einer Quelle, und rendersie Sie.

```csharp
RenderedAdaptiveCard renderedAdaptiveCard =  renderer.RenderAdaptiveCard(card);

// Check if the render was successful
if (renderedAdaptiveCard.FrameworkElement != null)
{
    // Get the framework element
    var uiCard = renderedAdaptiveCard.FrameworkElement;

    // Add it to your UI
    myGrid.Children.Add(uiCard);
}
```

## <a name="example"></a>Beispiel

Im folgenden finden Sie ein Beispiel aus dem UWP-Renderer.

```csharp
var renderer = new AdaptiveCardRenderer();
var card = AdaptiveCard.FromJsonString(jsonString);
var renderedAdaptiveCard = renderer.RenderAdaptiveCard(card.AdaptiveCard);
if (renderedAdaptiveCard.FrameworkElement != null)
{
    myGrid.Children.Add(renderedAdaptiveCard.FrameworkElement);
}
...
```