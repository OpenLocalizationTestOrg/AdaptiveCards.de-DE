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
# <a name="render-a-card---uwp"></a><span data-ttu-id="fd85a-102">Rendering einer Karte (UWP)</span><span class="sxs-lookup"><span data-stu-id="fd85a-102">Render a card - UWP</span></span>

<span data-ttu-id="fd85a-103">Im folgenden wird beschrieben, wie Sie eine Karte mithilfe des UWP SDK Rendering.</span><span class="sxs-lookup"><span data-stu-id="fd85a-103">Here's how to render a card using the UWP SDK.</span></span>

## <a name="create-an-instance-of-your-renderer"></a><span data-ttu-id="fd85a-104">Erstellen einer Instanz des Renderers</span><span class="sxs-lookup"><span data-stu-id="fd85a-104">Create an instance of your renderer</span></span>

<span data-ttu-id="fd85a-105">Erstellen Sie eine Instanz der rendererbibliothek.</span><span class="sxs-lookup"><span data-stu-id="fd85a-105">Create an instance of the renderer library.</span></span> 

```csharp
using AdaptiveCards.Rendering.Uwp;
// ...

var renderer = new AdaptiveCardRenderer();
```

## <a name="create-a-card-from-a-json-string"></a><span data-ttu-id="fd85a-106">Erstellen einer Karte aus einer JSON-Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="fd85a-106">Create a card from a JSON string</span></span>

```csharp
var card = AdaptiveCard.FromJsonString(jsonString);
```

## <a name="create-a-card-from-a-json-object"></a><span data-ttu-id="fd85a-107">Erstellen einer Karte aus einem JSON-Objekt</span><span class="sxs-lookup"><span data-stu-id="fd85a-107">Create a card from a JSON object</span></span>

```csharp
var card = AdaptiveCard.FromJson(jsonObject);
```

## <a name="render-a-card"></a><span data-ttu-id="fd85a-108">Rendering einer Karte</span><span class="sxs-lookup"><span data-stu-id="fd85a-108">Render a card</span></span>

<span data-ttu-id="fd85a-109">Erwerben Sie eine Karte aus einer Quelle, und rendersie Sie.</span><span class="sxs-lookup"><span data-stu-id="fd85a-109">Acquire a card from a source and render it.</span></span>

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

## <a name="example"></a><span data-ttu-id="fd85a-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fd85a-110">Example</span></span>

<span data-ttu-id="fd85a-111">Im folgenden finden Sie ein Beispiel aus dem UWP-Renderer.</span><span class="sxs-lookup"><span data-stu-id="fd85a-111">Here is an example from the UWP renderer.</span></span>

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