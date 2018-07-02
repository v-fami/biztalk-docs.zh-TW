---
title: 教學課程： 使用 TIBCO Rendezvous 配接器接收 |Microsoft Docs
description: 逐步說明如何使用 BizTalk Adapter for TIBCO Rendezvous 在 BizTalk Server 中，以接收來自 TIBCO 系統的資料
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58e7a739-701d-4085-a840-54f81c55e943
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 430c559d689ba9b56c28d81d37a1c87f91e14f2d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985287"
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data"></a>教學課程： 使用 BizTalk Adapter for TIBCO Rendezvous 來接收資料
您可以使用 BizTalk Adapter for TIBCO Rendezvous 接收來自 TIBCO 系統的資料。 這個逐步解說將說明示範這一點的 SDK 範例。  

## <a name="prerequisites"></a>必要條件  

在執行配接器的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。  

## <a name="about-the-sample"></a>關於範例 
- 此範例會使用 BizTalk Adapter for TIBCO Rendezvous 接收來自 TIBCO 系統的資料。 協調流程處理訊息，並使用 file 配接器，將資料寫入為 XML 檔案中指定的資料夾。  

- 以 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 設計的這個範例，示範了將 BizTalk Adapter for TIBCO Enterprise Message Service 與 BizTalk 協調流程搭配使用的基本功能。  

    > [!NOTE]
    >  此範例假設您已知道如何傳送來自 TIBCO 的訊息以讓應用程式處理。  

- 如需範例預設位置是`C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWayReceive`，並包含下列檔案： 

    |**執行階段專案檔案名稱**|**執行階段專案檔案描述**|  
    |---|---|  
    |OneWayReceive.btproj、<br /><br /> OneWayReceive.sln|應用程式的專案和方案檔。|  
    |PureMessage.xsd，|這個應用程式的結構描述檔案。|  
    |TIBCORvOWR.odx|這個應用程式使用的協調流程。|  
    |TIBCORv.snk|強式命名金鑰檔。|  


## <a name="step-1-add-the-adapter-to-biztalk-administration"></a>步驟 1： 新增配接器至 BizTalk 管理

1.  在  **BizTalk Server 管理**，展開**BizTalk 群組**，展開**平台設定**，然後按一下 **配接器**。  

3.  以滑鼠右鍵按一下**配接器**，指向**新增**，**配接器...** 若要顯示**配接器屬性**對話方塊。  

4.  輸入的值**名稱**欄位，例如**TIBCO Rendezvous**。  

5.  選取**TIBCO(r) Rendezvous(r)** 從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。  

## <a name="step-2-create-a-receive-port"></a>步驟 2： 建立接收埠  

1.  在**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，展開**BizTalk Application 1**，然後按一下**接收埠**。  

2.  以滑鼠右鍵按一下接收埠 資料夾，然後按一下**的新**，**單向接收埠...** 以顯示**接收埠屬性**對話方塊。  

3.  輸入的值**名稱**欄位，例如**TIBCORvOneWayRP**，然後按一下**確定**。  

## <a name="step-3-create-a-receive-location"></a>步驟 3： 建立接收位置  

1. 以滑鼠右鍵按一下新的接收埠，然後按一下**的新**，**接收位置...** 若要顯示**接收位置屬性**對話方塊。  

2. 輸入的值**名稱**欄位。 例如，輸入**TIBCORvOneWayRL**。  

3. 從使用中的配接器清單中選取 TIBCO Rendezvous 配接器**型別**下拉式清單方塊，然後按一下**設定** 按鈕以顯示配接器**傳輸屬性**  對話方塊。  

   > [!NOTE]
   >  這個值是在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中建立 TIBCO 配接器時指定的名稱。  

4. 輸入的值**RendezvousSubjectName**下方**AdapterRequiredProperties**。  

5. 輸入的值**認證的接聽程式屬性**:  


   |   **屬性**   |                                                                         **ReplTest1**                                                                          |
   |------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | 分類帳檔案名稱 |                                             要用於永續性認證訊息傳遞的分類帳檔案名稱。                                             |
   |  可重複使用的名稱   | 要用於認證訊息傳遞的可重複使用對應名稱。 在網路上所有認證訊息通訊人名稱當中，這必須是唯一名稱。 |


6. 輸入的值**認證**:  


   | **屬性** |                   **ReplTest1**                    |
   |--------------|------------------------------------------------|
   |   [密碼]   | TIBCO Rendezvous 伺服器的密碼。  |
   |  [使用者名稱]   | TIBCO Rendezvous 伺服器的使用者名稱。 |


7. 輸入的值**RendezvousTransport**:  

   |**屬性**|**ReplTest1**|  
   |------------------|---------------|  
   |精靈|Rendezvous 傳輸精靈參數。|  
   |Network|Rendezvous 傳輸網路參數。|  
   |服務|Rendezvous 傳輸服務參數。|  

    如需有關屬性的詳細資訊，請參閱[建立接收成品](../core/creating-tibco-rendezvous-receive-handlers.md)。  

8. 按一下 [確定] 。  

9. 選取  **XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。  

10. 以滑鼠右鍵按一下接收位置，然後按一下 **啟用**。  

## <a name="step-4-create-a-one-way-send-port"></a>步驟 4： 建立單向傳送埠  

1. 建立傳送埠所要使用的目標資料夾，例如 C:\FilesOut。  

2. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。  

3. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，**靜態單向傳送埠...** 若要顯示**傳送埠屬性**對話方塊。  

4. 輸入的值**名稱**欄位，例如**TIBCORvOneWayFileSP**。  

5. 選取 **檔案**從清單中的可用配接器**型別**下拉式清單方塊，然後按一下**設定** 按鈕以顯示配接器**傳輸屬性** 對話方塊。  

6. 針對**目的地資料夾** 屬性中，輸入您稍早建立之資料夾的位置，然後按一下**確定**。  

7. 選取  **XMLTransmit**從清單中可用的管線的管線**傳送管線**下拉式清單中，按一下 **確定**。  

8. 以滑鼠右鍵按一下傳送埠，然後按一下 **啟動**登錄並啟動傳送埠。  

## <a name="step-5-build-and-deploy-the-project"></a>步驟 5： 建置並部署專案  

1. 以滑鼠右鍵按一下方案總管] 中的 Onewaysend 專案，然後按一下 [**屬性**啟動專案的專案設計工具。  

2. 按一下 [**部署**] 索引標籤。  

3. 輸入適當的值，如**伺服器**屬性並**組態資料庫**下的屬性**BizTalk 群組**類別。  

4. 以滑鼠右鍵按一下方案總管] 中的 Onewaysend 專案，然後按一下 [ **Deploy**以建置專案並部署組件，以[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。  

## <a name="step-6-bind-enlist-and-start-the-orchestration"></a>步驟 6： 繫結、 登錄，並啟動協調流程  

1. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。  

2. 按一下 **重新整理**按鈕[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台工具列或按下**F5**若要重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。  

3. 按兩下協調流程，以顯示**協調流程屬性**對話方塊。  

4. 按一下 [**繫結**以顯示協調流程繫結選項] 對話方塊的左窗格中。  

5. 指定適當的繫結選項值，例如：  


   | **參數** |        **ReplTest1**         |
   |---------------|--------------------------|
   |     Host      | BizTalkServerApplication |
   |   SendPort    |   TIBCORvOneWayFileSP    |
   |  ReceivePort  |     TIBCORvOneWayRP      |


6. 按一下 [確定] 。  

7. 以滑鼠右鍵按一下協調流程，然後按一下 **啟動**登錄並啟動協調流程。  

## <a name="step-7-confirm-the-application-receives-a-message"></a>步驟 7： 確認應用程式收到的訊息  

- 開啟檔案傳送埠設定為傳送到，並確認已產生輸出文件的資料夾。  

  如果文件執行個體處理成功，則會發生以下一系列的事件：  

1.  TIBCO Rendezvous 配接器接收來自 TIBCO 系統的訊息，並以 BizTalk 訊息的形式將其發佈至 MessageBox。  

2.  協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程的執行個體，然後將訊息傳送至這個協調流程執行個體。  

3.  協調流程執行個體將訊息發佈回 MessageBox。  

4.  檔案傳送埠訂閱這個訊息，因此 BizTalk 會將訊息傳送至檔案配接器。  

5.  檔案配接器將包含結果集的訊息寫入至指定的輸出資料夾。  

## <a name="see-also"></a>另請參閱  
 [教學課程： 使用 BizTalk Adapter for TIBCO Rendezvous 來傳送資料](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data.md)   
 [教學課程： 使用 Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md)   
 [快速入門](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)