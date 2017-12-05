---
title: "步驟 1： 提交 0c2 要求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, submitting requests
ms.assetid: 698c4a43-20b9-46b7-ab66-1dfa24232024
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f05aa5200bd1df6207a962849cd776a03fe71805
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-submitting-a-0c2-request"></a>步驟 1： 提交 0 C 2 要求
在此步驟中，您將使用「0C2 - 非同步測試要求夥伴介面程序 (PIP)」來準備並提交要求。 此 PIP 可以確保兩個不同組織之間的非同步通訊管道正常運作。 此 PIP 遵循與其他非同步雙向動作 PIP (例如「3A4 - 訂單要求 PIP」) 相同的模式。  
  
### <a name="to-submit-a-0c2---asynchronous-test-request"></a>提交 0C2 - 非同步測試要求  
  
1.  在 Fabrikam 電腦上，使用 Internet Explorer 找出並開啟 http://localhost/LOBWebApplication/default.aspx。  
  
2.  在**提交訊息**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**主要組織**|型別**FABRIKAM**。|  
    |**夥伴組織**|型別**CONTOSO**。|  
    |**Pip 代碼**|型別**0c2**。|  
    |**Pip 版本**|型別**R01.02**。|  
    |**Pip 執行個體識別碼**|型別**0C2_Test**。 **重要事項：**您必須確定**PIP**都是唯一的每個您送出以避免發生重複訊息識別碼錯誤的訊息。 如果將來要執行 0C2 測試，您必須變更此欄位。|  
    |**訊息類別**|型別**動作**。|  
  
3.  使用 [記事本] 或其他文字編輯器，開啟中的 0C2_Request.xml 檔案\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances 資料夾，然後複製並貼上內容**服務內容**lobwebapplication 的欄位。  
  
    > [!NOTE]
    >  若要刪除現有的文字服務內容提交訊息] 表單的欄位中，將游標放在開頭文字，按下並按住**Shift**和**Ctrl**按鈕、 按一下**結束**，然後按一下 [**刪除**。  
  
4.  按一下**送出**提交 0 C 2 要求至 Contoso 電腦。  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a>確認 Fabrikam 電腦成功進行通訊  
  
-   在**訊息狀態**lobwebapplication 頁面上，確認您收到兩個內送訊息。  
  
    > [!NOTE]
    >  您應該會先收到類別 25 的訊息，表示 Contoso 電腦收到通知。 接著，您應該會收到類別 50 的訊息，這是來自 Contoso 電腦的回應訊息。 類別 -99 的訊息代表錯誤。 您可以使用**事件檢視器**來判斷實際的錯誤訊息。  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a>確認 Contoso 電腦成功進行通訊  
  
1.  按一下 **[開始]**，依序指向 **[所有程式]**和 **[Microsoft SQL Server]**，然後按一下 **[SQL Server Management Studio]**。  
  
2.  在**連接到伺服器**對話方塊中，於**SQL Server**方塊中，輸入**localhost**，選取**Windows 驗證**，然後按一下**連接**。  
  
    > [!NOTE]
    >  如果未啟動 SQL Server 代理程式，以滑鼠右鍵按一下，然後再按一下**啟動**。  
  
3.  在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。  
  
4.  在\<資料表\>文字對話方塊方塊中，選取**BTARNDATA**從清單中，然後按一下**確定**。  
  
5.  在 SQL 視窗中輸入下列 SQL 陳述式：  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  在**查詢**功能表上，按一下  **Execute**執行 SQL 陳述式。  
  
7.  在查詢視窗中，在 [結果] 窗格中，確認您看到兩個內送訊息。  
  
    > [!NOTE]
    >  您應該會先收到類別 10 的訊息，代表 Fabrikam 電腦所傳送的原始要求。 接著，您應該會收到類別 25 的訊息，表示收到通知訊息。  
  
8.  在 SQL 視窗中輸入下列 SQL 陳述式：  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. 按一下**Execute**執行 SQL 陳述式。  
  
10. 在 [查詢] 視窗的 [結果] 窗格中，確認您看到一個外寄訊息。  
  
    > [!NOTE]
    >  您應該會看到類別 25 的訊息，代表從 Contoso 傳送到 Fabrikam 電腦的接收通知。 您應該也會看到類別 50 的訊息，代表從 Contoso 商務營運系統 (LOB) 應用程式傳送到 Fabrikam 電腦的回應。  
  
## <a name="see-also"></a>請參閱  
 [步驟 2： 提交 0 C 4 查詢](../../adapters-and-accelerators/accelerator-rosettanet/step-2-submitting-a-0c4-query.md)   
 [BTARN 中的訊息流程](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)