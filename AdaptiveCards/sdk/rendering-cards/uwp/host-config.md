---
title: Host Konfiguration-UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 6f14830a643b064c6169cf3143bbc7cd4ce45937
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732487"
---
# <a name="host-config---uwp"></a>Host Konfiguration-UWP

Zum Anpassen des Renderers geben Sie eine Instanz des hostconfig-Objekts an. (Die vollständige Beschreibung finden Sie unter [Host config Schema](../../../rendering-cards/host-config.md) .)

> Das hostconfig-Objekt wird mit Standardwerten instanziiert, sodass Sie nur die Eigenschaften festlegen können, die Sie ändern möchten.

Beispiel:

```csharp
var hostConfig = new AdaptiveHostConfig() 
{
    FontSizes = {
        Small = 15,
        Normal = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};
renderer.HostConfig = hostConfig;
```

> Alternativ können Sie die hostconfig aus einer JSON-Zeichenfolge laden.

Beispiel:

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

Wenn Sie Sie an den uwprenderer übergeben, legen Sie die Standard Host Konfiguration fest, die für jede von Ihnen renderkarte verwendet werden soll.