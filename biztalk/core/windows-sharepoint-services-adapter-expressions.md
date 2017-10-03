---
title: "Windows SharePoint Services 配接器運算式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- macros, Windows SharePoint Services adapters
- configuring [Windows SharePoint Services adapters], supported macros
- configuring [Windows SharePoint Services adapters], expressions
- Windows SharePoint Services adapters, expressions
ms.assetid: 15e3afb2-0ef8-41b4-b3ec-de84af738c12
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf777931837f036f7228c4a359eef77faa9e97e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="windows-sharepoint-services-adapter-expressions"></a>Windows Sharepoint Services 配接器運算式
本主題說明格式與意義可以指定為值的字串**檔案 NameProperty 來源**Windows SharePoint Services 配接器的屬性。 它也會描述相關的內容屬性， **WSS。檔名**和**WSS。ConfigPropertiesXml**。 這些運算式可讓您根據常值與從訊息或 BizTalk 系統擷取的值，輕鬆地定義檔案名稱值或是自訂的 Windows SharePoint Service 資料行值。  
  
 運算式可以包含常值與巨集。 常值將依照您的輸入出現在檔案名稱中。 巨集必須放置在 '%' 字元之間。 巨集的範例是 `%MessageID%`，執行階段中會將這個巨集取代成訊息的 GUID。  
  
> [!NOTE]
>  使用 %字元時為常值或是用於 XPATH 中，則必須逸出如下\\%。 單一 %將會視為巨集分隔符號，其中\\於執行階段由單一 %取代 %。 \ 必須逸出字元，就像這樣\\ \\。  
  
## <a name="expression-examples"></a>運算式範例  
  
|設計階段值|執行階段值|  
|-----------------------|-------------------|  
|XYZ|XYZ|  
|PurchaseOrder|PurchaseOrder|  
|%MessageID%|55B93F27-7455-4066-ABE1-B4EBE6839A1A|  
|PurchaseOrder - %MessageID%|PurchaseOrder - 55B93F27-7455-4066-ABE1-B4EBE6839A1A|  
|折扣\\%10|Discount %10|  
|PurchaseOrder - %XPATH=//ns0:PurchaseOrder/ns0:ID%|PurchaseOrder – 10001|  
|PurchaseOrder - %XPATH=//ns0:PurchaseOrder/ns0:PartnerName%-%XPATH=//ns0:PurchaseOrder/ns0:ID%|PurchaseOrder – Contoso-10001|  
  
## <a name="supported-macros"></a>支援的巨集  
  
|設計階段值|執行階段值|  
|-----------------------|-------------------|  
|%MessageID%|BizTalk 訊息識別碼是唯一的 GUID。|  
|%SendingOrchestrationID%|產生訊息的協調流程執行個體之 BizTalk 識別碼。|  
|%SendingOrchestrationType%|產生訊息的協調流程類型名稱。|  
|%Xpath =\<xpath > %|允許指定要用來擷取訊息值的 XPATH。 「\<xpath >"必須取代有效的 XPATH 運算式。 **注意：**命名空間別名必須定義在 ' Namespace Aliases' 或 WSS 運算式外。ConfigNamespaceAliases 欄位。|  
|%Filename%|取代成從訊息內容屬性 WSS.Filename 擷取的檔案名稱值。 從 SharePoint 接收的訊息會將 WSS.Filename 內容屬性設定為 SharePoint 檔案的名稱。 傳回的值是使用 Path.GetFilenameWithoutExtension 來預先處理。 **注意：**這個巨集不能用於在 WSS。Config * 內容屬性 （從協調流程）。|  
|%Extension%|取代成從訊息內容屬性 WSS.Filename 擷取的副檔名值。 從 SharePoint 接收的訊息會將 WSS.Filename 內容屬性設定為 SharePoint 檔案的名稱。 傳回值會使用 Path.GetExtension 進行前置處理。 傳回的值不會包含 "."。 **注意：**這個巨集不能用於在 WSS。Config * 內容屬性 （從協調流程）。|  
  
 屬性升級支援的任何有效運算式都是有效的設計階段檔案名稱。 此設計階段檔案名稱將在執行階段擴充成 Windows SharePoint Services 檔案名稱。 此 Windows SharePoint Services 檔案名稱有一些其他的限制，如下所述：  
  
-   有效的 Windows 檔案名稱可以包含任何 Unicode 字元，但下列字元除外：/  \  :  *  ?  \<> &#124; "# {} %& ~ 或定位字元和多個句號。  
  
-   檔案名稱不能超過 256 個字元，而且整個 URL 必須少於或等於 256 個字元。  
  
-   若擴充的 Windows SharePoint Services 檔案名稱包含無效的字元，或是若擴充的檔案名稱或 URL 太長，則會在應用程式事件日誌中記錄錯誤，並且擱置訊息。 錯誤和訊息狀態也會顯示在使用訊息事件和服務執行個體追蹤的 [群組中樞] 頁面中。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 Windows SharePoint Services 接收位置](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [如何設定 Windows SharePoint Services 傳送處理常式](../core/how-to-configure-a-windows-sharepoint-services-send-handler.md)   
 [如何設定 Windows SharePoint Services 傳送埠](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)   
 [支援 Windows SharePoint Services 資料行類型](../core/supported-windows-sharepoint-services-column-types.md)