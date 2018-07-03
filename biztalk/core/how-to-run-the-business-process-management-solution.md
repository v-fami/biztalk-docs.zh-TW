---
title: 如何執行商務程序管理解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, validating
- process management solution tutorial, submitting orders
- process management solution tutorial, stopping orders
- process management solution tutorial, updating orders
ms.assetid: cb77651e-e16c-49dc-9f8a-88584cd68a8b
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fc88a2999b9c38e95b70150e0686c8a353a1a32
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023340"
---
# <a name="how-to-run-the-business-process-management-solution"></a>如何執行商務程序管理解決方案
下列步驟描述如何在單一電腦上執行和驗證商務程序管理解決方案。  
  
-   [啟動商務程序管理解決方案](#step1)  
  
-   [執行和驗證商務程序管理解決方案](#step3)  
  
## <a name="prerequisites"></a>必要條件  
 在執行 BPM 解決方案之前，您必須執行中的步驟[如何安裝商務程序管理解決方案](../core/how-to-install-the-business-process-management-solution.md)。  
  
##  <a name="step1"></a> 啟動商務程序管理解決方案  
  
#### <a name="to-start-the-business-process-management-solution"></a>啟動商務程序管理解決方案  
  
1. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在  **BizTalk Server 管理主控台**，展開**BizTalk 群組**，展開**平台設定**，展開**主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下**開始**。  
  
3. 在  **BizTalk Server 管理主控台**，展開**BizTalk 群組**，然後展開**應用程式**。  
  
   1.  以滑鼠右鍵按一下 BTSScn.BPM.MessagingApp，按一下 [**開始**，然後按一下**開始**上**啟動應用程式**] 對話方塊。  
  
   2.  以滑鼠右鍵按一下 BTSScn.BPM.OrderBrokerApp，按一下 [**開始**，然後按一下**開始**上**啟動應用程式**] 對話方塊。  
  
   3.  以滑鼠右鍵按一下 BTSScn.BPM.CableOrderApp，按一下 [**開始**，然後按一下**開始**上**啟動應用程式**] 對話方塊。  
  
   4.  以滑鼠右鍵按一下 BTSScn.BPM.OrderBrokerApp.Test，然後按一下 **停止**。 在 **停止應用程式**對話方塊中，選取**完全停止-終止執行個體**，然後按一下**停止**。  
  
   > [!NOTE]
   >  將資訊插入歷程記錄資料庫。 OrderBroker 協調流程會使用其中的 HistoryPort 傳送埠**Delivery Notification**屬性設定**傳輸**。 傳送埠會與 HistoryInsert-SPG 傳送埠群組繫結，此群組包含 HistoryInsert-SP 與 HistoryInsert-Test-SP 傳送埠。 對於這兩個傳送埠，訊息引擎會發佈兩個通知訊息到 OrderBroker 協調流程。 它會因為未使用訊息而擱置協調流程。 若要避免此情況，您必須取消登錄其中一個傳送埠。 在此逐步解說中，會透過完全停止 BTSScn.BPM.OrderBrokerApp.Test 應用程式以取消登錄 HistoryInsert-Test-SP 傳送埠。 如需 OrderBroker 協調流程的詳細資訊，請參閱[OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)。 如需詳細資訊**Delivery Notification**屬性，請參閱[使用的通知](../core/using-acknowledgments.md)。  
  
4. 執行 Facilities Simulator，方式如下：  
  
   1.  開啟命令提示字元，將目錄變更為 %BTSSolutionsPath%\BPM\FacilitiesSimulator\bin\debug 資料夾。  
  
   2.  輸入 `BTSScnBPMFacilities.exe`，然後按下 ENTER。 讓 FacilitiesSimulator 繼續執行。 此應用程式模擬在 Southridge Video 處理後端系統的設備。  
  
   3.  在 FacilitiesSimulator 中，輸入下列接收和傳輸佇列：  
  
       |[屬性]|ReplTest1|  
       |----------|-----------|  
       |**接收佇列**|`.\private$\ToFacilitiesQ`|  
       |**傳輸佇列**|`.\private$\FromFacilitiesQ`|  
  
   4.  在 FacilitiesSimulator 中按一下**啟動**。  
  
5. 執行 Operation Server，方式如下：  
  
   1.  開啟新的命令提示字元，將目前的目錄變更為 %BTSSolutionsPath%\BPM\OperationsServer\bin\debug 資料夾。  
  
   2.  型別`BTSScnBPMOperations.exe 8881`命令提示字元中，然後按 ENTER 鍵。 讓 Operation Server 繼續執行。 Operation Server 會監聽 TCP 連接埠 8881，以接收來自 Ops 配接器的錯誤訊息。 它會顯示 Ops 配接器接收的錯誤訊息。  
  
6. 執行 Cable Provisioning System，方式如下：  
  
   1.  開啟新的命令提示字元，將目前的目錄變更為 %BTSSolutionsPath%\BPM\CableProvisioningSystemServer\bin\debug 資料夾。  
  
   2.  輸入 `BTSScnBPMProvisioning.exe 8880`，然後按下 ENTER。 然後，讓 Cable Provisioning System 繼續執行。 Cable Provisioning System 會接聽 TCP 連接埠 8880。 此應用程式會模擬後端訂單系統，並顯示最終的訂單。  
  
##  <a name="step3"></a> 執行和驗證商務程序管理解決方案  
  
#### <a name="to-submit-a-new-order-and-validate-the-solution"></a>提交新訂單和驗證解決方案  
  
1.  在 Internet Explorer 中**地址**方塊中，輸入客戶服務 Web 應用程式的 URL，如下所示：  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，在下列資料表中，輸入新的訂單，然後按一下**提交訂單。**  
  
    |項目|ReplTest1|  
    |-----------|-----------|  
    |客戶識別碼|@shouldalert|  
    |Order ID|@shouldalert|  
    |序號|@shouldalert|  
    |服務類型碼|新標準服務|  
  
3.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：  
  
     **客戶識別碼 1 訂單識別碼 1 序號 1**  
  
4.  在執行 Cable Provisioning System 的命令提示字元驗證提出的訂單。 應用程式會顯示提交的訂單已分析、啟動並完成的訊息。  
  
5.  確認在 Facilities Simulator 上的總訊息數目是否增加 1。  
  
#### <a name="to-submit-a-duplicate-while-the-biztalk-server-is-processing-the-original-order"></a>在 BizTalk Server 處理原始訂單時提交重複的訂單  
  
1.  在 Internet Explorer 中**地址**方塊中，輸入客戶服務 Web 應用程式的 URL，如下所示：  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  在 FacilitiesSimulator 中按一下**停止**。 可防止進一步處理提交的訂單。  
  
3.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，在下列資料表中，輸入新的訂單，然後按一下**提交訂單**兩次以模擬重複的訂單。  
  
    |項目|ReplTest1|  
    |-----------|-----------|  
    |客戶識別碼|2|  
    |Order ID|@shouldalert|  
    |序號|@shouldalert|  
    |服務類型碼|新標準服務|  
  
4.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：  
  
     **客戶識別碼 2 訂單識別碼 1 序號 1**  
  
5.  在 FacilitiesSimulator 中按一下**啟動**。 等待 Facilities Simulator 回應的協調流程將會繼續。 它會模擬在處理第一個訂單時提交重複的訂單。  
  
6.  在執行 Cable Provisioning System 的命令提示字元檢查提出的訂單。 應用程式會顯示只有第一個訂單已分析、啟動並完成的訊息。  
  
7.  在執行 Operation Server 的命令提示字元檢查重複訂單的錯誤訊息。  
  
#### <a name="to-update-an-order-while-the-biztalk-server-is-processing-the-order"></a>在 BizTalk Server 處理訂單時更新訂單  
  
1.  在 Internet Explorer 中**地址**方塊中，輸入客戶服務 Web 應用程式的 URL，如下所示：  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  在 FacilitiesSimulator 中按一下**停止**。  
  
3.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，在下列資料表中，輸入新的訂單，然後按一下**提交訂單**。  
  
    |項目|ReplTest1|  
    |-----------|-----------|  
    |客戶識別碼|3|  
    |Order ID|@shouldalert|  
    |序號|@shouldalert|  
    |服務類型碼|新標準服務|  
  
4.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：  
  
     **客戶 ID 3 訂單識別碼 1 序號 1**  
  
5.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，在下列資料表中，輸入更新的訂單，然後按一下**提交訂單**。  
  
    |項目|ReplTest1|  
    |-----------|-----------|  
    |客戶識別碼|3|  
    |Order ID|@shouldalert|  
    |序號|2|  
    |服務類型碼|新個性化服務|  
  
6.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：  
  
     **客戶 ID 3 訂單識別碼 1 序號 2**  
  
7.  在 FacilitiesSimulator 中按一下**開始**  
  
8.  檢查結果訊息**Southridge Video 客戶服務代表訂單項目表單**頁面。  
  
9. 在執行 Cable Provisioning System 的命令提示字元檢查提出的訂單。 應用程式會顯示已經分析兩個訂單，但僅啟動和完成更新訂單的訊息。  
  
10. 按一下 **開始**，指向**所有程式**，指向**系統管理工具**，按一下 **事件檢視器**，然後檢查 會有新的警告，原始訂單已中斷。  
  
11. 在執行 Operation Server 的命令提示字元檢查路由失敗錯誤訊息。  
  
    > [!NOTE]
    >  事件日誌和 Operation Server 中將會有錯誤。 Facilities System 的回應訊息與商務程序的執行個體不再相互關聯，因為序號較高的新訂單造成中斷而使它終止。 因此，回應訊息便被遺棄，將會路由至 Operation Server。 如需訂單更新的詳細資訊，請參閱[訂單流程的程序管理員透過](../core/order-flow-through-the-process-manager.md)。  
  
12. 使用「記事本」開啟 %SystemDrive%:\BPMTest\HistoryUpdate-SP 資料夾中的最新訊息。 檢查**CustName**， **OrderNum**， **OrderSeqNum**，以及**狀態**欄位，以查看是否已經建立新的訂單訊息，**狀態**欄位是**已完成**。  
  
#### <a name="to-terminate-an-order-while-the-biztalk-server-is-processing-the-order"></a>在 BizTalk Server 處理訂單時終止訂單  
  
1.  在 Internet Explorer 中**地址**方塊中，輸入客戶服務 Web 應用程式的 URL，如下所示：  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  在 FacilitiesSimulator 中按一下**停止**。  
  
3.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，在下列資料表中，輸入新的訂單，然後按一下**提交訂單**。  
  
    |項目|ReplTest1|  
    |-----------|-----------|  
    |客戶識別碼|4|  
    |Order ID|@shouldalert|  
    |序號|@shouldalert|  
    |服務類型碼|新標準服務|  
  
4.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：  
  
     **客戶識別碼 4 訂單識別碼 1 序號 1**  
  
5.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，按一下**終止訂單**。  
  
6.  在  **Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：  
  
     **客戶識別碼 4 訂單識別碼 1 序號 1**  
  
7.  在 FacilitiesSimulator 中按一下**啟動**。  
  
8.  在執行 Cable Provisioning System 的命令提示字元檢查提出的訂單。 應用程式會顯示僅分析和啟動訂單的訊息。  
  
9. 按一下 **開始**，指向**所有程式**，指向**系統管理工具**，按一下 **事件檢視器**，然後檢查 會有新的警告，使用者已終止訂單。  
  
    > [!NOTE]
    >  如需有關終止訂單的詳細資訊，請參閱[訂單流程的程序管理員透過](../core/order-flow-through-the-process-manager.md)。  
  
10. 在執行 Operation Server 的命令提示字元檢查路由失敗錯誤訊息。  
  
## <a name="see-also"></a>另請參閱  
 [安裝商務程序管理解決方案之前](../core/before-installing-the-business-process-management-solution.md)   
 [商務程序管理解決方案的開發人員電腦設定](../core/developer-machine-setup-for-the-business-process-management-solution.md)