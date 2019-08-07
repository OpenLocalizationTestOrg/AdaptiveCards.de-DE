---
title: 'Host Konfiguration: IOS SDK'
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34d28ef0f0cd7200965fb6967bb2f252f6a47456
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732932"
---
# <a name="host-config---ios"></a>Host Konfiguration-IOS

Der Host kann über die hostconfig konfiguriert werden, die durch eine JSON-Zeichenfolge generiert werden kann.

```objective-c
ACOParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
```

Standardhostconfig kann instanziiert werden.

```objective-c
ACOHostConfig *defaultConfig = [[ACHostConfig alloc] init];
```

## <a name="render-a-card-using-host-config"></a>Rendering einer Karte mithilfe der Host Konfiguration

Der Rederer nimmt die Adaptive Karte und die Host Konfiguration vor. Hostconfig kann NULL sein, und wenn NULL, wird der Standardwert verwendet.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```