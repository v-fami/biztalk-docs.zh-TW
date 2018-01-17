---
title: "設定 SharePoint Services 接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9afed0e4-0f72-4df4-a2cb-d999c6fbbc86
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 807f13611b7e8977e0d5067787717427efc4bed2
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="configure-sharepoint-services-receive-location"></a>設定 SharePoint Services 接收位置
本主題列出建立步驟[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]接收位置。  
  
## <a name="create-a-receive-location"></a>建立接收位置  
 在建立接收位置時，接收位置會使用的預設的接收處理常式相關聯的傳輸類型。 當使用[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]配接器、 預設接收處理常式為**BizTalkServerApplication**。 如需加入新的接收處理常式的步驟，請移至 [如何建立配接器處理常式](http://go.microsoft.com/fwlink/p/?LinkId=263646)。  
  
 建立接收位置︰  
  
1.  在**BizTalk Server 管理**主控台中，展開**BizTalk 群組 [*GroupName*]**，依序展開**應用程式**，然後展開包含接收位置的應用程式。  
  
2.  建立 **單向接收埠**。 [如何建立接收埠](../core/how-to-create-a-receive-port.md)列出的步驟。  
  
    > [!IMPORTANT]
    >  A**要求回應接收位置**不是使用[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]配接器。  
  
     其他接收埠的設定選項包括︰  
  
     [如何將接收位置新增至接收埠](../core/how-to-add-a-receive-location-to-a-receive-port.md)： 下一個步驟中新增接收位置。  
  
     [如何設定的輸入的對應接收埠](../core/how-to-configure-inbound-maps-for-a-receive-port.md)  
  
     [如何設定追蹤接收埠](../core/how-to-configure-tracking-for-a-receive-port.md)  
  
3.  按一下  **確定** 儲存設定。  
  
4.  以滑鼠右鍵按一下 **接收位置**, ，按一下  **新增**, ，然後按一下  **單向接收位置**。  
  
    > [!IMPORTANT]
    >  A**要求回應接收位置**不是使用[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]配接器。  
  
5.  選取接收埠，然後按一下 **確定**。  
  
6.  在  **屬性**, ，輸入 **名稱** 和 **管線** 屬性。 在 **類型** 下拉式清單中，按一下  **Windows SharePoint Services** ，然後選取 **接收處理常式** 屬性。  
  
7.  按一下  **設定**。 在  **屬性**, ，設定下列各項︰  
  
    |||  
    |-|-|  
    |配接器 Web 服務連接埠|**需要**。 在裝載 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 配接器 Web 服務的 IIS 網站上設定的連接埠。<br /><br /> 預設為連接埠 **80**, ，這是標準的 HTTP 連接埠。 如果使用 80 以外的連接埠，請更新此值。|  
    |逾時|**需要**。 此值決定配接器從 Web 服務接收回應的時間 (以毫秒為單位)。<br /><br /> 預設值是 **100000 毫秒** （100 秒）。<br /><br /> 如果訊息或批次大小高於預期，則提高此值。|  
    |使用用戶端 OM|**需要**。 決定使用 SharePoint Client Side Object Model (CSOM) 或 Service Side Object Model (SSOM)。<br /><br /> 預設值是 **是**。 設定為**是**上使用 SharePoint CSOM [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 電腦沒有任何需求。<br /><br /> 設定為**否**使用 SharePoint ssom，其包含在上安裝的 web 服務[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]電腦。<br /><br /> [附錄 b： 安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)提供所用 SSOM 和 CSOM 元件的相關特定資訊[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]配接器。|  
    |封存檔案名稱|**選擇性**。 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Web 服務可以封存文件中的 SharePoint 文件庫。 輸入備份檔案的名稱。<br /><br /> 輸入檔案名稱，如 **PurchaseOrder0001.xml** 或運算式。 運算式可以混合任何常值、巨集和 XPATH 查詢。 例如，"PurchOrd-%XPATH=//po:PurchaseOrderId%-%MessageID%.xml"。 提供沒有任何檔案名稱時，會使用原始程式檔的檔案名稱。 請參閱[Windows SharePoint Services 配接器運算式](../core/windows-sharepoint-services-adapter-expressions.md)如需詳細資訊。 **注意︰**  的"%sendingorchestrationid%"和"%sendingorchestrationtype%"巨集不支援此欄位。|  
    |封存位置 URL|**選擇性**。 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]封存文件儲存的資料夾 URL。 輸入 SharePoint 網站的相對路徑。 例如， **封存** 或 **共用 Documents/Processed Orders /**。 如果未指定封存位置，配接器處理之後，會刪除文件。 **注意︰**  SharePoint 文件庫或資料夾 URL 可以不同於它的名稱。 請檢查 Web 瀏覽器中的位址以找出正確的 URL。|  
    |封存覆寫|**需要**。 指定覆寫現有檔案。<br /><br /> 預設值是 **否**, ，這無法封存，如果具有相同名稱的檔案存在於封存。 在此案例中，已簽出檔案，且必須手動封存。 **注意︰**  封存檔案，將封存檔案名稱值使用巨集時的檔案名稱是唯一。 例如，使用封存檔案名稱，例如**PO-%MessageID%.xml 或 PO-%XPATH=//ns0:PurchaseOrder/ns0:*識別碼*%.xml**，其中 ID 是唯一的採購訂單識別碼。|  
    |批次大小|**需要**。 以批次的 web 服務所處理的文件數目上限。 已處理的批次可能包含較少的郵件超過定義的批次大小。 它不包含多個訊息。<br /><br /> 預設值是 **20** ，至少必須有值為 **1**。|  
    |錯誤閾值|**需要**。 停用接收位置前，配接器的連續輪詢失敗的數目上限。<br /><br /> 預設值是 **10**。 若要停止從停用接收位置，請設為 **0**。|  
    |命名空間別名|**選擇性**。 命名空間別名定義的逗號或分號分隔清單。<br /><br /> 使用此欄位來定義上面所列的封存檔案名稱 欄位中引用的 XPATH 查詢所使用的命名空間別名。 例如，輸入 **po = 'http://OrderProcess/POrder'，conf = 'http://OrderProcess/Confirmation' ipsol = '{D8217CF1-4EF7-4bb5-A30D-765ECB09E0D9}'**。|  
    |輪詢間隔|**需要**。 以秒為單位，等待新訊息的配接器所執行的兩個連續查詢之間的時間。<br /><br /> 預設值是 **60** ，至少必須有值為 **1**。 **注意︰**  若要改善配接器的輸送量和回應時間，請輸入較低的值。|  
    |SharePoint 網站 URL|**選擇性**。 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 網站的完整 URL。 例如，http:// *SharePointServer*/sites/testsite。 **注意︰**  傳送埠或接收位置 URI 不能超過 256 個字元。|  
    |來源文件庫 URL|**選擇性**。 URL 相對路徑的[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]的擷取文件的文件庫。 例如， **/Shared Documents /** 或 **/new Purchase Orders /**。 **注意︰**  SharePoint 文件庫可以不同於它的名稱。 請檢查 Web 瀏覽器中的位址以找出正確的 URL。|  
    |檢視表名稱|**選擇性**。 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]配接器處理用來篩選的文件的檢視。 例如， **核准的訂單**。<br /><br /> 若要處理在來源文件庫中的所有現有文件，將此欄位留空。 在檢視中的資料夾和那些資料夾中的訊息不是由配接器處理。 建立一般檢視，顯示所有文件簡維結構，包括子資料夾中的現有文件中。|  
    |Microsoft Office 整合|**需要**。 對於二進位訊息，您必須使用 [否] 或 [選擇性] 值。<br /><br /> 預設值是 **選擇性**。<br /><br /> 這些選項包括：<br /><br /> -   **否**： 處理文件 「 現狀 」。 對於二進位訊息，可以使用這個選項。<br />-   **選擇性**︰ 嘗試移除 InfoPath 處理指示。 處理指示不會被移除，如果 「 現狀 」 處理文件。 對於二進位訊息，可以使用這個選項。<br />-   **是**︰ 移除 InfoPath 處理指示。 如果發生錯誤時，會略過訊息。|  
    |SharePoint 線上密碼|**選擇性**。 SharePoint 線上帳戶的密碼。|  
    |SharePoint 線上使用者名稱|**選擇性**。 SharePoint 線上帳戶的使用者名稱。|  
  
8.  按一下  **確定** 儲存設定。  
  
9. 接收位置的其他組態選項包括︰  
  
     [如何設定排程的接收位置](../core/how-to-configure-scheduling-for-a-receive-location.md)  
  
10. 按一下  **確定** 儲存設定。  
  
 其他接收埠和接收位置的主題︰  
  
 [管理接收埠](../core/managing-receive-ports.md)  
  
 [管理接收位置](../core/managing-receive-locations.md)  
  
 接下來，建立[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]傳送埠：  
  
 [設定 SharePoint Services 傳送埠](../core/configure-sharepoint-services-send-port.md)  
  
## <a name="see-also"></a>另請參閱  
 [設定 SharePoint Services 傳送埠](../core/configure-sharepoint-services-send-port.md)   
 [SharePoint Services 配接器疑難排解](../core/troubleshooting-sharepoint-services-adapter.md)   
 [CSOM：SharePoint Services 配接器](../core/csom-sharepoint-services-adapter.md)