---
title: 步驟 8： 檢視 BTARN 資料庫中的訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, viewing
- loopback tutorial, viewing messages
- databases, viewing messages
ms.assetid: c549670c-4428-483c-906c-eff163ddef9a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 018bd2515dc2c363474c8058a861fd763cb73352
ms.sourcegitcommit: 436ebffd959a9c4bdaafd4da9a5843c59a018eb7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "34855441"
---
# <a name="step-8-view-messages-in-the-btarn-databases"></a>步驟 8： 檢視 BTARN 資料庫中的訊息
在此步驟中，您將使用 SQL Query Analyzer 檢視 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 資料庫中儲存的企業營運系統 (LOB) 訊息，以確認回送實例能夠正確運作。  
  
 在 LOB 應用程式公用程式產生 LOB 訊息並提交至 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 後，啟動者 (組織) 和回應者 (交易夥伴) 會發生以下事件：  
  
 啟動者工作流程  
  
-   SubmitRNIF 會將 LOB 訊息提交到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA 資料庫的 MessagesFromLOB 資料表。  
  
-   SQL 配接器接收位置會挑出訊息，然後送到 MessageBox 資料庫。 SQL 配接器每執行一次 `GetMessagesFromLOB` 預存程序，就會挑出一個訊息。  
  
-   私用啟動者會從 MessageBox 資料庫挑出訊息，然後加上額外的升級內容屬性後，再次放到 MessageBox 資料庫。  
  
-   公開啟動者則根據訂閱篩選從 MessageBox 資料庫挑出訊息。  
  
-   HTTP 傳送埠會根據訂閱挑出具有 RNIFSend 管線的訊息， 為不可否認性目的，將訊息儲存於 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 封存資料庫的 MessageStorageOut 資料表，然後再將訊息傳送到 RNIFSend.aspx 頁面。  
  
-   RNIFSend.aspx 頁面會接收具有查詢字串變數的 MIME 編碼訊息，那些變數中包含訊息的最終目的地 (交易夥伴組織 URL)。  
  
 回應者工作流程  
  
-   [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將 RNIF 訊息傳送到 RNIFReceive.aspx 頁面，在該頁面中已移除 MIME 解碼包裝函式。 訊息會被識別為同步或非同步，接著再轉寄到同步或非同步接收位置 (RNIF_Sync_Receive 或 RNIF_Async_Receive)。  
  
-   HTTP 接收位置首先會為不可否認性目的，將訊息以傳輸格式儲存於 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 封存資料庫的 MessageStorageIn 資料表內， 然後解碼、解密 (適用 RNIF 2.0)、驗證簽章、解譯 XML 訊息部分、根據簽章進行授權，最後加上正確的升級屬性後，放置到 MessageBox 資料庫。  
  
-   公用回應者會根據訂閱挑出訊息，然後依照正確的 RNIF 標準驗證及處理訊息。 服務內容部分會加上正確的內容屬性，然後將訊息放置於 MessageBox 資料庫。  
  
-   SQL 傳送埠會根據訂閱篩選挑出訊息， 然後將訊息儲存至 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA 資料庫的 MessagesToLOB 資料表。  
  
> [!NOTE]
>  在回應者端，公用回應者負責產生接收通知或例外信號回到起始端。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不會儲存在 MessagesFromLOB 資料表中的信號訊息。 因為 LOB 應用程式不會產生信號訊息。 動作訊息將繼續通過「私用回應者」，且 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將它儲存至 MessagesToLOB 資料表。  
  
> [!NOTE]
>  雙向動作 Pip，回應者端的 LOB 是負責產生回應訊息。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 卸除它 MessagesFromLOB 資料表移到起始端程序相同的程序。 在這個情形下，啟動者端的「公開啟動者程序」會傳回接收通知或例外信號做為回應訊息。  
  
### <a name="to-view-messages-in-the-btarn-databases"></a>檢視 BTARN 資料庫中的訊息  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server\<版本\>**，然後按一下  **SQL ServerManagement Studio**。  
  
2.  在 連接到伺服器 對話方塊中，按一下 **連接**。  
  
    > [!NOTE]
    >  在 [物件總管] 窗格中，確認 SQL Server Agent 是否已啟動。 如果沒有，請以滑鼠右鍵按一下**SQL Server Agent**，然後按一下**啟動**。  
  
3.  在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。  
  
4.  在 [空白的查詢] 視窗中，輸入以下程式碼：  
  
    ```  
    use BTARNArchive  
    SELECT * FROM         MessageStorageIn ORDER BY TIMECREATED ASC  
    SELECT * FROM         MessageStorageOut ORDER BY TIMECREATED ASC  
  
    use BTARNData  
    SELECT     * FROM         MessagesFromLOB ORDER BY TIMECREATED ASC  
    SELECT     * FROM         MessagesToLOB ORDER BY TIMECREATED ASC  
    SELECT     * FROM         Attachments ORDER BY TIMECREATED ASC  
    ```  
  
5.  在 Microsoft SQL Server Management Studio 中，按一下  **Execute**。  
  
 您將看到 MessagesFromLOB 資料表中的動作訊息。若在數分鐘內再次執行查詢 (取決於您系統的組態時間可能不同)，您將看到 MessagesToLOB 資料表中產生兩個訊息，分別具有 AsyncAckSignal (25) 和 AsyncAction (10) 的 MessageCategory 值。  
  
## <a name="see-also"></a>另請參閱  
 [回送](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md)   
 [回送教學課程](../../adapters-and-accelerators/accelerator-rosettanet/loopback-tutorial.md)
