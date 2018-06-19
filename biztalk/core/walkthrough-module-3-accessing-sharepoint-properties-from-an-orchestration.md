---
title: 逐步解說： 模組 3-從協調流程存取 SharePoint 屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, Windows SharePoint Services adapters
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, orchestrations
- Windows SharePoint Services adapter tutorials, accessing SharePoint properties
ms.assetid: 310c4002-3416-44c6-b409-1d5467063e28
caps.latest.revision: 45
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23bc9f0b1f2d350864509536a393de639e108e2d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010959"
---
# <a name="walkthrough-module-3---accessing-sharepoint-properties-from-an-orchestration"></a>逐步解說： 模組 3-從協調流程存取 SharePoint 屬性
這個逐步解說是工作的接續[逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)，並示範如何存取內送訊息在 Windows SharePoint Services 內容屬性執行階段，然後決定該使用動態連接埠的協調流程中的屬性為基礎的訊息的目的地。 如需 Windows SharePoint Services 配接器的簡介，請參閱[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)。  
  
## <a name="prerequisites"></a>必要條件  
 下列是執行本主題所述程序的必要條件：  
  
-   您必須擁有與完整安裝 BizTalk Server 上執行的單一伺服器部署[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。  
  
-   您必須完成下列逐步解說：[逐步解說： 模組 1-傳送和接收訊息，Windows SharePoint Services 配接器](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md)和[逐步解說： 模組 2-整合 Office 與 WindowsSharePoint Services 配接器](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)  
  
 如需在多重伺服器部署中使用 Windows SharePoint Services 配接器的資訊，請參閱[設定和部署 Windows SharePoint Services 配接器](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md)。  
  
## <a name="modify-the-biztalk-project"></a>修改 BizTalk 專案  
 您可以在此程序修改 PurchaseOrder 結構描述從[逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)。 本程序說明如何升級結構描述屬性，以便能在 BizTalk 協調流程中輕鬆存取。  
  
#### <a name="modify-the-purchaseorderxsd-schema"></a>修改 PurchaseOrder.xsd 結構描述  
  
1.  啟動**Microsoft Visual Studio**。  
  
2.  按一下**檔案**，按一下 **開啟**，然後按一下 **專案/方案**。  
  
3.  瀏覽至`OrderProcess.sln`檔案，然後再按一下**開啟**。  
  
4.  在**方案總管 中**，以滑鼠右鍵按一下`OrderProcessSchema.xsd`檔案，然後再按一下**開啟**。  
  
5.  在**BizTalk 編輯器**，依序展開`PurchaseOrder`。  
  
6.  以滑鼠右鍵按一下`Amount`，按一下 **升階**，然後按一下 **快速升級**。  
  
7.  按一下 **[確定]**。  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 會在目前的專案中為此建立屬性結構描述。  
  
8.  儲存 `PurchaseOrder.xsd`。  
  
## <a name="create-an-orchestration"></a>建立協調流程  
 在此程序中，您要建立新的 BizTalk 協調流程。 此程序會建立用來處理由 Windows Sharepoint Services 配接器接收之訊息的協調流程。  
  
#### <a name="add-a-biztalk-orchestration"></a>新增 BizTalk 協調流程  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下`OrderProcess`專案中，按一下 **新增**，然後按一下 **新項目**。  
  
2.  在下**類別**，選取**協調流程檔案**。  
  
3.  在下**範本**，選取**BizTalk 協調流程**。  
  
4.  型別`MyCompanyOrderProcessing`中**名稱**欄位，，然後按一下**新增**。  
  
## <a name="create-receive-information"></a>建立接收資訊  
 在此程序中，您要為協調流程建立新訊息、接收埠以及接收圖形。 此程序說明如何設定協調流程收到來自訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
#### <a name="create-a-new-message"></a>新立新訊息  
  
1.  在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。 這樣將會產生名稱為 `Message_1` 的新訊息。  
  
2.  以滑鼠右鍵按一下`Message_1`，按一下 **重新命名**，然後輸入`Message_PO`。  
  
3.  以滑鼠右鍵按一下`Message_PO`，然後按一下 [**屬性] 視窗**。  
  
4.  在**訊息類型**屬性中，展開**結構描述**，然後選取`OrderProcess.OrderProcessSchema`結構描述。  
  
#### <a name="add-a-receive-port-to-the-orchestration"></a>新增接收埠至協調流程  
  
1.  在下**BizTalk 協調流程**在 工具箱 拖曳**連接埠**連接埠介面 圖形。 將會啟動 [連接埠組態精靈]。  
  
2.  在 歡迎使用畫面上，按一下 **下一步**。  
  
3.  型別`ReceivePurchaseOrder`中**名稱**欄位，，然後按一下**下一步**。  
  
4.  選取**建立新的連接埠類型**。  
  
5.  型別`PurchaseOrderPT`中**連接埠類型名稱**欄位，，然後按一下**下一步**。  
  
6.  在**連接埠繫結螢幕**，保留預設值，然後按**下一步**。  
  
7.  按一下 **[完成]**。  
  
8.  在**協調流程檢視**下**連接埠類型**，依序展開`PurchaseOrderPT`連接埠類型。  
  
9. 以滑鼠右鍵按一下`Operation_1`，按一下 **重新命名**，然後輸入`PurchaseOrderOperation`。  
  
#### <a name="add-a-receive-shape-to-the-orchestration"></a>新增 [接收] 圖形至協調流程  
  
1.  在下**BizTalk 協調流程**在 [工具箱] 拖曳**接收**圖形至協調流程。  
  
2.  「 接收 」 圖形，以滑鼠右鍵按一下，然後按一下 [**屬性] 視窗**。  
  
3.  設定**Activate**屬性`True`。  
  
    > [!NOTE]
    >  如果 [啟動] 屬性設定為 false，您就會收到下列錯誤：「錯誤 X2214: 您必須為位於非自我相互關聯連接埠上的非啟動接收，至少指定一個已經初始化的相互關聯集合」。  
  
4.  型別`Receive_PO`中**名稱**欄位。  
  
5.  在**屬性 視窗**，選取`Message_PO`訊息屬性。  
  
6.  選取`ReceivePurchaseOrder.PurchaseOrderOperation.Request`如**作業**屬性。 這會結合到 「 接收 」 圖形在協調流程設計師的連接埠。  
  
## <a name="create-send-information"></a>建立傳送資訊  
 在此程序中，您要為協調流程建立新訊息、傳送埠以及決策結構。 此程序說明如何以決策邏輯來設定協調流程，以及如何設定協調流程將訊息傳送到傳送埠。  
  
#### <a name="create-a-new-message"></a>新立新訊息  
  
1.  在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。 這樣將會產生名稱為 `Message_1` 的新訊息。  
  
2.  以滑鼠右鍵按一下`Message_1`，按一下 **重新命名**，然後輸入`Message_Task`。  
  
3.  以滑鼠右鍵按一下`Message_Task`，然後按一下 [**屬性] 視窗**。  
  
4.  在**訊息類型**屬性中，展開**結構描述**，然後選取`OrderProcess.OrderProcessSchema`結構描述。  
  
#### <a name="add-a-send-port-to-the-orchestration"></a>新增傳送埠至協調流程  
  
1.  在下**BizTalk 協調流程**在 工具箱 拖曳**連接埠**連接埠介面 圖形。 將會啟動 [連接埠組態精靈]。  
  
2.  在 歡迎使用畫面上，按一下 **下一步**。  
  
3.  型別`SendPurchaseOrder`中**名稱**欄位，，然後按一下**下一步**。  
  
4.  選取**使用現有的連接埠類型**。  
  
5.  在下**可用的連接埠類型**，選取`OrderProcess.PurchaseOrderPT`，然後按一下 **下一步**。  
  
6.  上**連接埠繫結螢幕**下**連接埠通訊方向**，選取`I'll always be sending messages on this port`，然後按一下 **下一步**。  
  
7.  按一下 **[完成]**。  
  
#### <a name="add-a-send-shape-to-the-orchestration"></a>新增 [傳送] 圖形至協調流程  
  
1.  在下**BizTalk 協調流程**在 [工具箱] 拖曳**傳送**圖形至協調流程設計工具。 將它放在 `Receive_PO` 接收圖形下方。  
  
2.  以滑鼠右鍵按一下 傳送 圖形，然後按一下**屬性 視窗**。  
  
3.  型別`Send_PO`中**名稱**欄位。  
  
4.  選取`Message_PO`如**訊息**屬性。  
  
5.  選取`SendPurchaseOrder.PurchaseOrderOperation.Request`如**作業**屬性。 這會結合連接埠至 [協調流程設計師] 中的 [傳送] 圖形。  
  
#### <a name="add-a-decide-shape-to-the-orchestration"></a>新增 [決定] 圖形至協調流程  
  
1.  在下**BizTalk 協調流程**在 [工具箱] 拖曳**決定**圖形至協調流程設計工具。 將它放在 `Send_PO` 傳送圖形下方。  
  
2.  以滑鼠右鍵按一下 決定 圖形，然後按一下**屬性 視窗。**  
  
3.  型別`NeedsApproval`中**名稱**欄位。  
  
4.  在協調流程設計師中，按一下  **Rule_1** 「 決定 」 圖形上。  
  
5.  在 [屬性] 視窗中，輸入`ApprovalRequired`如**名稱**屬性。  
  
6.  按一下**運算式**屬性欄位，，然後按一下省略符號 (**...**) 按鈕。  
  
7.  在 [BizTalk 運算式編輯器] 中，輸入或複製下列運算式：  
  
    ```  
    Message_PO(OrderProcess.PropertySchema.Amount) > 1000  
    ```  
  
8.  按一下 **[確定]**。  
  
#### <a name="add-another-send-port-to-the-orchestration"></a>新增另一個傳送埠至協調流程  
  
1.  在下**BizTalk 協調流程**在 工具箱 拖曳**連接埠**連接埠介面 圖形。 將會啟動 [連接埠組態精靈]。  
  
2.  在 歡迎使用畫面上，按一下 **下一步**。  
  
3.  型別`SendToTasksList`中**名稱**欄位，，然後按一下**下一步**。  
  
4.  選取**使用現有的連接埠類型**。  
  
5.  在下**可用的連接埠類型**，選取`OrderProcess.PurchaseOrderPT`，然後按一下 **下一步**。  
  
6.  在**連接埠繫結螢幕**下**連接埠通訊方向**，選取`I'll always be sending messages on this port`。  
  
7.  在下**連接埠繫結**，選取`Dynamic`，然後按一下 **下一步**。  
  
8.  按一下 **[完成]**。  
  
#### <a name="add-a-send-shape-to-the-decide-shape"></a>新增 [傳送] 圖形至 [決定] 圖形  
  
1.  在下**BizTalk 協調流程**在 [工具箱] 拖曳**傳送**圖形至協調流程設計工具。 將圖形放置在 `ApprovalRequired` 圖形的下方。  
  
2.  以滑鼠右鍵按一下 傳送 圖形，然後按一下**屬性 視窗**  
  
3.  型別`CreateApprovalTask`中**名稱**欄位。  
  
4.  選取`Message_Task`如**訊息**屬性。  
  
5.  選取`SendToTasksList.PurchaseOrderOperation.Request`如**作業**屬性。 這會結合連接埠至 [協調流程設計師] 中的 [傳送] 圖形。  
  
## <a name="create-an-expression"></a>建立運算式  
 在此程序中，您要新增 [運算式] 圖形至指派工作路徑值給變數的解決方案中。 此程序說明如何將邏輯新增到協調流程，以修改動態傳送埠的屬性。  
  
#### <a name="create-a-new-expression"></a>新立新的運算式  
  
1.  在下**BizTalk 協調流程**在 [工具箱] 拖曳**運算式**圖形之前`CreateApprovalTask`傳送 」 圖形。  
  
2.  以滑鼠右鍵按一下 運算式 圖形，然後按一下**屬性 視窗。**  
  
3.  型別`SetPortDestination`中**名稱**欄位。  
  
4.  按一下**運算式**屬性欄位，，然後按一下省略符號 (**...**) 按鈕。  
  
5.  在**BizTalk 運算式編輯器**，輸入下列命令：  
  
    ```  
    SendToTasksList(Microsoft.XLANGs.BaseTypes.Address) = "wss://localhost/sites/WSSAdapterWalkthrough/Lists/Tasks/";  
    ```  
  
6.  按一下 **[確定]**。  
  
## <a name="construct-a-new-message"></a>建構新訊息  
 在此程序中，您要新增 [建構] 圖形至將在協調流程中建構新的訊息類型執行個體的解決方案中。 此程序說明如何建立同時也是輸入訊息複本的新訊息，然後修改此新訊息的內容屬性。 由於訊息在 BizTalk 中是不變的，因此需要執行此步驟；也就是說，一旦您建構了訊息，便無法修改原始訊息。  
  
#### <a name="add-a-construct-shape"></a>新增 [建構] 圖形  
  
1.  在下**BizTalk 協調流程**在 [工具箱] 拖曳**建構訊息**圖形之前`SetPortDestination`運算式 」 圖形。  
  
2.  以滑鼠右鍵按一下 [建構訊息 」 圖形，然後按一下**屬性] 視窗。**  
  
3.  型別`ConstructTaskMessage`中**名稱**欄位。  
  
4.  選取`Message_Task`如**建構的訊息**屬性。  
  
5.  在下**BizTalk 協調流程**在 [工具箱] 拖曳**訊息指派**塑造成`ConstructTaskMessage`**建構訊息**圖形。  
  
6.  在**屬性 視窗**，型別`InitTaskMessage`中**名稱**欄位。  
  
7.  按一下**運算式**屬性欄位，，然後按一下省略符號 (**...**) 按鈕。  
  
8.  在**BizTalk 運算式編輯器**中，輸入或複製下列：  
  
    ```  
    Message_Task = Message_PO;  
    Message_Task(WSS.ConfigOverwrite) = "no";  
    Message_Task(WSS.ConfigNamespaceAliases)= "orchns='http://OrderProcess.PurchaseOrder'";  
    Message_Task(WSS.ConfigPropertiesXml) = "<ConfigPropertiesXml><PropertyName1>Title</PropertyName1><PropertySource1>Approve %XPATH=//orchns:PurchaseOrder/orchns:PurchaseOrderID%</PropertySource1><PropertyName3>Status</PropertyName3><PropertySource3>Not Started</PropertySource3><PropertyName4>Priority</PropertyName4><PropertySource4>(1) High</PropertySource4></ConfigPropertiesXml>";  
    ```  
  
    > [!IMPORTANT]
    >  提供給內容屬性的這些值有區分大小寫。 在設定具有內容屬性的動態連接埠之組態值時，您必須確定使用適當的大小寫，否則，當 BizTalk 嘗試路由文件至指定的傳送埠時，會發生錯誤。  
  
9. 按一下 **[確定]**。  
  
10. 按一下**檔案**，然後按一下 **全部儲存**。  
  
## <a name="build-the-biztalk-project"></a>建置 BizTalk 專案  
 在此程序中，您要建置和部署 BizTalk 專案。 這必要步驟來建立和部署組件的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]於執行階段使用。  
  
#### <a name="build-and-deploy-the-solution"></a>建置和部署解決方案  
  
1.  按一下**建置**，然後按一下 **建置 OrderProcess**。  
  
2.  按一下**建置**，然後按一下 **部署 OrderProcess**。  
  
3.  關閉 [Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]]。  
  
## <a name="modify-the-receive-location-and-send-port"></a>修改接收位置與傳送埠  
 在此程序中，您要修改現有的接收位置和傳送埠，以便在管線中使用 XML 處理。 接收 XML 管線會保存協調流程處理期間使用的訊息屬性，而傳送 XML 管線會保存套用到協調流程中的訊息屬性，且此屬性後續會用於訊息路由。  
  
#### <a name="modify-the-receive-location"></a>修改接收位置  
  
1.  按一下**啟動**，指向**所有程式**，指向 **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 [ **BizTalk Server 管理]。**  
  
2.  展開**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **管理嵌入式管理單元**，依序展開**BizTalk 群組**，依序展開**應用程式**，依序展開  **BizTalk Application 1**，然後按一下 **接收位置**節點。  
  
3.  以滑鼠右鍵按一下`SourceLocation`，然後按一下 **屬性**。  
  
4.  在**接收位置屬性**對話方塊的 **一般**，選取`XMLReceive`如**接收管線**屬性。  
  
5.  按一下 **[確定]**。  
  
#### <a name="modify-the-send-port"></a>修改傳送埠  
  
1.  按一下**傳送埠**節點。  
  
2.  以滑鼠右鍵按一下`SendToDestination`，然後按一下 **屬性**。  
  
3.  在**傳送埠屬性**對話方塊的 **一般**，選取`XMLTransmit`如**傳送管線**屬性。  
  
4.  選取**篩選** 索引標籤。  
  
5.  選取現有的條件，按下 DELETE，然後按**確定**。  
  
#### <a name="start-a-new-send-port"></a>啟動新的傳送埠  
  
1.  按一下**傳送埠**節點。  
  
2.  以滑鼠右鍵按一下`OrderProcess_1.0.0.0_OrderProcess.MyCompanyOrderProcess_SendToTasksList_<GUID>`，然後按一下 **啟動**。  
  
> [!NOTE]
>  若看不見此項目，您可能需要重新整理主控台。  
  
## <a name="bind-the-orchestration"></a>繫結協調流程  
 在此程序中，您要繫結協調流程至指定的連接埠。 此程序必須將實體連接埠結合至您建立和部署的協調流程。  
  
#### <a name="bind-the-orchestration"></a>繫結協調流程  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **協調流程**節點。  
  
2.  以滑鼠右鍵按一下`OrderProcess.MyCompanyOrderProcessing`協調流程，然後再按一下**屬性**。  
  
3.  選取**繫結** 索引標籤。  
  
4.  在下**主機**，選取`BizTalkServerApplication`中**主機**欄位。  
  
5.  在下**繫結**，選取`FromSource`如`ReceivePurchaseOrder`輸入邏輯連接埠。  
  
6.  在下**繫結**，選取`SendToDestination`如`SendPurchaseOrder`輸出邏輯連接埠。  
  
7.  按一下 **[確定]**。  
  
8.  以滑鼠右鍵按一下`OrderProcess.MyCompanyOrderProcessing`協調流程，然後再按一下**啟動**。  
  
## <a name="send-a-message-through-the-system"></a>透過系統傳送訊息  
 在此程序中，您要建立 InfoPath 表單，並將它上載至 Windows SharePoint Services 網站。 Windows SharePoint Services 配接器會取得該訊息、封存至「封存」文件庫，然後傳送至「目的地」文件庫。 在處理此訊息期間，將存取 Windows SharePoint Services 內容屬性，以協助決定目的地。  
  
#### <a name="create-an-infopath-form-to-send-through-the-system"></a>建立 InfoPath 表單以透過系統傳送  
  
1.  開啟 Web 瀏覽器，巡覽至您所建立的網站 URL。 例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。  
  
2.  在 [快速啟動] 功能表中，按一下 `InfoPathSolutions`。  
  
3.  按一下`PurchaseOrder`檔案，以顯示**檔案下載**對話方塊，然後按一下**開啟**。 InfoPath 將載入此表單。  
  
4.  在**採購單識別碼**欄位中，輸入`1003`。  
  
5.  在**帳單寄送地**欄位中，輸入`John Doe`。  
  
6.  在**量**欄位中，輸入`1750`。  
  
7.  在**訂單日期**欄位中，輸入`1/3/2005`。  
  
8.  按一下 **[儲存]**。  
  
9. 在**存** 對話方塊中，輸入`http://<server_name>/sites/WSSAdapterWalkthrough/Source`中**檔案名稱**欄位，然後按 ENTER。  
  
10. 型別`PurchaseOrder3.xml`中**檔案名稱**欄位，，然後按一下**儲存**。  
  
11. 關閉 InfoPath。  
  
12. 在 Web 瀏覽器中，按一下**文件，並列出**。  
  
13. 在下**文件庫**，按一下 **目的地**。  
  
14. 在 [目的地] 文件庫中，您現在會看見已列出您的訊息。 您也可以在 [封存] 文件庫中找到封存的複本。  
  
15. 按一下 [首頁]。  
  
16. 在下**列出**，按一下 **工作**。  
  
17. 在 [工作] 清單中，您會看見新建立的核准工作。  
  
> [!NOTE]
>  由於訂單金額超過 $1,000.00，所以建立此工作。  
  
## <a name="summary"></a>摘要  
 在此逐步解說中，您已經瞭解如何存取 Windows SharePoint Services 內容屬性，以及如何決定通過動態連接埠之訊息的目的地。  
  
## <a name="next-steps"></a>後續步驟  
 繼續檢視 Windows SharePoint Services 配接器章節的其他部分。 如需詳細資訊，請參閱＜另請參閱＞中的主題。  
  
## <a name="see-also"></a>請參閱  
 [什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)   
 [Windows SharePoint Services 配接器逐步解說](../core/windows-sharepoint-services-adapter-walkthroughs.md)