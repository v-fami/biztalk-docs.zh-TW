---
title: 教學課程： 使用 TIBCO Rendezvous 配接器傳送 |Microsoft Docs
description: 若要使用 BizTalk Adapter for TIBCO Rendezvous 在 BizTalk Server 中，將資料傳送至 TIBCO 系統的逐步指南
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b761ce2d-3465-43e0-bd8d-4d68b523226a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef842eacf261904173b90728ba2702513973cf53
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966935"
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data"></a>教學課程：使用 BizTalk Adapter for TIBCO Rendezvous 來傳送資料
您可以使用 BizTalk Adapter for TIBCO Rendezvous 將資料傳送至 TIBCO 系統。 這個逐步解說將說明示範這一點的 SDK 範例。  

## <a name="prerequisites"></a>必要條件  

- 在執行配接器的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。  

- 此範例會使用包含訊息內容屬性的 DLL：Microsoft.BizTalk.Adapters.TibRV.Properties.dll。 您可能需要更新方案對這個程式庫的參考。 如需詳細資訊，請參閱 < [BizTalk Server 訊息內容屬性 （傳送處理常式）](../core/biztalk-server-message-context-properties-send-handlers.md)。  

## <a name="about-the-sample"></a>關於範例 

- 此範例會從某個檔案資料夾收取某個 XML 檔案、將該檔案傳送至協調流程，然後使用 BizTalk Adapter for TIBCO Rendezvous 在 TIBCO 系統中建立一筆記錄。  

- 以 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 設計的這個範例，示範了將 BizTalk Adapter for TIBCO Rendezvous 與 BizTalk 協調流程搭配使用的基本功能。  

- 如需範例預設位置是`C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWaySend`，並包含下列檔案： 

    |**執行階段專案檔案名稱**|**執行階段專案檔案描述**|  
    |---|---|  
    |OneWaySend.btproj<br /><br /> OneWaySend.sln|應用程式的專案和方案檔。|  
    |Schema.xsd<br /><br /> PropertySchema.xsd|這個應用程式的結構描述和屬性結構描述檔案。|  
    |Orchestration.odx|這個應用程式使用的協調流程。|  
    |TIBCORendezvousOneWaySend.snk|強式命名金鑰檔。|  

## <a name="step-1-add-the-adapter-to-biztalk-administration"></a>步驟 1： 新增配接器至 BizTalk 管理

1.  在  **BizTalk Server 管理**，展開**BizTalk 群組**，展開**平台設定**，然後按一下 **配接器**。  

3.  以滑鼠右鍵按一下**配接器**，指向**新增**，**配接器...** 若要顯示**配接器屬性**對話方塊。  

4.  輸入的值**名稱**欄位。 例如，輸入**TIBCO Rendezvous**。  

5.  選取**TIBCO(r) Rendezvous(r)** 從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。  

## <a name="step-2-create-a-send-port"></a>步驟 2： 建立傳送埠  

1. 在**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。  

2. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，**靜態單向傳送埠...** 若要顯示**傳送埠屬性**對話方塊。  

3. 輸入的值**名稱**欄位，例如**TIBCORndOneWaySP**。  

4. 從使用中的配接器清單中選取 TIBCO Rendezvous 配接器**型別**下拉式清單方塊，然後按一下**設定** 按鈕以顯示配接器**傳輸屬性**  對話方塊。  

   > [!NOTE]
   >  這個值是在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 中建立 TIBCO Enterprise Message System 配接器時指定的名稱。  

5. 輸入的值**認證的寄件者屬性**:  


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

    如需有關屬性的詳細資訊，請參閱[建立傳送成品](../core/creating-tibco-rendezvous-send-handlers.md)。  

8. 按一下 [確定] 。  

9. 選取**XML 傳輸**從清單中可用的管線的管線**傳送管線**下拉式清單中，按一下 **確定**。  

10. 以滑鼠右鍵按一下傳送埠，然後按一下 **啟動**登錄並啟動傳送埠。  

## <a name="step-3-create-a-receive-port"></a>步驟 3： 建立接收埠  

1.  在**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，展開**BizTalk Application 1**，然後按一下**接收埠**。  

2.  以滑鼠右鍵按一下接收埠 資料夾，然後按一下**的新**，**單向接收埠...** 以顯示 接收埠屬性 對話方塊。  

3.  輸入的值**名稱**欄位，例如**TIBCORndOneWayFileRP**，然後按一下**確定**。  

## <a name="step-4-create-a-receive-location"></a>步驟 4： 建立接收位置  

1.  為檔案接收位置建立一個資料夾來監視，例如 C:\Filesource。  

2.  以滑鼠右鍵按一下新的接收埠，然後按一下**的新**，**接收位置...** 若要顯示**接收位置屬性**對話方塊。  

3.  輸入的值**名稱**欄位，例如**TIBCORndOneWayFileRL**。  

4.  選取 **檔案**從清單中的可用配接器**型別**下拉式清單方塊，然後按一下**設定** 按鈕以顯示配接器**傳輸屬性** 對話方塊。  

5.  輸入您稍早建立的資料夾的位置**接收資料夾**屬性，然後按一下**確定**。  

6.  選取  **XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。  

7.  以滑鼠右鍵按一下接收位置，然後按一下 **啟用**。  

## <a name="step-5-generate-a-document-instance-from-the-schema"></a>步驟 5： 從結構描述產生文件執行個體  

1.  在 Visual Studio 中，按一下滑鼠右鍵在 [方案總管] 中的 Schema.xsd，按一下**屬性**。  

2.  在 [屬性] 視窗中，按一下以選取**輸出執行個體的檔名**選項底下**一般**一節。  

3.  按一下省略符號按鈕 （...） 以顯示**選取輸出檔案**對話方塊。  

4.  指定的資料夾，然後輸出檔案執行個體名稱，例如**C:\instance.xml**然後按一下**儲存**。  

    > [!NOTE]
    >  請勿在這裡指定剛才針對檔案接收位置指定的資料夾位置。  

5.  以滑鼠右鍵按一下方案總管] 中的 Schema.xsd，然後按一下 [**產生的執行個體**產生文件執行個體中指定的位置。  

## <a name="step-6-update-the-generated-document-instance"></a>步驟 6： 更新產生的文件執行個體  

1.  在文字編輯器中 （適用於 「 記事本 」），開啟產生的文件執行個體，然後編輯文件執行個體，以確保資料會在 TIBCO 系統中產生唯一的記錄內容。 例如，下列程式碼顯示的資料檔案的第一個部分：  

    ```  
    <ns0:Root xmlns:ns0="http://TibcoRendezvousOneWaySend.TibcoRendezvousOneWaySendSchema">  
        <Name>Punya Palit</Name>  
        <MailAddress>Prose Ware, Inc.</MailAddress>  
    </ns0:Root>  
    ```  

2.  儲存已修改的文件執行個體。  

## <a name="step-7-build-and-deploy-the-project"></a>步驟 7： 建置並部署專案  

1. 以滑鼠右鍵按一下**OneWaySend**方案總管 中專案，然後按一下**屬性**啟動專案的專案設計工具。  

2. 按一下 [**部署**] 索引標籤。  

3. 輸入適當的值，如**伺服器**屬性並**組態資料庫**下的屬性**BizTalk 群組**。  

4. 以滑鼠右鍵按一下方案總管] 中的 OneWaySend 專案，然後按一下 [ **Deploy**以建置專案並部署組件，以[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。  

## <a name="step-8-bind-enlist-and-start-the-orchestration"></a>步驟 8： 繫結、 登錄和啟動協調流程  

1. 在**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。  

2. 按一下 **重新整理**中的 MMC 工具列或按下按鈕**F5**若要重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。  

3. 按兩下協調流程，以顯示**協調流程屬性**對話方塊。  

4. 按一下 [**繫結**以顯示協調流程繫結選項] 對話方塊的左窗格中。  

5. 指定適當的繫結選項值，例如：  


   |    **參數**    |        **ReplTest1**         |
   |---------------------|--------------------------|
   |        Host         | BizTalkServerApplication |
   |   FileReceivePort   |   TIBCORndOneWayFileRP   |
   | TibcoRendezvousSend |     TIBCORndOneWaySP     |


6. 按一下 [確定]。  

7. 以滑鼠右鍵按一下協調流程，然後按一下 **啟動**登錄並啟動協調流程。  

## <a name="step-9-drop-a-document-and-check-the-tibco-system"></a>步驟 9： 卸除文件，並檢查 TIBCO 系統

-   將稍早建立的文件執行個體複製到應用程式所監視的檔案接收資料夾。  

-   使用 TIBCO Web 介面，確認已從 XML 檔案中的資料建立記錄。  


如果文件執行個體處理成功，則會發生以下一系列的事件：  

1.  檔案配接器從資料夾擷取到檔案，並將其發佈到 MessageBox 做為 BizTalk 訊息。  

2.  協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程執行個體，然後將訊息傳送至這個協調流程執行個體。  

3.  協調流程執行個體使用指定的協調流程中的邏輯處理訊息，並將訊息發佈回 MessageBox。  

4.  TIBCO 傳送埠訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會將訊息傳送至 TIBCO 傳送埠。  

5.  傳送埠將訊息交給 BizTalk Adapter for TIBCO Rendezvous。  

6.  BizTalk Adapter for TIBCO Rendezvous 將訊息傳送至 TIBCO 系統。  

## <a name="see-also"></a>另請參閱  
 [教學課程： 使用 BizTalk Adapter for TIBCO Rendezvous 來接收資料](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data.md)   
 [教學課程： 使用 Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md)   
 [快速入門](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)