---
title: Implementieren eines Renderers
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: 607ce40e70e0e54e61a572853a521d2dd70a5c23
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732612"
---
# <a name="adaptive-card-renderer-specification"></a><span data-ttu-id="d124b-102">Spezifikation für adaptiver Karten-Renderer</span><span class="sxs-lookup"><span data-stu-id="d124b-102">Adaptive Card Renderer Specification</span></span>

<span data-ttu-id="d124b-103">In der folgenden Spezifikation wird beschrieben, wie ein adaptiver Karten-Renderer auf jeder UI-Plattform implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="d124b-103">The following specification describes how implement an Adaptive Card renderer on any UI platform.</span></span>

> [!IMPORTANT]
> 
> <span data-ttu-id="d124b-104">Dieser Inhalt ist noch nicht abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="d124b-104">This content is not finished yet.</span></span> <span data-ttu-id="d124b-105">Überprüfen Sie es in Kürze.</span><span class="sxs-lookup"><span data-stu-id="d124b-105">Check back shortly.</span></span>

## <a name="sdk-versioning"></a><span data-ttu-id="d124b-106">SDK-Versionsverwaltung</span><span class="sxs-lookup"><span data-stu-id="d124b-106">SDK Versioning</span></span>

1. <span data-ttu-id="d124b-107">Die Haupt-und neben Version des SDKs `schema` sollten der Version entsprechen.</span><span class="sxs-lookup"><span data-stu-id="d124b-107">The SDK major and minor version **SHOULD** match the `schema` version.</span></span> 
1. <span data-ttu-id="d124b-108">Patch/Build **sollte** für rendererupdates verwendet werden, die keine Schema Änderungen aufweisen.</span><span class="sxs-lookup"><span data-stu-id="d124b-108">Patch/build **SHOULD** be used for renderer updates that don't have schema changes.</span></span>

## <a name="parsing-json"></a><span data-ttu-id="d124b-109">JSON-JSON</span><span class="sxs-lookup"><span data-stu-id="d124b-109">Parsing JSON</span></span>

### <a name="error-conditions"></a><span data-ttu-id="d124b-110">Fehlerbedingungen</span><span class="sxs-lookup"><span data-stu-id="d124b-110">Error conditions</span></span>
1. <span data-ttu-id="d124b-111">Ein Parser **muss** prüfen, ob es sich um gültige JSON-Inhalte handelt.</span><span class="sxs-lookup"><span data-stu-id="d124b-111">A parser **MUST** check that it's valid JSON content</span></span>
1. <span data-ttu-id="d124b-112">Ein Parser **muss** anhand des Schemas (erforderliche Eigenschaften usw.) überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-112">A parser **MUST** validate against the schema (required properties, etc)</span></span>
1. <span data-ttu-id="d124b-113">Die obigen Fehler **müssen** der Host-app (Ausnahme oder Äquivalent) gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-113">The above errors **MUST** be reported to the host app (exception or equivalent)</span></span>

### <a name="unknown-types"></a><span data-ttu-id="d124b-114">Unbekannte Typen</span><span class="sxs-lookup"><span data-stu-id="d124b-114">Unknown types</span></span>
1. <span data-ttu-id="d124b-115">Wenn Unbekannte "Typen" gefunden werden, müssen Sie aus dem Ergebnis **gelöscht werden** .</span><span class="sxs-lookup"><span data-stu-id="d124b-115">If unknown "types" are encountered they **MUST BE DROPPED** from the result</span></span>
1. <span data-ttu-id="d124b-116">Alle Änderungen an der Nutzlast (wie oben) **sollten** als Warnungen an die Host-App gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-116">Any alterations of the payload (like above) **SHOULD** be reported as warnings to the host app</span></span>

### <a name="unknown-properties"></a><span data-ttu-id="d124b-117">Unbekannte Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="d124b-117">Unknown properties</span></span>
1. <span data-ttu-id="d124b-118">Ein Parser **muss** **zusätzliche** Eigenschaften für Elemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="d124b-118">A parser **MUST** include **additional** properties on elements</span></span>

### <a name="additional-considerations"></a><span data-ttu-id="d124b-119">Weitere Überlegungen</span><span class="sxs-lookup"><span data-stu-id="d124b-119">Additional considerations</span></span>
1. <span data-ttu-id="d124b-120">Die `speak` -Eigenschaft kann SSML-Markup enthalten und **muss** wie angegeben an die Host-App zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-120">The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified</span></span>

## <a name="parsing-host-config"></a><span data-ttu-id="d124b-121">Die Host Konfiguration wird verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="d124b-121">Parsing Host Config</span></span>
1. <span data-ttu-id="d124b-122">TODO</span><span class="sxs-lookup"><span data-stu-id="d124b-122">TODO</span></span>

## <a name="versioning"></a><span data-ttu-id="d124b-123">Versionskontrolle</span><span class="sxs-lookup"><span data-stu-id="d124b-123">Versioning</span></span>

1. <span data-ttu-id="d124b-124">Ein Renderer **muss** eine bestimmte Version des Schemas implementieren.</span><span class="sxs-lookup"><span data-stu-id="d124b-124">A renderer **MUST** implement a particular version of the schema.</span></span> 
1. <span data-ttu-id="d124b-125">Der `AdaptiveCard` Konstruktor **muss** der `version` Eigenschaft basierend auf der aktuellen Schema Version einen Standardwert zuordnen.</span><span class="sxs-lookup"><span data-stu-id="d124b-125">The `AdaptiveCard` constructor **MUST** give the `version` property a default value based on the current schema version</span></span> 
1. <span data-ttu-id="d124b-126">Wenn ein Renderer auf eine `version` Eigenschaft in der `AdaptiveCard` trifft, die höher als die unterstützte Version ist, muss `fallbackText` er stattdessen den zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="d124b-126">If a renderer encounters a `version` property in the `AdaptiveCard` that is higher than the supported version, it **MUST** return the `fallbackText` instead.</span></span>

## <a name="rendering"></a><span data-ttu-id="d124b-127">Rendern</span><span class="sxs-lookup"><span data-stu-id="d124b-127">Rendering</span></span>

<span data-ttu-id="d124b-128">Ein `AdaptiveCard` besteht aus einem `body` und `actions`.</span><span class="sxs-lookup"><span data-stu-id="d124b-128">An `AdaptiveCard` consists of a `body` and `actions`.</span></span> <span data-ttu-id="d124b-129">Der `body` ist eine Auflistung von `CardElement`s, die ein Renderer in der Reihenfolge aufzählt und renderert.</span><span class="sxs-lookup"><span data-stu-id="d124b-129">The `body` is a collection of `CardElement`s that a renderer will enumerate and render in order.</span></span> 

1. <span data-ttu-id="d124b-130">Jedes Element **muss** sich auf die Breite seines übergeordneten Elements ( `display: block` in HTML-Code) ausdehnen.</span><span class="sxs-lookup"><span data-stu-id="d124b-130">Each Element **MUST** stretch to the width of its parent (think `display: block` in HTML).</span></span>
1. <span data-ttu-id="d124b-131">Ein Renderer **muss** unbekannte Elementtypen ignorieren und das Rendering der restlichen Nutzlast fortsetzen.</span><span class="sxs-lookup"><span data-stu-id="d124b-131">A renderer **MUST** ignore unknown element types, and continue rendering the rest of the payload.</span></span>

### <a name="spacing-and-separators"></a><span data-ttu-id="d124b-132">Abstände und Trennzeichen</span><span class="sxs-lookup"><span data-stu-id="d124b-132">Spacing and Separators</span></span>

1. <span data-ttu-id="d124b-133">Die `spacing` -Eigenschaft für jedes Element wirkt sich auf die Menge des Speicherplatzes zwischen dem aktuellen und dem **aktuellen** Element aus.</span><span class="sxs-lookup"><span data-stu-id="d124b-133">The `spacing` property on every element influences the amount of space between the **CURRENT** element and the one **BEFORE** it.</span></span>
1. <span data-ttu-id="d124b-134">Der Abstand **darf nur** angewendet werden, wenn ein Element vorangestellt ist.</span><span class="sxs-lookup"><span data-stu-id="d124b-134">Spacing **MUST ONLY** apply when there actually is an element preceding it.</span></span> <span data-ttu-id="d124b-135">(Z. b. gilt nicht für das erste Element in einem Array)</span><span class="sxs-lookup"><span data-stu-id="d124b-135">(E.g., won't apply to the first item in an array)</span></span>
1. <span data-ttu-id="d124b-136">Ein Renderer **muss** den zu verwendenden Speicherplatz aus dem `hostConfig` Abstand für den Enumerationswert nachschlagen, der auf das aktuelle Element angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="d124b-136">A renderer **MUST** look up the amount of space to use from the `hostConfig` spacing for the enum value applied to the current element.</span></span>
1. <span data-ttu-id="d124b-137">Wenn das-Element den `separator` `true`Wert hat, **muss** eine sichtbare Linie zwischen dem aktuellen Element und dem Element vor dem Element gezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-137">If the element has a `separator` value of `true`, then a visible line **MUST** be drawn between the current element and the one before it.</span></span>
1. <span data-ttu-id="d124b-138">Die Trennlinie **muss** mit `container.style.default.foregroundColor`gezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-138">The separator line **MUST** be drawn using the `container.style.default.foregroundColor`.</span></span>
1. <span data-ttu-id="d124b-139">Ein Trennzeichen **darf nur** gezeichnet werden, wenn **es sich** bei dem Element nicht um das erste Element im Array handelt.</span><span class="sxs-lookup"><span data-stu-id="d124b-139">A separator **MUST ONLY** be drawn if the item **IS NOT** the first in the array.</span></span>

### <a name="columns"></a><span data-ttu-id="d124b-140">Spalten</span><span class="sxs-lookup"><span data-stu-id="d124b-140">Columns</span></span>

1. <span data-ttu-id="d124b-141">`Column`Muss durch "Auto", "Stretch" oder ein gewichtetes Verhältnis interpretiert werden. `width`</span><span class="sxs-lookup"><span data-stu-id="d124b-141">`Column` `width` **MUST** be interpreted by "auto", "stretch" or a weighted ratio.</span></span>

### <a name="textblock"></a><span data-ttu-id="d124b-142">TextBlock</span><span class="sxs-lookup"><span data-stu-id="d124b-142">TextBlock</span></span>

1. <span data-ttu-id="d124b-143">Ein TextBlock **muss** eine einzelne Zeile annehmen, es sei `wrap` denn, `true`die-Eigenschaft ist.</span><span class="sxs-lookup"><span data-stu-id="d124b-143">A TextBlock **MUST** take up a single line unless the `wrap` property is `true`.</span></span> 
1. <span data-ttu-id="d124b-144">Der TextBlock **muss** überzähligen Text mit Auslassungs Zeichen (...) kürzen.</span><span class="sxs-lookup"><span data-stu-id="d124b-144">The text block **SHOULD** trim any excess text with an ellipsis (...)</span></span>

#### <a name="markdown"></a><span data-ttu-id="d124b-145">Markdown</span><span class="sxs-lookup"><span data-stu-id="d124b-145">Markdown</span></span>

1. <span data-ttu-id="d124b-146">Adaptive Karten ermöglichen eine Teilmenge von markdown und **sollten** in `TextBlock`unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-146">Adaptive Cards allow for a subset of Markdown and **SHOULD** be supported in `TextBlock`.</span></span> 
1. <span data-ttu-id="d124b-147">Vollständige [markdown-Anforderungen](../authoring-cards/text-features.md)</span><span class="sxs-lookup"><span data-stu-id="d124b-147">See full [markdown requirements](../authoring-cards/text-features.md)</span></span>

#### <a name="formatting-functions"></a><span data-ttu-id="d124b-148">Formatierungsfunktionen</span><span class="sxs-lookup"><span data-stu-id="d124b-148">Formatting functions</span></span>

1. <span data-ttu-id="d124b-149">`TextBlock`ermöglicht [Formatierungsfunktionen für Datum/Uhrzeit](../authoring-cards/text-features.md) , die für jeden Renderer unterstützt werden **müssen** .</span><span class="sxs-lookup"><span data-stu-id="d124b-149">`TextBlock` allows [DATE/TIME formatting functions](../authoring-cards/text-features.md) that **MUST** be supported on every renderer.</span></span>
1. <span data-ttu-id="d124b-150">**Alle Fehler müssen** die rohzeichenfolge in der Karte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d124b-150">**ALL FAILURES MUST** display the raw string in the card.</span></span> <span data-ttu-id="d124b-151">Es wurde keine benutzerfreundliche Nachricht versucht.</span><span class="sxs-lookup"><span data-stu-id="d124b-151">No friendly message attempted.</span></span> <span data-ttu-id="d124b-152">(Das Ziel, den Entwickler sofort zu beachten, dass ein Problem vorliegt)</span><span class="sxs-lookup"><span data-stu-id="d124b-152">(The goal being to make the developer immediately aware there is a problem)</span></span>

1. <span data-ttu-id="d124b-153">TODO: Regex einschließen</span><span class="sxs-lookup"><span data-stu-id="d124b-153">TODO: Include regex</span></span>

### <a name="images"></a><span data-ttu-id="d124b-154">Bilder</span><span class="sxs-lookup"><span data-stu-id="d124b-154">Images</span></span>

1. <span data-ttu-id="d124b-155">Mit einem Renderer können Host-apps erkennen, wann alle http-Images heruntergeladen wurden und die Karte vollständig gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="d124b-155">A renderer **SHOULD** allow host apps to know when all HTTP images have been downloaded and the card is "fully rendered"</span></span>
1. <span data-ttu-id="d124b-156">Ein Renderer **muss** beim Herunterladen von `maxImageSize` http-Images den Host Konfigurationsparameter überprüfen.</span><span class="sxs-lookup"><span data-stu-id="d124b-156">A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images</span></span>
1. <span data-ttu-id="d124b-157">Ein Renderer **muss** und `.png` unterstützen.`.jpeg`</span><span class="sxs-lookup"><span data-stu-id="d124b-157">A renderer **MUST** support `.png` and `.jpeg`</span></span>
1. <span data-ttu-id="d124b-158">Ein Renderer **sollte** Bilder `.gif` unterstützen.</span><span class="sxs-lookup"><span data-stu-id="d124b-158">A renderer **SHOULD** support `.gif` images</span></span>

### <a name="host-config"></a><span data-ttu-id="d124b-159">Host Konfiguration</span><span class="sxs-lookup"><span data-stu-id="d124b-159">Host Config</span></span>

* <span data-ttu-id="d124b-160">TODO: Wie lauten die Standardwerte?</span><span class="sxs-lookup"><span data-stu-id="d124b-160">TODO: What should the defaults be?</span></span> <span data-ttu-id="d124b-161">Sollten Sie alle diese freigeben?</span><span class="sxs-lookup"><span data-stu-id="d124b-161">Should they all share it?</span></span> <span data-ttu-id="d124b-162">Sollte eine gängige hostconfig. JSON-Datei in die Binärdateien eingebettet werden?</span><span class="sxs-lookup"><span data-stu-id="d124b-162">Should we embed a common hostConfig.json file in the binaries?</span></span>
* <span data-ttu-id="d124b-163">TODO: Ich denke, die hostconfig muss mit Versions Angabe versehen werden, um die Verarbeitung zu übernehmen?</span><span class="sxs-lookup"><span data-stu-id="d124b-163">TODO: I think HostConfig needs to be versioned as well for parsing?</span></span>

<span data-ttu-id="d124b-164">[`HostConfig`](host-config.md)ein frei gegebenes Konfigurationsobjekt, das angibt, wie ein adaptiver Karten-Renderer eine Benutzeroberfläche generiert.</span><span class="sxs-lookup"><span data-stu-id="d124b-164">[`HostConfig`](host-config.md) is a shared configuration object that specifies how an Adaptive Card Renderer generates UI.</span></span>  

<span data-ttu-id="d124b-165">Dadurch können Eigenschaften, die plattformunabhängig sind, von rendererarbeitern auf verschiedenen Plattformen und Geräten gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-165">This allows properties which are platform agnostic to be shared among renderers on different platforms and devices.</span></span> <span data-ttu-id="d124b-166">Außerdem können Tools erstellt werden, die Ihnen eine Vorstellung davon vermitteln, dass diese Karte für eine bestimmte Umgebung vorhanden wäre.</span><span class="sxs-lookup"><span data-stu-id="d124b-166">It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.</span></span>

1. <span data-ttu-id="d124b-167">Renderer **müssen** einen **Host Konfigurations** Parameter zum Hosten von apps verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="d124b-167">Renderers **MUST** expose a **Host Config** parameter to host apps</span></span>
1. <span data-ttu-id="d124b-168">Alle Elemente **müssen** entsprechend ihren jeweiligen Host Konfigurationseinstellungen formatiert werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-168">All elements **MUST** be styled according to their respective Host Config settings</span></span>

### <a name="native-platform-styling"></a><span data-ttu-id="d124b-169">Native Platt Form Formatierung</span><span class="sxs-lookup"><span data-stu-id="d124b-169">Native platform styling</span></span>

1. <span data-ttu-id="d124b-170">Jeder Elementtyp **sollte** mit dem generierten UI-Element einen nativen Platt Form Stil anfügen.</span><span class="sxs-lookup"><span data-stu-id="d124b-170">Each element type **SHOULD** attach a native platform style with the generated UI element.</span></span> <span data-ttu-id="d124b-171">Beispiel: in HTML haben wir den Elementtypen eine CSS-Klasse hinzugefügt, und in XAML weisen wir einen bestimmten Stil zu.</span><span class="sxs-lookup"><span data-stu-id="d124b-171">E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.</span></span>

## <a name="extensibility"></a><span data-ttu-id="d124b-172">Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="d124b-172">Extensibility</span></span> 

1. <span data-ttu-id="d124b-173">Ein Renderer **muss** zulassen, dass Host-apps standardmäßige Element-Renderer überschreiben.</span><span class="sxs-lookup"><span data-stu-id="d124b-173">A renderer **MUST** allow host apps to override default element renderers.</span></span> <span data-ttu-id="d124b-174">Ersetzen `TextBlock` Sie z. b. Rendering durch ihre eigene Logik.</span><span class="sxs-lookup"><span data-stu-id="d124b-174">E.g., replace `TextBlock` rendering with their own logic.</span></span>
1. <span data-ttu-id="d124b-175">Ein Renderer **muss** es Host-apps ermöglichen, benutzerdefinierte Elementtypen zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="d124b-175">A renderer **MUST** allow host apps to register custom element types.</span></span> <span data-ttu-id="d124b-176">Fügen Sie beispielsweise Unterstützung für ein `Rating` benutzerdefiniertes Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="d124b-176">E.g., add support for a custom `Rating` element</span></span>
1. <span data-ttu-id="d124b-177">Ein Renderer **muss** es Host-apps ermöglichen, die Unterstützung für ein Standardelement zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="d124b-177">A renderer **MUST** allow host apps to remove support for a default element.</span></span> <span data-ttu-id="d124b-178">Entfernen `Action.Submit` Sie z. b., wenn diese nicht unterstützt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="d124b-178">E.g., remove `Action.Submit` if they don't want it supported.</span></span>

## <a name="actions"></a><span data-ttu-id="d124b-179">Aktionen</span><span class="sxs-lookup"><span data-stu-id="d124b-179">Actions</span></span>

1. <span data-ttu-id="d124b-180">Wenn hostconfig `supportsInteractivity` ist `false`, **darf** ein Renderer keine Aktionen Renren.</span><span class="sxs-lookup"><span data-stu-id="d124b-180">If HostConfig `supportsInteractivity` is `false`, a renderer **MUST NOT** render any actions.</span></span>
1. <span data-ttu-id="d124b-181">Die `actions` -Eigenschaft **muss** als Schaltflächen in einer Aktionsleiste gerendert werden, normalerweise am unteren Rand der Karte.</span><span class="sxs-lookup"><span data-stu-id="d124b-181">The `actions` property **MUST** be rendered as buttons in some kind of action bar, usually at the bottom of the card.</span></span> 
1. <span data-ttu-id="d124b-182">Wenn eine Schaltfläche getippt wird, **muss** die Host-APP das Ereignis verarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="d124b-182">When a button is tapped it **MUST** allow the host app to handle the event.</span></span> 
1. <span data-ttu-id="d124b-183">Das Ereignis **muss** alle zugeordneten Eigenschaften mit der Aktion übergeben.</span><span class="sxs-lookup"><span data-stu-id="d124b-183">The event **MUST** pass along all associated properties with the action</span></span>
1. <span data-ttu-id="d124b-184">Das Ereignis **muss** an der `AdaptiveCard` übergeben werden, die ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="d124b-184">The event **MUST** pass along the `AdaptiveCard` which was executed</span></span>

<span data-ttu-id="d124b-185">Aktion</span><span class="sxs-lookup"><span data-stu-id="d124b-185">Action</span></span> | <span data-ttu-id="d124b-186">Verhalten</span><span class="sxs-lookup"><span data-stu-id="d124b-186">Behavior</span></span>
--- | ---
<span data-ttu-id="d124b-187">**Action.OpenUrl**</span><span class="sxs-lookup"><span data-stu-id="d124b-187">**Action.OpenUrl**</span></span> | <span data-ttu-id="d124b-188">Öffnen einer externen URL zum Anzeigen</span><span class="sxs-lookup"><span data-stu-id="d124b-188">Open an external URL for viewing</span></span>
<span data-ttu-id="d124b-189">**Action.ShowCard**</span><span class="sxs-lookup"><span data-stu-id="d124b-189">**Action.ShowCard**</span></span> | <span data-ttu-id="d124b-190">Fordert an, dass dem Benutzer eine unter Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d124b-190">Requests a sub-card to be shown to the user.</span></span>
<span data-ttu-id="d124b-191">**Action.Submit**</span><span class="sxs-lookup"><span data-stu-id="d124b-191">**Action.Submit**</span></span> | <span data-ttu-id="d124b-192">Bitten Sie, alle Eingabeelemente in einem Objekt zu erfassen, das dann über eine Methode, die von der Host Anwendung definiert wird, an Sie gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="d124b-192">Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

### <a name="actionopenurl"></a><span data-ttu-id="d124b-193">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="d124b-193">Action.OpenUrl</span></span>
1. <span data-ttu-id="d124b-194">`Action.OpenUrl`Eine URL **muss** mithilfe des nativen Platt Form Mechanismus geöffnet werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-194">`Action.OpenUrl` **SHOULD** open a URL using the native platform mechanism</span></span>
1. <span data-ttu-id="d124b-195">Wenn dies nicht möglich ist, **muss** es ein Ereignis für die Host-App zum Verarbeiten des Öffnens der URL ausführen.</span><span class="sxs-lookup"><span data-stu-id="d124b-195">If this is not possible it **MUST** raise an event to the host app to handle opening the URL.</span></span> <span data-ttu-id="d124b-196">Dieses Ereignis **muss** der Host-App ermöglichen, das Standardverhalten zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="d124b-196">This event **MUST** allow the host app to override the default behavior.</span></span> <span data-ttu-id="d124b-197">Beispielsweise können Sie die URL in ihrer eigenen APP öffnen.</span><span class="sxs-lookup"><span data-stu-id="d124b-197">E.g., let them open the URL within their own app.</span></span>

### <a name="actionshowcard"></a><span data-ttu-id="d124b-198">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="d124b-198">Action.ShowCard</span></span>

1. <span data-ttu-id="d124b-199">`Action.ShowCard`**Muss** auf irgendeine Weise unterstützt werden, basierend auf der hostconfig-Einstellung.</span><span class="sxs-lookup"><span data-stu-id="d124b-199">`Action.ShowCard` **MUST** be supported in some way, based on the hostConfig setting.</span></span> <span data-ttu-id="d124b-200">Es gibt zwei Modi: Inline und Popup.</span><span class="sxs-lookup"><span data-stu-id="d124b-200">There are two modes: inline, and popup.</span></span> <span data-ttu-id="d124b-201">Inline Karten **sollten** die Karten Sichtbarkeit automatisch umschalten.</span><span class="sxs-lookup"><span data-stu-id="d124b-201">Inline cards **SHOULD** toggle the card visibility automatically.</span></span> <span data-ttu-id="d124b-202">Im Popup Modus **sollte** ein Ereignis für die Host-App ausgelöst werden, um die Karte auf irgendeine Weise anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d124b-202">In popup mode, an event **SHOULD** be fired to the host app to show the card in some way.</span></span>

### <a name="actionsubmit"></a><span data-ttu-id="d124b-203">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="d124b-203">Action.Submit</span></span>

<span data-ttu-id="d124b-204">Die Submit-Aktion verhält sich wie ein HTML-Formular, mit dem Unterschied, dass der HTML-Code in der Regel eine HTTP Post-Methode auslöst</span><span class="sxs-lookup"><span data-stu-id="d124b-204">The Submit Action behaves like an HTML form submit, except that where HTML typically triggers an HTTP post, Adaptive Cards leaves it up to each host app to determine what "submit" means to them.</span></span> 

1. <span data-ttu-id="d124b-205">Wenn dadurch ein Ereignis ausgelöst werden **muss** , tippt der Benutzer auf die aufgerufene Aktion.</span><span class="sxs-lookup"><span data-stu-id="d124b-205">When this **MUST** raise an event the user taps the action invoked.</span></span>  
1. <span data-ttu-id="d124b-206">Die `data` -Eigenschaft **muss** in der Rückruf Nutzlast enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="d124b-206">The `data` property **MUST** be included in the callback payload.</span></span>
1. <span data-ttu-id="d124b-207">Für `Action.Submit` **muss** ein Renderer alle Eingaben auf der Karte erfassen und seine Werte abrufen.</span><span class="sxs-lookup"><span data-stu-id="d124b-207">For `Action.Submit`, a renderer **MUST** gather all inputs on the card and retrieve their values.</span></span> 

### <a name="selectaction"></a><span data-ttu-id="d124b-208">selectAction</span><span class="sxs-lookup"><span data-stu-id="d124b-208">selectAction</span></span>

1. <span data-ttu-id="d124b-209">Wenn die Host `supportedInteractivity` Konfiguration `false` ist `selectAction` , **darf nicht** als Berührungs Ziel dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-209">If Host Config `supportedInteractivity` is `false` then a `selectAction` **MUST NOT** render as a touch target.</span></span>
1. <span data-ttu-id="d124b-210">`Image`, `ColumnSet`und `Column` bieten eine`selectAction` Eigenschaft, die ausgeführt werden **soll** , wenn der Benutzer Sie aufruft, z. b. durch Tippen auf das-Element.</span><span class="sxs-lookup"><span data-stu-id="d124b-210">`Image`, `ColumnSet`, and `Column` offer a `selectAction` property, which **SHOULD** be executed when the user invokes it, e.g., by tapping the element.</span></span>

## <a name="inputs"></a><span data-ttu-id="d124b-211">Eingaben</span><span class="sxs-lookup"><span data-stu-id="d124b-211">Inputs</span></span>

1. <span data-ttu-id="d124b-212">Wenn hostconfig `supportsInteractivity` ein `false` Renderer ist, **darf** keine Eingaben gerbt werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-212">If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.</span></span>
2. <span data-ttu-id="d124b-213">Eingaben **sollten** mit der höchsten Genauigkeit gerbt werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-213">Inputs **SHOULD** render with the highest fidelity possible.</span></span> <span data-ttu-id="d124b-214">Beispielsweise `Input.Date` würde eine Datumsauswahl idealerweise einem Benutzer anbieten, aber wenn dies auf dem UI-Stapel nicht möglich ist, **muss** der Renderer auf das Rendern eines Standard Textfelds zurückgreifen.</span><span class="sxs-lookup"><span data-stu-id="d124b-214">For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then the renderer **MUST** fall back to rendering a standard text box.</span></span>
3. <span data-ttu-id="d124b-215">Ein Renderer **sollte** nach Möglichkeit `placeholderText` die Anzeige anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d124b-215">A renderer **SHOULD** display the `placeholderText` if possible</span></span>
4. <span data-ttu-id="d124b-216">Ein Renderer muss die Überprüfung der Eingabe **nicht** implementieren.</span><span class="sxs-lookup"><span data-stu-id="d124b-216">A renderer **DOES NOT** have to implement validation of the input.</span></span> <span data-ttu-id="d124b-217">Benutzer von adaptiven Karten müssen planen, beliebige empfangene Daten auf Ihrem Ende zu validieren.</span><span class="sxs-lookup"><span data-stu-id="d124b-217">Users of Adaptive Cards must plan to validate any received data on their end.</span></span>
5. <span data-ttu-id="d124b-218">Eingabe Wert Bindung **muss** ordnungsgemäß mit Escapezeichen versehen werden</span><span class="sxs-lookup"><span data-stu-id="d124b-218">Input value binding **MUST** be properly escaped</span></span>

6. <span data-ttu-id="d124b-219">Das Objekt **muss** wie folgt an die Host-App zurückgegeben werden:</span><span class="sxs-lookup"><span data-stu-id="d124b-219">The object **MUST** be returned to the host app as follows:</span></span>

   <span data-ttu-id="d124b-220">Wir machen keine Zusagen der Eingabe Überprüfung in adaptiven Karten. Daher liegt es an der empfangenden Partei, die Antwort ordnungsgemäß zu analysieren.</span><span class="sxs-lookup"><span data-stu-id="d124b-220">We do not make any promises of input validation in adaptive cards, so it's up to the receiving party to properly parse the response.</span></span> <span data-ttu-id="d124b-221">Beispielsweise kann eine Eingabe. Number "Hello" zurückgeben, und Sie müssen darauf vorbereitet werden.</span><span class="sxs-lookup"><span data-stu-id="d124b-221">E.g., a Input.Number could return "hello" and they need to be prepared for that.</span></span>


## <a name="events"></a><span data-ttu-id="d124b-222">Ereignisse</span><span class="sxs-lookup"><span data-stu-id="d124b-222">Events</span></span>

1. <span data-ttu-id="d124b-223">Ein Renderer **sollte** ein Ereignis auslösen, wenn sich die Sichtbarkeit eines Elements geändert hat, sodass die Host-APP einen Bildlauf zur Position durchführen kann.</span><span class="sxs-lookup"><span data-stu-id="d124b-223">A renderer **SHOULD** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.</span></span>
