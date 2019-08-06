---
title: Tools für Adaptive Karten
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: f0c5a61d3406e1defffefc575ee0a6ec78fba93d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733027"
---
# <a name="tools-and-samples"></a><span data-ttu-id="69563-102">Tools und Beispiele</span><span class="sxs-lookup"><span data-stu-id="69563-102">Tools and Samples</span></span>

## <a name="card-designer"></a><span data-ttu-id="69563-103">Karten-Designer</span><span class="sxs-lookup"><span data-stu-id="69563-103">Card Designer</span></span> 

<span data-ttu-id="69563-104">Benötigen Sie ein Tool zum Entwerfen Ihrer Karten?</span><span class="sxs-lookup"><span data-stu-id="69563-104">Need for a tool to design your cards?</span></span> <span data-ttu-id="69563-105">Sehen Sie sich den browserbasierten adaptiven Karten-Designer unter an.[https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="69563-105">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="69563-106">[![Designer-Bildschirmfoto](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="69563-106">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

### <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="69563-107">Einbinden des Designers in Ihre APP</span><span class="sxs-lookup"><span data-stu-id="69563-107">Embed the designer into your app</span></span>

<span data-ttu-id="69563-108">Aber warum sollten Sie Ihre Benutzer dorthin schicken, wenn Sie den Karten-Designer mithilfe der JavaScript-Bibliothek **direkt in Ihre Web-App einbetten** können.</span><span class="sxs-lookup"><span data-stu-id="69563-108">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="69563-109">Sehen Sie sich das [adaptivecards-Designer-](https://npmjs.com/adaptivecards-designer) Paket an, um zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="69563-109">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

## <a name="schema-validation"></a><span data-ttu-id="69563-110">Schemavalidierung</span><span class="sxs-lookup"><span data-stu-id="69563-110">Schema validation</span></span>

<span data-ttu-id="69563-111">Die Schema Validierung ist eine leistungsstarke Möglichkeit, das Erstellen von Tools zu vereinfachen und Tools zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="69563-111">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

<span data-ttu-id="69563-112">Wir haben eine komplette [JSON-Schema Datei](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) zum Bearbeiten und validieren adaptiver Karten in JSON bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="69563-112">We have provided a complete [JSON Schema file](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) for editing and validating adaptive cards in json.</span></span> <span data-ttu-id="69563-113">Beachten Sie, dass die Schema-URL versioniert ist, neuere Versionen von adaptiven Karten über eine entsprechende URL verfügen.</span><span class="sxs-lookup"><span data-stu-id="69563-113">Note that the schema URL is versioned, newer versions of Adaptive Cards will have a corresponding URL.</span></span>

<span data-ttu-id="69563-114">In Visual Studio und Visual Studio Code können Sie die automatische IntelliSense-Funktion durch `$schema` einschließen eines Verweises erhalten.</span><span class="sxs-lookup"><span data-stu-id="69563-114">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![bad](media/tools/invalidjson1.png)

![AutoComplete](media/tools/autocomplete.png)

## <a name="example"></a><span data-ttu-id="69563-117">Beispiel</span><span class="sxs-lookup"><span data-stu-id="69563-117">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a><span data-ttu-id="69563-118">Visual Studio Code Erweiterung</span><span class="sxs-lookup"><span data-stu-id="69563-118">Visual Studio Code Extension</span></span>

<span data-ttu-id="69563-119">Wir haben eine Visual Studio Code-Erweiterung erstellt, mit der Sie die Karte, die Sie bearbeiten, in Echtzeit innerhalb des Editors selbst visualisieren können.</span><span class="sxs-lookup"><span data-stu-id="69563-119">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![Erweiterung](media/tools/vscode-extension.png)

<span data-ttu-id="69563-121">Öffnen Sie zum Installieren von den Extensions Marketplace, und suchen Sie nach **Adaptive Card Viewer**.</span><span class="sxs-lookup"><span data-stu-id="69563-121">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![Wein](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="69563-123">Verwendung</span><span class="sxs-lookup"><span data-stu-id="69563-123">Usage</span></span>

<span data-ttu-id="69563-124">Wenn Sie eine JSON-Datei mit einer adaptiven Karten `$schema` Eigenschaft bearbeiten, können Sie Sie mithilfe `Ctrl+Shift+V A`von anzeigen.</span><span class="sxs-lookup"><span data-stu-id="69563-124">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="69563-125">Optionen</span><span class="sxs-lookup"><span data-stu-id="69563-125">Options</span></span>

<span data-ttu-id="69563-126">Die folgende Visual Studio Code Einstellung ist für den adaptivecards-Viewer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="69563-126">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="69563-127">Dies kann in den Benutzereinstellungen oder Arbeitsbereichs Einstellungen festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="69563-127">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="69563-128">Beispiel für WPF-Schnellansicht</span><span class="sxs-lookup"><span data-stu-id="69563-128">WPF Visualizer Sample</span></span>

<span data-ttu-id="69563-129">Mit dem [Beispiel Projekt für die WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) -Schnellansicht können Sie Karten mithilfe von WPF/XAML auf einem Windows-Computer visualisieren.</span><span class="sxs-lookup"><span data-stu-id="69563-129">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="69563-130">Zum `hostconfig` bearbeiten und Anzeigen von Host Konfigurationseinstellungen ist ein Editor integriert.</span><span class="sxs-lookup"><span data-stu-id="69563-130">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="69563-131">Speichern Sie diese Einstellungen als JSON, um Sie im Rendering in Ihrer Anwendung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="69563-131">Save these settings as a JSON to use them in rendering in your application.</span></span>

![WPF-Schnellansicht](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="69563-133">WPF imagerender-Beispiel</span><span class="sxs-lookup"><span data-stu-id="69563-133">WPF ImageRender Sample</span></span>

<span data-ttu-id="69563-134">Das [imagerender-Beispiel Projekt](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) wandelt eine beliebige Karte mithilfe von WPF aus der Befehlszeile in eine PNG-Datei um.</span><span class="sxs-lookup"><span data-stu-id="69563-134">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 
