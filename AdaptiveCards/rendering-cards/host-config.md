---
title: Hostconfig für Adaptive Karten
author: paulcam206
ms.author: paulcam
ms.date: 09/18/2018
ms.topic: reference
ms.openlocfilehash: 848ce3dd2ccca1f975dfd330c1c88292c753641d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733097"
---
# <a name="what-is-hostconfig"></a>Was ist hostconfig?
`HostConfig`ist ein **plattformübergreifendes Konfigurationsobjekt** , das angibt, wie ein adaptiver Karten-Renderer eine Benutzeroberfläche generiert.

Dadurch können Eigenschaften, die plattformunabhängig sind, von rendererarbeitern auf verschiedenen Plattformen und Geräten gemeinsam genutzt werden. Außerdem können Tools erstellt werden, die Ihnen eine Vorstellung davon vermitteln, dass diese Karte für eine bestimmte Umgebung vorhanden wäre.

Sehen Sie sich das Beispiel [hostconfig. JSON](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) an, um ein Gefühl für seine Inhalte zu erhalten.

---

   * [`AdaptiveCardConfig`](#schema-adaptivecardconfig)-Toplevel-Optionen für`AdaptiveCards`
   * [`ActionsConfig`](#schema-actionsconfig)-Optionen für `Action`s
   * [`ContainerStylesConfig`](#schema-containerstylesconfig)-Steuert das Formatieren für Standard-und Schwerpunkt Container
   * [`FactSetConfig`](#schema-factsetconfig)-Steuert die Anzeige von `FactSet`
   * [`FontSizesConfig`](#schema-fontsizesconfig)-Steuert Schriftart Größen Metriken für verschiedene Text Stile
   * [`FontWeightsConfig`](#schema-fontweightsconfig)-Steuert Schrift Gewichtungs Metriken
   * [`ForegroundColorsConfig`](#schema-foregroundcolorsconfig)-Steuert verschiedene Schriftart Farben.
   * [`ImageSetConfig`](#schema-imagesetconfig)-Steuert, `ImageSet`wie s angezeigt werden
   * [`ImageSizesConfig`](#schema-imagesizesconfig)-Steuerelement Größen `Image`
   * [`MediaConfig`](#schema-mediaconfig)-Steuert die Anzeige und das Verhalten `Media` von Elementen
   * [`SeparatorConfig`](#schema-separatorconfig)-Steuert, wie Trennzeichen angezeigt werden
   * [`ShowCardConfig`](#schema-showcardconfig)-Steuert das Verhalten und die Formatierung von`Action.ShowCard`
   * [`SpacingsConfig`](#schema-spacingsconfig)-Steuert, wie Elemente angelegt werden sollen
   * [`TextBlockConfig`](#schema-textblockconfig)-Parameter, die die Anzeige von Text Steuern

# <a name="card-configuration"></a>Karten Konfiguration

<a name="schema-adaptivecardconfig"></a>
## <a name="adaptivecardconfig"></a>AdaptiveCardConfig

Toplevel-Optionen für`AdaptiveCards`

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**allowCustomStyle**|`boolean`| Nein, Standard:`true`|Steuert, ob die benutzerdefinierte Formatierung zulässig ist.|1.0
|**supportsInteractivity**|`boolean`| Nein, Standard:`true`|Steuern, ob `Action`interaktive e aufgerufen werden dürfen|1.0
|**imageBaseUrl**|`string`| Nein|Beim Laden von Ressourcen zu verwendende Basis-URL|1.0
|**fontFamily**|`string`| Nein, Standard:`"Calibri"`|Schriftart, die beim Rendern von Text verwendet werden soll|1.0
|**actions**|`object`| Nein|Optionen für `Action`s|1.0
|**adaptiveCard**|`object`| Nein|Toplevel-Optionen für`AdaptiveCards`|1.0
|**containerStyles**|`object`| Nein|Steuert das Formatieren für Standard-und Schwerpunkt Container|1.0
|**imageSizes**|`object`| Nein|Steuer `Image` Element Größen|1.0
|**imageSet**|`object`| Nein|Steuert, `ImageSet`wie s angezeigt werden.|1.0
|**factSet**|`object`| Nein|Steuert die Anzeige von `FactSet`|1.0
|**fontSizes**|`object`| Nein|Steuert Schriftart Größen Metriken für verschiedene Text Stile|1.0
|**fontWeights**|`object`| Nein|Steuert Schriftart Gewichtungs Metriken|1.0
|**spacing**|`object`| Nein|Steuert, wie Elemente angelegt werden sollen.|1.0
|**separator**|`object`| Nein|Steuert, wie Trennzeichen angezeigt werden.|1.0
|**media**|`object`| Nein|Steuert die Anzeige und das Verhalten `Media` von Elementen.|1.1


<a name="schema-actionsconfig"></a>
## <a name="actionsconfig"></a>ActionsConfig

Optionen für `Action`s

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**actionsOrientation**|`string`| Nein, Standard:`"horizontal"`|Steuert, wie Schaltflächen angelegt werden|1.0
|**actionAlignment**|`string`| Nein, Standard:`"stretch"`|Steuerelement Layout von Schaltflächen|1.0
|**buttonSpacing**|`integer`| Nein, Standard:`10`|Steuert, wie viel Abstand zwischen Schaltflächen verwendet werden soll.|1.0
|**maxActions**|`integer`| Nein, Standard:`5`|Steuert, wie viele Aktionen insgesamt zulässig sind.|1.0
|**spacing**|`string`| Nein, Standard:`"default"`|Steuert den Gesamtabstand des Action-Elements.|1.0
|**showCard**|`object`| Nein|Steuert das Verhalten und die Formatierung von`Action.ShowCard`|1.0
|**iconPlacement**|`string`| Nein, Standard:`"aboveTitle"`|Steuert, wo das Aktions Symbol platziert werden soll.|1.0
|**iconSize**|`integer`| Nein, Standard:`30`|Steuerelement Größe des Aktions Symbols|1.0


<a name="schema-containerstylesconfig"></a>
## <a name="containerstylesconfig"></a>ContainerStylesConfig

Steuert das Formatieren für Standard-und Schwerpunkt Container

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**default**|`object`| Nein|Standardcontainer Stil|1.0
|**emphasis**|`object`| Nein|Der zu verwendende Container Stil.|1.0


<a name="schema-factsetconfig"></a>
## <a name="factsetconfig"></a>FactSetConfig

Steuert die Anzeige von `FactSet`

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**title**|`object`| Nein, Standard:`{"weight":"bolder","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":150}`|Parameter, die die Anzeige von Text Steuern|1.0
|**value**|`object`| Nein, Standard:`{"weight":"default","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":0}`|Parameter, die die Anzeige von Text Steuern|1.0
|**spacing**|`integer`| Nein, Standard:`10`|&nbsp;|1.0


<a name="schema-fontsizesconfig"></a>
## <a name="fontsizesconfig"></a>FontSizesConfig

Steuert Schriftart Größen Metriken für verschiedene Text Stile

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Nein, Standard:`10`|Kleiner Schrift Grad|1.0
|**default**|`integer`| Nein, Standard:`12`|Standardschrift Größe|1.0
|**medium**|`integer`| Nein, Standard:`14`|Mittlere Schriftgröße|1.0
|**large**|`integer`| Nein, Standard:`17`|Große Schriftgröße|1.0
|**extraLarge**|`integer`| Nein, Standard:`20`|Sehr große Schriftgröße|1.0


<a name="schema-fontweightsconfig"></a>
## <a name="fontweightsconfig"></a>FontWeightsConfig

Steuert Schriftart Gewichtungs Metriken

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**lighter**|`integer`| Nein, Standard:`200`|&nbsp;|1.0
|**default**|`integer`| Nein, Standard:`400`|&nbsp;|1.0
|**bolder**|`integer`| Nein, Standard:`800`|&nbsp;|1.0


<a name="schema-foregroundcolorsconfig"></a>
## <a name="foregroundcolorsconfig"></a>ForegroundColorsConfig

Steuert verschiedene Schriftart Farben.

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**default**|`object`| Nein, Standard:`{"default":"#FF000000","subtle":"#B2000000"}`|&nbsp;|1.0
|**accent**|`object`| Nein, Standard:`{"default":"#FF0000FF","subtle":"#B20000FF"}`|&nbsp;|1.0
|**dark**|`object`| Nein, Standard:`{"default":"#FF101010","subtle":"#B2101010"}`|&nbsp;|1.0
|**light**|`object`| Nein, Standard:`{"default":"#FFFFFFFF","subtle":"#B2FFFFFF"}`|&nbsp;|1.0
|**good**|`object`| Nein, Standard:`{"default":"#FF008000","subtle":"#B2008000"}`|&nbsp;|1.0
|**warning**|`object`| Nein, Standard:`{"default":"#FFFFD700","subtle":"#B2FFD700"}`|&nbsp;|1.0
|**attention**|`object`| Nein, Standard:`{"default":"#FF8B0000","subtle":"#B28B0000"}`|&nbsp;|1.0


<a name="schema-imagesetconfig"></a>
## <a name="imagesetconfig"></a>ImageSetConfig

Steuert, `ImageSet`wie s angezeigt werden.

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**imageSize**|`string`| Nein, Standard:`"auto"`|Steuert die Größe einzelner Bildgrößen.|1.0
|**maxImageHeight**|`integer`| Nein, Standard:`100`|Bildhöhe auf diesen Wert einschränken|1.0


<a name="schema-imagesizesconfig"></a>
## <a name="imagesizesconfig"></a>ImageSizesConfig

Steuer `Image` Element Größen

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Nein, Standard:`80`|Kleiner Bildgrößen Wert|1.0
|**medium**|`integer`| Nein, Standard:`120`|Wert für mittlere Bild Größe|1.0
|**large**|`integer`| Nein, Standard:`180`|Wert für große Bild Größe|1.0


<a name="schema-mediaconfig"></a>
## <a name="mediaconfig"></a>MediaConfig

Steuert die Anzeige und das Verhalten `Media` von Elementen.

#### <a name="introduced-in-version-11"></a>Eingeführt in Version 1,1

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**defaultPoster**|`string`| Nein|URI zum Bild, das angezeigt werden soll, wenn Wiedergabe Schaltfläche nicht aufgerufen|1.1
|**playButton**|`string`| Nein|Bild, das als Wiedergabe Schaltfläche angezeigt wird|1.1
|**allowInlinePlayback**|`boolean`| Nein, Standard:`true`|Ob Medien Inline angezeigt oder extern aufgerufen werden soll|1.1


<a name="schema-separatorconfig"></a>
## <a name="separatorconfig"></a>SeparatorConfig

Steuert, wie Trennzeichen angezeigt werden.

|Eigenschaft|Typ|Erforderlich|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**lineThickness**|`integer`| Nein, Standard:`1`|Stärke der Trennlinie|1.0
|**lineColor**|`string,null`| Nein, Standard:`#B2000000`|Beim Zeichnen der Trennlinie zu verwendende Farbe|1.0


<a name="schema-showcardconfig"></a>
## <a name="showcardconfig"></a>ShowCardConfig

Steuert das Verhalten und die Formatierung von`Action.ShowCard`

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**actionMode**|`string`| Nein, Standard:`"inline"`|Steuert, wie die Karte angezeigt wird.|1.0
|**style**|`object`| Nein, Standard:`emphasis`|Steuert das Formatieren eines Containers|1.0
|**inlineTopMargin**|`integer`| Nein, Standard:`16`|Der für die Anzeige der Karte zu verwendende Rand.|1.0


<a name="schema-spacingsconfig"></a>
## <a name="spacingsconfig"></a>SpacingsConfig

Steuert, wie Elemente angelegt werden sollen.

|Eigenschaft|Typ|Erforderlich|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Nein, Standard:`3`|Kleiner Abstands Wert|1.0
|**default**|`integer`| Nein, Standard:`8`|Standardabstand Wert|1.0
|**medium**|`integer`| Nein, Standard:`20`|Wert für mittlere Abstände|1.0
|**large**|`integer`| Nein, Standard:`30`|Wert für große Abstände|1.0
|**extraLarge**|`integer`| Nein, Standard:`40`|Zusätzlicher Wert für große Abstände|1.0
|**padding**|`integer`| Nein, Standard:`20`|Padding-Wert|1.0


<a name="schema-textblockconfig"></a>
## <a name="textblockconfig"></a>TextBlockConfig

Parameter, die die Anzeige von Text Steuern

|Eigenschaft|Typ|Required|Beschreibung|Version|
|--------|----|--------|-----------|-------|
|**size**|`string`| Nein, Standard:`"default"`|Schrift Grad, der verwendet werden soll, wenn eine Karte nicht angegeben wird|1.0
|**weight**|`string`| Nein, Standard:`"normal"`|Zu verwendende Schrift Breite, wenn eine Karte nicht angegeben wird|1.0
|**color**|`string`| Nein, Standard:`"default"`|Zu verwendende Schriftfarbe, wenn eine Karte nicht angegeben wird|1.0
|**isSubtle**|`boolean`| Nein, Standard:`false`|Sollte Text fein sein, wenn eine Karte nicht angibt|1.0
|**wrap**|`boolean`| Nein, Standard:`true`|Sollte Text Umbruch, wenn eine Karte nicht angegeben wird|1.0
|**maxWidth**|`integer`| Nein, Standard:`0`|Maximale Breite, die verwendet werden soll, wenn eine Karte nicht angibt|1.0
