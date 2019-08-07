---
title: Rendererstatus
author: matthidinger
ms.author: mahiding
ms.date: 10/12/2018
ms.topic: article
ms.openlocfilehash: 63426b2250407cc40af8c46975c10f57d1028a40
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733087"
---
# <a name="renderer-status"></a>Rendererstatus
Die folgenden Tabellen zeigen den aktuellen Status jedes Renderers, basierend auf den öffentlich veröffentlichten Versionen.

### <a name="parsing"></a>Analyse

|Funktionalität | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Rückgabe von Validierungs Fehlern | ✅ | ✅ | ✅ | ✅ | ✅ |
|Unbekannte Eigenschaften analysieren | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="card-rendering"></a>Karten Rendering

|Funktionalität | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Auf unterstützte Version überprüfen | ✅ | ✅ | ✅ | ✅ | ✅  |
|Vollständiges Schema Rendering | ✅ | ✅ | ✅ | ✅ | ✅ |
|Leiste der Rendering-Aktionen | ✅ | ✅ | ✅ | ✅ | ✅ |
|Unbekannte Elemente ignorieren | ✅ | ✅ | ✅ | ✅ | ✅ |
|Unterstützung für Host Konfigurationen | ✅ | ✅ | ✅ | ✅ | ✅ |
|Native Platt Form Formatierung | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="element-rendering"></a>Element Rendering

|Funktionalität | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Abstand und Trennzeichen | ✅ | ✅ | ✅ | ✅ | ✅ |
|[TextBlock-Datums-/Uhrzeitformatierung](../authoring-cards/text-features.md#datetime-formatting-and-localization) | ✅ | ✅ | ✅ | ✅ | ✅ |
|[TextBlock-markdown-Unterstützung](../authoring-cards/text-features.md#markdown) | ✅* | ✅ | ✅ | ✅ | ✅ |
|Vollständige Eingabe Unterstützung | ✅ | ✅ | ✅ | ✅ | ✅ |

\*Der HTML-Renderer schließt keine integrierte markdown-Unterstützung ein, um die Größe der Bibliothek zu minimieren und die Nutzung von Anwendungen zu ermöglichen, die Ihren bevorzugten markdown-Prozessor verwenden. Der HTML-Renderer verwendet jedoch automatisch markdown, wenn er geladen wird.

### <a name="extensibility"></a>Erweiterungen

|Funktionalität | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Element-Renderer überschreiben | ✅ | ✅ | ✅ | ✅ | ✅ |
|Neuen elementrenderer hinzufügen | ✅ | ✅ | ✅ | ✅ | ✅ |
|Element-Renderer entfernen | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Aktions-Renderer außer Kraft setzen/hinzufügen/entfernen](https://github.com/Microsoft/AdaptiveCards/issues/1671) | ✅ | ✅ | ❌ | ✅ | ✅ |

### <a name="actions"></a>Aktionen

| Funktionalität | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
| Action. OpenURL-Unterstützung | ✅ | ✅ | ✅ | ✅ | ✅  |
| Action. showcard-Unterstützung  | ✅ | ✅ | ✅ | ✅ | ✅ |
| Action. Submit-Unterstützung  | ✅ | ✅ | ✅ | ✅ | ✅  |
| Unterstützung von SelectAction | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="events"></a>Ereignisse

|       Funktionalität        | HTML | .NET | UWP | iOS | Android | 
|----------------------------|------|------|-----|-----|---------|
| Element Sichtbarkeit geändert |  ✅   |  ❌   |  ❌  |  ❌  | ❌ |

