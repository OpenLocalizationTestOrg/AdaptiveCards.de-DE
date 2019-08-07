---
title: Host Konfiguration-JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: a011ffc43c2990cd8eb568b9f1c449cf541f9a70
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732897"
---
# <a name="host-config---javascript"></a>Host Konfiguration-JavaScript

```js
// Create an AdaptiveCard instance
var adaptiveCard = new AdaptiveCards.AdaptiveCard();

// Set its hostConfig property unless you want to use the default Host Config
// Host Config defines the style and behavior of a card
adaptiveCard.hostConfig = new AdaptiveCards.HostConfig({
    fontFamily: "Segoe UI, Helvetica Neue, sans-serif"
    // More host config options
});

// Render the card to an HTML element:
var renderedCard = adaptiveCard.render();
```

## <a name="customization"></a>Anpassung

Es gibt drei Möglichkeiten, das Rendering von adaptiven Karten anzupassen: 
1. Host Konfiguration
2. CSS-Formatvorlagen
3. Benutzerdefiniertes Element Rendering

### <a name="hostconfig"></a>HostConfig 

Eine [Host Konfiguration](../../../rendering-cards/host-config.md) ist ein gemeinsam verwendeter Konfigurationsobjekt, das alle Renderer verstehen. Dies ermöglicht es Ihnen, gängige Stile (z. b. Schriftfamilie, Schriftgrößen, Standard Abstände) und Verhalten (z. b. die maximale Anzahl von Aktionen) zu definieren, die automatisch von den einzelnen Platt formrenderer interpretiert werden. 

Das Ziel ist, dass die systemeigene Benutzeroberfläche, die von jedem Platt formrenderer generiert wird, mit minimaler Arbeit an Ihrem Part sehr ähnlich aussieht.

```javascript
var renderOptions = {
    ...
    hostConfig: {
        // Define your host config object here
        // See the HostConfig docs for details
    }
};
```