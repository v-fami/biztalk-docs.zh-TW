---
title: 步驟 3： 提交 3A2 要求 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, submitting requests
ms.assetid: 09f22be8-6d7d-48bf-862b-73248bae0506
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 312e5980636d211f1e023331826e016eb141eb4b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967532"
---
# <a name="step-3-submitting-a-3a2-request"></a>步驟 3： 提交 3A2 要求
在此步驟中，您將使用夥伴介面程序 (PIP) 3A2 準備並提交「要求價格與可用性」要求。 這個 PIP 可以讓購買者組織取得特定產品的資訊，例如價格以及可用單位。 購買者稍後可以透過商務規則處理這項資訊，以決定是否要向供應商購買產品。  
  
### <a name="to-submit-a-3a2---request-price-and-availability"></a>提交 3A2 - 要求價格與可用性  
  
1.  在 Fabrikam 電腦上，使用 Internet Explorer 找出並開啟 http://localhost/LOBWebApplication/default.aspx。  
  
2.  在**提交訊息**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**主要組織**|型別**FABRIKAM**。|  
    |**夥伴組織**|型別**Contoso**。|  
    |**Pip 代碼**|型別**3A2**。 **重要事項：** 為了避免發生重複訊息識別碼錯誤，您必須確定**Pip**都是唯一的每個您所提交的訊息。 如果您將來要執行 3A2 測試，則必須變更此欄位。|  
    |**Pip 版本**|型別**R02.00.00A**。|  
    |**Pip 執行個體識別碼**|型別**3A2_Test**。|  
    |**訊息類別**|型別**動作**。|  
  
3.  使用 [記事本] 或其他文字編輯器，開啟中的 3A2_Request.xml 檔案*\<磁碟機\>*: \程式 Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances 資料夾，然後複製並貼上內容**服務內容**欄位LOBWebApplication。  
  
4.  按一下**送出**提交 3A2 要求至 Contoso 電腦。  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a>確認 Fabrikam 電腦成功進行通訊  
  
-   在**訊息狀態**lobwebapplication 頁面上，確認您收到兩個內送訊息。  
  
    > [!NOTE]
    >  您應該會先收到類別 25 的訊息，表示 Contoso 電腦收到通知。 接著，您應該會收到類別 50 的訊息，這是來自 Contoso 電腦的回應訊息。 類別 -99 的訊息代表錯誤。 您可以使用**事件檢視器**來判斷實際的錯誤訊息。  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a>確認 Contoso 電腦成功進行通訊  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到伺服器**對話方塊中，於**SQL Server**方塊中，輸入**localhost**，選取**Windows 驗證**，然後按一下**連接**。  
  
3.  在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。  
  
4.  在\<資料表\>文字方塊中，選取**BTARNDATA**從清單中。  
  
5.  在 SQL 視窗中輸入下列 SQL 陳述式：  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  按一下**Execute**執行 SQL 陳述式。  
  
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
 [步驟 4： 提交 3A4 要求](../../adapters-and-accelerators/accelerator-rosettanet/step-4-submitting-a-3a4-request.md)   
 [BTARN 中的訊息流程](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)