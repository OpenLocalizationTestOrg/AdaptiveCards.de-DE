---
title: Rendern von Karten in der Anwendung
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: a562a05a91676dc5e6d8b51690acc4788802fb99
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732607"
---
# <a name="rendering-cards-inside-your-application"></a>Rendern von Karten in der Anwendung

Es ist einfach, Adaptive Karten in Ihrer Anwendung zu Rendering. Wir stellen sdche für alle gängigen Plattformen bereit und bieten eine [Ausführliche Spezifikation](implement-a-renderer.md) für die Erstellung eines eigenen Adapters für Adaptive Karten.

1. **Installieren Sie ein Renderer-SDK** für Ihre Zielplattform.
2. **Erstellen Sie eine rendererinstanz** , die mit dem Stil, den Regeln und Aktions Ereignis Handlern ihrer App konfiguriert wurde.
3. **Rendering einer Karte in eine native Benutzeroberfläche** : automatisch für Ihre APP formatiert.

## <a name="adaptive-cards-sdks"></a>Adaptiver Karten (sdert)

|Platform|Installieren|Build|Docs|Status|
|---|---|---|---|---|
| JavaScript | [![NPM-Installation](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards) | [Quelle](https://github.com/Microsoft/AdaptiveCards/tree/master/source/nodejs)| [Tions](../sdk/rendering-cards/javascript/getting-started.md) | ![Buildstatus](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20564.svg) |
| .NET WPF | [![Nuget-Installation](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf) | [Quelle](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet)| [Tions](../sdk/rendering-cards/net-wpf/getting-started.md) | ![Buildstatus](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| .NET HTML | [![Nuget-Installation](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Html.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Html) | [Quelle](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet) | [Tions](../sdk/rendering-cards/net-html/getting-started.md) | ![Buildstatus](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| Windows UWP | [![Nuget-Installation](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Uwp.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Uwp) | [Quelle](https://github.com/Microsoft/AdaptiveCards/tree/master/source/uwp) | [Tions](../sdk/rendering-cards/uwp/getting-started.md) | ![Buildstatus](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20583.svg) |
| Android | [![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22) | [Quelle](https://github.com/Microsoft/AdaptiveCards/tree/master/source/android) | [Tions](../sdk/rendering-cards/android/getting-started.md) | ![Buildstatus](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/17651.svg)
| iOS | [![CocoaPods](https://img.shields.io/cocoapods/v/AdaptiveCards.svg)](https://cocoapods.org/pods/AdaptiveCards) | [Quelle](https://github.com/Microsoft/AdaptiveCards/tree/master/source/ios) | [Tions](../sdk/rendering-cards/ios/getting-started.md) |  ![Buildstatus](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/16990.svg) |

## <a name="create-an-instance-of-the-renderer"></a>Erstellen einer Instanz des Renderers

Der nächste Schritt besteht darin, eine Instanz von `AdaptiveCardRenderer`zu erstellen. 

### <a name="hook-up-action-events"></a>Aktions Ereignisse anschließen

Standardmäßig werden die Aktionen als Schaltflächen auf der Karte gerendet, aber es liegt an Ihrer APP, dass Sie sich erwartungsgemäß verhalten. Jedes SDK verfügt über ein `OnAction` entsprechendes Ereignis, das Sie behandeln müssen.

* **Action. OpenURL** : öffnet die angegebene `url`.  
* **Action. Submit** : nehmen Sie das Ergebnis des Sendevorgangs an, und senden Sie es an die Quelle. Die Art und Weise, wie Sie Sie an die Quelle der Karte senden, ist vollständig.
* **Action. showcard** : Ruft ein Dialogfeld auf und rendert die unter Karte in diesem Dialogfeld. Beachten Sie, dass Sie diesen nur behandeln müssen `ShowCardActionMode` , wenn auf `popup`festgelegt ist.

## <a name="render-a-card"></a>Rendering einer Karte

Nachdem Sie eine Karten Nutzlast abgerufen haben, rufen Sie einfach den Renderer auf, und übergeben Sie die Karte. Sie erhalten ein natives Benutzeroberflächen Objekt, das aus dem Karteninhalt besteht. Fügen Sie diese Benutzeroberfläche jetzt in Ihre APP ein.

## <a name="customization"></a>Anpassung

Es gibt mehrere Möglichkeiten, wie gerendert werden kann. 

### <a name="hostconfig"></a>HostConfig

Ein [hostconfig](host-config.md) ist ein frei gegebenes, plattformübergreifendes Konfigurationsobjekt, das die grundlegende Formatierung und das Verhalten von Karten in der APP steuert. Es definiert Dinge wie Schriftgrößen, Abstand zwischen Elementen, Farben, Anzahl unterstützter Aktionen usw. 

### <a name="native-platform-styling"></a>Native Platt Form Formatierung

Die meisten Benutzeroberflächen-Frameworks ermöglichen das Formatieren der gerenderten Karte mithilfe des nativen UI-frameworkstils In HTML können Sie z. b. CSS-Klassen für den HTML-Code oder in XAML angeben, um ein benutzerdefiniertes ResourceDictionary für eine differenzierte Steuerung der Ausgabe zu übergeben.

### <a name="customize-per-element-rendering"></a>Anpassen des Renderings pro Element

Mit jedem SDK können Sie das Rendering eines beliebigen Elements überschreiben oder sogar die Unterstützung für völlig neue Elemente hinzufügen, die Sie definieren.  Beispielsweise können Sie den `Input.Date` Renderer so ändern, dass ein eigenes benutzerdefiniertes Steuerelement ausgegeben wird, während der Rest der Ausgabe des Renderers beibehalten wird. Oder Sie können Unterstützung für ein von `Rating` Ihnen definiertes benutzerdefiniertes Element hinzufügen.



