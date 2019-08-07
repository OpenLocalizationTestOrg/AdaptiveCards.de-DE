---
title: .NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 999f8ac3cd6a18fbbfc8b8bbdcf47465d8bb314f
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732732"
---
# <a name="getting-started---net-wpf"></a><span data-ttu-id="1e1aa-102">Getting Started (.net WPF)</span><span class="sxs-lookup"><span data-stu-id="1e1aa-102">Getting started - .NET WPF</span></span>

<span data-ttu-id="1e1aa-103">Wie auf der Seite [Getting Started](../../../authoring-cards/getting-started.md) mit den ersten Schritten beschrieben, handelt es sich bei einer adaptiven Karte um ein JSON-serialisiertes Karten Objektmodell.</span><span class="sxs-lookup"><span data-stu-id="1e1aa-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="1e1aa-104">Diese Bibliothek erleichtert das Rendering dieses JSON-Code in der WPF-Benutzeroberfläche, die Sie in Ihrer APP verwenden können.</span><span class="sxs-lookup"><span data-stu-id="1e1aa-104">This library makes it easy to render that JSON into WPF UI that you can use within your app.</span></span>

## <a name="nuget-install"></a><span data-ttu-id="1e1aa-105">Nuget-Installation</span><span class="sxs-lookup"><span data-stu-id="1e1aa-105">NuGet install</span></span>

<span data-ttu-id="1e1aa-106">[![Nuget-Installation](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span><span class="sxs-lookup"><span data-stu-id="1e1aa-106">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a><span data-ttu-id="1e1aa-107">Xceed Enhanced Input Package</span><span class="sxs-lookup"><span data-stu-id="1e1aa-107">Xceed enhanced input package</span></span>

<span data-ttu-id="1e1aa-108">Mithilfe dieses optionalen Pakets werden die Eingabesteuerelemente der adaptiven Karte erweitert, die über die Standard-WPF hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="1e1aa-108">This optional package enhances the Adaptive Card Input controls beyond what WPF provides out of the box.</span></span> <span data-ttu-id="1e1aa-109">Sie hat eine Abhängigkeit von`Extended.Wpf.Toolkit`</span><span class="sxs-lookup"><span data-stu-id="1e1aa-109">It has a dependency on `Extended.Wpf.Toolkit`</span></span>

<span data-ttu-id="1e1aa-110">[![Nuget-Installation](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span><span class="sxs-lookup"><span data-stu-id="1e1aa-110">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="1e1aa-111">Beispiel für WPF-Schnellansicht</span><span class="sxs-lookup"><span data-stu-id="1e1aa-111">WPF Visualizer Sample</span></span>

![Bildschirm Abbildung von Visualisierungen](../../../resources/media/tools/wpfvisualizer.png)

<span data-ttu-id="1e1aa-113">Mit dem Beispiel für eine [WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) -Schnellansicht können Sie Karten mithilfe von WPF visualisieren.</span><span class="sxs-lookup"><span data-stu-id="1e1aa-113">The [WPF Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF.</span></span>  <span data-ttu-id="1e1aa-114">Zum `Host Config` bearbeiten und Anzeigen von Host Konfigurationseinstellungen ist ein Editor integriert.</span><span class="sxs-lookup"><span data-stu-id="1e1aa-114">A `Host Config` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="1e1aa-115">Speichern Sie diese Einstellungen als JSON, um Sie im Rendering in Ihrer Anwendung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="1e1aa-115">Save these settings as a JSON to use them in rendering in your application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1e1aa-116">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="1e1aa-116">Next steps</span></span>

<span data-ttu-id="1e1aa-117">Die nächsten Schritte finden Sie unter [Rendering a Card](render-a-card.md) !</span><span class="sxs-lookup"><span data-stu-id="1e1aa-117">See [Render a card](render-a-card.md) for the next steps!</span></span>
