---
title: 'Erweiterbarkeit: JavaScript SDK'
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 4c43637d81bcf43251638133c66d1c77b92ace56
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732912"
---
# <a name="extensibility---javascript"></a><span data-ttu-id="e1b4f-102">Erweiterbarkeit: JavaScript</span><span class="sxs-lookup"><span data-stu-id="e1b4f-102">Extensibility - JavaScript</span></span>

## <a name="implement-and-register-a-custom-element"></a><span data-ttu-id="e1b4f-103">Implementieren und Registrieren eines benutzerdefinierten Elements</span><span class="sxs-lookup"><span data-stu-id="e1b4f-103">Implement and register a custom element</span></span>

<span data-ttu-id="e1b4f-104">Die Schritte zum Erstellen eines benutzerdefinierten Adaptive Card-Elementtyps lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-104">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="e1b4f-105">Erstellen Sie eine neue Klasse, die von`CardElement`</span><span class="sxs-lookup"><span data-stu-id="e1b4f-105">Create a new class driving from `CardElement`</span></span>
- <span data-ttu-id="e1b4f-106">Implementieren der `getJsonTypeName`Methoden `parse`, `toJSON`, und`internalRender` `renderSpeech`</span><span class="sxs-lookup"><span data-stu-id="e1b4f-106">Implement its `getJsonTypeName`, `parse`, `toJSON`, `internalRender` and `renderSpeech` methods</span></span>
- <span data-ttu-id="e1b4f-107">Registrieren Sie Sie, indem Sie Sie der Element Registrierung des Renderers hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-107">Register it by adding it to the renderer's element registry</span></span>

<span data-ttu-id="e1b4f-108">Sehen wir uns ein Beispiel an, um ein einfaches Statusanzeige Element zu implementieren:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-108">Let's take an example and implement a simple Progress Bar element:</span></span>

```typescript
import * as Adaptive from "adaptivecards";

export class ProgressBar extends Adaptive.CardElement {
    private _title: string;
    private _value: number = 0;
    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new Adaptive.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return "ProgressBar";
    }

    toJSON(): any {
        let result = super.toJSON();

        Adaptive.setProperty(result, "title", this.title);
        Adaptive.setProperty(result, "value", this.value);

        return result;
    }

    parse(json: any, errors?: Array<Adaptive.IValidationError>) {
        super.parse(json, errors);

        this.title = Adaptive.getStringValueOrDefault(json["title"], undefined);
        this.value = Adaptive.getValueOrDefault(json["value"], this._value);
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (Adaptive.isNullOrEmpty(this.title)) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }

    renderSpeech(): string {
        return (Adaptive.isNullOrEmpty(this.title) ? "Progress" : this.title) + " " + Math.ceil(this.value) + "%";
    }

    get title(): string {
        return this._title;
    }

    set title(value: string) {
        if (this._title !== value) {
            this._title = value;

            this.updateLayout();
        }
    }

    get value(): number {
        return this._value;
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this._value !== adjustedValue) {
            this._value = adjustedValue;

            this.updateLayout();
        }
    }
}
```

<span data-ttu-id="e1b4f-109">Das ist alles.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-109">That's it.</span></span> <span data-ttu-id="e1b4f-110">Registrieren Sie nun einfach die Statusanzeige Klasse beim Renderer:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-110">Now just register the Progress Bar class with the renderer:</span></span>

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## <a name="implement-and-register-a-custom-action"></a><span data-ttu-id="e1b4f-111">Implementieren und Registrieren einer benutzerdefinierten Aktion</span><span class="sxs-lookup"><span data-stu-id="e1b4f-111">Implement and register a custom action</span></span>

<span data-ttu-id="e1b4f-112">Die Schritte zum Erstellen einer benutzerdefinierten adaptiven kartenaktion sind im Wesentlichen identisch mit denen für benutzerdefinierte Elemente.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-112">The steps for creating a custom Adaptive Card action are essentially the same as those for custom elements.</span></span> <span data-ttu-id="e1b4f-113">Im folgenden finden Sie ein einfaches Beispiel für eine Warnungs Aktion, bei der einfach ein Meldungs Feld mit konfigurier barem Text angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-113">Here is a simple example of an Alert Action that simply displays a message box with configurable text:</span></span>

```typescript
import * as Adaptive from "adaptivecards";

export class AlertAction extends Adaptive.Action {
    text: string;

    getJsonTypeName(): string {
        return "Action.ALert";
    }

    execute() {
        alert(this.text);
    }

    parse(json: any) {
        super.parse(json);

        this.text = Adaptive.getStringValueOrDefault(json["text"], "Alert!");
    }

    toJSON() {
        let result = super.toJSON();

        Adaptive.setProperty(result, "text", this.text);

        return result;
    }
}
```

<span data-ttu-id="e1b4f-114">Registrieren Sie nun die neue Aktion:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-114">Now register the new action:</span></span>

```
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## <a name="example"></a><span data-ttu-id="e1b4f-115">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e1b4f-115">Example</span></span>

<span data-ttu-id="e1b4f-116">Hier sehen Sie eine Beispiel Karte, die sowohl das ProgressBar-Element als auch die alertaction-Aktion verwendet:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-116">Here is a sample card that uses both the ProgressBar element and AlertAction action:</span></span>
```
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "size": "Medium",
            "weight": "Bolder",
            "text": "Custom ProgressBar element"
        },
        {
            "type": "ProgressBar",
            "title": "Please wait...",
            "value": 10
        }
    ],
    "actions": [
        {
            "type": "Action.Alert",
            "title": "Click me",
            "text": "Hello world!"
        }
    ]
}
```

<span data-ttu-id="e1b4f-117">Und so wird es gerendert ![: Image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span><span class="sxs-lookup"><span data-stu-id="e1b4f-117">And here is how it renders: ![image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span></span>
