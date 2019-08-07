---
title: 'Host Konfiguration: .net html SDK'
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: a51b64f5f9783a187d7c3eb56c563a1d4497d3e2
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732822"
---
# <a name="host-config---net-html"></a>Host Konfiguration: .net-html

Eine [Host Konfiguration](../../../rendering-cards/host-config.md) ist ein gemeinsam verwendeter Konfigurationsobjekt, das alle Renderer verstehen. Dies ermöglicht es Ihnen, gängige Stile (z. b. Schriftfamilie, Schriftgrößen, Standard Abstände) und Verhalten (z. b. die maximale Anzahl von Aktionen) zu definieren, die automatisch von den einzelnen Platt formrenderer interpretiert werden. 

Das Ziel ist, dass die systemeigene Benutzeroberfläche, die von jedem Platt formrenderer generiert wird, mit minimaler Arbeit an Ihrem Part sehr ähnlich aussieht.

```csharp
// Construct programmatically
renderer.HostConfig = new AdaptiveHostConfig() 
{
    FontFamily = "Comic Sans",
    FontSizes = {
        Small = 15,
        Default = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};

// Or parse from JSON
renderer.HostConfig  = AdaptiveHostConfig.FromJson(@"{
    ""fontFamily"": ""Comic Sans"",
    ""fontSizes"": {
        ""small"": 25,
        ""default"": 26,
        ""medium"": 27,
        ""large"": 28,
        ""extraLarge"": 29
    }
}");
```