---
title: Windows SharePoint Services 4.0 支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84be7aa0-2ff2-4e40-9c39-5cb89549c636
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6920de947165f7f3065f190d077d55dcbef30c7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971031"
---
# <a name="windows-sharepoint-services-40-support"></a>Windows SharePoint Services 4.0 支援
BizTalk Server 的 Windows SharePoint Services 配接器提供的 Windows SharePoint Services 配接器的功能同位檢查[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]。 BizTalk Server 的 Windows SharePoint Services 配接器也支援 Windows SharePoint Services 4.0 提供的下列功能：  

- 傳送訊息至 Windows SharePoint Services 4.0 部落格網站。  

- 傳送訊息至 Windows SharePoint Services 4.0 Wiki 網站，以及從 Windows SharePoint Services 4.0 Wiki 網站接收訊息。  

  BizTalk Server 的 Windows SharePoint Services 配接器不提供支援 Windows SharePoint Services 4.0 中可用的下列功能：  

- **資源回收筒**: BizTalk Server 配接器的 Windows SharePoint Services 配接器不支援接收訊息或明確傳送訊息從/至資源回收筒。  

- **列出資料夾**: BizTalk server 的 Windows SharePoint Services 配接器可以傳送訊息至清單，但不是能從清單接收訊息。 Windows SharePoint Services 4.0 支援清單中的資料夾，但 BizTalk Server 的 Windows SharePoint Services 配接器不支援這項功能。 因此，BizTalk Server 的 Windows SharePoint Services 配接器無法在根資料夾以外的清單資料夾中建立清單項目。  

- 下列各節更詳細說明如何使用 BizTalk Server 的 Windows SharePoint Services 配接器將訊息傳送至 Windows SharePoint Services 4.0 部落格網站以及如何傳送和接收訊息，從 Windows SharePoint Services4.0 Wiki 網站。  

## <a name="sending-to-a-windows-sharepoint-services-40-blog-site"></a>傳送至 Windows SharePoint Services 4.0 部落格網站  
 在 Windows SharePoint Services 4.0 部落格網站中，文章儲存在**張貼**中所定義的清單，而文章類別**類別**清單。  

 若要將訊息張貼至 Windows SharePoint Services 4.0 部落格網站中，輸入下列值在配接器**傳輸屬性**時設定使用 Windows SharePoint Services 配接器的傳送埠 對話方塊中：  


|        屬性        |                                                                                            ReplTest1                                                                                            |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 目的資料夾 URL |                                            相對於 SharePoint 網站之 Posts 清單 (例如 "Lists/Posts") 的目的資料夾 URL。                                            |
|  SharePoint 網站 URL   | Windows SharePoint Services 4.0 部落格網站，例如 http:// 的 URL<em>\<servername\></em>/網站/部落格/位置*\<servername\>* 是Web 伺服器的實際名稱的預留位置。 |

 然後設定的值**類別目錄**，**已發佈**，**標題**，以及**主體**設定相對應的部落格的屬性在 WSS 中的值。ConfigPropertiesXml 的訊息內容屬性。 此步驟可以在自訂管線或協調流程中進行。 例如，協調流程中的下列運算式會設定 Message_Out 訊息之 WSS.ConfigPropertiesXml 內容屬性中的值：  

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

 這種方式建立的文章將會設定為狀態**未核准**，這會需要部落格擁有者的核准，才能顯示在網站上。  

 支援的清單資料行類型可以在清單的設定頁面上檢視。 如需支援的 Windows SharePoint Services 配接器的 Windows SharePoint Services 資料行類型的詳細資訊，請參閱[Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)。  

## <a name="sending-to-and-receiving-from-a-windows-sharepoint-services-40-wiki-document-library"></a>傳送訊息至 Windows SharePoint Services 4.0 Wiki 文件庫，以及從 Windows SharePoint Services 4.0 Wiki 文件庫接收訊息  
 在 Windows SharePoint Services 4.0 網站中，Wiki 網站會使用**Wiki 頁面**文件庫。 Wiki 頁面文件庫是存放在 Wiki 頁面的文字**Wiki 內容**資料行使用的 UI 型別**多行文字**。 **多行文字**UI 型別相互關聯**SPFieldType.Note** SharePoint 物件模型類型。 如需支援的 Windows SharePoint Services 配接器的 Windows SharePoint Services 資料行類型詳細資訊，請參閱[Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)。  

### <a name="sending-to-a-windows-sharepoint-services-40-wiki-document-library"></a>傳送至 Windows SharePoint Services 4.0 Wiki 文件庫  
 Wiki 頁面的內容時傳送訊息至 Windows SharePoint Services 4.0 Wiki 網站，會儲存在名為 Windows SharePoint Services 配接器內容屬性**WSS。ConfigPropertiesXml**。 若要張貼訊息至 Windows SharePoint Services 4.0 Wiki 網站，請輸入下列值在配接器**傳輸屬性**時設定使用 Windows SharePoint Services 配接器的傳送埠 對話方塊中：  


|        屬性        |                                                                                            ReplTest1                                                                                            |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 目的資料夾 URL |                                                   相對於 SharePoint 網站的 Wiki 網站 (例如 "wikiSP") 首頁 URL。                                                    |
|  SharePoint 網站 URL   | Windows SharePoint Services 4.0 Wiki 網站，例如 http:// 的 URL<em>\<servername\></em>/sites/wiki/位置*\<servername\>* 是web 伺服器的實際名稱的預留位置。 |

 然後將設定的值**Wiki 內容**Wiki 頁面，藉由在 WSS 中設定的對應值的屬性。ConfigPropertiesXml 的訊息內容屬性。 此步驟可以在自訂管線或協調流程中進行。 例如，協調流程中的下列運算式會設定 Message_Out 訊息之 WSS.ConfigPropertiesXml 內容屬性中的值：  

```  
str_Wiki = "This is a sample Wiki page entry.";  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Wiki Content</PropertyName1>  
<PropertySource1>” + str_Wiki + “</PropertySource1>  
</ConfigPropertiesXml>”;  
```  

 此運算式中的 str_Wiki 變數會使用**System.String**資料型別。  

> [!IMPORTANT]
>  Windows SharePoint Services 4.0 Wiki 文件庫支援版本設定，不過，BizTalk Server 2010does 的 Windows SharePoint Services 配接器不支援版本設定。 因此，BizTalk server 的 Windows SharePoint Services 配接器所更新的 Wiki 頁面將會失去其先前版本。 由於此限制，是 BizTalk Server 的 Windows SharePoint Services 配接器接收和封存在其他 Wiki 文件程式庫在 Wiki 頁面僅會保留其最後一個版本，與所有其他版本都會被刪除。  

### <a name="receiving-from-a-windows-sharepoint-services-40-wiki-document-library"></a>從 Windows SharePoint Services 4.0 Wiki 文件庫接收  
 從 Windows SharePoint Services 4.0 Wiki 網站接收訊息時，Wiki 頁面的內容會儲存在名為 Windows SharePoint Services 配接器內容屬性**WSS。InPropertiesXml**。  

 若要從 Windows SharePoint Services 4.0 Wiki 頁面接收訊息，請輸入下列值在配接器**傳輸屬性**對話方塊中設定使用的 Windows SharePoint Services 配接器的接收位置時：  

|屬性|ReplTest1|  
|--------------|-----------|  
|SharePoint 網站 URL|相對於 SharePoint 網站的 Wiki 網站 (例如 "wiki") 首頁 URL。|  
|來源文件庫 URL|相對於 SharePoint 網站的 Wiki 網站 (例如 "wikiRL") 首頁 URL。|  

 然後在擷取 wiki 頁面內容，從**Wiki 內容**節點的**WSS。InPropertiesXml**接收的訊息內容屬性。 此步驟可以在自訂管線或協調流程中進行。 例如，在下列的協調流程運算式中， **str_Wiki**的值擴展變數**Wiki 內容**節點從**WSS。InPropertiesXml**內容屬性**str_wiki**訊息。 然後， **Wiki 內容**屬性**WSS。ConfigPropertiesXml**內容屬性**Message_Out**訊息設定的值為**str_Wiki**變數：  

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