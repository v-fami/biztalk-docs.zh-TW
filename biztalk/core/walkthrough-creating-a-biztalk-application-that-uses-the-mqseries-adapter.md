---
title: "逐步解說： 建立 BizTalk 應用程式使用 MQSeries 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IBM WebSphere MQ queues
- MQSeries adapters, tutorial
- MQSeries adapters, testing
- tutorials, MQSeries adapters
- MQSeries adapters, IBM WebSphere MQ queues
- testing, MQSeries adapters
- MQSeries adapters, queues
- configuring [MQSeries adapters], tutorial
ms.assetid: e9e169e4-d41c-4e5d-b165-7bd36b481f24
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0132387b86e048c26c0dab61ca174f3e10c55012
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-creating-a-biztalk-application-that-uses-the-mqseries-adapter"></a>逐步解說： 建立使用 MQSeries 配接器的 BizTalk 應用程式
本節將帶領您建立使用 MQSeries 配接器的簡單 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式。  
  
> [!NOTE]
>  此應用程式假設您已經在與 BizTalk Server 相同的電腦上安裝 IBM WebSphere MQ (適用於 Windows 平台的伺服器元件)。 它也假設您尚未建立任何傳送埠或接收位置。 若您有現有的傳送埠或接收位置，當逐步進行這些步驟時請以適當的名稱來替代。  
  
 此應用程式是一個簡單以內容為基礎的路由應用程式，只使用一個接收位置和傳送埠。 接收位置會從 IBM WebSphere MQ 佇列讀取。 傳送埠會從接收位置取得訊息，並將它傳送到不同的 IBM WebSphere MQ 佇列。  
  
 若要建立此應用程式，您必須建立 IBM WebSphere MQ 佇列、設定 BizTalk Server 接收位置與傳送埠、啟動傳送埠和啟用接收位置，並將測試訊息放在佇列中。  
  
 若您擁有 IBM WebSphere MQ 安裝所需的權限，您可以透過配接器對話方塊建立 IBM WebSphere MQ 佇列，並可略過下一個程序。 若您沒有這類存取權限，您可以使用 IBM WebSphere MQ (適用於 Windows 平台總管的用戶端元件) 來建立佇列。 若要透過 IBM WebSphere MQ Explorer 嵌入式管理單元來建立佇列，請執行下列程序。  
  
## <a name="to-create-the-ibm-websphere-mq-queues-through-the-ibm-websphere-mq-explorer"></a>透過 IBM WebSphere MQ Explorer 建立 IBM WebSphere MQ 佇列  
 請依照以下步驟執行，透過 IBM WebSphere MQ Explorer 建立 IBM WebSphere MQ 佇列：  
  
1.  按一下**啟動**，指向 **程式**，指向  **IBM WebSphere MQ**，然後按一下  **WebSphere MQ Explorer**。  
  
2.  按兩下**佇列管理員**，然後按兩下預設佇列管理員。 預設佇列管理員通常會命名為**Qm_<***< machine_name >*其中*machine_name*是您的電腦名稱。  
  
3.  以滑鼠右鍵按一下**佇列**，指向 **新增**，然後按一下 **本機佇列**。  
  
4.  中**建立本機佇列**對話方塊中，於**佇列名稱**，型別**BTStoMQS**，然後按一下 **確定**。  
  
5.  以滑鼠右鍵按一下**佇列**，指向 **新增**，然後按一下 **本機佇列**。  
  
6.  中**建立本機佇列**對話方塊中，於**佇列名稱**，型別**MQStoBTS**，然後按一下 **確定**。  
  
 接下來的步驟會建立接收位置和傳送埠，並啟動傳送埠及啟用接收位置。 並且也會建立 IBM WebSphere MQ 佇列。  
  
## <a name="to-create-the-receive-location-and-the-mqseries-queue"></a>建立接收位置與 MQSeries 佇列  
 請依照以下步驟執行，建立接收位置與 MQSeries 佇列：  
  
1.  在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 預設值應用程式 (**BizTalk Application 1**依預設)。  
  
2.  以滑鼠右鍵按一下**接收埠**節點中，按一下 **新增**，然後選取**單向連接埠**。  
  
3.  在**接收埠屬性**對話方塊中，於**名稱**方塊中，輸入**MQStoBTS**。  
  
4.  在左窗格中，按一下 **接收位置**，然後在右窗格中，按一下**新增**。  
  
5.  在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**MQStoBTS**。  
  
6.  選取**MQSeries**旁的下拉式清單**類型**選項。  
  
7.  在**傳輸**區段中，按一下**設定**。  
  
8.  在**MQSeries 傳輸屬性**對話方塊中，於**輪詢間隔**方塊中，輸入**1**。  
  
9. 在**佇列定義**方塊中，按一下省略符號 (**...**) 按鈕。  
  
10. 在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。  
  
11. 在**佇列管理員**方塊中，選取預設佇列管理員。  
  
12. 在**佇列**方塊中，輸入**MQStoBTS**，然後按一下 **匯出**。  
  
13. 中**匯出**對話方塊中，按一下**Create Queue**，然後按一下 [**確定**和**[確定]** ，以返回**接收位置屬性**] 對話方塊。  
  
14. 在**接收處理常式**方塊中，選取**BizTalkServerApplication**。  
  
15. 在**接收管線**方塊中，選取**PassThruReceive**。  
  
16. 按一下**確定**套用變更。  
  
## <a name="to-create-the-send-port-and-the-mqseries-queue"></a>建立傳送埠與 MQSeries 佇列  
 請依照以下步驟執行，建立傳送埠與 MQSeries 佇列：  
  
1.  以滑鼠右鍵按一下**傳送埠**，按一下 **新增**，然後選取**靜態單向傳送埠**。  
  
2.  在**傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入**BTStoMQS。**  
  
3.  選取**MQSeries**旁的下拉式清單**類型**選項。  
  
4.  在**傳輸**區段中，按一下**設定**。  
  
5.  在**MQSeries 傳輸屬性**對話方塊中，於**佇列定義**方塊中，按一下省略符號 (**...**) 按鈕。  
  
6.  在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。  
  
7.  在**佇列管理員**方塊中，選取預設佇列管理員。  
  
8.  在**佇列**方塊中，輸入**BTStoMQS**，然後按一下 **匯出**。  
  
9. 中**匯出**對話方塊中，按一下**Create Queue**，然後按一下 [**確定**和**[確定]** ，以返回**傳送埠屬性**] 對話方塊。  
  
10. 在**傳送管線**方塊中，選取**PassThruTransmit**。  
  
11. 按一下以選取**篩選**在左窗格中，然後在右窗格中設定篩選選項。  
  
12. 在**屬性**下拉式清單中，選取**BTS。ReceivePortName**。  
  
13. 在**值**方塊中，輸入**MQStoBTS**。  
  
14. 按一下**確定**套用變更。  
  
## <a name="to-enable-the-receive-location-and-start-the-send-port"></a>啟用接收位置和啟動傳送埠  
 請依照以下步驟執行，啟用接收位置和啟動傳送埠：  
  
1.  以滑鼠右鍵按一下**MQStoBTS**接收位置，然後按一下**啟用**。  
  
2.  以滑鼠右鍵按一下**BTStoMQS**傳送埠，然後**啟動**。  
  
 下一步是藉由傳送測試訊息到接收佇列，以測試應用程式。  
  
## <a name="to-test-the-application"></a>若要測試應用程式  
 請依照以下步驟執行來測試應用程式：  
  
1.  按一下**啟動**，指向 **程式**，指向  **IBM WebSphere MQ**，然後按一下  **WebSphere MQ Explorer**。  
  
2.  以滑鼠右鍵按一下**MQStoBTS**，然後按一下 **放入測試訊息**。  
  
3.  在**訊息資料**方塊中，輸入測試訊息。 按一下 **[確定]**。  
  
 輸入資料之後,**目前深度**如**MQStoBTS**佇列是一 (1)。 當應用程式處理訊息時，計數會傳回零 (0) 和**目前深度**的**BTStoMQS**會變成一 （1)。 您也可以檢視訊息內容。  
  
## <a name="to-view-the-message"></a>檢視訊息  
 請依照以下步驟執行來檢視訊息：  
  
1.  按兩下**BTStoMQS**佇列。  
  
2.  按兩下訊息，然後選取**資料**工作表。 您可以檢視中的訊息文字**訊息資料**方塊。  
  
3.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [何謂 MQSeries 配接器？](../core/what-is-the-mqseries-adapter.md)   
 [MQSeries 配接器架構](../core/mqseries-adapter-architecture.md)