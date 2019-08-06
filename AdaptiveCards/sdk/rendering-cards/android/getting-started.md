---
title: Android-SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 4723175bf94685c22d99fb15f3d1887ac37b8c57
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733007"
---
# <a name="getting-started---android"></a><span data-ttu-id="7ad9b-102">Einstieg: Android</span><span class="sxs-lookup"><span data-stu-id="7ad9b-102">Getting started - Android</span></span>

<span data-ttu-id="7ad9b-103">Dies ist ein Renderer, der auf Android native-Steuerelemente abzielt.</span><span class="sxs-lookup"><span data-stu-id="7ad9b-103">This is a renderer which targets Android native controls.</span></span>

## <a name="install-maven-package"></a><span data-ttu-id="7ad9b-104">Maven-Paket installieren</span><span class="sxs-lookup"><span data-stu-id="7ad9b-104">Install Maven package</span></span>

<span data-ttu-id="7ad9b-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span><span class="sxs-lookup"><span data-stu-id="7ad9b-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span></span>

<span data-ttu-id="7ad9b-106">Sie finden die veröffentlichten Pakete.</span><span class="sxs-lookup"><span data-stu-id="7ad9b-106">You can find the published packages</span></span> ![hier,](https://search.maven.org/search?q=g:io.adaptivecards)

<span data-ttu-id="7ad9b-108">Wenn Sie die Bibliothek in Ihr Projekt einschließen möchten, müssen Sie diese Zeile in das Projekt "gradle. Build" im Abschnitt "Abhängigkeiten" einschließen.</span><span class="sxs-lookup"><span data-stu-id="7ad9b-108">To include library to your project you must include this line into your project gradle.build under the dependencies section</span></span>

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
<span data-ttu-id="7ad9b-109">Abhängig von der Version, die Sie in Ihr Projekt einschließen möchten, müssen Sie die Versionsnummer ändern.</span><span class="sxs-lookup"><span data-stu-id="7ad9b-109">You need to change the version number depending on the version you want to include into your project</span></span>

## <a name="add-import"></a><span data-ttu-id="7ad9b-110">Import hinzufügen</span><span class="sxs-lookup"><span data-stu-id="7ad9b-110">Add import</span></span>

<span data-ttu-id="7ad9b-111">Fügen Sie diesen Import hinzu, um das Objektmodell einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="7ad9b-111">To include the object model, add this import</span></span>

```
 import io.adaptivecards.objectmodel.*;
```

<span data-ttu-id="7ad9b-112">Um den Renderer einzuschließen, fügen Sie diesen Import hinzu.</span><span class="sxs-lookup"><span data-stu-id="7ad9b-112">To include the renderer, add this import</span></span>

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a><span data-ttu-id="7ad9b-113">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="7ad9b-113">Next steps</span></span>

<span data-ttu-id="7ad9b-114">Die nächsten Schritte finden Sie unter [Rendering a Card](render-a-card.md) !</span><span class="sxs-lookup"><span data-stu-id="7ad9b-114">See [Render a card](render-a-card.md) for the next steps!</span></span>
