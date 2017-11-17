---
title: "配接器設計問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e5568be-a046-40ff-a94a-eda086457564
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79c6228db8342f3d1ad2628d4e4caf418efd9b29
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-design-issues"></a><span data-ttu-id="f7aca-102">配接器設計問題</span><span class="sxs-lookup"><span data-stu-id="f7aca-102">Adapter Design Issues</span></span>
<span data-ttu-id="f7aca-103">當使用者在設計階段進行組態變更時，配接器組態便會存放到單一登入 (SSO) 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="f7aca-103">Adapter configuration is stored in the Single Sign-On (SSO) database when the user makes configuration changes during design time.</span></span> <span data-ttu-id="f7aca-104">在執行階段時，傳訊引擎便會擷取配接器的組態，並且將其傳遞到配接器。</span><span class="sxs-lookup"><span data-stu-id="f7aca-104">At run time the Messaging Engine retrieves the adapter's configuration and delivers it to the adapter.</span></span> <span data-ttu-id="f7aca-105">有四種類型的組態資訊會傳遞到配接器：</span><span class="sxs-lookup"><span data-stu-id="f7aca-105">Four types of configuration information are delivered to adapters:</span></span>  
  
-   <span data-ttu-id="f7aca-106">接收處理常式組態</span><span class="sxs-lookup"><span data-stu-id="f7aca-106">Receive handler configuration</span></span>  
  
-   <span data-ttu-id="f7aca-107">接收位置 (端點) 組態</span><span class="sxs-lookup"><span data-stu-id="f7aca-107">Receive location (endpoint) configuration</span></span>  
  
-   <span data-ttu-id="f7aca-108">傳送處理常式組態</span><span class="sxs-lookup"><span data-stu-id="f7aca-108">Send handler configuration</span></span>  
  
-   <span data-ttu-id="f7aca-109">傳送位置 (端點) 組態</span><span class="sxs-lookup"><span data-stu-id="f7aca-109">Send location (endpoint) configuration</span></span>  
  
## <a name="receive-and-send-handler-configuration"></a><span data-ttu-id="f7aca-110">接收和傳送處理常式組態</span><span class="sxs-lookup"><span data-stu-id="f7aca-110">Receive and Send Handler Configuration</span></span>  
 <span data-ttu-id="f7aca-111">配接器的處理常式組態會傳遞至配接器實作的選擇性**IPersistPropertyBag**。**負載**介面。</span><span class="sxs-lookup"><span data-stu-id="f7aca-111">An adapter's handler configuration is delivered to the adapter on its implementation of the optional **IPersistPropertyBag**.**Load** interface.</span></span> <span data-ttu-id="f7aca-112">處理常式組態只會傳遞一次，因此，如果配接器處理常式組態在 BizTalk 服務已經啟動後變更，配接器便不會更新。</span><span class="sxs-lookup"><span data-stu-id="f7aca-112">The handler configuration is delivered only once, so if the adapter handler configuration is changed after the BizTalk service has started the adapter is not updated.</span></span> <span data-ttu-id="f7aca-113">通用模型是讓配接器將處理常式組態視為預設組態，並讓端點組態針對每個端點覆寫處理常式組態。</span><span class="sxs-lookup"><span data-stu-id="f7aca-113">The common model is for the adapter to treat the handler configuration as the default configuration; endpoint configuration overrides the handler configuration on a per-endpoint basis.</span></span>  
  
 <span data-ttu-id="f7aca-114">下列程式碼片段示範剖析組態。</span><span class="sxs-lookup"><span data-stu-id="f7aca-114">The following code fragment demonstrates parsing the configuration.</span></span> <span data-ttu-id="f7aca-115">配接器的組態會在傳遞至屬性**負載**字串屬性中呼叫**AdapterConfig**。</span><span class="sxs-lookup"><span data-stu-id="f7aca-115">The adapter's configuration is in the property passed in to the **Load** call in the string property **AdapterConfig**.</span></span> <span data-ttu-id="f7aca-116">這個屬性值包含代表配接器之組態的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="f7aca-116">This property value contains an XML document representing the adapter's configuration.</span></span> <span data-ttu-id="f7aca-117">配接器需要將此組態載入至文件物件模組 (DOM) 或 XML 讀取器中，並使用 XPath 來擷取個別的屬性。</span><span class="sxs-lookup"><span data-stu-id="f7aca-117">The adapter needs to load this configuration into a document object model (DOM) or an XML reader and use XPath to retrieve the individual properties.</span></span>  
  
```  
public class MyAdapter : IBTTransport,   
 IBTTransportConfig,   
 IBTTransportControl,  
 IPersistPropertyBag,   
 IBaseComponent  
{  
...  
// Handler configuration properties...  
private int defaultBatchSize = 0;  
private string defaultHeader;  
  
// IPersistPropertyBag.Load() implementation...  
public void Load(IPropertyBag pb, int pErrorLog)  
{  
// The adapter configuration is in the property  
 // “AdapterConfig” in the form of an Xml blob...  
object obj = null;  
pb.Read("AdapterConfig", out obj, 0);  
  
// Create a DOM and load the Xml blob...  
XmlDocument dom = new XmlDocument();  
string adapterConfig = (string)obj;  
dom.LoadXml(adapterConfig);  
  
// XPath the individual properties...  
XmlNode node =   
 document.SelectSingleNode(“/Config/batchSize”);  
defaultBatchSize = int.Parse(node.InnerText);  
  
node = document.SelectSingleNode(“/Config/header”);  
defaultHeader = node.InnerText;  
}  
}  
```  
  
## <a name="receive-location-configuration"></a><span data-ttu-id="f7aca-118">接收位置組態</span><span class="sxs-lookup"><span data-stu-id="f7aca-118">Receive Location Configuration</span></span>  
 <span data-ttu-id="f7aca-119">接收位置組態資訊會傳遞給配接器的實作**IBTTransportConfig**。</span><span class="sxs-lookup"><span data-stu-id="f7aca-119">Receive location configuration information is delivered to an adapter on its implementation of **IBTTransportConfig**.</span></span> <span data-ttu-id="f7aca-120">這個介面包含三個方法**AddReceiveEndpoint**， **UpdateEndpointConfig**，和**RemoveReceiveEndpoint**。</span><span class="sxs-lookup"><span data-stu-id="f7aca-120">This interface contains the three methods **AddReceiveEndpoint**, **UpdateEndpointConfig**, and **RemoveReceiveEndpoint**.</span></span> <span data-ttu-id="f7aca-121">傳訊引擎通知配接器：需要接聽哪些端點以便接收訊息。</span><span class="sxs-lookup"><span data-stu-id="f7aca-121">The Messaging Engine notifies the adapter of which endpoints it needs to listen on to receive messages.</span></span> <span data-ttu-id="f7aca-122">當個別端點的組態變更時，便會通知配接器關於該端點的變更。</span><span class="sxs-lookup"><span data-stu-id="f7aca-122">When the configuration for an individual endpoint is changed the adapter is notified of the change for that endpoint.</span></span> <span data-ttu-id="f7aca-123">相較之下，當處理常式組態變更時，配接器並不會獲得通知。</span><span class="sxs-lookup"><span data-stu-id="f7aca-123">This is in contrast to the fact that when handler configuration changes the adapter is not notified.</span></span> <span data-ttu-id="f7aca-124">相同地，配接器不需要處理服務視窗。因為 BizTalk Server 會在服務視窗具有作用或停止作用時新增或移除端點。</span><span class="sxs-lookup"><span data-stu-id="f7aca-124">Similarly, the adapter does not need to handle service windows because BizTalk Server adds or removes endpoints as service windows become active or inactive.</span></span>  
  
### <a name="addreceiveendpoint"></a><span data-ttu-id="f7aca-125">AddReceiveEndpoint</span><span class="sxs-lookup"><span data-stu-id="f7aca-125">AddReceiveEndpoint</span></span>  
 <span data-ttu-id="f7aca-126">若要開始接聽的端點，引擎會呼叫配接器需要時**IBTTransportConfig.AddReceiveEndpoint**接收位置的 URI，包含該端點，配接器的組態屬性包中傳送和第二個屬性包，其中包含 BizTalk Server 特有的組態，為該端點。</span><span class="sxs-lookup"><span data-stu-id="f7aca-126">When an adapter needs to begin listening on an endpoint, the engine calls **IBTTransportConfig.AddReceiveEndpoint** passing in the receive location's URI, a property bag containing the adapter's configuration for that endpoint, and a second property bag containing BizTalk Server-specific configuration for that endpoint.</span></span> <span data-ttu-id="f7aca-127">配接器要寫入至訊息內容做為 BizTalk Server 系統屬性，URI **InboundTransportLocation**。</span><span class="sxs-lookup"><span data-stu-id="f7aca-127">The adapter needs to write the URI to the message context as the BizTalk Server system property **InboundTransportLocation**.</span></span>  
  
 <span data-ttu-id="f7aca-128">讀取配接器屬性包中的接收位置屬性，與以上述的讀取處理常式組態相同。</span><span class="sxs-lookup"><span data-stu-id="f7aca-128">Reading the receive location properties from the adapter's property bag is the same as reading the handler configuration as detailed above.</span></span> <span data-ttu-id="f7aca-129">傳遞到配接器的 BizTalk Server 組態包含單一屬性， **TwoWayReceivePort**，這表示連接埠為單向或雙向。</span><span class="sxs-lookup"><span data-stu-id="f7aca-129">The BizTalk Server configuration passed into the adapter contains a single property, **TwoWayReceivePort**, which indicates whether the port is one-way or two-way.</span></span> <span data-ttu-id="f7aca-130">下列程式碼片斷說明如何從 BizTalk Server 屬性包評估接收埠為單向或雙向：</span><span class="sxs-lookup"><span data-stu-id="f7aca-130">The following code fragment illustrates how to evaluate if the receive port is one-way or two-way from the BizTalk Server property bag:</span></span>  
  
```  
public void AddReceiveEndpoint(  
 string  url,   
 IPropertyBag adapterConfig,   
 IPropertyBag bizTalkConfig )  
{  
...  
  
// The property "TwoWayReceivePort" in the BizTalk Config  
// property bag indicates whether the port is one or two  
 // way...  
  
 // Add receive location to config cache (not shown here)  
  
object obj = null;  
bizTalkConfig.Read("TwoWayReceivePort", out obj, 0);  
  
if ( null != obj )  
this.twoWay = (bool)obj;  
}  
```  
  
### <a name="updateendpointconfig"></a><span data-ttu-id="f7aca-131">UpdateEndpointConfig</span><span class="sxs-lookup"><span data-stu-id="f7aca-131">UpdateEndpointConfig</span></span>  
 <span data-ttu-id="f7aca-132">當的作用中設定接收位置變更時，此引擎會使用**UpdateEndpointConfig** API 來通知配接器必須使用不同的組態。</span><span class="sxs-lookup"><span data-stu-id="f7aca-132">When the configuration of an active receive location is changed, the engine uses the **UpdateEndpointConfig** API to notify the adapter that it needs to use a different configuration.</span></span> <span data-ttu-id="f7aca-133">所有的組態都會傳遞到配接器，其中包括 BizTalk Server 的特定組態。</span><span class="sxs-lookup"><span data-stu-id="f7aca-133">All of the configuration is delivered to the adapter, including the BizTalk Server-specific configuration.</span></span>  
  
### <a name="removereceiveendpoint"></a><span data-ttu-id="f7aca-134">RemoveReceiveEndpoint</span><span class="sxs-lookup"><span data-stu-id="f7aca-134">RemoveReceiveEndpoint</span></span>  
 <span data-ttu-id="f7aca-135">當接收位置不再作用中時，透過通知配接器**RemoveReceiveEndpoint**。</span><span class="sxs-lookup"><span data-stu-id="f7aca-135">When a receive location is no longer active, the adapter is notified through **RemoveReceiveEndpoint**.</span></span> <span data-ttu-id="f7aca-136">配接器會傳回從之後**RemoveReceiveEndpoint**不再允許使用該 URI 來將訊息提交至引擎。</span><span class="sxs-lookup"><span data-stu-id="f7aca-136">After the adapter returns from **RemoveReceiveEndpoint** it is no longer allowed to use that URI to submit messages into the engine.</span></span>  
  
## <a name="send-port-configuration"></a><span data-ttu-id="f7aca-137">傳送埠組態</span><span class="sxs-lookup"><span data-stu-id="f7aca-137">Send Port Configuration</span></span>  
 <span data-ttu-id="f7aca-138">在將訊息傳遞給配接器之前，傳訊引擎會將傳送埠的組態寫入配接器之命名空間中的訊息內容。</span><span class="sxs-lookup"><span data-stu-id="f7aca-138">The Messaging Engine writes the configuration for the send port to the message context in the adapter’s namespace before delivering the message to the adapter.</span></span> <span data-ttu-id="f7aca-139">讀取和驗證組態會是配接器的責任，之後，配接器便會使用該組態來控制訊息的傳輸。</span><span class="sxs-lookup"><span data-stu-id="f7aca-139">It is the adapters’ responsibility to read and validate the configuration, which it subsequently uses to control the transmission of the message.</span></span> <span data-ttu-id="f7aca-140">對於支援批次傳送的傳送配接器，目的地為不同傳送埠的訊息可能會在相同的批次中，因此配接器會需要處理這些「混合」批次。</span><span class="sxs-lookup"><span data-stu-id="f7aca-140">For send adapters that support batched sends, messages destined for different send ports may be in the same batch, so the adapter needs to handle these "mixed" batches.</span></span>  
  
 <span data-ttu-id="f7aca-141">下列程式碼片段說明如何讀取**OutboundTransportLocation**也就是傳送埠的 URI。</span><span class="sxs-lookup"><span data-stu-id="f7aca-141">The following code fragment illustrates how to read the **OutboundTransportLocation** that is the URI for the send port.</span></span> <span data-ttu-id="f7aca-142">同時顯示如何讀取包含配接器之組態的 XML BLOB，然後讀取個別的屬性。</span><span class="sxs-lookup"><span data-stu-id="f7aca-142">It also shows how to read the XML blob containing the adapter's configuration and then read the individual properties.</span></span>  
  
```  
...  
 private static readonly PropertyBase UriProperty =   
 new BTS.OutboundTransportLocation();  
  
 private string propertyNamespace =   
  "http://schemas.mySchemas.com/MyAdapter/myadapter-properties";  
private string uri;  
private string headers;  
private int timeOut = 1000;  
  
private void ReadSendPortConfig(IBaseMessage msg)  
{  
// Read the OutboundTransportLocation,   
 // i.e. the send port uri....  
uri = (string)msg.Context.Read(  
 UriProperty.Name.Name, UriProperty.Name.Namespace);  
  
// Read the adapters configuration Xml blob from   
 // the message...  
XmlDocument locationConfigDom = null;  
object obj = msg.Context.Read(  
 "AdapterConfig", this.propertyNamespace);  
  
// If this is a dynamic send there will not be   
 // any configuration...  
if ( null != obj )  
{  
locationConfigDom = new XmlDocument();  
locationConfigDom.LoadXml((string)obj);  
  
this.headers = Extract(  
 locationConfigDom, "/Config/headers", true);  
  
 this.timeOut = ExtractInt32(  
 locationConfigDom, "/Config/timeOut", true);  
}  
}  
  
 // Helper method to XPath string properties...  
private static string Extract(  
 XmlDocument document, string path, bool required)  
{  
XmlNode node = document.SelectSingleNode(path);  
if (!required && null == node)  
return String.Empty;  
if (null == node)  
throw new ApplicationException(string.Format(  
 "No property was found at {0}", path));  
return node.InnerText;  
}  
  
  // Helper method to XPath int32 properties...  
private static int ExtractInt32(  
 XmlDocument document, string path, bool required)  
{  
string s = Extract(document, path, required);  
return int.Parse(s);  
}   
```  
  
 <span data-ttu-id="f7aca-143">**實作秘訣：**配接器一般都會使用**OutboundTransportLocation**訊息內容屬性來判斷要將訊息傳送至的位址。</span><span class="sxs-lookup"><span data-stu-id="f7aca-143">**Implementation Tip:** Adapters should in general use the **OutboundTransportLocation** message context property to determine the address to send the message to.</span></span> <span data-ttu-id="f7aca-144">藉著這樣做，配接器即可一致地處理對於靜態和動態傳送的傳輸。</span><span class="sxs-lookup"><span data-stu-id="f7aca-144">By doing this the adapter can handle transmissions to both static and dynamic sends consistently.</span></span> <span data-ttu-id="f7aca-145">這樣也可以簡化在實際執行繫結檔案中的位址修改。</span><span class="sxs-lookup"><span data-stu-id="f7aca-145">This also simplifies the modification of addresses in production binding files.</span></span>  
  
## <a name="xsd"></a><span data-ttu-id="f7aca-146">XSD</span><span class="sxs-lookup"><span data-stu-id="f7aca-146">XSD</span></span>  
 <span data-ttu-id="f7aca-147">SDK 檔案配接器範例中所包含的四個 XSD 檔主要處理配接器組態： ReceiveHandler.xsd、 ReceiveLocation.xsd、 TransmitLocation.xsd 和 TransmitHandler.xsd。</span><span class="sxs-lookup"><span data-stu-id="f7aca-147">Four XSD files included in the SDK File Adapter sample primarily handle adapter configuration: ReceiveHandler.xsd, ReceiveLocation.xsd, TransmitLocation.xsd, and TransmitHandler.xsd.</span></span>  
  
 <span data-ttu-id="f7aca-148">下列主題會個別討論這些檔案，並描述您如何能夠修改這些檔案。</span><span class="sxs-lookup"><span data-stu-id="f7aca-148">The following topics discuss each of these files and describe how you can modify them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7aca-149">本節內容</span><span class="sxs-lookup"><span data-stu-id="f7aca-149">In This Section</span></span>  
  
-   [<span data-ttu-id="f7aca-150">正在驗證配接器組態</span><span class="sxs-lookup"><span data-stu-id="f7aca-150">Validating the Adapter Configuration</span></span>](../core/validating-the-adapter-configuration.md)  
  
-   [<span data-ttu-id="f7aca-151">註冊配接器</span><span class="sxs-lookup"><span data-stu-id="f7aca-151">Registering an Adapter</span></span>](../core/registering-an-adapter.md)  
  
-   [<span data-ttu-id="f7aca-152">配接器架構組態結構描述延伸模組</span><span class="sxs-lookup"><span data-stu-id="f7aca-152">Adapter Framework Configuration Schema Extensions</span></span>](../core/adapter-framework-configuration-schema-extensions.md)  
  
-   [<span data-ttu-id="f7aca-153">支援的配接器 XSD 項目類型</span><span class="sxs-lookup"><span data-stu-id="f7aca-153">Supported Adapter XSD Element Types</span></span>](../core/supported-adapter-xsd-element-types.md)  
  
-   [<span data-ttu-id="f7aca-154">配接器 XSD 項目屬性建構</span><span class="sxs-lookup"><span data-stu-id="f7aca-154">Adapter XSD Element-Attribute Constructs</span></span>](../core/adapter-xsd-element-attribute-constructs.md)  
  
-   [<span data-ttu-id="f7aca-155">配接器 XSD 資料型別 Facet 建構</span><span class="sxs-lookup"><span data-stu-id="f7aca-155">Adapter XSD Data Type-Facet Constructs</span></span>](../core/adapter-xsd-data-type-facet-constructs.md)  
  
-   [<span data-ttu-id="f7aca-156">配接器的進階的組態元件</span><span class="sxs-lookup"><span data-stu-id="f7aca-156">Advanced Configuration Components for Adapters</span></span>](../core/advanced-configuration-components-for-adapters.md)