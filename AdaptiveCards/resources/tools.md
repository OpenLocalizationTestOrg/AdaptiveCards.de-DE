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
# <a name="tools-and-samples"></a>Tools und Beispiele

## <a name="card-designer"></a>Karten-Designer 

Benötigen Sie ein Tool zum Entwerfen Ihrer Karten? Sehen Sie sich den browserbasierten adaptiven Karten-Designer unter an.[https://adaptivecards.io/designer](https://adaptivecards.io/designer)

[![Designer-Bildschirmfoto](media/tools/designer.jpg)](https://adaptivecards.io/designer)

### <a name="embed-the-designer-into-your-app"></a>Einbinden des Designers in Ihre APP

Aber warum sollten Sie Ihre Benutzer dorthin schicken, wenn Sie den Karten-Designer mithilfe der JavaScript-Bibliothek **direkt in Ihre Web-App einbetten** können. 

Sehen Sie sich das [adaptivecards-Designer-](https://npmjs.com/adaptivecards-designer) Paket an, um zu beginnen.

## <a name="schema-validation"></a>Schemavalidierung

Die Schema Validierung ist eine leistungsstarke Möglichkeit, das Erstellen von Tools zu vereinfachen und Tools zu aktivieren.

Wir haben eine komplette [JSON-Schema Datei](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) zum Bearbeiten und validieren adaptiver Karten in JSON bereitgestellt. Beachten Sie, dass die Schema-URL versioniert ist, neuere Versionen von adaptiven Karten über eine entsprechende URL verfügen.

In Visual Studio und Visual Studio Code können Sie die automatische IntelliSense-Funktion durch `$schema` einschließen eines Verweises erhalten.

![bad](media/tools/invalidjson1.png)

![AutoComplete](media/tools/autocomplete.png)

## <a name="example"></a>Beispiel

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a>Visual Studio Code Erweiterung

Wir haben eine Visual Studio Code-Erweiterung erstellt, mit der Sie die Karte, die Sie bearbeiten, in Echtzeit innerhalb des Editors selbst visualisieren können. 

![Erweiterung](media/tools/vscode-extension.png)

Öffnen Sie zum Installieren von den Extensions Marketplace, und suchen Sie nach **Adaptive Card Viewer**.

![Wein](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a>Verwendung

Wenn Sie eine JSON-Datei mit einer adaptiven Karten `$schema` Eigenschaft bearbeiten, können Sie Sie mithilfe `Ctrl+Shift+V A`von anzeigen.
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a>Optionen

Die folgende Visual Studio Code Einstellung ist für den adaptivecards-Viewer verfügbar. Dies kann in den Benutzereinstellungen oder Arbeitsbereichs Einstellungen festgelegt werden.

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a>Beispiel für WPF-Schnellansicht

Mit dem [Beispiel Projekt für die WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) -Schnellansicht können Sie Karten mithilfe von WPF/XAML auf einem Windows-Computer visualisieren.  Zum `hostconfig` bearbeiten und Anzeigen von Host Konfigurationseinstellungen ist ein Editor integriert. Speichern Sie diese Einstellungen als JSON, um Sie im Rendering in Ihrer Anwendung zu verwenden.

![WPF-Schnellansicht](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a>WPF imagerender-Beispiel

Das [imagerender-Beispiel Projekt](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) wandelt eine beliebige Karte mithilfe von WPF aus der Befehlszeile in eine PNG-Datei um. 
