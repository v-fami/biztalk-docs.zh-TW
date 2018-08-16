---
title: 步驟 2： 提交 0c4 查詢 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, submitting requests
ms.assetid: ce50b892-c87c-414a-94c5-b40947fec68f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88c621b6891b816f72603202bd6f2214882eb4b5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965676"
---
# <a name="step-2-submitting-a-0c4-query"></a>步驟 2： 提交 0 C 4 查詢
在此步驟中，您將使用夥伴介面程序 (PIP) 0C4 準備並提交「同步測試查詢」要求。 RosettaNet 定義此 PIP，確保兩個不同組織之間的同步通訊管道正常運作。 由於此 PIP 具有同步通訊模式，所以 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 不會傳送接收通知。 此 PIP 遵循與其他同步雙向動作 PIP (例如 PIP 2A9 - 查詢技術產品資訊) 相同的模式。  
  
### <a name="to-submit-a-0c4---synchronous-test-query"></a>提交 0C4 - 同步測試查詢  
  
1.  在 Fabrikam 電腦上，使用 Internet Explorer 找出並開啟 http://localhost/LOBWebApplication/default.aspx。  
  
2.  在**提交訊息**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**主要組織**|型別**FABRIKAM**。|  
    |**夥伴組織**|型別**CONTOSO**。|  
    |**Pip 代碼**|型別**0c4**。|  
    |**Pip 版本**|型別**R01.02**。|  
    |**Pip 執行個體識別碼**|型別**0C4_Test**。 **重要事項：** 為了避免發生重複訊息識別碼錯誤，您必須確定**PIP**都是唯一的每個您所提交的訊息。 如果將來要執行 0C4 測試，您必須變更此欄位。|  
    |**訊息類別**|型別**動作**。|  
  
3.  使用 [記事本] 或其他文字編輯器，開啟中的 0C4_Request.xml 檔案*\<磁碟機\>*: \Program Files\Microsoft BizTalk 2009 Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances 資料夾然後複製並貼上內容**服務內容**lobwebapplication 的欄位。  
  
4.  按一下**送出**提交 0 C 4 查詢至 Contoso 電腦。  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a>確認 Fabrikam 電腦成功進行通訊  
  
-   在**訊息狀態**lobwebapplication 頁面上，確認您收到兩個內送訊息。  
  
    > [!NOTE]
    >  您應該會收到類別 50 的訊息，這是來自 Contoso 電腦的回應訊息。 類別 -99 的訊息代表錯誤。 您可以使用 [事件檢視器] 查看實際的錯誤訊息。  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a>確認 Contoso 電腦成功進行通訊  
  
1.  按一下 **[開始]**，依序指向 **[所有程式]** 和 **[Microsoft SQL Server]**，然後按一下 **[SQL Server Management Studio]**。  
  
2.  在**連接到伺服器**對話方塊中，於**SQL Server**方塊中，輸入**localhost**，選取**Windows 驗證**，然後按一下**連接**。  
  
    > [!NOTE]
    >  如果未啟動 SQL Server 代理程式，以滑鼠右鍵按一下，然後再按一下**啟動**。  
  
3.  在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。  
  
4.  在\<資料表\>文字方塊中，選取**BTARNDATA**從清單中。  
  
5.  在 SQL 視窗中輸入下列 SQL 陳述式：  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  按一下**Execute**執行 SQL 陳述式。  
  
7.  在 [查詢] 視窗的 [結果] 窗格中，確認您看到一個內送訊息。  
  
    > [!NOTE]
    >  您應該會看到類別 10 的訊息，代表 Fabrikam 電腦所傳送的原始要求。  
  
8.  在 SQL 視窗中輸入下列 SQL 陳述式：  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. 按一下**Execute**執行 SQL 陳述式。  
  
10. 在 [查詢] 視窗的 [結果] 窗格中，確認您看到一個外寄訊息。  
  
    > [!NOTE]
    >  您應該會看到類別 50 的訊息，代表 Contoso 對 Fabrikam 傳送的 PIP 0C4 查詢所發出的回應。 在雙向動作同步實例中，回應者電腦不會為了回應初查詢訊息而傳送通知給啟動者電腦。 回應訊息是做為通知使用。  
  
## <a name="see-also"></a>請參閱  
 [步驟 3： 提交 3A2 要求](../../adapters-and-accelerators/accelerator-rosettanet/step-3-submitting-a-3a2-request.md)   
 [BTARN 中的訊息流程](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)