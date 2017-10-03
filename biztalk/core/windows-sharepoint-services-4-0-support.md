---
title: "Windows SharePoint Services 4.0 支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84be7aa0-2ff2-4e40-9c39-5cb89549c636
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45f3fedbdc4217ef5379b5e890568346a565a235
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="windows-sharepoint-services-40-support"></a>Windows SharePoint Services 4.0 支援
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 專用的 Windows SharePoint Services 配接器可提供與 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 專用的 Windows SharePoint Services 配接器同等的功能。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 專用的 Windows SharePoint Services 配接器還支援 Windows SharePoint Services 4.0 提供的下列功能︰  
  
-   傳送訊息至 Windows SharePoint Services 4.0 部落格網站。  
  
-   傳送訊息至 Windows SharePoint Services 4.0 Wiki 網站，以及從 Windows SharePoint Services 4.0 Wiki 網站接收訊息。  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 專用的 Windows SharePoint Services 配接器不支援 Windows SharePoint Services 4.0 提供的下列功能：  
  
-   **資源回收筒**: Windows SharePoint Services 配接器[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]配接器不支援接收，或明確傳送訊息從至資源回收筒。  
  
-   **列出資料夾**: Windows SharePoint Services 配接器[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]可以傳送訊息至清單，但不是能從清單接收訊息。 Windows SharePoint Services 4.0 支援清單中的資料夾，但 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 專用的 Windows SharePoint Services 配接器不支援這項功能。 因此，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 專用的 Windows SharePoint Services 配接器不能在根資料夾以外的清單資料夾中建立清單項目。  
  
-   下列章節會更詳細說明如何使用 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 專用的 Windows SharePoint Services 配接器傳送訊息至 Windows SharePoint Services 4.0 部落格網站，以及如何傳送訊息至 Windows SharePoint Services 4.0 Wiki 網站和從 Windows SharePoint Services 4.0 Wiki 網站接收訊息。  
  
## <a name="sending-to-a-windows-sharepoint-services-40-blog-site"></a>傳送至 Windows SharePoint Services 4.0 部落格網站  
 在 Windows SharePoint Services 4.0 部落格網站中，文章儲存在**文章**中所定義的清單，而文章類別**類別**清單。  
  
 若要張貼訊息至 Windows SharePoint Services 4.0 部落格網站，請輸入下列值在配接器**傳輸屬性**時設定使用 Windows SharePoint Services 配接器的傳送埠 對話方塊：  
  
|屬性|值|  
|--------------|-----------|  
|目的資料夾 URL|相對於 SharePoint 網站之 Posts 清單 (例如 "Lists/Posts") 的目的資料夾 URL。|  
|SharePoint 網站 URL|Windows SharePoint Services 4.0 部落格網站，例如 http:// URL*\<servername >*/sites/部落格/其中 *\<servername >*是實際名稱的預留位置Web 伺服器。|  
  
 然後設定的值**類別**，**發佈**，**標題**，和**主體**張貼設定對應的屬性WSS 中的值。ConfigPropertiesXml 的訊息內容屬性。 此步驟可以在自訂管線或協調流程中進行。 例如，協調流程中的下列運算式會設定 Message_Out 訊息之 WSS.ConfigPropertiesXml 內容屬性中的值：  
  
```  
int_Category = 1;  
str_Published = Microsoft.SharePoint.Utilities.SPUtility.CreateISO8601DateTimeFromSystemDateTime(System.DateTime.Now);  
// requires a reference to Microsoft.SharePoint.dll  
str_Title = "This is the title of the post from the WSS adapter";  
str_Body = "This is the body of the post from the WSS adapter";  
  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Category</PropertyName1>  
<PropertySource1>” + int_Category + “</PropertySource1>  
<PropertyName2>Published</PropertyName2>  
<PropertySource2>” + str_Published + “</PropertySource2>  
<PropertyName3>Title</PropertyName3>  
<PropertySource3>” + str_Title + “</PropertySource3>  
<PropertyName4>Body</PropertyName4>  
<PropertySource4>” + str_Body + “</PropertySource4>  
</ConfigPropertiesXml>”;  
```  
  
 此運算式中的變數會使用下列型別：  
  
|變數名稱|類型|  
|-------------------|----------|  
|int_Category|System.Int32|  
|str_Published|System.String|  
|str_Title|System.String|  
|str_Body|System.String|  
  
 建立這種方式的文章將設定的狀態**未核准**，這會需要部落格擁有者的核准，才能顯示站台上。  
  
 支援的清單資料行類型可以在清單的設定頁面上檢視。 如需 Windows SharePoint Services 配接器所支援的 Windows SharePoint Services 資料行類型的詳細資訊，請參閱[Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)。  
  
## <a name="sending-to-and-receiving-from-a-windows-sharepoint-services-40-wiki-document-library"></a>傳送訊息至 Windows SharePoint Services 4.0 Wiki 文件庫，以及從 Windows SharePoint Services 4.0 Wiki 文件庫接收訊息  
 在 Windows SharePoint Services 4.0 網站中，Wiki 網站會使用**Wiki Pages**文件庫。 Wiki Pages 文件庫將文字儲存到中的 Wiki 頁面**Wiki Content**資料行使用的 UI 類型，**多行文字**。 **多行文字**UI 類型相互關聯至**SPFieldType.Note** SharePoint 物件模型類型。 如需 Windows SharePoint Services 配接器所支援的 Windows SharePoint Services 資料行類型詳細資訊，請參閱[Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)。  
  
### <a name="sending-to-a-windows-sharepoint-services-40-wiki-document-library"></a>傳送至 Windows SharePoint Services 4.0 Wiki 文件庫  
 當傳送訊息至 Windows SharePoint Services 4.0 Wiki 網站，Wiki 頁面的內容會儲存在名為 Windows SharePoint Services 配接器內容屬性**WSS。ConfigPropertiesXml**。 若要張貼訊息至 Windows SharePoint Services 4.0 Wiki 網站，請輸入下列值在配接器**傳輸屬性**時設定使用 Windows SharePoint Services 配接器的傳送埠 對話方塊：  
  
|屬性|值|  
|--------------|-----------|  
|目的資料夾 URL|相對於 SharePoint 網站的 Wiki 網站 (例如 "wikiSP") 首頁 URL。|  
|SharePoint 網站 URL|Windows SharePoint Services 4.0 Wiki 網站，例如 http:// URL*\<servername >*/sites/wiki/其中 *\<servername >*是實際名稱的預留位置web 伺服器。|  
  
 然後將設定的值**Wiki Content** Wiki 頁面設定 WSS 中對應值的屬性。ConfigPropertiesXml 的訊息內容屬性。 此步驟可以在自訂管線或協調流程中進行。 例如，協調流程中的下列運算式會設定 Message_Out 訊息之 WSS.ConfigPropertiesXml 內容屬性中的值：  
  
```  
str_Wiki = "This is a sample Wiki page entry.";  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Wiki Content</PropertyName1>  
<PropertySource1>” + str_Wiki + “</PropertySource1>  
</ConfigPropertiesXml>”;  
```  
  
 此運算式中的 str_Wiki 變數會使用**System.String**資料型別。  
  
> [!IMPORTANT]
>  Windows SharePoint Services 4.0 Wiki 文件庫支援版本設定，不過，BizTalk Server 2010does 的 Windows SharePoint Services 配接器不支援版本設定。 因此，由 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 專用的 Windows SharePoint Services 配接器所更新的 Wiki 頁面，會失去其先前版本。 由於這項限制，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 專用的 Windows SharePoint Services 配接器接收到的 Wiki 頁面以及封存在其他 Wiki 文件庫中的 Wiki 頁面僅會保留最後一個版本，其他版本都會被刪除。  
  
### <a name="receiving-from-a-windows-sharepoint-services-40-wiki-document-library"></a>從 Windows SharePoint Services 4.0 Wiki 文件庫接收  
 從 Windows SharePoint Services 4.0 Wiki 網站接收訊息時的 Wiki 頁面內容會儲存在名為 Windows SharePoint Services 配接器內容屬性**WSS。InPropertiesXml**。  
  
 若要從 Windows SharePoint Services 4.0 Wiki 頁面接收訊息，請輸入下列值的介面卡**傳輸屬性**對話方塊中設定使用 Windows SharePoint Services 配接器的接收位置時：  
  
|屬性|值|  
|--------------|-----------|  
|SharePoint 網站 URL|相對於 SharePoint 網站的 Wiki 網站 (例如 "wiki") 首頁 URL。|  
|來源文件庫 URL|相對於 SharePoint 網站的 Wiki 網站 (例如 "wikiRL") 首頁 URL。|  
  
 然後擷取 wiki 頁面內容從**Wiki Content**節點**WSS。InPropertiesXml**接收到訊息內容屬性。 此步驟可以在自訂管線或協調流程中進行。 例如，下列協調流程運算式中， **str_Wiki**的值擴展變數**Wiki Content**節點從**WSS。InPropertiesXml**內容屬性**str_wiki**訊息。 然後， **Wiki Content**屬性**WSS。ConfigPropertiesXml**內容屬性**Message_Out**訊息設定的值為**str_Wiki**變數：  
  
```  
str_PropertiesXml = Message_In(WSS.InPropertiesXml);  
doc = doc.LoadXml(str_PropertiesXml);  
node = doc.SelectSingleNode("InPropertiesXml/Property[@name='Wiki Content']);  
str_Wiki = node.InnerText;  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Wiki Content</PropertyName1>  
<PropertySource1>” + str_Wiki + “</PropertySource1>  
</ConfigPropertiesXml>”;  
```  
  
 此運算式中的變數會使用下列型別：  
  
|變數名稱|類型|  
|-------------------|----------|  
|str_PropertiesXml|System.Xml.XmlDocument|  
|doc|System.Xml.XmlDocument|  
|node|System.Xml.XmlNode|  
|str_Wiki|System.String|  
  
## <a name="see-also"></a>另請參閱  
 [Windows SharePoint Services 配接器](../core/windows-sharepoint-services-adapter.md)