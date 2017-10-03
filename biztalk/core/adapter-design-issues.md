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
# <a name="adapter-design-issues"></a>配接器設計問題
當使用者在設計階段進行組態變更時，配接器組態便會存放到單一登入 (SSO) 資料庫中。 在執行階段時，傳訊引擎便會擷取配接器的組態，並且將其傳遞到配接器。 有四種類型的組態資訊會傳遞到配接器：  
  
-   接收處理常式組態  
  
-   接收位置 (端點) 組態  
  
-   傳送處理常式組態  
  
-   傳送位置 (端點) 組態  
  
## <a name="receive-and-send-handler-configuration"></a>接收和傳送處理常式組態  
 配接器的處理常式組態會傳遞至配接器實作的選擇性**IPersistPropertyBag**。**負載**介面。 處理常式組態只會傳遞一次，因此，如果配接器處理常式組態在 BizTalk 服務已經啟動後變更，配接器便不會更新。 通用模型是讓配接器將處理常式組態視為預設組態，並讓端點組態針對每個端點覆寫處理常式組態。  
  
 下列程式碼片段示範剖析組態。 配接器的組態會在傳遞至屬性**負載**字串屬性中呼叫**AdapterConfig**。 這個屬性值包含代表配接器之組態的 XML 文件。 配接器需要將此組態載入至文件物件模組 (DOM) 或 XML 讀取器中，並使用 XPath 來擷取個別的屬性。  
  
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
  
## <a name="receive-location-configuration"></a>接收位置組態  
 接收位置組態資訊會傳遞給配接器的實作**IBTTransportConfig**。 這個介面包含三個方法**AddReceiveEndpoint**， **UpdateEndpointConfig**，和**RemoveReceiveEndpoint**。 傳訊引擎通知配接器：需要接聽哪些端點以便接收訊息。 當個別端點的組態變更時，便會通知配接器關於該端點的變更。 相較之下，當處理常式組態變更時，配接器並不會獲得通知。 相同地，配接器不需要處理服務視窗。因為 BizTalk Server 會在服務視窗具有作用或停止作用時新增或移除端點。  
  
### <a name="addreceiveendpoint"></a>AddReceiveEndpoint  
 若要開始接聽的端點，引擎會呼叫配接器需要時**IBTTransportConfig.AddReceiveEndpoint**接收位置的 URI，包含該端點，配接器的組態屬性包中傳送和第二個屬性包，其中包含 BizTalk Server 特有的組態，為該端點。 配接器要寫入至訊息內容做為 BizTalk Server 系統屬性，URI **InboundTransportLocation**。  
  
 讀取配接器屬性包中的接收位置屬性，與以上述的讀取處理常式組態相同。 傳遞到配接器的 BizTalk Server 組態包含單一屬性， **TwoWayReceivePort**，這表示連接埠為單向或雙向。 下列程式碼片斷說明如何從 BizTalk Server 屬性包評估接收埠為單向或雙向：  
  
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
  
### <a name="updateendpointconfig"></a>UpdateEndpointConfig  
 當的作用中設定接收位置變更時，此引擎會使用**UpdateEndpointConfig** API 來通知配接器必須使用不同的組態。 所有的組態都會傳遞到配接器，其中包括 BizTalk Server 的特定組態。  
  
### <a name="removereceiveendpoint"></a>RemoveReceiveEndpoint  
 當接收位置不再作用中時，透過通知配接器**RemoveReceiveEndpoint**。 配接器會傳回從之後**RemoveReceiveEndpoint**不再允許使用該 URI 來將訊息提交至引擎。  
  
## <a name="send-port-configuration"></a>傳送埠組態  
 在將訊息傳遞給配接器之前，傳訊引擎會將傳送埠的組態寫入配接器之命名空間中的訊息內容。 讀取和驗證組態會是配接器的責任，之後，配接器便會使用該組態來控制訊息的傳輸。 對於支援批次傳送的傳送配接器，目的地為不同傳送埠的訊息可能會在相同的批次中，因此配接器會需要處理這些「混合」批次。  
  
 下列程式碼片段說明如何讀取**OutboundTransportLocation**也就是傳送埠的 URI。 同時顯示如何讀取包含配接器之組態的 XML BLOB，然後讀取個別的屬性。  
  
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
  
 **實作秘訣：**配接器一般都會使用**OutboundTransportLocation**訊息內容屬性來判斷要將訊息傳送至的位址。 藉著這樣做，配接器即可一致地處理對於靜態和動態傳送的傳輸。 這樣也可以簡化在實際執行繫結檔案中的位址修改。  
  
## <a name="xsd"></a>XSD  
 SDK 檔案配接器範例中所包含的四個 XSD 檔主要處理配接器組態： ReceiveHandler.xsd、 ReceiveLocation.xsd、 TransmitLocation.xsd 和 TransmitHandler.xsd。  
  
 下列主題會個別討論這些檔案，並描述您如何能夠修改這些檔案。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [正在驗證配接器組態](../core/validating-the-adapter-configuration.md)  
  
-   [註冊配接器](../core/registering-an-adapter.md)  
  
-   [配接器架構組態結構描述延伸模組](../core/adapter-framework-configuration-schema-extensions.md)  
  
-   [支援的配接器 XSD 項目類型](../core/supported-adapter-xsd-element-types.md)  
  
-   [配接器 XSD 項目屬性建構](../core/adapter-xsd-element-attribute-constructs.md)  
  
-   [配接器 XSD 資料型別 Facet 建構](../core/adapter-xsd-data-type-facet-constructs.md)  
  
-   [配接器的進階的組態元件](../core/advanced-configuration-components-for-adapters.md)