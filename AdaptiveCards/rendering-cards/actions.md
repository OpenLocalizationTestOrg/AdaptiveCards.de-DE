---
title: Aktionen
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34283b52f0c4902c71ea33634676832c7dfec5c9
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733107"
---
# <a name="actions"></a>Aktionen

Standardmäßig werden die Aktionen als Schaltflächen auf der Karte gerendet, aber es liegt an Ihrer APP, dass Sie sich erwartungsgemäß verhalten. Jedes SDK verfügt über ein `OnAction` entsprechendes Ereignis, das Sie behandeln müssen.

* **Action. OpenURL** : öffnet die angegebene `url`.  
* **Action. Submit** : nehmen Sie das Ergebnis des Sendevorgangs an, und senden Sie es an die Quelle. Die Art und Weise, wie Sie Sie an die Quelle der Karte senden, ist vollständig.
* **Action. showcard** : Ruft ein Dialogfeld auf und rendert die unter Karte in diesem Dialogfeld. Beachten Sie, dass Sie diesen nur behandeln müssen `ShowCardActionMode` , wenn auf `popup`festgelegt ist.