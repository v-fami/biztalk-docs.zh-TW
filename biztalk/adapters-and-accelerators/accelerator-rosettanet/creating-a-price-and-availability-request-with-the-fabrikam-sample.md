---
title: "建立價格與可用性要求使用 Fabrikam 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, creating requests
ms.assetid: 6e4f4589-8f01-4b9e-93ee-c9371f32e04a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0619dc77496fd1547505221ff2f437bf486fb8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="creating-a-price-and-availability-request-with-the-fabrikam-sample"></a>使用 Fabrikam 範例建立價格與可用性要求
在此步驟中，您將使用 LOBWebApplication 工具建立「3A2 價格與可用性」要求。  
  
### <a name="to-submit-a-3a2-price-and-availability-request-to-contoso"></a>提交 3A2 價格與可用性要求至 Contoso  
  
1.  在 Internet Explorer 中，移至 http://\<*fabrikam_computername*\>/LOBWebApplication/default.aspx。  
  
2.  在**LOBWebApplication**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**主要組織**|型別**FABRIKAM**。|  
    |**夥伴組織**|型別**CONTOSO**。|  
    |**PIP 代碼**|型別**3A2**。|  
    |**PIP 版本**|型別**R02.00.00A**。|  
    |**訊息類別**|型別**動作**。|  
  
3.  使用 [記事本] 或其他文字編輯器，開啟**3A2_Request.xml**檔案在 C:\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication\SampleInstancesfolder然後複製並貼到文字放到**服務內容**LOBWebApplication 工具中的欄位。  
  
4.  按一下**送出**提交 3A2 要求至 Contoso。  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a>確認 Fabrikam 電腦成功進行通訊  
  
1.  在**訊息狀態**lobwebapplication 頁面上，確認您收到兩個內送訊息。  
  
    > [!NOTE]
    >  您應該會先收到類別 25 的訊息，表示 Contoso 電腦收到通知。 接著，您應該會收到類別 50 的訊息，這是來自 Contoso 電腦的回應訊息。 類別 -99 的訊息代表錯誤。 您可以使用**事件檢視器**來判斷實際的錯誤訊息。  
  
2.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。  
  
3.  在 連接到伺服器 對話方塊中**SQL Server**方塊中，輸入**localhost**，選取**Windows 驗證**，然後按一下 **連接**.  
  
4.  在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。  
  
5.  在**\<資料表\>文字**對話方塊中，選取**BTARNDATA**從清單中。  
  
6.  在**SQL**視窗中，輸入下列 SQL 陳述式：  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
7.  按一下**Execute**執行 SQL 陳述式。  
  
8.  在查詢視窗中，在 [結果] 窗格中，確認您看到兩個內送訊息。  
  
    > [!NOTE]
    >  您應該會看到類別 25 的訊息，代表從 Contoso 傳送到 Fabrikam 電腦的接收通知。 您應該也會看到類別 50 的訊息，代表從 Contoso 商務營運系統 (LOB) 應用程式傳送到 Fabrikam 電腦的回應。 您也可以透過 ServiceContent 欄位確認回應結果。  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a>確認 Contoso 電腦成功進行通訊  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。  
  
2.  在 連接到伺服器 對話方塊中**SQL Server**方塊中，輸入**localhost**，選取**Windows 驗證**，然後按一下 **連接**.  
  
3.  在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。  
  
4.  在**\<資料表\>文字**對話方塊中，選取**BTARNDATA**從清單中。  
  
5.  在**SQL**視窗中，輸入下列 SQL 陳述式：  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  按一下**Execute**執行 SQL 陳述式。  
  
7.  在查詢視窗中，在 [結果] 窗格中，確認您看到兩個內送訊息。  
  
    > [!NOTE]
    >  您應該會先收到類別 10 的訊息，代表 Fabrikam 電腦所傳送的原始要求。 接著，您應該會收到類別 25 的訊息，表示收到通知訊息。  
  
8.  在**SQL**視窗中，輸入下列 SQL 陳述式：  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. 按一下**Execute**執行 SQL 陳述式。  
  
10. 在 [查詢] 視窗的 [結果] 窗格中，確認您看到一個外寄訊息。  
  
    > [!NOTE]
    >  您應該會看到類別 25 的訊息，代表從 Contoso 傳送到 Fabrikam 電腦的接收通知。 您應該也會看到類別 50 的訊息，代表從 Contoso 商務營運系統 (LOB) 應用程式傳送到 Fabrikam 電腦的回應。  
  
## <a name="see-also"></a>請參閱  
 [私用程序教學課程](../../adapters-and-accelerators/accelerator-rosettanet/private-process-tutorial.md)