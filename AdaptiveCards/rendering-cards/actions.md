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
# <a name="actions"></a><span data-ttu-id="34b6a-102">Aktionen</span><span class="sxs-lookup"><span data-stu-id="34b6a-102">Actions</span></span>

<span data-ttu-id="34b6a-103">Standardmäßig werden die Aktionen als Schaltflächen auf der Karte gerendet, aber es liegt an Ihrer APP, dass Sie sich erwartungsgemäß verhalten.</span><span class="sxs-lookup"><span data-stu-id="34b6a-103">By default, the actions will render as buttons on the card, but it's up to your app to make them behave as you expect.</span></span> <span data-ttu-id="34b6a-104">Jedes SDK verfügt über ein `OnAction` entsprechendes Ereignis, das Sie behandeln müssen.</span><span class="sxs-lookup"><span data-stu-id="34b6a-104">Each SDK has the equivalent of an `OnAction` event that you must handle.</span></span>

* <span data-ttu-id="34b6a-105">**Action. OpenURL** : öffnet die angegebene `url`.</span><span class="sxs-lookup"><span data-stu-id="34b6a-105">**Action.OpenUrl** - open the specified `url`.</span></span>  
* <span data-ttu-id="34b6a-106">**Action. Submit** : nehmen Sie das Ergebnis des Sendevorgangs an, und senden Sie es an die Quelle.</span><span class="sxs-lookup"><span data-stu-id="34b6a-106">**Action.Submit** - take the result of the submit and send it to the source.</span></span> <span data-ttu-id="34b6a-107">Die Art und Weise, wie Sie Sie an die Quelle der Karte senden, ist vollständig.</span><span class="sxs-lookup"><span data-stu-id="34b6a-107">How you send it to the source of the card is entirely up to you.</span></span>
* <span data-ttu-id="34b6a-108">**Action. showcard** : Ruft ein Dialogfeld auf und rendert die unter Karte in diesem Dialogfeld.</span><span class="sxs-lookup"><span data-stu-id="34b6a-108">**Action.ShowCard** - invokes a dialog and renders the sub-card into that dialog.</span></span> <span data-ttu-id="34b6a-109">Beachten Sie, dass Sie diesen nur behandeln müssen `ShowCardActionMode` , wenn auf `popup`festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="34b6a-109">Note that you only need to handle this if `ShowCardActionMode` is set to `popup`.</span></span>