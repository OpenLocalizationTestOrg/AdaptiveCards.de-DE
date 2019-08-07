---
title: Android-SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: e565606f4a112d4f1fa08e2989f392f1abf0887f
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732537"
---
# <a name="extensibility---android"></a><span data-ttu-id="19d8d-102">Erweiterbarkeit: Android</span><span class="sxs-lookup"><span data-stu-id="19d8d-102">Extensibility - Android</span></span>

<span data-ttu-id="19d8d-103">Der Android-Renderer kann erweitert werden, um mehrere Szenarien zu unterstützen, darunter:</span><span class="sxs-lookup"><span data-stu-id="19d8d-103">The Android renderer can be extended to support multiple scenarios including:</span></span>
* [<span data-ttu-id="19d8d-104">Benutzerdefinierte Verarbeitung von Karten Elementen</span><span class="sxs-lookup"><span data-stu-id="19d8d-104">Custom Parsing of Card Elements</span></span>](#custom-parsing-of-card-elements)
* [<span data-ttu-id="19d8d-105">Benutzerdefiniertes Rendering von Karten Elementen</span><span class="sxs-lookup"><span data-stu-id="19d8d-105">Custom Rendering of Card Elements</span></span>](#custom-rendering-of-card-elements)
* <span data-ttu-id="19d8d-106">[Benutzerdefiniertes Rendering von Aktionen](#custom-rendering-of-actions) (Seit v 1.2)</span><span class="sxs-lookup"><span data-stu-id="19d8d-106">[Custom Rendering of Actions](#custom-rendering-of-actions) (Since v1.2)</span></span>
* <span data-ttu-id="19d8d-107">[Laden von benutzerdefinierten Images](#custom-image-loading) (Seit v 1.0.1)</span><span class="sxs-lookup"><span data-stu-id="19d8d-107">[Custom Image Loading](#custom-image-loading) (Since v1.0.1)</span></span>
* <span data-ttu-id="19d8d-108">[Laden benutzerdefinierter Medien](#custom-media-loading) (Seit v 1.1)</span><span class="sxs-lookup"><span data-stu-id="19d8d-108">[Custom Media Loading](#custom-media-loading) (Since v1.1)</span></span>

## <a name="custom-parsing-of-card-elements"></a><span data-ttu-id="19d8d-109">Benutzerdefinierte Verarbeitung von Karten Elementen</span><span class="sxs-lookup"><span data-stu-id="19d8d-109">Custom Parsing of Card Elements</span></span>

<span data-ttu-id="19d8d-110">Sie können den Parser erweitern, um Kartenelemente zu unterstützen, die Sie definiert haben.</span><span class="sxs-lookup"><span data-stu-id="19d8d-110">You may extend the parser to support card elements that you have defined.</span></span> <span data-ttu-id="19d8d-111">Angenommen, wir haben einen neuen Elementtyp, der wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="19d8d-111">For example, say we have a new element type that looks like this:</span></span>
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

<span data-ttu-id="19d8d-112">Anschließend zeigen die folgenden Zeilen, wie Sie Sie in ein cardelta-Element analysieren können, das sich vom basecardelta-Element erstreckt:</span><span class="sxs-lookup"><span data-stu-id="19d8d-112">Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:</span></span>
```java
public class MyCustomCardElement extends BaseCardElement
{

    public MyCustomCardElement(CardElementType type) {
        super(type);
    }

    public String getMyTypeData()
    {
        return myTypeData;
    }

    public void setMyTypeData(String data)
    {
        myTypeData = data;
    }

    private String myTypeData;
}

public class MyCardElementParser extends BaseCardElementParser
{
    @Override
    public BaseCardElement Deserialize(ElementParserRegistration elementParserRegistration, ActionParserRegistration actionParserRegistration, JsonValue value)
    {
        MyCustomCardElement element = new CustomCardElement(CardElementType.Custom);
        element.SetElementTypeString("MyType");
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setMyTypeData(obj.getString("secret"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setMyTypeData("Failed");
        }
        return element;
    }
}
```

<span data-ttu-id="19d8d-113">Und auf diese Weise können Sie den Parser registrieren und ein adaptivecard-Objekt abrufen, das das benutzerdefinierte Element enthält:</span><span class="sxs-lookup"><span data-stu-id="19d8d-113">And this is how to register the parser and get an AdaptiveCard object that contains the custom element:</span></span>
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

<span data-ttu-id="19d8d-114">Nächstes kommt zum Rendern des benutzerdefinierten Elements.</span><span class="sxs-lookup"><span data-stu-id="19d8d-114">Next comes rendering the custom element</span></span>

## <a name="custom-rendering-of-card-elements"></a><span data-ttu-id="19d8d-115">Benutzerdefiniertes Rendering von Karten Elementen</span><span class="sxs-lookup"><span data-stu-id="19d8d-115">Custom Rendering of Card Elements</span></span>

> [!IMPORTANT]
>
> <span data-ttu-id="19d8d-116">**Liste der wichtigen Änderungen**</span><span class="sxs-lookup"><span data-stu-id="19d8d-116">**List of Breaking Changes**</span></span>
>
> [<span data-ttu-id="19d8d-117">Wichtige Änderungen für v 1.2</span><span class="sxs-lookup"><span data-stu-id="19d8d-117">Breaking changes for v1.2</span></span>](#breaking-changes-for-v12)

<span data-ttu-id="19d8d-118">Um unseren eigenen benutzerdefinierten Renderer für den Typ zu definieren, müssen wir zuerst eine Klasse erstellen, ```BaseCardElementRenderer```die sich von erstreckt:</span><span class="sxs-lookup"><span data-stu-id="19d8d-118">To define our own custom renderer for our type, we must first create a class that extends from ```BaseCardElementRenderer```:</span></span>
```java
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(Context context, FragmentManager fragmentManager, ViewGroup viewGroup, BaseCardElement baseCardElement, Vector<IInputHandler> inputActionHandlerList, ICardActionHandler cardActionHandler, HostConfig hostConfig, ContainerStyle containerStyle) {

        //Call findImplObj on baseCardElement to get the instance we returned at parse. We can then cast that object to our type
        CustomCardElement element = (CustomCardElement) baseCardElement.findImplObj();

        //Create some view and add it to the view group
        TextView textView = new TextView(context);
        textView.setText(element.getMyTypeData());
        textView.setAllCaps(true);
        viewGroup.addView(textView);

        //return the view
        return textView;
    }
}
```

<span data-ttu-id="19d8d-119">Anschließend registrieren wir diesen Renderer wie folgt:</span><span class="sxs-lookup"><span data-stu-id="19d8d-119">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a><span data-ttu-id="19d8d-120">Wichtige Änderungen für v 1.2</span><span class="sxs-lookup"><span data-stu-id="19d8d-120">Breaking changes for v1.2</span></span>

<span data-ttu-id="19d8d-121">Die ```render``` -Methode wurde so geändert, ```RenderedAdaptiveCard``` dass Sie ```ContainerStyle``` den-Parameter enthält, und wurde für eine renderargs geändert, in der das ContainerStyle jetzt enthalten ist, sodass eine Klasse, die den basecardelta-entrenderer erweitert, wie folgt aussehen sollte:</span><span class="sxs-lookup"><span data-stu-id="19d8d-121">The ```render``` method was changed to include the ```RenderedAdaptiveCard``` parameter and ```ContainerStyle``` was changed for a RenderArgs where the ContainerStyle is now contained so a class that extends BaseCardElementRenderer should look like this</span></span>

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a><span data-ttu-id="19d8d-122">Benutzerdefinierte Verarbeitung von Karten Aktionen</span><span class="sxs-lookup"><span data-stu-id="19d8d-122">Custom Parsing of Card Actions</span></span>

<span data-ttu-id="19d8d-123">Ähnlich wie beim Analysieren von benutzerdefinierten Karten Elementen in v 1.2 wurde die Möglichkeit, benutzerdefinierte Aktionen zu analysieren, eingeführt.</span><span class="sxs-lookup"><span data-stu-id="19d8d-123">Similarly to parsing custom card elements in v1.2 the possibility to parse custom actions was introduced.</span></span> <span data-ttu-id="19d8d-124">Angenommen, wir haben einen neuen Aktionstyp, der wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="19d8d-124">For example, say we have a new action type that looks like this:</span></span>
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

<span data-ttu-id="19d8d-125">Anschließend zeigen die folgenden Zeilen, wie Sie Sie in ein "aktionelement" analysieren können, ```BaseActionElement```das sich von erstreckt:</span><span class="sxs-lookup"><span data-stu-id="19d8d-125">Then the following lines demonstrate how to parse it into a ActionElement that extends from the ```BaseActionElement```:</span></span>
```java
public class MyActionElement extends BaseActionElement
{
    public MyActionElement(ActionType type) 
    {
        super(type);
    }

    public String getActionData()
    {
        return mActionData;
    }

    public void setActionData(String s)
    {
        mActionData = s;
    }

    private String mActionData;
    public static final String MyActionId = "myAction";
}

public class MyActionParser extends ActionElementParser
{
    @Override
    public BaseActionElement Deserialize(ParseContext context, JsonValue value)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setActionData(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setActionData("Failure");
        }
        return element;
    }

    @Override
    public BaseActionElement DeserializeFromString(ParseContext context, String jsonString)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        try {
            JSONObject obj = new JSONObject(jsonString);
            element.setBackwardString(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setBackwardString("Failure");
        }
        return element;
    }
}
```

<span data-ttu-id="19d8d-126">In den nächsten Zeilen wird veranschaulicht, wie Sie den Parser registrieren und ein adaptivecard-Objekt abrufen, das das benutzerdefinierte Action-Element enthält:</span><span class="sxs-lookup"><span data-stu-id="19d8d-126">And the next lines demonstrate how to register the parser and get an AdaptiveCard object that contains the custom action element:</span></span>
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="19d8d-127">Nächste Schritte zum Rendern der benutzerdefinierten Aktion</span><span class="sxs-lookup"><span data-stu-id="19d8d-127">Next comes rendering the custom action</span></span>

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="19d8d-128">Benutzerdefiniertes Rendering von Aktionen</span><span class="sxs-lookup"><span data-stu-id="19d8d-128">Custom Rendering of Actions</span></span>

<span data-ttu-id="19d8d-129">Um einen eigenen benutzerdefinierten aktionsrenderer für den Typ zu definieren, müssen wir zuerst eine Klasse erstellen ```BaseActionElementRenderer```, die sich von erstreckt:</span><span class="sxs-lookup"><span data-stu-id="19d8d-129">To define our own custom action renderer for our type, we must first create a class that extends from ```BaseActionElementRenderer```:</span></span>
```java
public class MyActionRenderer extends BaseActionElementRenderer
{
    @Override
    public Button render(RenderedAdaptiveCard renderedCard,
                         Context context,
                         FragmentManager fragmentManager,
                         ViewGroup viewGroup,
                         BaseActionElement baseActionElement,
                         ICardActionHandler cardActionHandler,
                         HostConfig hostConfig,
                         RenderArgs renderArgs)
    {
        Button myActionButton = new Button(context);

        CustomActionElement customAction = (CustomActionElement) baseActionElement.findImplObj();

        myActionButton.setBackgroundColor(getResources().getColor(R.color.greenActionColor));
        myActionButton.setText(customAction.getMessage());
        myActionButton.setAllCaps(false);
        myActionButton.setOnClickListener(new BaseActionElementRenderer.ActionOnClickListener(renderedCard, baseActionElement, cardActionHandler));

        viewGroup.addView(myActionButton);

        return myActionButton;
    }
}
```

<span data-ttu-id="19d8d-130">Anschließend registrieren wir diesen Renderer wie folgt:</span><span class="sxs-lookup"><span data-stu-id="19d8d-130">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="19d8d-131">Benutzerdefiniertes Rendering von Aktionen</span><span class="sxs-lookup"><span data-stu-id="19d8d-131">Custom rendering of actions</span></span>

[!IMPORTANT]
> <span data-ttu-id="19d8d-132">Änderungen am benutzerdefinierten Rendering von Aktionen sind für v 1.2 geplant, aber noch nicht abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="19d8d-132">Changes to the custom rendering of actions are planned for v1.2 but are not completed yet</span></span>

## <a name="custom-image-loading"></a><span data-ttu-id="19d8d-133">Laden von benutzerdefinierten Images</span><span class="sxs-lookup"><span data-stu-id="19d8d-133">Custom image loading</span></span>

### <a name="ionlineimageloader"></a><span data-ttu-id="19d8d-134">IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="19d8d-134">IOnlineImageLoader</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19d8d-135">**Es kann nur ein "ionlineimageloader" registriert werden, und es hat Vorrang vor der Standardmethode zum Abrufen von Bildern.**</span><span class="sxs-lookup"><span data-stu-id="19d8d-135">**Only one IOnlineImageLoader can be registered and it takes precedence against the default way of retrieving images**</span></span>

<span data-ttu-id="19d8d-136">Um Entwicklern das Abrufen von Bildern zu ermöglichen, die nicht nur aus einer Online Quelle heruntergeladen oder abgerufen werden konnten, bevor Sie abgerufen werden konnten, wurde der ionlineimageloader hinzugefügt, um diese Art von Situationen zu lösen.</span><span class="sxs-lookup"><span data-stu-id="19d8d-136">In order to allow developers to get images that could not just be downloaded or retrieved from an online source or required previous steps before they could be retrieved, the IOnlineImageLoader was added to solve this kind of situations.</span></span> <span data-ttu-id="19d8d-137">Um einen onlineimageloader zu implementieren, müssen Sie nur die-Methode implementieren.</span><span class="sxs-lookup"><span data-stu-id="19d8d-137">To implement an OnlineImageLoader you must only implement the method</span></span> 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

<span data-ttu-id="19d8d-138">Im folgenden finden Sie ein Beispiel für einen onlineimageloader, der alle Bilder für ein Cat-Bild ändert.</span><span class="sxs-lookup"><span data-stu-id="19d8d-138">Here's an example of an OnlineImageLoader which changes all images for a cat image</span></span>

```java
public class OnlineImageLoader implements IOnlineImageLoader
{
    public OnlineImageLoader(){}

    @Override
    public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
    {
        String catImnageUri = "http://adaptivecards.io/content/cats/1.png";
        byte[] bytes = HttpRequestHelper.get(catImnageUri);
        if (bytes == null)
        {
            throw new IOException("Failed to retrieve content from " + catImnageUri);
        }

        Bitmap bitmap = BitmapFactory.decodeByteArray(bytes, 0, bytes.length);

        if (bitmap == null)
        {
            throw new IOException("Failed to convert content to bitmap: " + new String(bytes));
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

<span data-ttu-id="19d8d-139">Zum Registrieren dieses Bild Lade Moduls müssen Sie schließlich nur diese Zeile zum Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="19d8d-139">Finally, to register this image loader, you must only add this line to your code.</span></span>

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a><span data-ttu-id="19d8d-140">Iresourceresolver (ist von "ionlineimageloader" veraltet)</span><span class="sxs-lookup"><span data-stu-id="19d8d-140">IResourceResolver (deprecates IOnlineImageLoader)</span></span>

<span data-ttu-id="19d8d-141">Für v 1.2 wurde dem Android-Renderer die Unterstützung für Full resourceresolvers hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="19d8d-141">For v1.2, the support for full ResourceResolvers was added to the android renderer.</span></span> <span data-ttu-id="19d8d-142">Die Implementierung eines ressourcenresolvers ähnelt der eines "ionlineimageloader", aber mit resourceresolvers kann ein Entwickler mehrere Methoden zum Abrufen von Bildern aus einer beliebigen Art von Quelle auf einer einzelnen Karte hinzufügen. Dies geschieht durch Verknüpfen der einzelnen resourceresolver. zu einem eindeutigen Präfix, das abgefragt wird, wenn versucht wird, ein Bild abzurufen.</span><span class="sxs-lookup"><span data-stu-id="19d8d-142">The implementation of a resource resolver is really similar to that of a IOnlineImageLoader but having ResourceResolvers allows a developer to add multiple ways to retrieve images from any kind of source in a single card, this is done by linking each ResourceResolver to a unique prefix which will be queried when trying to retrieve an image.</span></span> 

<span data-ttu-id="19d8d-143">Sie können einen resourceresolver implementieren, der diesem ähnelt.</span><span class="sxs-lookup"><span data-stu-id="19d8d-143">You can implement a ResourceResolver similar to this</span></span>

```java
public class ResourceResolver implements IResourceResolver
{
    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);
        byte[] decodedByteArray = Util.getBytes(decodedDataUri);
        bitmap = BitmapFactory.decodeByteArray(decodedByteArray, 0, decodedByteArray.length);

        return new HttpRequestResult<>(bitmap);
    }

    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);

        if (uri.startsWith("data:image/svg")) {
            String svgString = AdaptiveBase64Util.ExtractDataFromUri(uri);
            String decodedSvgString = URLDecoder.decode(svgString, "UTF-8");
            Sharp sharp = Sharp.loadString(decodedSvgString);
            Drawable drawable = sharp.getDrawable();
            bitmap = ImageUtil.drawableToBitmap(drawable, maxWidth);
        }
        else
        {
            try
            {
                return genericImageLoaderAsync.loadDataUriImage(uri);
            }
            catch (Exception e)
            {
                return new HttpRequestResult<>(e);
            }
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

<span data-ttu-id="19d8d-144">Wie bereits erwähnt, können Sie mehrere resourceresolvers registrieren. um einen resourceresolver zu registrieren, können Sie dies tun.</span><span class="sxs-lookup"><span data-stu-id="19d8d-144">As mentioned previously, you can register multiple ResourceResolvers, to register a ResourceResolver you can do this</span></span>

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a><span data-ttu-id="19d8d-145">Transformieren eines "ionlineimageloader" in einen "iresourceresolver"</span><span class="sxs-lookup"><span data-stu-id="19d8d-145">Transforming an IOnlineImageLoader to an IResourceResolver</span></span> 

<span data-ttu-id="19d8d-146">Die Transformation von "ionlineimageloader" in "iresourceresolver" ist eine recht einfache Aufgabe, da die Methoden der letzteren versucht haben, so ähnlich wie der "ionlineimageloader" wie möglich zu bleiben.</span><span class="sxs-lookup"><span data-stu-id="19d8d-146">Transforming an IOnlineImageLoader to an IResourceResolver is a fairly easy task as the methods for the latter were tried to keep as similar as the IOnlineImageLoader as possible</span></span>

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

<span data-ttu-id="19d8d-147">Wie Sie sehen können, sind die größten Änderungen</span><span class="sxs-lookup"><span data-stu-id="19d8d-147">As you can see, the biggest changes are</span></span>

* <span data-ttu-id="19d8d-148">```loadOnlineImage(String, GenericImageLoaderAsync)```wurde umbenannt in```resolveImageResource(String, GenericImageLoaderAsync)```</span><span class="sxs-lookup"><span data-stu-id="19d8d-148">```loadOnlineImage(String, GenericImageLoaderAsync)``` was renamed to ```resolveImageResource(String, GenericImageLoaderAsync)```</span></span>
* <span data-ttu-id="19d8d-149">eine Überladung ```resolveImageResource(String, GenericImageLoaderAsync)``` für wurde ```resolveImageResource(String, GenericImageLoaderAsync, int)``` hinzugefügt, um Szenarios zu unterstützen, in denen die maximale Breite erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="19d8d-149">an overload for ```resolveImageResource(String, GenericImageLoaderAsync)``` was added as ```resolveImageResource(String, GenericImageLoaderAsync, int)``` in order to support scenarios where the max width is required</span></span>

## <a name="custom-media-loading"></a><span data-ttu-id="19d8d-150">Laden benutzerdefinierter Medien</span><span class="sxs-lookup"><span data-stu-id="19d8d-150">Custom Media Loading</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19d8d-151">**Beachten Sie ```IOnlineMediaLoader```,dass die API-Ebene 23 oder Android M hinzugefügt wurde. ```MediaDataSource```**</span><span class="sxs-lookup"><span data-stu-id="19d8d-151">**Remember ```IOnlineMediaLoader``` requires ```MediaDataSource``` which was added in API level 23 or Android M**</span></span>

<span data-ttu-id="19d8d-152">Zusammen mit der Einbeziehung des Medien Elements war auch die Einbindung der ionlinemedialoader-Schnittstelle, die es Entwicklern ermöglicht, die für das zugrunde liegende Media Player-Element verwendete [mediadatasource](https://developer.android.com/reference/android/media/MediaDataSource) zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="19d8d-152">Along with the inclusion of the media element, also was the inclusion of the IOnlineMediaLoader interface which allows developers to override the [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) used for the underlying mediaPlayer element.</span></span> <span data-ttu-id="19d8d-153">**(Erfordert Android M)**</span><span class="sxs-lookup"><span data-stu-id="19d8d-153">**(Requires android M)**</span></span>

<span data-ttu-id="19d8d-154">Zuerst müssen Sie eine Klasse erstellen, die "ionlineimageloader" implementiert.</span><span class="sxs-lookup"><span data-stu-id="19d8d-154">The first needed thing to do is creating a class that implements IOnlineImageLoader</span></span>

```java
@RequiresApi(api = Build.VERSION_CODES.M)
public class OnlineMediaLoader implements IOnlineMediaLoader
{
    /* This class checks if the media source exists */
    public class OnlineFileAvailableChecker extends AsyncTask<String, Void, Boolean>
    {
        public OnlineFileAvailableChecker(String uri)
        {
            m_uri = uri;
        }

        @Override
        protected Boolean doInBackground(String... strings) {
            // if the provided uri is a valid uri or is valid with the resource resolver, then use that
            // otherwise, try to get the media from a local file
            try
            {
                HttpRequestHelper.query(m_uri);
                return true;
            }
            catch (Exception e)
            {
                // Do nothing if the media was not found at all
                e.printStackTrace();
                return false;
            }
        }

        private String m_uri;
   }

       
   @Override
   public MediaDataSource loadOnlineMedia(MediaSourceVector mediaSources, IMediaDataSourceOnPreparedListener mediaDataSourceOnPreparedListener)
   {
       final long mediaSourcesSize = mediaSources.size();
       for(int i = 0; i < mediaSourcesSize; i++)
       {
           String mediaUri = mediaSources.get(i).GetUrl();

           OnlineFileAvailableChecker checker = new OnlineFileAvailableChecker(mediaUri);
           try
           {
               Boolean fileExists = checker.execute("").get();
               if(fileExists)
               {
                   return new MediaDataSourceImpl(mediaUri, mediaDataSourceOnPreparedListener);
               }
           }
           catch (Exception e) { }
       }
       return null;
    }
}
```

<span data-ttu-id="19d8d-155">Nachdem Sie diese Klasse implementiert haben, können Sie Ihre onlinemedialoader-Klasse registrieren, indem Sie hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="19d8d-155">Once this class has been implemented, you can register your OnlineMediaLoader class by adding</span></span> 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
