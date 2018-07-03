---
title: 步驟 8 （內部部署）： 設定 BizTalk Server 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 2015-12-08
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5109fb54-8453-444f-bc9c-070a65053397
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93b3eafcc5e49bb6fa360f1db4b6e92d9393068a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996839"
---
# <a name="step-8-on-premises-configure-the-biztalk-server-application"></a>步驟 8 （內部部署）： 設定 BizTalk Server 應用程式
在上一個步驟中，您建立了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。 在此步驟中，您將建置、部署和設定應用程式。  

## <a name="build-and-deploy-the-application"></a>建置及部署應用程式  

1.  在 Visual Studio 中，以滑鼠右鍵按一下 方案總管 中的方案名稱，然後按一下 **建置**。  

2.  部署程序要求組件必須是以強式名稱簽署的。  您必須藉由建立專案與強式名稱組件金鑰檔案的關聯，簽署您的組件。  

    1.  在 [方案總管] 中，以滑鼠右鍵按一下 **[orderprocessingdemo]** 專案，然後再按一下**屬性**。  

    2.  按一下  **Signing**索引標籤，然後選取**簽署組件**核取方塊。  

    3.  從下拉式清單中**選擇強式名稱金鑰檔**方塊中，選取**\<新增...\>**.  

    4.  在 **建立強式名稱金鑰**對話方塊方塊中，輸入金鑰檔案名稱，例如`OrderProcessingDemo.snk`。 清除保護使用密碼，金鑰檔的核取方塊，然後按一下**確定**。  

3.  按一下 **部署**索引標籤上，在右邊的方塊**應用程式名稱**，型別`OrderProcessingDemo`。  

4.  從下拉式清單方塊的清單中的右邊**重新部署**，選取 **，則為 True**。  

5.  在 [方案總管] 中，以滑鼠右鍵按一下 **[orderprocessingdemo]**，然後按一下**部署**。  此時，[輸出] 視窗應該會顯示：  

    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  

    ```  

## <a name="configure-the-application"></a>設定應用程式  

1. 按一下 **開始**，指向**所有程式**，指向**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。  

2. 在左窗格中的主控台樹狀目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**重新整理**。  

3. 依序展開**BizTalk 群組**，展開**應用程式**，展開 **[orderprocessingdemo]**，然後按一下**協調流程**。 您會看到**OrderProcessingDemo.OrderProcessing**部署協調流程。  

4. 在協調流程中，您已建立了邏輯連接埠 (**ReceiveSO**) 以接收來自服務匯流排佇列訊息。 在此步驟中，您會建立實體接收埠以對應至邏輯連接埠。  

   1. 從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 **[orderprocessingdemo]** 節點，以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  

   2. 在 [一般] 索引標籤上，執行下列動作：  


      |                使用                |     以進行此動作      |
      |----------------------------------------|---------------------|
      |                **名稱**                | 型別**ReceiveSO**。 |
      | **啟用失敗訊息的路由** |       (清除)       |


   3. 按一下 **接收位置**，然後按一下**新增**。  

   4. 從 [Receive Location1 - 接收位置屬性] 對話方塊中，執行下列動作：  


      |       使用       |              以進行此動作              |
      |----------------------|--------------------------------------|
      |       **名稱**       |      型別**ReceiveOrders_SO**。      |
      |       **型別**       |       選取  **SB Messaging**。       |
      | **接收處理常式**  | 選取 **[BizTalkServerApplication]**。 |
      | **接收管線** |        選取  **XMLReceive**。        |


   5. 按一下 **設定**。  

   6. 從 [Sb-messaging 傳輸屬性] 對話方塊中上,**一般**索引標籤上，如**佇列或訂用帳戶的 URL**，輸入**sb://mynamespace.servicebus.appfabriclabs.com/queueordersedi**. 在這裡， *mynamespace*是服務匯流排命名空間並*queueordersedi*是您在建立服務匯流排佇列[(適用於 Azure) 的步驟 3： 建立服務匯流排佇列](../core/step-3-for-azure-create-a-service-bus-queue.md)。  

   7. 從 [Sb-messaging 傳輸屬性] 對話方塊中，在**驗證**索引標籤上，指定下列值：  

      |使用|以進行此動作|  
      |--------------|----------------|  
      |**存取控制服務 STS Uri**|輸入 `https://mynamespace-sb.accesscontrol.appfabriclabs.com/`|  
      |**簽發者名稱**|指定簽發者名稱。 通常這會設定為`owner`。|  
      |**簽發者金鑰**|指定簽發者金鑰。|  

      > [!NOTE]
      >  您可以取得的值佇列 URL、 ACS URL、 簽發者名稱和金鑰[Windows Azure CTP Management Portal](http://go.microsoft.com/fwlink/p/?LinkId=202886)。  

   8. 按一下 **確定**直到結束所有對話方塊為止。  

5. 在協調流程中，您已建立了邏輯連接埠 (**SendToSQL**) 將訊息傳送至**SalesOrder**資料庫資料表。 在此步驟中，您會建立實體傳送埠以對應至邏輯連接埠。  

   1. 從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 **[orderprocessingdemo]** 節點，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下  **靜態單向傳送埠**。  

   2. 在 [一般] 索引標籤上，執行下列動作：  


      |     使用      |              以進行此動作              |
      |-------------------|--------------------------------------|
      |     **名稱**      |         型別**SendToSQL**。          |
      |     **型別**      |         選取  **WCF-SQL**。          |
      | **傳送處理常式**  | 選取  **BizTAlkServerApplication**。 |
      | **傳送管線** |     選取  **PassThruTransmit**。     |


   3. 按一下 **設定**。  

   4. 從 [WCF-SQL 傳輸屬性] 上**一般**索引標籤上，執行下列動作：  


      |     使用      |                                                                                                                                                                                    以進行此動作                                                                                                                                                                                    |
      |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | **位址 (URI)** | 型別**mssql://computername/database_instance_name/databasename**。 例如，若要連接到**DemoDB**預設資料庫執行個體之下執行的本機電腦上的資料庫中，輸入 `mssql://.//DemoDB`<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 建立 SQL Server 連接 URI](../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。 |
      |    **動作**     |                                                                                                                                                                     型別**TableOp/Insert/dbo/SalesOrder**。                                                                                                                                                                      |


   5. 從 [WCF-SQL 傳輸屬性] 上**認證**索引標籤上，選取**不會使用單一登入**，並指定 （區分大小寫） 的認證，以連接到 SQL Server 資料庫中所指定連接字串。 如果您想使用 [Windows 驗證] 進行連線，請將認證空白。  

   6. 按一下 **確定**直到結束所有對話方塊為止。  

6. 在協調流程中，您已建立了邏輯連接埠 (**SendToFile**) 將訊息傳送至共用的檔案位置。 在此步驟中，您會建立實體傳送埠以對應至邏輯連接埠。  

   1. 從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 **[orderprocessingdemo]** 節點，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下  **靜態單向傳送埠**。  

   2. 在 [一般] 索引標籤上，執行下列動作：  


      |     使用      |              以進行此動作              |
      |-------------------|--------------------------------------|
      |     **名稱**      |         型別**SendToFile**。         |
      |     **型別**      |           選取 **檔案**。           |
      | **傳送處理常式**  | 選取  **BizTAlkServerApplication**。 |
      | **傳送管線** |       選取  **XML 傳輸**。       |


   3. 按一下 **設定**。  

   4. 從 [檔案傳輸屬性] 中，執行下列動作：  


      |      使用      |                        以進行此動作                        |
      |--------------------|----------------------------------------------------------|
      | **接收資料夾** | 指定您想要傳送訊息的位置。 |
      |   **檔案名稱**    |               保留 **%MessageID%.xml**。                |


   5. 按一下 **確定**直到結束所有對話方塊為止。  

7. 您現在必須繫結在一起，以設定應用程式的實體和邏輯連接埠。  

   1. 從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下 **[orderprocessingdemo]**，然後按一下**設定**。  

   2. 從 設定應用程式，在左窗格中，按一下**OrderProcessing**。  

   3. 使用下表中的值來設定應用程式。  


      |            使用             |             以進行此動作              |
      |---------------------------------|-------------------------------------|
      |          針對**主應用程式**           | 選取**BizTalkServerApplication** |
      | 對於邏輯連接埠**ReceiveSO**  | 選取實體連接埠**ReceiveSO**  |
      | 對於邏輯連接埠**SendToSQL**  | 選取實體連接埠**SendToSQL**  |
      | 對於邏輯連接埠 **[sendtofile]** | 選取實體連接埠 **[sendtofile]** |


   4. 按一下 **確定**儲存設定。  

## <a name="start-the-application"></a>啟動應用程式  

1. 從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下 **[orderprocessingdemo]**，然後按一下**啟動**。  

2. 在對話方塊中，按一下**啟動**。  

## <a name="see-also"></a>另請參閱  
 [教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)