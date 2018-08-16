---
title: 設定 SharePoint Services 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36aadbc2-316f-4e1c-a5a8-b162470acf9e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39e57d8480825a6473edfbeb64ac5922a91281b7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966959"
---
# <a name="configure-sharepoint-services-send-port"></a>設定 SharePoint Services 傳送埠
本主題比較靜態傳送埠與動態傳送埠，還列出了用於建立 [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] 傳送埠的步驟。 具體來說：  

 [靜態與動態傳送埠的傳送埠](../core/configure-sharepoint-services-send-port.md#BKMK_StaticvsDynamic)  

 [建立靜態傳送埠](../core/configure-sharepoint-services-send-port.md#BKMK_StaticSend)  

 [建立動態傳送埠](../core/configure-sharepoint-services-send-port.md#BKMK_DynamicSend)  

##  <a name="BKMK_StaticvsDynamic"></a> 靜態與動態傳送埠的傳送埠  

||靜態傳送埠|動態傳送埠|  
|-|----------------------|-----------------------|  
|使用具有不同配接器的單一傳送埠。|否<br /><br /> 建立靜態傳送埠時，需要傳輸類型。|是<br /><br /> 動態傳送埠通常會新增至協調流程。 傳輸類型是在協調流程邏輯中設定。|  
|使用具有不同傳送埠屬性 (如 URL) 的單一傳送埠。|否<br /><br /> 建立靜態傳送埠時，必須設定某些配接器屬性 (如 URL)。|是<br /><br /> 動態傳送埠通常會新增至協調流程。 這些屬性是在協調流程邏輯中設定。|  
|必須使用預設傳送處理常式。|否<br /><br /> 建立傳送埠時，可設定傳送處理常式。|否<br /><br /> 建立傳送埠時，可設定傳送處理常式。|  
|在您不知道訊息去處時使用。|否<br /><br /> 建立靜態傳送埠時，您會指定傳輸類型和結束位置。|是<br /><br /> 在協調流程和以內容為基礎的路由案例中，可以設定的結束位置。 這些規則也可以用來篩選訊息傳送目的地的位置。|  
|使用單一傳送埠將訊息傳送給多個合作夥伴。|否<br /><br /> 建立靜態傳送埠時，您會指定傳輸類型和結束位置。|是<br /><br /> 動態傳送埠通常會新增至協調流程。 這些屬性是在協調流程邏輯中設定，而且根據您指定的規則，可以將訊息傳送給多個合作夥伴。|  

##  <a name="BKMK_StaticSend"></a> 建立靜態傳送埠  
 建立靜態傳送埠時，傳送埠會使用與傳輸類型相關聯的預設傳送處理常式。 使用時[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]配接器、 傳送處理常式的預設**BizTalkServerApplication**。 如需新增傳送處理常式的步驟，請移至[如何建立配接器處理常式](http://go.microsoft.com/fwlink/p/?LinkId=263646)。  

 建立靜態傳送埠：  

1. 在**BizTalk Server 管理**主控台中，展開**BizTalk 群組 [*GroupName*]**，展開**應用程式**，然後展開包含傳送埠的應用程式。  

2. 以滑鼠右鍵按一下**傳送埠**，按一下**新增**，然後按一下**靜態單向傳送埠**。  

   > [!IMPORTANT]
   >  A**靜態請求-回應傳送埠**未設定使用[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]配接器。  

3. 在 **屬性**，按一下**Windows SharePoint Services**中**型別**下拉式清單。 請輸入**名稱**，**傳送處理常式**，並**傳送管線**屬性。  

4. 按一下 **設定**。 在 **屬性**，設定下列各項：  


   |                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   |-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |      配接器 Web 服務連接埠       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           **所需**。 在裝載 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 配接器 Web 服務的 IIS 網站上設定的連接埠。<br /><br /> 預設為連接埠**80**，這是標準的 HTTP 連接埠。 如果使用 80 以外的連接埠，請更新此值。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   |               逾時               |                                                                                                                                                                                                                                                                                                                                                                                                                     **所需**。 此值決定配接器從 Web 服務接收回應的時間 (以毫秒為單位)。<br /><br /> 預設值是**100000 毫秒**（100 秒）。<br /><br /> 如果訊息或批次大小高於預期，則提高此值。<br /><br /> 配接器執行階段 Web 服務對 Windows SharePoint Services 配接器 Web 服務的呼叫逾時 (以毫秒為單位)。 如果訊息或批次大小高於配接器所預期的平均值時，您可能需要增加這個值。                                                                                                                                                                                                                                                                                                                                                                                                                     |
   |            使用用戶端 OM            |                                                                                                                                                                                                         **所需**。 決定使用 SharePoint Client Side Object Model (CSOM) 或 Service Side Object Model (SSOM)。<br /><br /> 預設值是**是**。 設定為 **[是]** 上使用 SharePoint CSOM [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 電腦沒有任何需求。<br /><br /> 設定為**No**若要使用 SharePoint SSOM，其包含在上安裝的 web 服務[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]電腦。<br /><br /> [附錄 b： 安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)上所使用的 SSOM 和 CSOM 元件提供的特定資訊[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]配接器。                                                                                                                                                                                                         |
   |       目的資料夾 URL        |                                                                                                                                                                                                                                                                                                                                                               **所需**。 用於存放文件的 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 資料夾 URL。 輸入 SharePoint 網站的相對路徑。 例如， **Shared Documents**或是**Shared Documents/Purchase Orders /**。 清單也可作為目的地使用。 例如， **Lists/Tasks**。 如果指定清單，訊息本文不會與清單項目一起儲存。 從訊息擷取的值會升級到 SharePoint 資料行中。 **注意：** SharePoint 文件庫或資料夾 URL 可能會不同於它的名稱。 請檢查 Web 瀏覽器中的位址以找出正確的 URL。                                                                                                                                                                                                                                                                                                                                                                |
   |              檔名               |                                                                                                                                                                                                                                            **選擇性**。 輸入 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 檔案的名稱。<br /><br /> 輸入檔案名稱，例如**PurchaseOrder0001.xml**或運算式。 運算式可以混合任何常值、巨集和 XPATH 查詢。 例如，輸入**PurchOrd-%XPATH=//po:PurchaseOrderId%-%MessageID%.xml**。 若未提供檔案名稱，就會使用原始檔案的名稱、協調流程所提供的值，或 'Msg-%MessageID%.xml'。 請參閱[Windows SharePoint Services 配接器運算式](../core/windows-sharepoint-services-adapter-expressions.md)如需詳細資訊。 **注意：** 時傳送訊息至清單中，此 Filename 值會忽略且不會儲存在 SharePoint 資料行。 而是使用 16 個可用資料行的其中一個，以更新 [標題] 資料行。 SharePoint 清單沒有 [檔案名稱] 資料行。                                                                                                                                                                                                                                             |
   |         命名空間別名          |                                                                                                                                                                                                                                                                                                                                                                                                           **選擇性**。 命名空間別名定義的逗號或分號分隔清單。<br /><br /> 使用此欄位來定義 [檔案名稱] 或 [資料行值] 欄位中引用的 XPATH 查詢所使用的命名空間別名。 例如，輸入**po ='<http://OrderProcess/POrder>'，conf ='<http://OrderProcess/Confirmation>' xmlns =""; ipsol='{d8217cf1-4ef7-4bb5 = '{D8217CF1-4EF7-4bb5-A30D-765ECB09E0D9}'**。 **注意：** 這個屬性不會覆寫 WSS。ConfigNamespacesAliases 訊息的協調流程所定義的內容屬性。 反而會合併這兩個值。                                                                                                                                                                                                                                                                                                                                                                                                           |
   |              Overwrite              |                                                                                                                                                                                                                                                                                                                                    **所需**。 如有檔案存在，請判斷此檔案是否遭到覆寫。<br /><br /> 預設值是**No**。 這些選項包括：<br /><br /> -   **否**： 會引發錯誤並擱置訊息，如果存在具有相同名稱的檔案。<br />-   **協調流程**： 使用具有相同名稱的檔案是否存在，協調流程中定義的值。<br />-   **重新命名**： 重新命名新的檔案，如果存在具有相同名稱的檔案。<br />-   **是**： 覆寫現有的檔案，如果它具有相同的名稱。<br />     當設定為**是**，傳送大量同名的訊息可能會導致 SharePoint 事件檢視器錯誤。 這些錯誤並不會影響配接器，而且會重試所有失敗的訊息。                                                                                                                                                                                                                                                                                                                                     |
   |         SharePoint 網站 URL         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     **所需**。 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 網站的完整 URL。 例如 http://<em>SharePointServer</em>/sites/testsite。 **注意：** 傳送埠或接收位置 URI 不能超過 256 個字元。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |    Microsoft Office 整合     |                                       **所需**。 對於二進位訊息，您必須使用**No**或是**選擇性**。<br /><br /> 預設值是**選擇性**。 這些選項包括：<br /><br /> <ul><li>**否**： 儲存文件**為-是**。 對於二進位訊息，可以使用這個選項。</li><li>**選擇性**： 修改文件，讓它自動在 Office 應用程式，例如 InfoPath 開啟。 如果找不到處理指示，則會處理文件**為-是**。 對於二進位訊息，可以使用這個選項。</li><li>**協調流程**： 使用協調流程中定義的值。</li><li>**是**： 修改文件，讓它自動在 Office 應用程式，例如 InfoPath 開啟。 如果找不到處理指示，則會擱置資訊。<br /><br />     當設定為**是**，至少一個下列的屬性組會需要：<br /><br /> <ul><li>*範本文件庫*和*範本命名空間資料行*</li><li>*範本後援文件庫*和*範本後援命名空間資料行*</li></ul></li><li>**是 （InfoPath 表單庫）**： 如果 InfoPath 解決方案位於表單庫時，會修改文件，讓它自動在 Office 應用程式，例如 InfoPath 開啟。 若表單庫沒有解決方案，則會擱置訊息。</li></ul>                                       |
   |     範本文件庫      |                                                                                                                                                                                                                                                **所需*僅*當*範本命名空間資料行*已填入**。 存放 InfoPath 解決方案的 SharePoint 文件庫。 例如，**我的解決方案**。 配接器會尋找*範本文件庫*相符的 InfoPath 解決方案。 如果找不到解決方案，配接器會搜尋*範本後援文件庫*。 **注意︰** *範本文件庫*需要至少一個 '單行文字 」 SharePoint 資料行，其中會填入下列： <ul><li>命名空間和使用 InfoPath 解決方案開啟的 XML 文件的根節點</li><li>或者，XML 文件的根節點</li></ul> 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)。                                                                                                                                                                                                                                                 |
   | 範本後援文件庫 | **所需*僅*當*範本後援命名空間資料行*已填入**。 存放 InfoPath 解決方案的 SharePoint 文件庫。 例如，**範本**。<br /><br /> 中找不到方案*範本文件庫*，配接器會尋找*範本後援文件庫*相符的 InfoPath 解決方案。 *範本後援文件庫*並*範本文件庫*欄位可與兩組 InfoPath 解決方案。 目前有一些一般 InfoPath 解決方案適用於所有一般用途，而且還有供特定夥伴使用的專業 InfoPath 解決方案。 *範本後援文件庫*欄位應指向一般解決方案，而*範本文件庫*應指向供特定夥伴的特製化的解決方案。 **注意︰***範本後援文件庫*需要至少一個 '單行文字 」 SharePoint 資料行，其中會填入下列： <ul><li>命名空間和使用 InfoPath 解決方案開啟的 XML 文件的根節點</li><li>或者，XML 文件的根節點</li></ul> 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)。 |
   | 範本後援命名空間資料行 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         **所需*僅*當*範本後援文件庫*已填入**。 存放 InfoPath 解決方案命名空間的 SharePoint 文件庫。 例如， **myNamespace**。 **注意：** 此欄位會區分大小寫。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |     範本命名空間資料行      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    **所需*僅*當*範本文件庫*已填入**。 SharePoint*範本文件庫*儲存 InfoPath 解決方案之命名空間的資料行。 例如， **myNamespace**。 **注意：** 此欄位會區分大小寫。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
   |     SharePoint 線上密碼      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              **選擇性**。 SharePoint 線上帳戶的密碼。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |     SharePoint 線上使用者名稱      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              **選擇性**。 SharePoint 線上帳戶的使用者名稱。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |             資料行 `n`              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        **選擇性**。 SharePoint 資料行存在於*目的地文件庫*。 更新此資料行的值從訊息中擷取，或在指定*資料行值*欄位。 **注意：** 可以指定最多 16 個資料行。 在此欄位中，大小寫有所區分。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |          資料行 `n` 值           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        **選擇性**。 輸入要為此訊息設定的資料行值。 您可以輸入像是 'Purchase Order' 的常值或運算式。 運算式可以混合任何常值、巨集和 XPATH 查詢。 例如，輸入 **"%xpath=//po:poamount%"，"%sendingorchestrationid%"**。 **注意：** 可以指定最多 16 個資料行。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |


5. 按一下 **確定**儲存設定。  

6. 其他傳送埠設定選項包含：  

   1.  [如何設定傳送埠的傳輸進階選項](../core/how-to-configure-transport-advanced-options-for-a-send-port.md)  

   2.  [如何設定傳送埠備份傳輸選項](../core/how-to-configure-backup-transport-options-for-a-send-port.md)  

   3.  [如何設定傳送埠的輸出對應](../core/how-to-configure-outbound-maps-for-a-send-port.md)  

   4.  [如何設定傳送埠的篩選](../core/how-to-configure-filters-for-a-send-port.md)  

   5.  [如何指派憑證給傳送埠](../core/how-to-assign-a-certificate-to-a-send-port.md)  

   6.  [如何設定傳送埠的追蹤](../core/how-to-configure-tracking-for-a-send-port.md)  

##  <a name="BKMK_DynamicSend"></a> 建立動態傳送埠  
 建立動態傳送埠時，可針對每一個配接器設定傳送處理常式。 多個配接器可以共用單一動態傳送埠。 請參閱[動態傳送埠處理常式是可設定](../core/dynamic-send-port-handler-is-configurable.md)的步驟，以設定動態傳送埠處理常式。  

1. 在**BizTalk Server 管理**主控台中，展開**BizTalk 群組 [*GroupName*]**，展開**應用程式**，然後展開包含傳送埠的應用程式。  

2. 以滑鼠右鍵按一下**傳送埠**，按一下**新增**，然後選擇**動態單向傳送埠**或**動態請求-回應傳送埠**  

3. 在 **屬性**，輸入**名稱**並**管線**屬性  

    按一下 **設定**。  

4. 在 [**設定傳送處理常式**] 視窗中，選擇**傳送處理常式**個別配接器。 傳送處理常式的預設**BizTalkServerApplication**。 如需加入新的傳送處理常式的步驟，請移至[如何建立配接器處理常式](http://go.microsoft.com/fwlink/p/?LinkId=263646)。  

    使用個別主機的原因眾多，其中包括：  

   - **32 位元需求**： 有些配接器需要 32 位元主機，例如 FTP 和 POP3 配接器。 您可以將所有或個別 32 位元配接器劃分到各自的主機中。  

      [BizTalk Server 64 位元的支援](../core/biztalk-server-64-bit-support2.md)  

   - **目的主機**： 建立傳送的主機、 主機接收、 處理協調流程的主機與主機的追蹤。  

   - **不同的主控件設定**： 許多設定都實作主機層級。 因此，可針對各主機設定不同的節流設定。 例如，您可以停用節流設定在 HostA 上。 追蹤 HostB 中的每一個事件。 修改 HostC 的 .NET CLR 設定。 提高 HostD 的記憶體使用量。  

   - **安全性**： 在主機層級實作安全性。 每一個主機都會在專屬的 Windows 帳戶下執行。 例如，HostA 使用 FILE 配接器來存取檔案共用。 將 HostA 使用者帳戶權限提供給檔案共用。 HostB 使用 IIS 伺服器上裝載的 Web 服務。 將 HostB 使用者帳戶授權提供給 Web 服務。 這也可防止其他主機帳戶存取不需要存取的實體。  

   - **不同的介面卡**： 例如，您有數個成品 （接收位置和傳送埠） 使用 HTTP 配接器。 您希望與 HTTP 配接器相關聯的每個成品都位於專屬的主機中。  

   - **個別協調流程**： 個別的協調流程可以位於專屬的主機。 例如，若協調流程使用大量記憶體或大量 CPU，則將該協調流程放入專屬的主機中。  

     [BizTalk Server 效能最佳化指南](http://msdn.microsoft.com/library/dn775063\(v=bts.10\).aspx)並[如何維護和疑難排解 BizTalk Server 資料庫](http://support.microsoft.com/kb/952555)提供效能建議事項。  

5. 按一下 **確定**儲存設定。  

6. 其他傳送埠設定選項包含：  

   1.  [如何設定傳送埠的傳輸進階選項](../core/how-to-configure-transport-advanced-options-for-a-send-port.md)  

   2.  [如何設定傳送埠的輸出對應](../core/how-to-configure-outbound-maps-for-a-send-port.md)  

   3.  [如何設定傳送埠的篩選](../core/how-to-configure-filters-for-a-send-port.md)  

   4.  [如何指派憑證給傳送埠](../core/how-to-assign-a-certificate-to-a-send-port.md)  

   5.  [如何設定傳送埠的追蹤](../core/how-to-configure-tracking-for-a-send-port.md)  

7. 按一下 **確定**儲存設定。  

   其他傳送埠主題：  

   [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)  

   [建立和設定傳送埠群組](../core/creating-and-configuring-send-port-groups.md)  

## <a name="see-also"></a>另請參閱  
 [SharePoint Services 配接器疑難排解](../core/troubleshooting-sharepoint-services-adapter.md)   
 [設定 SharePoint Services 接收位置](../core/configure-sharepoint-services-receive-location.md)   
 [CSOM：SharePoint Services 配接器](../core/csom-sharepoint-services-adapter.md)