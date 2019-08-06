---
title: 'Native Formatierung: UWP SDK'
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: 565c61535adc5b316cb8b1f3ad77e511012e7612
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732542"
---
# <a name="native-styling---uwp"></a><span data-ttu-id="b8017-102">Native Formatierung-UWP</span><span class="sxs-lookup"><span data-stu-id="b8017-102">Native styling - UWP</span></span>

<span data-ttu-id="b8017-103">Obwohl die Host Konfiguration den größten Teil der einzelnen Plattformen bietet, ist es wahrscheinlich, dass Sie auf jeder Plattform eine native Formatierung ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="b8017-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="b8017-104">UWP vereinfacht dies, indem es Ihnen ermöglicht wird, ein ResourceDictionary für differenzierte Formatierung, Verhalten, Animationen usw. zu übergeben.</span><span class="sxs-lookup"><span data-stu-id="b8017-104">UWP makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="b8017-105">Element</span><span class="sxs-lookup"><span data-stu-id="b8017-105">Element</span></span> | <span data-ttu-id="b8017-106">Stilnamen</span><span class="sxs-lookup"><span data-stu-id="b8017-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="b8017-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="b8017-107">AdaptiveCard</span></span> | <span data-ttu-id="b8017-108">Adaptive.Card</span><span class="sxs-lookup"><span data-stu-id="b8017-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="b8017-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="b8017-109">Action.OpenUrl</span></span>  | <span data-ttu-id="b8017-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="b8017-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="b8017-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="b8017-111">Action.ShowCard</span></span> | <span data-ttu-id="b8017-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="b8017-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="b8017-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="b8017-113">Action.Submit</span></span>  | <span data-ttu-id="b8017-114">Adaptive.Action.Submit</span><span class="sxs-lookup"><span data-stu-id="b8017-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="b8017-115">Spalte</span><span class="sxs-lookup"><span data-stu-id="b8017-115">Column</span></span> | <span data-ttu-id="b8017-116">Adaptive.Column, Adaptive.Action.Tap</span><span class="sxs-lookup"><span data-stu-id="b8017-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="b8017-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="b8017-117">ColumnSet</span></span> | <span data-ttu-id="b8017-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="b8017-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="b8017-119">Container</span><span class="sxs-lookup"><span data-stu-id="b8017-119">Container</span></span> | <span data-ttu-id="b8017-120">Adaptive.Container</span><span class="sxs-lookup"><span data-stu-id="b8017-120">Adaptive.Container</span></span>|
| <span data-ttu-id="b8017-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="b8017-121">Input.ChoiceSet</span></span> | <span data-ttu-id="b8017-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="b8017-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="b8017-123">Input. Date</span><span class="sxs-lookup"><span data-stu-id="b8017-123">Input.Date</span></span> | <span data-ttu-id="b8017-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="b8017-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="b8017-125">Input.Number</span><span class="sxs-lookup"><span data-stu-id="b8017-125">Input.Number</span></span> | <span data-ttu-id="b8017-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="b8017-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="b8017-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="b8017-127">Input.Text</span></span> | <span data-ttu-id="b8017-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="b8017-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="b8017-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="b8017-129">Input.Time</span></span> | <span data-ttu-id="b8017-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="b8017-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="b8017-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="b8017-131">Input.Toggle</span></span>| <span data-ttu-id="b8017-132">Adaptive.Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="b8017-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="b8017-133">Bild</span><span class="sxs-lookup"><span data-stu-id="b8017-133">Image</span></span>  | <span data-ttu-id="b8017-134">Adaptive.Image</span><span class="sxs-lookup"><span data-stu-id="b8017-134">Adaptive.Image</span></span> |
| <span data-ttu-id="b8017-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="b8017-135">ImageSet</span></span>  | <span data-ttu-id="b8017-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="b8017-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="b8017-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="b8017-137">FactSet</span></span> | <span data-ttu-id="b8017-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="b8017-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="b8017-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="b8017-139">TextBlock</span></span>  | <span data-ttu-id="b8017-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="b8017-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="b8017-141">Dieses Beispiel-XAML-Ressourcen Wörterbuch, das den Hintergrund aller Textblöcke auf Aqua festlegt.</span><span class="sxs-lookup"><span data-stu-id="b8017-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="b8017-142">Wahrscheinlich möchten Sie etwas höher als dieses😁</span><span class="sxs-lookup"><span data-stu-id="b8017-142">You will probably want something more advanced than this 😁</span></span>

```xml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;
```
