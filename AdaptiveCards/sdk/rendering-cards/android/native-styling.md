---
title: Native Formatierung-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: c3190fbb31480f92c774d233476436ee2cfc52b3
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733022"
---
# <a name="native-styling---android"></a><span data-ttu-id="9a005-102">Native Formatierung: Android</span><span class="sxs-lookup"><span data-stu-id="9a005-102">Native styling - Android</span></span>

<span data-ttu-id="9a005-103">Das Native formatieren wird für den Android-Renderer nicht unterstützt, mit v 1.2 wird die Unterstützung für das Formatieren einiger Eigenschaften eingeführt</span><span class="sxs-lookup"><span data-stu-id="9a005-103">Native styling is not supported on the android renderer, v1.2 introduces the support for styling some properties:</span></span>

## <a name="action-sentiment"></a><span data-ttu-id="9a005-104">Aktions Stimmung</span><span class="sxs-lookup"><span data-stu-id="9a005-104">Action Sentiment</span></span>

<span data-ttu-id="9a005-105">Die Stimmungs Stimmung ist in **v 1.2** enthalten und unterstützt nicht so viele Stile wie andere Versionen. Aktionen mit *destruktiver* oder *positiver* Stimmungslage können durch Implementieren eines gültigen Stils und durch Hinzufügen der folgenden Zeile zum Styles. XML für Ihr Projekt</span><span class="sxs-lookup"><span data-stu-id="9a005-105">Action sentiment is included in **v1.2** and while not supporting as many styles as other versions, actions with *destructive* or *positive* sentiment can be styled by implementing a valid style and adding the following line into the styles.xml for your project</span></span>

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a><span data-ttu-id="9a005-106">Inline Aktion</span><span class="sxs-lookup"><span data-stu-id="9a005-106">Inline Action</span></span>

<span data-ttu-id="9a005-107">Text Eingaben mit einer Inline Aktion ermöglichen das Formatieren der Aktion, die gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="9a005-107">Text inputs with an inline action allows styling for the action being rendered.</span></span> <span data-ttu-id="9a005-108">Dies ermöglicht das Formatieren der Aktion als Schaltfläche (adaptiveinlineaction) oder als Bild (adaptiveinlineaction Image).</span><span class="sxs-lookup"><span data-stu-id="9a005-108">This allows styling the action as a button (adaptiveInlineAction) or as an image (adaptiveInlineActionImage)</span></span>

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> <span data-ttu-id="9a005-109">Alle Elementnamen müssen wie hier gezeigt beibehalten werden, da der Renderer genau nach diesen Namen sucht.</span><span class="sxs-lookup"><span data-stu-id="9a005-109">All item names must be kept as shown here as the renderer looks for those exact names</span></span>
