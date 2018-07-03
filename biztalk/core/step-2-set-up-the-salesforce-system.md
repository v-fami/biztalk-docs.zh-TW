---
title: 步驟 2︰ 設定 Salesforce 系統 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a4b09fb-70a7-4eec-b1e3-f05de0e84df1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 772c18f87351d17b726ad498122715659dca79bc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986527"
---
# <a name="step-2-set-up-the-salesforce-system"></a>步驟 2︰ 設定 Salesforce 系統
在此步驟中，您可在成功關閉商機時將 Salesforce 設定為傳送通知。 傳送通知之前，您必須執行下列步驟：  
  
-   在 Salesforce 中建立帳戶。 帳戶代表 northwind 客戶。  
  
-   為帳戶建立商機。 商機代表與客戶建立的正面銷售商機。 您也可以在商機中新增客戶感興趣的產品詳細資料。  
  
-   在 Salesforce 中建立工作流程。  
  
-   建立和應用程式定義連線的 Salesforce。  
  
> [!NOTE]
>  本主題中的步驟假設您已經擁有 Salesforce 開發人員帳戶。 若要在 Salesforce 中建立新的開發人員帳戶，請前往[ http://go.microsoft.com/fwlink/?LinkId=296424 ](http://go.microsoft.com/fwlink/?LinkId=296424)。  
  
### <a name="to-create-an-account-in-salesforce"></a>在 Salesforce 中建立帳戶  
  
1.  使用您的開發人員認證登入 Salesforce.com 入口網站。  
  
2.  在入口網站中，按一下 **帳號**索引標籤，然後再按一下**新增**。  
  
3.  在 **新帳戶**頁面上，提供各種欄位的值。 指定的值**帳戶名稱**是必要的。 本教學課程中，將帳戶名稱指定為`Customer1`。  
  
4.  按一下 **[儲存]**。  
  
### <a name="to-create-an-opportunity-for-the-customer"></a>為客戶建立商機  
  
1. 在 Salesforce.com 入口網站中，按一下 [**機會**] 索引標籤。  
  
2. 在 **最近商機**區段中，按一下**新增**。  
  
3. 在 新的商機頁面上，指定下列值：  
  
   1. 指定**商機名稱**，例如`Opportunity with Customer 1`。  
  
   2. 指定**帳戶名稱**。 這表示已關聯與此商機相關的帳戶。 本教學課程的帳戶設定為`Customer1`。 您已在先前的處理程序中建立了此帳戶。  
  
   3. 指定**關閉日期**。 這表示要關閉商機的日期。  
  
   4. 指定**階段**。 這表示商機的目前階段。 若要開始，您可以設定有機會到任何項目，例如**需要分析**。  
  
       ![在 Salesforce 中建立商機](../core/media/bts-sf-create-opp.jpg "BTS_SF_Create_Opp")  
  
      > [!NOTE]
      >  請確定您未設定階段**Closed Won**開始。 在本教學課程，每次當階段設為案例**Closed Won**通知上傳送的轉送端點[!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)]。 我們尚未設定該方案的一部分，因此您不應該將階段設**Closed Won**。  
  
   5. 指定其他可選欄位的值，然後按一下**儲存**。  
  
   6. 在有機會頁面 Customer1 底下**產品**區段中，按一下**新增產品**。  
  
   7. 從清單中的產品，請在選取的產品，客戶有興趣，，，然後按一下**選取**。  
  
   8. 針對每個選取的產品，指定客戶想，數量，然後按一下**儲存**。  
  
       ![新增產品至商機](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")  
  
## <a name="create-a-salesforce-workflow"></a>建立 Salesforce 工作流程  
 在此步驟中，我們會在每次成功關閉商機時，建立工作流程來傳出通知。 通知是 SOAP 訊息格式和傳送至轉送端點上裝載[!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)]。  
  
#### <a name="to-create-a-workflow-for-opportunities"></a>為商機建立工作流程  
  
1. 在上 Salesforce 入口網站中，按一下右上角的頁面上，在您登入名稱，然後按一下**安裝程式**。  
  
2. 在左窗格中，在**應用程式安裝程式**，展開**建立**，展開**工作流程與核准**，然後按一下**工作流程規則**。  
  
   > [!NOTE]
   >  若您是第一次開啟工作流程規則頁面，會看見一些相關的資訊，幫助您了解 Salesforce 中的工作流程如何運作。 閱讀這些資訊，然後按一下**繼續**。  
  
3. 在 **所有的工作流程規則**頁面上，按一下**新規則**。  
  
4. 從**選取物件**清單中，按一下**機會**，然後按一下**下一步**。  
  
5. 在下一個頁面中，指定以下項目：  
  
   1.  設定**規則名稱**做為`Closed Opportunity`。  
  
   2.  設定**Evaluation Criteria**作為**建立，並隨時編輯為準則相符**。  
  
   3.  針對**規則條件**，設定執行規則時**符合準則**。  
  
   4.  設定**欄位**來**機會： 階段**，**運算子**至**等於**，並**值**至`Closed Won`.  
  
        ![建立 Salesforce 工作流程](../core/media/bts-sf-create-workflow.jpg "BTS_SF_Create_Workflow")  
  
   5.  按一下 **儲存並下一步**。  
  
6. 定義新規則的工作流程動作：  
  
   1. 在 **指定工作流程動作**頁面上，按一下**加入工作流程動作**按鈕，然後按一下**新增輸出訊息**。  
  
   2. 設定**名稱**並**唯一名稱**欄位`NewOp1`。  
  
   3. 例如，指定描述， `Message sent when an opportunity is successfully closed`。  
  
   4. 指定**端點 URL**做為`https://btssalesforce.servicebus.windows.net/notifications/opportunity`。  
  
       在這裡， **btssalesforce**是您[!INCLUDE[sb](../includes/sb-md.md)]您在先前步驟中建立的命名空間。 **/notifications/opportunity/** 表示我們將在本教學課程的稍後步驟中建立的轉送。  
  
      > [!NOTE]
      >  您必須指定[!INCLUDE[sb](../includes/sb-md.md)]您稍早建立的命名空間。  
  
   5. 請確定**受保護的元件**已清除核取方塊並**傳送工作階段識別碼** 核取方塊。  
  
   6. 針對**機會欄位傳送**選取相關的欄位，從**可用的欄位**清單，然後按一下**新增** 按鈕。  
  
   7. 按一下 **儲存**，然後按一下**完成**。  
  
   8. 在左窗格中，在**應用程式安裝程式**，展開**建立**，展開**工作流程與核准**，然後按一下**工作流程規則**。 確認**已關閉商機**規則會列在那裡。 底下**動作**資料行**已關閉商機**規則中，按一下 **啟動**以啟動規則。  
  
## <a name="create-a-salesforce-connected-application"></a>建立 Salesforce 連線應用程式  
 建立連線的應用程式定義會產生在要求 OAuth 權杖以存取連線至 Salesforce 時所需的一組金鑰。 在本教學課程的之後階段，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會成為使用已連線應用程式定義來查詢 Salesforce 的已連線應用程式。  
  
#### <a name="to-create-a-connected-application-for-salesforce"></a>為 Salesforce 中建立連接的應用程式  
  
1. 在上 Salesforce 入口網站中，按一下右上角的頁面上，在您登入名稱，然後按一下**安裝程式**。  
  
2. 在左窗格中，在**應用程式安裝程式**，展開**建立**，然後展開**應用程式**。 在 **應用程式**頁面的 **連線到應用程式**區段中，按一下**新增**。  
  
3. 在 **新的連線應用程式**頁面上，指定下列項目：  
  
   1. 針對**連線的應用程式名稱**，指定`BizTalk_Salesforce`。  
  
   2. 針對**開發人員名稱**，指定您的登入名稱。  
  
   3. 針對**Contact Email**，指定您的電子郵件。  
  
   4. 針對**回呼 URL**，指定有效的 URL。  
  
      > [!NOTE]
      >  由於我們在此方案中透過 Salesforce 進行驗證的方法，您在這裡指定的值無法使用。  
  
   5. 底下**可用的 OAuth 領域**，選取**完整存取權**，**代替您執行要求，在任何時候**，和**存取及管理您的資料**，然後按一下 **新增**按鈕，以將它們移至**選取 OAuth 範圍**。  
  
   6. 按一下 **[儲存]**。 出現的頁面包含的相關資訊**取用者索引鍵**並**取用者祕密**。 您必須記下這些值。 當從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 連線至 Saleforce 時，您會需要這些值。  
  
       ![Salesforce 存取金鑰](../core/media/bts-sf-consumer-keys.jpg "BTS_SF_Consumer_Keys")  
  
4. 最後，會產生從不明網路位置連線至 Salesforce 所需的安全性權杖。  
  
   1.  在 Salesforce 入口網站的左窗格底下**個人的安裝程式**，展開**個人資訊**，然後按一下**重設我的安全性權杖**。  
  
   2.  閱讀警告，然後按一下**重設安全性權杖**。  
  
   3.  您應該會在建立 Salesforce 帳戶時指定的電子郵件位置收到安全性權杖。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 6： 整合 BizTalk Server 2013 與 Salesforce](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)