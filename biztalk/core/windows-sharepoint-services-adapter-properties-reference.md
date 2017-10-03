---
title: "Windows SharePoint Services 配接器屬性參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ConfigCustomTemplatesDocLib property [Windows SharePoint Services adapters]
- InFileSize property [Windows SharePoint Services adapters]
- InIconUrl property [Windows SharePoint Services adapters]
- InOfficeIntegration property [Windows SharePoint Services adapters]
- code samples, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, properties
- ConfigCustomTemplatesNamespaceCol property [Windows SharePoint Services adapters]
- configuring [Windows SharePoint Services adapters], properties
- ConfigTemplatesDocLib property [Windows SharePoint Services adapters]
- InPropertiesXml property [Windows SharePoint Services adapters]
- InItemId property [Windows SharePoint Services adapters]
- InListName property [Windows SharePoint Services adapters]
- InArchivedMsgUrl property [Windows SharePoint Services adapters]
- Filename property [Windows SharePoint Services adapters]
- InListUrl property [Windows SharePoint Services adapters]
- ConfigTemplatesNamespaceCol property [Windows SharePoint Services adapters]
- InLastModifiedBy property [Windows SharePoint Services adapters]
- ConfigOverwrite property [Windows SharePoint Services adapters]
- ConfigPropertiesXml property [Windows SharePoint Services adapters]
- TransmittedFileLocation property [Windows SharePoint Services adapters]
- InTitle property [Windows SharePoint Services adapters]
- Windows SharePoint Services adapters, code samples
- InCreated property [Windows SharePoint Services adapters]
- InCreatedBy property [Windows SharePoint Services adapters]
- InLastModified property [Windows SharePoint Services adapters]
- URL property [Windows SharePoint Services adapters]
- InEditUrl property [Windows SharePoint Services adapters]
- ConfigOfficeIntegration property [Windows SharePoint Services adapters]
- ConfigTimeout property [Windows SharePoint Services adapters]
- ConfigNamespaceAliases property [Windows SharePoint Services adapters]
- ConfigAdapterWSPort property [Windows SharePoint Services adapters]
ms.assetid: c64c43ac-05bb-427c-987a-71663ae8e43d
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 691708378d778eb0c91be73fe2b775d5bfd27cfd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="windows-sharepoint-services-adapter-properties-reference"></a>Windows SharePoint Services 配接器屬性參考
下列 Windows SharePoint Services 配接器屬性會升級到 BizTalk Server 或用來指定外寄訊息的傳送埠組態選項。 這些屬性可以用來存取與訊息相關的 Windows SharePoint Services 資訊，或提供資訊到來自協調流程內的 Windows SharePoint Services 配接器。  
  
## <a name="message-property-precedence"></a>訊息屬性優先順序  
 對於覆寫在協調流程和傳送埠中定義的訊息屬性，有一套優先順序的規則。  
  
 以下是這些規則：  
  
1.  在 PropertiesXML 內部協調流程中定義的屬性  
  
2.  在協調流程中定義的屬性  
  
3.  在屬性名稱/或屬性來源集合內部的傳送埠層級中定義的屬性  
  
4.  在傳送埠層級定義的屬性  
  
## <a name="considerations-and-known-issues"></a>考量與已知問題  
 下列是 Windows SharePoint Services 配接器屬性的考量：  
  
-   協調流程中的屬性清單已經根據屬性位置，與由連接埠定義的屬性合併。 若有衝突，協調流程屬性將會覆寫傳送埠屬性。  
  
## <a name="property-types"></a>屬性類型  
  
|屬性類型|Description|  
|-------------------|-----------------|  
|**IN**|IN 屬性是從 Windows SharePoint Services 取得其值的 BizTalk Server 屬性。 **注意：**您不應修改這些屬性在協調流程中的。|  
|**組態**|CONFIG 屬性是從 BizTalk 協調流程或自訂管線取得其值的屬性。 Windows SharePoint Services 配接器會在決定外寄訊息的目的地時，使用此值。 CONFIG 屬性可以讓您指定在協調流程或自訂管線中的部分屬性值，不然您必須在傳送埠中定義。 開頭不是 IN 或 CONFIG 的屬性皆是 IN 和 CONFIG，URL 屬性除外。|  
|**升級**|以內容為基礎的路由 (CBR) 可以使用 PROMOTED 屬性。 CBR 無法使用不是標示為 PROMOTED 的屬性。 **注意：**升級的屬性雖然所有配接器屬性會顯示在 CBR 篩選編輯器中，可用於 CBR。|  
|**特殊**|不適用|  
  
> [!NOTE]
>  所有屬性都存在於 http://schemas.microsoft.com/BizTalk/2006/WindowsSharePointServices-properties 命名空間之下，而且可以透過使用 `WSS.<WSS_Property_Name>` 語法，從協調流程或傳送埠篩選存取。  
  
## <a name="property-list"></a>屬性清單  
  
|Windows SharePoint Services 標準資料行|Windows SharePoint Services 屬性名稱與類型|類型|Description|屬性類型|  
|-------------------------------------------------|--------------------------------------------------------|----------|-----------------|-------------------|  
|名稱|檔名|xs:string|具有 Windows SharePoint Services 檔案副檔名的檔案名稱。 包括副檔名的檔案名稱，在文件庫中是唯一的。|IN/CONFIG/ PROMOTED|  
|不適用|Url|xs:string|檔案的 URL。|IN/PROMOTED|  
|不適用|TransmittedFileLocation|不適用|此屬性是用於商務活動監控 (BAM) 做為整合用途，並且在協調流程中無法使用。|SPECIAL|  
|不適用|InArchivedMsgUrl|xs:string|封存文件庫中檔案的 URL。 此屬性在接收位置未封存訊息時無法使用。|IN/PROMOTED|  
|類型|InIconUrl|xs:string|用來代表文件之 Windows SharePoint Services 圖示的 URL。|IN|  
|Title|InTitle|xs:string|Windows SharePoint Service 檔案的標題。 這與檔案名稱不同。 標題在文件庫中不須是唯一的。|IN/PROMOTED|  
|修改日期|InLastModified|xs:dateTime|上次修改 Windows SharePoint Service 的日期。|IN/PROMOTED|  
|修改者|InLastModifiedBy|xs:string|上次修改檔案的使用者名稱。|IN/PROMOTED|  
|ID|InItemId|xs:int|檔案的 ID。 這是在文件庫內唯一的整數，可用來存取檔案。|IN|  
|編輯|InEditUrl|xs:string|可以存取來編輯檔案屬性的 URL。|IN|  
|建立日期|InCreated|xs:dateTime|建立 Windows SharePoint Service 檔案的日期。|IN/PROMOTED|  
|建立者|InCreatedBy|xs:string|建立檔案的使用者。|IN/PROMOTED|  
|檔案大小|InFileSize|xs:int|Windows SharePoint Services 檔案的大小。|IN|  
|不適用|InListName|xs:string|此檔案所在的文件庫名稱。|IN/PROMOTED|  
|不適用|InListUrl|xs:string|此檔案所在的文件庫或文件庫資料夾名稱。|IN|  
|不適用|InPropertiesXml|xs:string|包含所有標準和使用者定義 Windows SharePoint Services 資料行的一般 XML 文件。 它可以從協調流程存取任何 Windows SharePoint Services 資料行，包括使用者定義資料行的值。 **注意：**它沒有 16 資料行的限制。 **注意：**請參閱本主題的下一節的範例 InPropertiesXml 值。|IN|  
|不適用|InOfficeIntegration|xs:string|根據接收位置的值。 這個值可以是 `yes`、`no` 或 `optional`。|IN|  
|不適用|ConfigOverwrite|xs:string|[是] 會以相同名稱覆寫已經存在的檔案。 [否] 會在相同名稱的檔案存在時引發一個錯誤。 [重新命名] 會藉由附加唯一的序列到檔案名稱，將檔案變成一個唯一名稱。 **注意：**這是與實體傳送埠的 [覆寫] 欄位相似。 **注意：** [協調流程] 不是有效的值，這個欄位。|CONFIG|  
|不適用|ConfigNamespaceAliases|xs:string|XPATHs 的別名定義。|CONFIG|  
|不適用|ConfigOfficeIntegration|xs:string|若應該呼叫 OfficeImporter 則為 [是]。 [否] 則依原狀處理訊息，不作任何變更。 若找到 IP 解決方案，則 [選擇性] 會導致 [是]，不然則為 [否]。 **注意：**這是與實體傳送埠的 [Microsoft Office 整合] 欄位相似。 **注意：** [協調流程] 不是有效的值，這個欄位。|CONFIG|  
|不適用|ConfigTemplatesDocLib|xs:string|後援文件庫名稱。 這是搜尋的第二個位置。 **注意：**這是與實體傳送埠的 [範本後援文件庫] 欄位相似。|CONFIG|  
|不適用|ConfigTemplatesNamespaceCol|xs:string|後援文件庫的命名空間資料行名稱。 **注意：**類似於實體傳送埠的 範本後援命名空間資料行 ' 欄位。|CONFIG|  
|不適用|ConfigCustomTemplatesDocLib|xs:string|主要文件庫名稱。 這是搜尋的第一個位置。 **注意：**這是與實體傳送埠的 [範本文件庫] 欄位相似。|CONFIG|  
|不適用|ConfigCustomTemplatesNamespaceCol|xs:string|主要文件庫的命名空間資料行名稱。 **注意：**這是與實體傳送埠的 [範本命名空間資料行] 欄位相似。|CONFIG|  
|不適用|ConfigPropertiesXml|xs:string|一般 XML 文件，其中包含所有 Windows SharePoint Services 資料行名稱，以及隨後在 Windows SharePoint Services 中更新的值。 它可以讓協調流程開發人員設定即將在 SharePoint 建立的後續訊息的 SharePoint 資料行值。 **注意：**類似於資料行 n 透過所提供的功能和資料行 n 值 欄位的實體傳送埠。 **注意：**它有 16 個資料行限制。 **注意：**請參閱本主題稍後的範例 ConfigPropertiesXml 值。|CONFIG|  
|不適用|ConfigTimeout|xs:int|Web 服務呼叫的逾時 (以毫秒為單位)。|CONFIG|  
|不適用|ConfigAdapterWSPort|xs:int|連接埠或 IIS 的網站，其中已安裝並設定配接器。 **注意：**協調流程中無效的連接埠組態值將會擱置該訊息，即使實體傳送埠的值覆寫協調流程定義。|CONFIG|  
  
## <a name="sample-inpropertiesxml"></a>範例 InPropertiesXml  
 以下是 InPropertiesXml 的範例 XML。  
  
```  
<InPropertiesXml>  
     <Property name="InItemId">2</Property>  
     <Property name="Created">12/14/2004 1:30:31 PM</Property>  
     <Property name="Author">3;#John Doe</Property>  
     <Property name="Modified">12/14/2004 1:30:31 PM</Property>  
     <Property name="Editor">3;#John Doe</Property>  
     <Property name="_ModerationStatus">0</Property>  
     <Property name="_ModerationComments" />  
     <Property name="FileRef">/sites/BASSite/SourceLibrary/PO1.xml</Property>  
     <Property name="FileDirRef">2;#sites/BASSite/SourceLibrary</Property>  
     <Property name="InLastModified">2004-12-14 13:30:31</Property>  
     <Property name="InCreated">2004-12-14 13:30:31</Property>  
     <Property name="InFileSize">7338</Property>  
     <Property name="FSObjType">0</Property>  
     <Property name="CheckedOutUserId">2;#3</Property>  
     <Property name="Filename">PO1.xml</Property>  
     <Property name="VirusStatus">2;#7338</Property>  
     <Property name="CheckedOutTitle">2;#John Doe</Property>  
     <Property name="LinkCheckedOutTitle">John Doe</Property>  
     <Property name="InLastModifiedBy">MyDomain\jdoe</Property>  
     <Property name="InCreatedBy">MyDomain\jdoe</Property>  
     <Property name="owshiddenversion">1</Property>  
     <Property name="File_x0020_Type">xml</Property>  
     <Property name="HTML_x0020_File_x0020_Type" />  
     <Property name="_SourceUrl" />  
     <Property name="_SharedFileIndex" />  
     <Property name="LinkFilenameNoMenu">PO1.xml</Property>  
     <Property name="LinkFilename">PO1.xml</Property>  
     <Property name="SelectTitle">2</Property>  
     <Property name="SelectFilename">2</Property>  
     <Property name="Edit">xml</Property>  
     <Property name="InIconUrl">/sites/BASSite/SourceLibrary/PO1.xml</Property>  
     <Property name="Url">http://localhost:80/sites/BASSite/SourceLibrary/PO1.xml</Property>  
     <Property name="EncodedAbsUrl">PO1</Property>  
     <Property name="BaseName">7338</Property>  
     <Property name="FileSizeDisplay" />  
     <Property name="InstanceID">200</Property>  
     <Property name="Order" />  
     <Property name="InTitle" />  
     <Property name="ColumnOne" />  
     <Property name="ColumnTwo" />  
     <Property name="ColumnThree" />  
     <Property name="ColumnFour" />  
     <Property name="InListName">SourceLibrary</Property>  
     <Property name="InListUrl">http://localhost:80/sites/BASSite/SourceLibrary</Property>  
     <Property name="InEditUrl">http://localhost:80/sites/BASSite/SourceLibrary/Forms/EditForm.aspx?ID=2</Property>  
     <Property name="InOfficeIntegration">yes</Property>  
</InPropertiesXml>  
```  
  
## <a name="sample-configpropertiesxml"></a>範例 ConfigPropertiesXml  
 以下是 ConfigPropertiesXml 的範例 XML。  
  
```  
<ConfigPropertiesXml>  
     <PropertyName1>PO number</PropertyName1>  
     <PropertySource1>%XPATH=//orchns:PurchaseOrder/orchns:Header/orchns:ID%</PropertySource1>  
     <PropertyName2>Charge To</PropertyName2>  
     <PropertySource2>%XPATH=//orchns:PurchaseOrder/orchns:orderBody/orchns:chargeTo%</PropertySource2>  
     <PropertyName3>PO Priority</PropertyName3>  
     <PropertySource3>%XPATH=//orchns:PurchaseOrder/orchns:orderBody/orchns:priority%</PropertySource3>  
     <PropertyName4>Order Date</PropertyName4>  
     <PropertySource4>%XPATH=//orchns:PurchaseOrder/orchns:orderBody/orchns:dateOrdered%</PropertySource4>  
</ConfigPropertiesXml>  
```  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 Windows SharePoint Services 接收位置](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [如何設定 Windows SharePoint Services 傳送處理常式](../core/how-to-configure-a-windows-sharepoint-services-send-handler.md)   
 [如何設定 Windows SharePoint Services 傳送埠](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)   
 [Windows SharePoint Services 配接器運算式](../core/windows-sharepoint-services-adapter-expressions.md)   
 [支援 Windows SharePoint Services 資料行類型](../core/supported-windows-sharepoint-services-column-types.md)