---
title: 步驟 2： 設定 Salesforce 系統 |Microsoft 文件
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
ms.openlocfilehash: d65a1c741103b9c8f1e9493b7bd2aa56eef8cf18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279926"
---
# <a name="step-2-set-up-the-salesforce-system"></a>步驟 2： 設定 Salesforce 系統
在此步驟中，您可在成功關閉商機時將 Salesforce 設定為傳送通知。 傳送通知之前，您必須執行下列步驟：  
  
-   在 Salesforce 中建立帳戶。 帳戶代表 Northwind 的客戶。  
  
-   為帳戶建立商機。 商機代表與客戶建立的正面銷售商機。 您也可以在商機中新增客戶感興趣的產品詳細資料。  
  
-   在 Salesforce 中建立工作流程。  
  
-   建立和應用程式定義連線的 Salesforce。  
  
> [!NOTE]
>  本主題中的步驟假設您已經擁有 Salesforce 開發人員帳戶。 若要在 Salesforce 中建立新的開發人員帳戶，請移至[http://go.microsoft.com/fwlink/?LinkId=296424](http://go.microsoft.com/fwlink/?LinkId=296424)。  
  
### <a name="to-create-an-account-in-salesforce"></a>在 Salesforce 中建立帳戶  
  
1.  使用您的開發人員認證登入 Salesforce.com 入口網站。  
  
2.  在入口網站中，按一下 **帳戶**索引標籤，然後再按一下**新增**。  
  
3.  在**新帳戶**頁面上，提供各種欄位的值。 指定的值**帳戶名稱**是強制性。 此教學課程中，將帳戶名稱指定為`Customer1`。  
  
4.  按一下 **[儲存]**。  
  
### <a name="to-create-an-opportunity-for-the-customer"></a>為客戶建立商機  
  
1.  在 Salesforce.com 入口網站中，按一下 [**機會**] 索引標籤。  
  
2.  在**最近商機**區段中，按一下**新增**。  
  
3.  在 新的商機頁面上，指定下列值：  
  
    1.  指定**商機名稱**，例如`Opportunity with Customer 1`。  
  
    2.  指定**帳戶名稱**。 這表示已關聯與此商機相關的帳戶。 此教學課程中，將帳戶設`Customer1`。 您已在先前的處理程序中建立了此帳戶。  
  
    3.  指定**關閉日期**。 這表示要關閉商機的日期。  
  
    4.  指定**階段**。 這表示商機的目前階段。 開始使用，您可以將商機設為任何項目，例如**需要分析**。  
  
         ![在 Salesforce 中建立商機](../core/media/bts-sf-create-opp.jpg "BTS_SF_Create_Opp")  
  
        > [!NOTE]
        >  請確定您未設定階段**Closed Won**開始使用。 在本教學課程，每次當階段設為案例**Closed Won**傳送通知給轉送端點[!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)]。 我們您尚未設定該方案的一部分，因此您不應該將階段設**Closed Won**。  
  
    5.  指定其他可選欄位的值，然後按一下**儲存**。  
  
    6.  在有機會 頁面上的 Customer1 底下**產品**區段中，按一下**新增產品**。  
  
    7.  從產品的清單，請在選取的產品的客戶感興趣，，，然後按一下**選取**。  
  
    8.  針對每個選取的產品，請指定客戶想，數量，然後按一下**儲存**。  
  
         ![新增產品至商機](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")  
  
## <a name="create-a-salesforce-workflow"></a>建立 Salesforce 工作流程  
 在此步驟中，我們會在每次成功關閉商機時，建立工作流程來傳出通知。 通知是 SOAP 訊息的格式，且會傳送到上裝載的轉送端點[!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)]。  
  
#### <a name="to-create-a-workflow-for-opportunities"></a>為商機建立工作流程  
  
1.  在 Salesforce 入口網站中，按一下右上角的頁面上，在您登入的名稱，然後按一下 **安裝**。  
  
2.  在左窗格中下,**應用程式安裝**，依序展開**建立**，展開**工作流程 （& s) 核准**，然後按一下**工作流程規則**。  
  
    > [!NOTE]
    >  若您是第一次開啟工作流程規則頁面，會看見一些相關的資訊，幫助您了解 Salesforce 中的工作流程如何運作。 閱讀這些資訊，然後按一下**繼續**。  
  
3.  在**所有工作流程規則**頁面上，按一下**新規則**。  
  
4.  從**選取物件**清單中，按一下**機會**，然後按一下 **下一步**。  
  
5.  在下一個頁面中，指定以下項目：  
  
    1.  設定**規則名稱**為`Closed Opportunity`。  
  
    2.  設定**評估準則**為**建立，並隨時編輯為準則相符**。  
  
    3.  如**規則條件**，設定執行規則時**符合準則**。  
  
    4.  設定**欄位**至**機會： 階段**，**運算子**至**等於**，和**值**至`Closed Won`.  
  
         ![建立 Salesforce 工作流程](../core/media/bts-sf-create-workflow.jpg "BTS_SF_Create_Workflow")  
  
    5.  按一下**儲存與下一步**。  
  
6.  定義新規則的工作流程動作：  
  
    1.  在**指定工作流程動作**頁面上，按一下**加入工作流程動作**按鈕，然後按一下**新增輸出訊息**。  
  
    2.  設定**名稱**和**唯一名稱**欄位`NewOp1`。  
  
    3.  指定描述，例如， `Message sent when an opportunity is successfully closed`。  
  
    4.  指定**端點 URL**為`https://btssalesforce.servicebus.windows.net/notifications/opportunity`。  
  
         在這裡， **btssalesforce**是您[!INCLUDE[sb](../includes/sb-md.md)]您在先前步驟中建立的命名空間。 **/notifications/opportunity/** 表示我們將在本教學課程的後續步驟中建立的轉送。  
  
        > [!NOTE]
        >  您必須指定[!INCLUDE[sb](../includes/sb-md.md)]您稍早建立的命名空間。  
  
    5.  請確定**保護元件**核取方塊已清除和**傳送工作階段識別碼**核取方塊。  
  
    6.  如**商機欄位傳送**選取相關欄位從**可用的欄位**清單，然後按一下**新增** 按鈕。  
  
    7.  按一下**儲存**，然後按一下 **完成**。  
  
    8.  在左窗格中下,**應用程式安裝**，依序展開**建立**，展開**工作流程 （& s) 核准**，然後按一下**工作流程規則**。 確認**已關閉商機**規則已列於此處。 在下**動作**資料行**已關閉商機**規則中，按一下**Activate**來啟用規則。  
  
## <a name="create-a-salesforce-connected-application"></a>建立 Salesforce 連接應用程式  
 建立連線的應用程式定義會產生在要求 OAuth 權杖以存取連線至 Salesforce 時所需的一組金鑰。 在本教學課程的之後階段，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會成為使用已連線應用程式定義來查詢 Salesforce 的已連線應用程式。  
  
#### <a name="to-create-a-connected-application-for-salesforce"></a>若要連接的應用程式建立 salesforce  
  
1.  在 Salesforce 入口網站中，按一下右上角的頁面上，在您登入的名稱，然後按一下 **安裝**。  
  
2.  在左窗格中下,**應用程式安裝**，依序展開**建立**，然後展開**應用程式**。 在**應用程式**頁面的 **己連線應用程式**區段中，按一下**新增**。  
  
3.  在**新連線應用程式**頁面上，指定下列項目：  
  
    1.  如**連線應用程式名稱**，指定`BizTalk_Salesforce`。  
  
    2.  如**開發人員名稱**，指定您的登入名稱。  
  
    3.  如**Contact Email**，指定您的電子郵件。  
  
    4.  如**回呼 URL**，指定有效的 URL。  
  
        > [!NOTE]
        >  由於我們在此方案中透過 Salesforce 進行驗證的方法，您在這裡指定的值無法使用。  
  
    5.  下**可用的 OAuth 領域**，選取**完整存取權**，**代替您執行要求，在任何時候**，和**存取及管理 wit_nextref**，然後按一下 [**新增**] 按鈕，將它們移入**選取 OAuth 範圍**。  
  
    6.  按一下 **[儲存]**。 出現的頁面包含有關的資訊**取用者索引鍵**和**取用者秘密**。 您必須記下這些值。 當從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 連線至 Saleforce 時，您會需要這些值。  
  
         ![Salesforce 存取金鑰](../core/media/bts-sf-consumer-keys.jpg "BTS_SF_Consumer_Keys")  
  
4.  最後，會產生從不明網路位置連線至 Salesforce 所需的安全性權杖。  
  
    1.  在 Salesforce 入口網站的左窗格下**個人設定**，依序展開**個人資訊**，然後按一下 **重設我的安全性 Token**。  
  
    2.  閱讀警告，然後按一下**重設安全性 Token**。  
  
    3.  您應該會在建立 Salesforce 帳戶時指定的電子郵件位置收到安全性權杖。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 6： 與 Salesforce 整合 BizTalk Server 2013](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)