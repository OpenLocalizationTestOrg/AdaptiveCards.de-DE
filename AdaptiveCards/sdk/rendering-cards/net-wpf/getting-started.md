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
# <a name="getting-started---net-wpf"></a>Getting Started (.net WPF)

Wie auf der Seite [Getting Started](../../../authoring-cards/getting-started.md) mit den ersten Schritten beschrieben, handelt es sich bei einer adaptiven Karte um ein JSON-serialisiertes Karten Objektmodell. Diese Bibliothek erleichtert das Rendering dieses JSON-Code in der WPF-Benutzeroberfläche, die Sie in Ihrer APP verwenden können.

## <a name="nuget-install"></a>Nuget-Installation

[![Nuget-Installation](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a>Xceed Enhanced Input Package

Mithilfe dieses optionalen Pakets werden die Eingabesteuerelemente der adaptiven Karte erweitert, die über die Standard-WPF hinausgehen. Sie hat eine Abhängigkeit von`Extended.Wpf.Toolkit`

[![Nuget-Installation](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a>Beispiel für WPF-Schnellansicht

![Bildschirm Abbildung von Visualisierungen](../../../resources/media/tools/wpfvisualizer.png)

Mit dem Beispiel für eine [WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) -Schnellansicht können Sie Karten mithilfe von WPF visualisieren.  Zum `Host Config` bearbeiten und Anzeigen von Host Konfigurationseinstellungen ist ein Editor integriert. Speichern Sie diese Einstellungen als JSON, um Sie im Rendering in Ihrer Anwendung zu verwenden.

## <a name="next-steps"></a>Nächste Schritte

Die nächsten Schritte finden Sie unter [Rendering a Card](render-a-card.md) !
