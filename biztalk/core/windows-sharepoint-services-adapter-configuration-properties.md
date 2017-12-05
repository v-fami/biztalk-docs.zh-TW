---
title: "Windows Sharepoint Services 配接器組態屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code samples, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, properties
- receive locations, adapters
- Windows SharePoint Services adapters, code sample
- Windows SharePoint Services adapters, send ports
- Windows SharePoint Services adapters, receive locations
- Windows SharePoint Services adapters
- send ports, adapters
ms.assetid: 20b08959-75d3-4613-9cea-582ac2813415
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbb08d32ad85be68922a2ddf0b6fe4ac0d8c915e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="windows-sharepoint-services-adapter-configuration-properties"></a>Windows Sharepoint Services 配接器組態屬性
下表列出可為 Windows Sharepoint Services 配接器接收位置設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|SiteUrl|VT_BSTR|指定 Windows SharePoint Services 網站的完整 URL。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
|WssLocation|VT_BSTR|指定相對於 SharePoint 網站的擷取文件之 Windows SharePoint Services 文件庫的 URL。|您不能接收來自 SharePoint 清單或資料夾的訊息。|有時 SharePoint 文件庫會與該項目的名稱不同。 請檢查 Internet Explorer 中的網址列，以找出正確的 URL。|  
|ViewName|VT_BSTR|指定用來篩選配接器所處理文件的 Windows SharePoint Services 檢視。|無|一般檢視中的所有訊息都會被處理。|  
|ArchiveLocation|VT_BSTR|指定相對於 SharePoint 網站的 Windows SharePoint Services 資料夾 URL，已處理的檔案將在此封存。|無|有時 SharePoint 文件庫或資料夾 URL 會與該項目的名稱不同。 請檢查 Internet Explorer 中的網址列，以找出正確的 URL。|  
|NamespaceAliases|VT_BSTR|指定命名空間別名定義的逗號或分號分隔清單。|無|無|  
|ArchiveFileName|VT_BSTR|指定封存的 Windows SharePoint Services 檔案名稱。|此欄位不支援 "%SendingOrchestrationID%" 和 "%SendingOrchestrationType%" 巨集。|無|  
|Overwrite|VT_BSTR|指定是否覆寫封存中的現有檔案。|有效值為：<br /><br /> -[是]<br />-沒有|預設值為 no。|  
|ErrorThreshold|VT_BSTR|指定停用接收位置前，配接器發生連續輪詢失敗的數目上限。|有效值介於 0 到 2147483647 之間。|將此屬性設為 0，永不停用接收位置。<br /><br /> 預設值是 10。|  
|PollingInterval|VT_BSTR|指定配接器所執行的兩個連續查詢之間的時間間隔 (以秒為單位)，以查看是否有任何新訊息可供處理。|有效值從 1 到 2147483647 之間。|指定較低的值可以改善配接器的輸送量和回應時間。<br /><br /> 預設值為 60。|  
|BatchSize|VT_BSTR|指定 Windows SharePoint Services 傳訊配接器 Web 服務視為一個批次進行處理的文件數目上限。|有效值從 1 到 2147483647 之間。|處理的批次所包含的訊息可能少於定義的批次大小，但絕不會超過定義的批次大小。<br /><br /> 預設值為 20。|  
|OfficeIntegration|VT_BSTR|指定 Office 整合的層級。|有效值為：<br /><br /> -   **選擇性**-嘗試移除 InfoPath 處理指示如果可能的話，或做為處理是若不可能。<br />-   **否**-處理文件 「 如同現狀。 」<br />-   **[是]** -移除 InfoPath 處理指示或略過錯誤訊息。|預設值為 optional。|  
|逾時|VT_BSTR|指定配接器執行階段 Web 服務對 Windows SharePoint Services 配接器 Web 服務的呼叫逾時 (以毫秒為單位)。|有效值介於 1000年到 2147483647 之間。|預設值為 100000。|  
|AdapterWSPort|VT_BSTR|指定安裝 Windows SharePoint Services 配接器 Web 服務的 IIS 網站的 HTTP 連接埠。|無|預設值是 80。|  
|uri|VT_BSTR|指定 Windows SharePoint Services 文件庫的完整路徑。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
  
 下列程式碼顯示您用來設定屬性的字串格式：  
  
```  
<CustomProps><AdapterConfig vt="8"><ReceiveLocation xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><SiteUrl>http://BTS2006/sites/BASSite/</SiteUrl><WssLocation>Shared Docs</WssLocation><ViewName>Approved</ViewName><ArchiveLocation>Archive</ArchiveLocation><NamespaceAliases>po='http://POProcess/POrder'</NamespaceAliases><ArchiveFileName>PurchaseOrder0001.xml</ArchiveFileName><Overwrite>no</Overwrite><ErrorThreshold>10</ErrorThreshold><PollingInterval>60</PollingInterval><BatchSize>20</BatchSize><OfficeIntegration>optional</OfficeIntegration><Timeout>100000</Timeout><AdapterWSPort>80</AdapterWSPort><uri>wss://bts2006:80/sites/BASSite/Shared+Docs?ViewName=Approved</uri></ReceiveLocation></AdapterConfig></CustomProps>  
```  
  
 下表列出可為 Windows Sharepoint Services 配接器傳送埠設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|SiteUrl|VT_BSTR|指定 Windows SharePoint Services 網站的完整 URL|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
|WssLocation|VT_BSTR|指定相對於 SharePoint 網站的 Windows SharePoint Services 目的資料夾 URL。|無|有時 SharePoint 文件庫、清單或資料夾 URL 會與該項目名稱不同。 請檢查 Internet Explorer 中的網址列以找出正確的 URL。|  
|Overwrite|VT_BSTR|指定是否要覆寫現有的檔案。|有效值為：<br /><br /> -沒有<br />-協調流程<br />-重新命名<br />-[是]|預設值為 no。|  
|NamespaceAliases|VT_BSTR|指定命名空間別名定義的逗號或分號分隔清單。|無|使用此欄位，來定義欄位中引用之 XPATH 查詢所用的命名空間別名。<br /><br /> 此屬性不會覆寫協調流程所定義的 WSS.ConfigNamespacesAliases 訊息內容屬性。 這兩個值會合併。|  
|FileName|VT_BSTR|指定 Windows SharePoint Services 檔案名稱。|無|傳送訊息至清單時，會略過指定在「檔案名稱」屬性的值，而且不會儲存在任何 SharePoint 資料行。 SharePoint 清單沒有 [檔案名稱] 資料行。 而是使用 16 個可用資料行的其中一個，以更新 [標題] 資料行。|  
|OfficeIntegration|VT_BSTR|指定要變更文件，讓它自動在 Office 應用程式 (例如 InfoPath) 開啟，或者若找不到 InfoPath 解決方案，就依原狀儲存文件。|有效值為：<br /><br /> -沒有<br />-選擇性<br />-協調流程<br />-[是]<br />-yesformlibrary|預設值為 optional。|  
|TemplatesDocLib|VT_BSTR|指定儲存 InfoPath 解決方案的 SharePoint 文件庫名稱。|如果 TemplatesNamespaceCol 屬性包含值，此屬性也必須含有值。|文件庫必須至少有一個類型為「單行文字」的 SharePoint 資料行，可使用此 InfoPath 解決方案開啟的 XML 文件的命名空間和根節點會填入該資料行，或僅根節點會填入該資料行。|  
|TemplatesNamespaceCol|VT_BSTR|指定儲存 InfoPath 解決方案之命名空間的 [範本後援文件庫] 的 SharePoint 資料行名稱。|如果 TemplatesDocLib 屬性包含值，此屬性也必須含有值。<br /><br /> 在此欄位中，大小寫有所區分。|無|  
|CustomTemplatesDocLib|VT_BSTR|指定儲存 InfoPath 解決方案的 SharePoint 文件庫名稱。|如果 CustomTemplatesNamespaceCol 屬性包含值，此屬性也必須含有值。<br /><br /> 在此欄位中，大小寫有所區分。|無|  
|CustomTemplatesNamespaceCol|VT_BSTR|指定儲存 InfoPath 解決方案之命名空間的 [範本文件庫] 的 SharePoint 資料行名稱。|如果 CustomTemplatesDocLib 屬性包含值，此屬性也必須含有值。<br /><br /> 在此欄位中，大小寫有所區分。|無|  
|PropertyName(n)|VT_BSTR|指定存在於目的地文件庫的 Windows SharePoint Services 資料行名稱。|在此欄位中，大小寫有所區分。|您最多可以指定 16 個資料行。|  
|PropertySource(n)|VT_BSTR|指定要為此訊息設定的資料行值。|無|您最多可以指定 16 個資料行值。|  
|逾時|VT_BSTR|指定配接器執行階段 Web 服務對 Windows SharePoint Services 配接器 Web 服務的呼叫逾時 (以毫秒為單位)。|有效值介於 1000年到 2147483647 之間。|預設值為 100000。|  
|AdapterWSPort|VT_BSTR|指定安裝 Windows SharePoint Services 配接器 Web 服務的 IIS 網站的 HTTP 連接埠。|無|預設值是 80。|  
|uri|VT_BSTR|指定 Windows SharePoint Services 目的資料夾 URL 的完整路徑。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
  
 下列程式碼顯示您用來設定屬性的字串格式：  
  
> [!NOTE]
>  這個字串中省略了 PropertyName2 到 PropertyName16 以及 PropertySource2 到 PropertySource16 的定義。  
  
```  
<CustomProps><AdapterConfig vt="8"><SendPort xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><SiteUrl>http://BizTalkServer/sites/BASSite/</SiteUrl><WssLocation>Shared Documents/Purchase Orders</WssLocation><Overwrite>yes</Overwrite><NamespaceAliases>po='http://OrderProcess/POrder'</NamespaceAliases><FileName>PurchaseOrder0001.xml</FileName><OfficeIntegration>yesformlibrary</OfficeIntegration><TemplatesDocLib>Templates</TemplatesDocLib><TemplatesNamespaceCol>NamespaceFallback</TemplatesNamespaceCol><CustomTemplatesDocLib>Shared Documents</CustomTemplatesDocLib><CustomTemplatesNamespaceCol>Namespace</CustomTemplatesNamespaceCol><PropertyName1>Column1</PropertyName1><PropertySource1>Column1 Value</PropertySource1><Timeout>100000</Timeout><AdapterWSPort>80</AdapterWSPort><uri>wss://biztalkserver:80/sites/BASSite/Shared%20Documents/Purchase%20Orders</uri></SendPort></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  在指定的使用配接器架構所建置的配接器的 TransportTypeData 組態資料時，所使用的名稱/值組必須全部儲存到\<AdapterConfig\>項目。 因為\<AdapterConfig\>項目會指定 VT_BSTR (vt ="8") 資料型別然後\<\>必須逸出字元資料中的。