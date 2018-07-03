---
title: 步驟 3a： 到 BizTalk Server 中的 Salesforce Opportunity Notification 接收 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be9de6e3-6bd9-4275-b2fb-0a756c51aabf
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a51340d8812a8b42871d63c8fc52eeee6e05312
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999439"
---
# <a name="step-3a-receive-salesforce-opportunity-notification-into-biztalk-server"></a>步驟 3a： 到 BizTalk Server 中的 Salesforce Opportunity Notification 接收
在此步驟中，我們開始建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 首先，我們應該包含商機通知訊息，我們將用來從 Salesforce 取得，並再啟動 建立協調流程處理訊息的訊息結構描述。  
  
### <a name="to-include-the-salesforce-opportunities-notification-schema"></a>要包含的 Salesforce 商機通知結構描述  
  
1. 登入 Salesforce.com 入口網站。 在上 Salesforce 入口網站中，按一下右上角的頁面上，在您登入名稱，然後按一下**安裝程式**。  
  
2. 在左窗格中，在**應用程式安裝程式**，展開**建立**，展開**工作流程與核准**，然後按一下**工作流程規則**。  
  
3. 在 **所有的工作流程規則**頁面上，按一下**已關閉商機**您稍早建立的工作流程。  
  
4. 在 **已關閉商機**工作流程規則頁面上，按一下**NewOp1**外寄訊息的工作流程動作。  
  
5. 中**NewOp1**外寄訊息的工作流程動作頁面上，以滑鼠右鍵按一下該連結**按一下 wsdl**，按一下**另存目標**，然後指定您要儲存的位置在 WSDL 中。  
  
   > [!NOTE]
   >  您必須以副檔名.wsdl 儲存檔案。  
  
6. 建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 本教學課程中，我們將專案命名為`BtsSalesforceIntegration`。  
  
7. 以滑鼠右鍵按一下[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案總管 中專案，指向**新增**，然後按一下**加入產生的項目**。  
  
8. 在**加入產生的項目** 對話方塊中，按一下**取用 WCF 服務**，然後按一下**新增**啟動**BizTalk WCF 服務取用**精靈。 在 歡迎使用 頁面上，按一下**下一步**。  
  
9. 在 [**中繼資料來源**頁面上，選取**中繼資料檔案 （WSDL 和 XSD）** 選項，然後再按一下**下一步]**。  
  
10. 在 **中繼資料檔案**頁面上，按一下**新增**，然後瀏覽至您用來儲存從 Salesforce 入口網站下載的 WSDL 檔案的位置。 選取 WSDL 檔案，然後按一下**下一步**。  
  
11. 在下一步] 頁面中，設定為命名空間`NotificationService`，然後按一下 [**匯入**。 精靈將結構描述檔案和協調流程，以加入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。 會接收來自 Salesforce 的商機通知的訊息結構描述**NotificationService_soap_sforce_com_2005_09_outbound.xsd**。  
  
### <a name="to-create-an-orchestration-to-receive-the-notification-message"></a>若要建立協調流程以接收通知訊息  
  
1. 完成後**BizTalk WCF 服務取用**精靈]、 [協調流程 (**NotificationService.odx**，在此範例中) 新增至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。  
  
2. 開啟協調流程檔案，並在協調流程檢視中，新增兩個新的訊息變數。 它們的名稱`NotificationMessage`和`NotificationAck`。 設定訊息類型的這些訊息變數，如下所示：  
  
   1.  設定**NotificationMessage**要*NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notifications*。 此訊息變數代表從 Salesforce 收到的商機通知訊息。  
  
   2.  設定**NotificationAck**要*NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notificationsResponse*。 此訊息變數代表傳回給 Salesforce 商機通知的通知訊息。  
  
3. 新增 「 接收 」 圖形至協調流程。 在圖形上設定下列屬性：  
  
   1.  設定**啟用**要 **，則為 True**。  
  
   2.  設定**名稱**要*ReceiveNotificationMessage*。  
  
   3.  設定**訊息**要*NotificationMessage*。  
  
4. 新增 「 接收 」 圖形之後的 「 建構訊息 」 圖形。 名稱為 「 訊息 」 圖形`ConstructNotificationResponse`並設定**建構的訊息**屬性設`NotificationAck`。 建構訊息的一部分，我們也會建立對應，以產生通知的通知訊息，以傳回至 Salesforce。  
  
   1.  在 [建構訊息] 圖形中，新增 「 轉換 」 圖形。 按兩下 [轉換] 圖形，然後在 [轉換組態] 對話方塊中，選取**新的對應**選項。  
  
   2.  指定對應名稱為`BtsSalesforceIntegration.MapNotificationResponse`。  
  
   3.  設定為來源**NotificationMessage**和 做為目的地**NotificationAck**。  
  
   4.  請確定核取方塊**當我按一下 [確定] 時，啟動 BizTalk 對應工具**已選取。  
  
   5.  在  **MapNotificationResponse.btm**，我們將建立的通知回應傳回至 Salesforce。 每次 Salesforce 中，會傳送通知，它預期傳回收到通知。 通知回應訊息結構描述會顯示**Ack**在回應中的項目為布林值類型。 因此，在對應中，您必須先卸除**值對應**運算質，並設定其兩個輸入值 （「 條件 」 和 「 結果 」） 到`true`。 按一下 **確定**儲存運算質。  
  
   6.  連接**值對應**運算質**Ack**目的結構描述中的項目。  
  
5. 在協調流程中之後 [建構訊息] 圖形中，, 新增將用來傳送通知回至 Salesforce 「 傳送 」 圖形。  
  
   -   設定**名稱**要*SendNotificationAck*。  
  
   -   設定**訊息**要*NotificationAck*。  
  
6. 在協調流程中，新增連接埠以接收 Salesforce 通知訊息，並在回應中傳送通知。 在 [連接埠組態精靈] 中，選取下列選項：  
  
   - 將連接埠名稱指定為`SalesforceNotificationPort`。  
  
   - 選取 [建立新的連接埠類型] 選項。  
  
   - 設定**通訊模式**要*要求-回應*。  
  
   - 設定**連接埠通訊方向**要*我就可以接收要求並傳送回應*並設定**連接埠繫結**至*指定更新*.  
  
     連接**要求**作業的 「 接收 」 圖形的連接埠 (*ReceiveNotificationMessage*) 和**回應**「 傳送 」 圖形的連接埠的作業 (*SendNotificationAck*)。 下列螢幕擷取畫面說明接收來自 Salesforce 的商機通知和傳送通知回覆的協調流程的一部分：  
  
     ![接收機會通知並傳送回應](../core/media/bts-sf-recvnotificationorch.jpg "BTS_SF_RecvNotificationOrch")  
  
   到目前為止，我們已設定的解決方案，其中從 Salesforce 收到商機通知，且會將認可傳回到。 在後續主題中，我們會建置此解決方案，以開始處理機會通知，以取得更多詳細的銷售機會種類。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3：在 Visual Studio 中建立 BizTalk Server 解決方案](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)