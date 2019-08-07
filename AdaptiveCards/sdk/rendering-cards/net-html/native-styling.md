---
title: 'Native Formatierung: .net html SDK'
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 5b829d9eefe933f133c8532030856849802c5eb5
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732837"
---
# <a name="native-styling---net-html"></a><span data-ttu-id="886d9-102">Native Formatierung: .net-html</span><span class="sxs-lookup"><span data-stu-id="886d9-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="886d9-103">Obwohl die Host Konfiguration den größten Teil der einzelnen Plattformen bietet, ist es wahrscheinlich, dass Sie auf jeder Plattform eine native Formatierung ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="886d9-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="886d9-104">Durch HTML werden jedem Element CSS-Klassen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="886d9-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="886d9-105">Element</span><span class="sxs-lookup"><span data-stu-id="886d9-105">Element</span></span> | <span data-ttu-id="886d9-106">CSS-Klasse</span><span class="sxs-lookup"><span data-stu-id="886d9-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="886d9-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="886d9-107">AdaptiveCard</span></span> | <span data-ttu-id="886d9-108">ac-adaptivecard</span><span class="sxs-lookup"><span data-stu-id="886d9-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="886d9-109">Alle Aktionen</span><span class="sxs-lookup"><span data-stu-id="886d9-109">All Actions</span></span> | <span data-ttu-id="886d9-110">ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="886d9-110">ac-pushButton</span></span> | 
| <span data-ttu-id="886d9-111">Aktionen auswählen</span><span class="sxs-lookup"><span data-stu-id="886d9-111">Select Actions</span></span> | <span data-ttu-id="886d9-112">ac-selectable</span><span class="sxs-lookup"><span data-stu-id="886d9-112">ac-selectable</span></span> |
| <span data-ttu-id="886d9-113">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="886d9-113">Action.OpenUrl</span></span>  | <span data-ttu-id="886d9-114">ac-action-openUrl</span><span class="sxs-lookup"><span data-stu-id="886d9-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="886d9-115">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="886d9-115">Action.ShowCard</span></span> | <span data-ttu-id="886d9-116">ac-action-showCard</span><span class="sxs-lookup"><span data-stu-id="886d9-116">ac-action-showCard</span></span> |
| <span data-ttu-id="886d9-117">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="886d9-117">Action.Submit</span></span>  | <span data-ttu-id="886d9-118">ac-action-submit</span><span class="sxs-lookup"><span data-stu-id="886d9-118">ac-action-submit</span></span>  |
| <span data-ttu-id="886d9-119">ActionSet</span><span class="sxs-lookup"><span data-stu-id="886d9-119">ActionSet</span></span> | <span data-ttu-id="886d9-120">ac-actionset</span><span class="sxs-lookup"><span data-stu-id="886d9-120">ac-actionset</span></span> |
| <span data-ttu-id="886d9-121">Spalte</span><span class="sxs-lookup"><span data-stu-id="886d9-121">Column</span></span> | <span data-ttu-id="886d9-122">AC-Column</span><span class="sxs-lookup"><span data-stu-id="886d9-122">ac-column</span></span> |
| <span data-ttu-id="886d9-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="886d9-123">ColumnSet</span></span> | <span data-ttu-id="886d9-124">ac-columnset</span><span class="sxs-lookup"><span data-stu-id="886d9-124">ac-columnset</span></span> |
| <span data-ttu-id="886d9-125">Container</span><span class="sxs-lookup"><span data-stu-id="886d9-125">Container</span></span> | <span data-ttu-id="886d9-126">ac-container</span><span class="sxs-lookup"><span data-stu-id="886d9-126">ac-container</span></span> |
| <span data-ttu-id="886d9-127">Alle Eingaben</span><span class="sxs-lookup"><span data-stu-id="886d9-127">All Inputs</span></span> | <span data-ttu-id="886d9-128">AC-Eingabe</span><span class="sxs-lookup"><span data-stu-id="886d9-128">ac-input</span></span> |
| <span data-ttu-id="886d9-129">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="886d9-129">Input.ChoiceSet</span></span> | <span data-ttu-id="886d9-130">ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="886d9-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="886d9-131">Input. Date</span><span class="sxs-lookup"><span data-stu-id="886d9-131">Input.Date</span></span> | <span data-ttu-id="886d9-132">ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="886d9-132">ac-dateInput</span></span> |
| <span data-ttu-id="886d9-133">Input.Number</span><span class="sxs-lookup"><span data-stu-id="886d9-133">Input.Number</span></span> | <span data-ttu-id="886d9-134">ac-numberInput</span><span class="sxs-lookup"><span data-stu-id="886d9-134">ac-numberInput</span></span> |
| <span data-ttu-id="886d9-135">Input.Text</span><span class="sxs-lookup"><span data-stu-id="886d9-135">Input.Text</span></span> | <span data-ttu-id="886d9-136">ac-textInput</span><span class="sxs-lookup"><span data-stu-id="886d9-136">ac-textInput</span></span> |
| <span data-ttu-id="886d9-137">Input.Time</span><span class="sxs-lookup"><span data-stu-id="886d9-137">Input.Time</span></span> | <span data-ttu-id="886d9-138">ac-timeInput</span><span class="sxs-lookup"><span data-stu-id="886d9-138">ac-timeInput</span></span> |
| <span data-ttu-id="886d9-139">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="886d9-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="886d9-140">Bild</span><span class="sxs-lookup"><span data-stu-id="886d9-140">Image</span></span>  | <span data-ttu-id="886d9-141">AC-Image</span><span class="sxs-lookup"><span data-stu-id="886d9-141">ac-image</span></span> |
| <span data-ttu-id="886d9-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="886d9-142">ImageSet</span></span>  | <span data-ttu-id="886d9-143">ac-imageset</span><span class="sxs-lookup"><span data-stu-id="886d9-143">ac-imageset</span></span> |
| <span data-ttu-id="886d9-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="886d9-144">FactSet</span></span> | <span data-ttu-id="886d9-145">ac-factset</span><span class="sxs-lookup"><span data-stu-id="886d9-145">ac-factset</span></span> |
| <span data-ttu-id="886d9-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="886d9-146">TextBlock</span></span>  | <span data-ttu-id="886d9-147">AC-TextBlock</span><span class="sxs-lookup"><span data-stu-id="886d9-147">ac-textblock</span></span> |