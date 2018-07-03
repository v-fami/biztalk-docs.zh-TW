---
title: 如何設定 Windows SharePoint Services 接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, Windows SharePoint Services adapters
- configuring [Windows SharePoint Services adapters], receive locations
- Windows SharePoint Services adapters, receive locations
ms.assetid: 5db3d5cf-4a77-4985-bd03-307c520247ec
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78548238da2a07a0fdadfa787c02ab97bb2e337b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022188"
---
# <a name="how-to-configure-a-windows-sharepoint-services-receive-location"></a>如何設定 Windows SharePoint Services 接收位置
本主題將描述如何使用 BizTalk Server 管理主控台，來建立和設定 Windows SharePoint Services 接收位置。  

### <a name="to-create-and-configure-a-windows-sharepoint-services-receive-location"></a>建立和設定 Windows SharePoint Services 接收位置  

1. 確定您的接收埠已正確設定。 如需有關如何建立和設定接收埠的資訊，請參閱 <<c0> [ 如何建立接收埠](../core/how-to-create-a-receive-port.md)。  

2. 在  **BizTalk Server 管理主控台**，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組 [GroupName]**，展開**應用程式**，然後展開您想要在其中建立接收位置的應用程式。  

3. 以滑鼠右鍵按一下**接收位置**，按一下**新增**，然後按一下**單向接收位置**。  

4. 選取的接收埠，將會包含此接收位置，然後按一下**確定**。  

5. 在 **接收位置屬性**對話方塊的 **傳輸**，請在**型別**下拉式清單方塊中，選取**Windows SharePoint Services**.  

6. 按一下 **設定**。  

7. 在  **Windows SharePoint Services 傳輸屬性**對話方塊方塊中，執行下列動作：  


   |           使用           |                                                                                                                                                                                                                                                                                                                                    以進行此動作                                                                                                                                                                                                                                                                                                                                    |
   |------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |   配接器 Web 服務連接埠   |                                                                                                                                                                      安裝 Windows SharePoint Services 配接器 Web 服務的 IIS 網站的 HTTP 連接埠。 根據預設，這是預設的網站連接埠 80 上的設定。 如果您已在預設的網站以外的任何 IIS Web 站台上設定 Windows SharePoint Services Web 服務，您必須更新此值。                                                                                                                                                                       |
   |           逾時            |                                                                                                                                                                                                        配接器執行階段 Web 服務對 Windows SharePoint Services 配接器 Web 服務的呼叫逾時 (以毫秒為單位)。 如果訊息或批次大小高於配接器所預期的平均值時，您可能需要增加這個值。                                                                                                                                                                                                        |
   |       封存檔案名稱       |                (選擇性) 封存的 Windows SharePoint Services 檔案名稱。 您可以輸入像是 'PurchaseOrder0001.xml' 的常值或運算式。 運算式可以混合任何常值、巨集和 XPATH 查詢。 例如，"PurchOrd-%XPATH=//po:PurchaseOrderId%-%MessageID%.xml"。 若未提供檔案名稱，就會使用來源檔的檔案名稱。 如需有關運算式的詳細資訊，請參閱 < [Windows SharePoint Services 配接器運算式](../core/windows-sharepoint-services-adapter-expressions.md)。 **注意：** 的"%sendingorchestrationid%"和"%sendingorchestrationtype%"巨集不支援此欄位。                |
   |     封存位置 URL     |                                                                                                  相對於 SharePoint 網站的 Windows SharePoint Services 資料夾 URL，已處理的檔案會封存於此處。 例如，Archive 或 /Shared Documents/Processed Orders/。 若未指定封存位置，配接器在處理文件後，就會將文件刪除。 **注意：** 有時候 SharePoint 文件庫或資料夾 URL 會與該項目的名稱不同。 請檢查 Internet Explorer 中的網址列，以找出正確的 URL。                                                                                                   |
   |      封存覆寫       |                              決定是否覆寫封存中的現有檔案。 選取 [是] 以覆寫現有檔案。 當封存中已經有相同名稱的檔案存在時，選取 [否] 讓封存失敗。 在此情況下，檔案仍會被取出，且必須手動封存。 **注意：** 封存檔案時，我們建議使用巨集使用封存檔案名稱值，以便讓檔案名稱成為唯一。 基於此原因，您可以使用如 PO-%MessageID%.xml or PO-%XPATH=//ns0:PurchaseOrder/ns0:ID%.xml 的「封存檔案名稱」，其中 ID 是訂單的唯一識別碼。                              |
   |          批次大小          |                                                                                                                                                                                                              Windows SharePoint Services 傳訊配接器 Web 服務視為一個批次進行處理的文件數目上限。 處理的批次所包含的訊息可能少於定義的批次大小，但絕不會超過定義的批次大小。                                                                                                                                                                                                               |
   |       錯誤閾值        |                                                                                                                                                                                                                                            停用接收位置前，配接器發生連續輪詢失敗的數目上限。 將此欄位設為 0，永不停用接收位置。                                                                                                                                                                                                                                             |
   |      命名空間別名      |                                                                                                                                                              (選擇性) 命名空間別名定義的逗號或分號分隔清單。 使用此欄位，來定義 [封存檔案名稱] 欄位中引用之 XPATH 查詢所用的命名空間別名。 例如，po ='<http://OrderProcess/POrder>'，conf ='<http://OrderProcess/Confirmation>' ipsol='{d8217cf1-4ef7-4bb5 = '{D8217CF1-4EF7-4bb5-A30D-765ECB09E0D9}'                                                                                                                                                               |
   |       輪詢間隔       |                                                                                                                                                                                                                 配接器所執行的兩個連續查詢之間的時間間隔 (以秒為單位)，以查看是否有任何新訊息可供處理。 **注意：** 指定較低的值可改善配接器的輸送量和回應時間。                                                                                                                                                                                                                  |
   |     SharePoint 網站 URL      |                                                                                                                                                                                                                                       Windows SharePoint Services 網站的完整 URL。 例如， http://BizTalkServer/sites/TestSite。 **注意：** URI 傳送埠或接收位置不能超過 256 個字元。                                                                                                                                                                                                                                       |
   | 來源文件庫 URL  | 這是相對於 SharePoint 網站的擷取文件之 Windows SharePoint Services 文件庫的 URL。 例如，/Shared Documents/ 或 /New Purchase Orders/。 **注意：** 您無法從 SharePoint 清單接收訊息。 除非使用會顯示所有資料夾內訊息的檢視，否則您無法從 SharePoint 資料夾接收訊息。 若要這樣做您設定**資料夾**屬性設為值的**顯示所有文件，但不使用資料夾**建立檢視時。 **注意：** 有時 SharePoint 文件庫會與該項目的名稱不同。 請檢查 Internet Explorer 中的網址列，以找出正確的 URL。 |
   |          檢視表名稱           |                                                                            這是用來篩選配接器所處理文件的 Windows SharePoint Services 檢視。 例如，「核准的訂單」。 讓此欄位空白以處理來源文件庫中的所有現有文件。 配接器將不會處理檢視中所顯示的資料夾和其中的訊息。 您可以建立一般檢視，以一般結構顯示所有文件 (包括在子資料夾中的現有文件)。 **注意：** 將會處理一般檢視中的所有訊息。                                                                            |
   | Microsoft Office 整合 |                                                                                                                                                        [選擇性]，在可能時嘗試移除 InfoPath 處理指示，但若不可能時，則以原始格式處理 (例如，二進位文件)。 選擇 [是] 以移除 InfoPath 處理指示，或在發生錯誤時略過訊息。 選擇 [否] 以原始格式處理文件。 對於二進位訊息，您必須使用 [否] 或 [選擇性] 值。                                                                                                                                                         |


8. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
 [如何設定 Windows SharePoint Services 傳送處理常式](../core/how-to-configure-a-windows-sharepoint-services-send-handler.md)   
 [如何設定 Windows SharePoint Services 傳送埠](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)   
 [Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)   
 [Windows SharePoint Services 配接器運算式](../core/windows-sharepoint-services-adapter-expressions.md)   
 [支援的 Windows SharePoint Services 資料行類型](../core/supported-windows-sharepoint-services-column-types.md)