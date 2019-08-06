---
title: Host Konfiguration-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 2828a379d8fda151b1cfca51e5898135186333ae
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733012"
---
# <a name="host-config---android"></a>Host Konfiguration-Android

Zum Anpassen des Renderers geben Sie eine Instanz des hostconfig-Objekts an. (Die vollständige Beschreibung finden Sie unter [Host config Schema](../../../rendering-cards/host-config.md) .)

Verwenden Sie die deserializefromstring-Methode, um ein hostconfig-Objekt aus einer Zeichenfolge zu erstellen.

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```