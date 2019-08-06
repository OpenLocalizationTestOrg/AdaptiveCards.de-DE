---
title: Host Konfiguration-.net WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 65e68c2c3e7fa244ba790afc3749912937ea8470
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732727"
---
# <a name="host-config---net-wpf"></a>Host Konfiguration-.net WPF

Eine [Host Konfiguration](../../../rendering-cards/host-config.md) ist ein gemeinsam verwendeter Konfigurationsobjekt, das alle Renderer verstehen. Dies ermöglicht es Ihnen, gängige Stile (z. b. Schriftfamilie, Schriftgrößen, Standard Abstände) und Verhalten (z. b. die maximale Anzahl von Aktionen) zu definieren, die automatisch von den einzelnen Platt formrenderer interpretiert werden. 

Das Ziel ist, dass die systemeigene Benutzeroberfläche, die von jedem Platt formrenderer generiert wird, mit minimaler Arbeit an Ihrem Part sehr ähnlich aussieht.

```csharp
// Construct programmatically
renderer.HostConfig = new AdaptiveHostConfig()
{
    FontStyles = new FontStylesConfig()
    {
        Default = new FontStyleConfig()
        {
            FontFamily = "Consolas",
            FontSizes = {
                Small = 15,
                Default = 20,
                Medium = 25,
                Large = 30,
                ExtraLarge= 40
            }
        },
    }
};

// Or parse from JSON
renderer.HostConfig = AdaptiveHostConfig.FromJson(@"{
    ""fontStyles"": {
        ""default"": {
            ""fontFamily"": ""Consolas"",
            ""fontSizes"": {
                ""small"": 15,
                ""default"": 20,
                ""medium"": 25,
                ""large"": 30,
                ""extraLarge"": 40
            }
        }
    }}");
```
