---
title: 'Native Formatierung: JavaScript SDK'
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 687a90dd572ba2df786816fdd9dc313746cca982
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732622"
---
# <a name="native-styling---javascript"></a><span data-ttu-id="a5993-102">Native Formatierung: JavaScript</span><span class="sxs-lookup"><span data-stu-id="a5993-102">Native styling - JavaScript</span></span>

<span data-ttu-id="a5993-103">Verwenden Sie CSS für eine differenzierte Formatierung des Karten-HTML.</span><span class="sxs-lookup"><span data-stu-id="a5993-103">Use CSS for fine-grained styling of the card HTML.</span></span>

<span data-ttu-id="a5993-104">Die folgenden CSS-Klassen werden verschiedenen Elementen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a5993-104">The following CSS classes will be added to various elements.</span></span>

| <span data-ttu-id="a5993-105">CSS-Klasse</span><span class="sxs-lookup"><span data-stu-id="a5993-105">CSS class</span></span> | <span data-ttu-id="a5993-106">Verwendung</span><span class="sxs-lookup"><span data-stu-id="a5993-106">Usage</span></span> |
|---|---|
| <span data-ttu-id="a5993-107">.ac-container</span><span class="sxs-lookup"><span data-stu-id="a5993-107">.ac-container</span></span> | <span data-ttu-id="a5993-108">Container</span><span class="sxs-lookup"><span data-stu-id="a5993-108">containers</span></span> |
| <span data-ttu-id="a5993-109">.ac-selectable</span><span class="sxs-lookup"><span data-stu-id="a5993-109">.ac-selectable</span></span>  | <span data-ttu-id="a5993-110">Elemente mit`selectAction`</span><span class="sxs-lookup"><span data-stu-id="a5993-110">elements with `selectAction`</span></span> |
| <span data-ttu-id="a5993-111">. AC-Image</span><span class="sxs-lookup"><span data-stu-id="a5993-111">.ac-image</span></span> | <span data-ttu-id="a5993-112">Bild</span><span class="sxs-lookup"><span data-stu-id="a5993-112">image</span></span> |
| <span data-ttu-id="a5993-113">.ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="a5993-113">.ac-pushButton</span></span> | <span data-ttu-id="a5993-114">Aktionen gerendert wie Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="a5993-114">actions rendered like buttons</span></span> |
| <span data-ttu-id="a5993-115">.ac-linkButton</span><span class="sxs-lookup"><span data-stu-id="a5993-115">.ac-linkButton</span></span>  | <span data-ttu-id="a5993-116">Aktionen gerendert wie Links</span><span class="sxs-lookup"><span data-stu-id="a5993-116">actions rendered like links</span></span> |
| <span data-ttu-id="a5993-117">. AC-Eingabe</span><span class="sxs-lookup"><span data-stu-id="a5993-117">.ac-input</span></span> | <span data-ttu-id="a5993-118">Eingabesteuerelemente</span><span class="sxs-lookup"><span data-stu-id="a5993-118">input controls</span></span>|
| <span data-ttu-id="a5993-119">. AC-TextInput</span><span class="sxs-lookup"><span data-stu-id="a5993-119">.ac-textInput</span></span>| <span data-ttu-id="a5993-120">Texteingabe</span><span class="sxs-lookup"><span data-stu-id="a5993-120">text input</span></span> |
| <span data-ttu-id="a5993-121">. AC-Multiline</span><span class="sxs-lookup"><span data-stu-id="a5993-121">.ac-multiline</span></span> | <span data-ttu-id="a5993-122">mehrzeilige Texteingabe</span><span class="sxs-lookup"><span data-stu-id="a5993-122">multiline text input</span></span> |
| <span data-ttu-id="a5993-123">.ac-numberInput</span><span class="sxs-lookup"><span data-stu-id="a5993-123">.ac-numberInput</span></span> | <span data-ttu-id="a5993-124">Zahlen Eingabe</span><span class="sxs-lookup"><span data-stu-id="a5993-124">number input</span></span>|
| <span data-ttu-id="a5993-125">.ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="a5993-125">.ac-dateInput</span></span> | <span data-ttu-id="a5993-126">Datums Eingabe</span><span class="sxs-lookup"><span data-stu-id="a5993-126">date input</span></span>|
| <span data-ttu-id="a5993-127">.ac-timeInput</span><span class="sxs-lookup"><span data-stu-id="a5993-127">.ac-timeInput</span></span> | <span data-ttu-id="a5993-128">Uhrzeit Eingabe</span><span class="sxs-lookup"><span data-stu-id="a5993-128">time input</span></span> |
| <span data-ttu-id="a5993-129">.ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="a5993-129">.ac-multichoiceInput</span></span> | <span data-ttu-id="a5993-130">Eingabe für mehr Wahl</span><span class="sxs-lookup"><span data-stu-id="a5993-130">multichoice input</span></span>|