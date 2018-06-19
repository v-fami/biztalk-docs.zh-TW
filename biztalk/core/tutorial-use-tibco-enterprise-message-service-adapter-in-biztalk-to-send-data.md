---
title: 教學課程： 使用 BizTalk Adapter for TIBCO Enterprise Message Service 來傳送資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1912d594-3839-4e04-bc40-93bd7cc0b309
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e2e2dc6fe0c1427ac959ce77d6ff4f46b4f4285
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010679"
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-enterprise-message-service-to-send-data"></a>教學課程： 使用 BizTalk Adapter for TIBCO Enterprise Message Service 來傳送資料
您可以使用 BizTalk Adapter for TIBCO Enterprise Message Service (EMS)，將資料傳送至 TIBCO 系統。 這個逐步解說將說明示範這一點的 SDK 範例。  
  
## <a name="prerequisites"></a>必要條件  
  
-   BizTalk Adapter for TIBCO EMS 會要求您加入 TIBCO EMS C# API，TIBCO。EMS.dll 至全域組件快取 (GAC)。 如需安裝組件的詳細資訊，請參閱[TIBCO Enterprise Message Service 的需求和限制](../core/tibco-enterprise-message-service-requirements-and-limitations.md)。  
  
-   在執行配接器的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會收取某個 XML 檔案，從檔案資料夾、 將該檔案傳送至協調流程，並再使用 BizTalk Adapter for TIBCO Enterprise Message Service 在 TIBCO 系統中建立的記錄。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 在 Visual Studio 中設計的這個範例說明使用 BizTalk Adapter for TIBCO Enterprise Message Service 與 BizTalk 協調流程的基本功能。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 此範例的預設位置是  
  
 C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) 企業訊息 Service(TM) \Sdk\OneWaySend  
  
 下表列出此範例中的檔案並提供描述。  
  
|**執行階段專案檔案名稱**|**執行階段專案檔案描述**|  
|----------------------------------|------------------------------------------|  
|OneWaySend.btproj<br /><br /> OneWaySend.sln|應用程式的專案和方案檔。|  
|Schema.xsd|這個應用程式的結構描述檔案。|  
|Orchestration.odx|這個應用程式使用的協調流程。|  
|TIBCOEMSOneWaySend.snk|強式命名金鑰檔。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
  
#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-ems"></a>建立新的 BizTalk Adapter for TIBCO EMS 執行個體  
  
1.  啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。 按一下**啟動**，**所有程式**， **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]， **BizTalk Server 管理**。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下  **配接器**。  
  
3.  以滑鼠右鍵按一下**配接器**指向**新增**，**配接器**顯示**配接器屬性**對話方塊。  
  
4.  輸入一個值**名稱**欄位，例如**TIBCO EMS**。  
  
5.  選取**TIBCO Enterprise Message System**從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。  
  
#### <a name="create-a-biztalk-send-port"></a>建立 BizTalk 傳送埠  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。  
  
2.  以滑鼠右鍵按一下**傳送埠**指向**新增**，**靜態單向傳送埠**顯示**傳送埠屬性**對話方塊。  
  
3.  輸入一個值**名稱**欄位，例如**TIBCOEMSOneWaySP**。  
  
4.  從使用中的配接器清單選取 TIBCO EMS 配接器**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性**對話方塊。  
  
    > [!NOTE]
    >  這個值是在建立 TIBCO Enterprise Message System 配接器時指定了名稱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
5.  輸入的值**伺服器連線定義**:  
  
    |**屬性**|**值**|  
    |------------------|---------------|  
    |目的地|伺服器目的地佇列或主題名稱。|  
    |通訊埠編號|TIBCO 伺服器接聽的連接埠。 預設值為 7222。|  
    |伺服器名稱|TIBCO EMS 伺服器的名稱。|  
  
6.  輸入的值**使用者認證**:  
  
    |**屬性**|**值**|  
    |------------------|---------------|  
    |密碼|TIBCO EMS 伺服器的密碼。|  
    |使用者名稱|TIBCO EMS 伺服器的使用者名稱。|  
  
     如需屬性的詳細資訊，請參閱[建立 TIBCO 企業訊息服務傳送處理常式](../core/creating-tibco-enterprise-message-service-send-handlers.md)。  
  
7.  按一下 **[確定]**。  
  
8.  選取**XML 傳輸**管線就會從管線中可用的清單**傳送管線**下拉式清單中，按一下 **確定**。  
  
9. 以滑鼠右鍵按一下傳送埠，然後按一下**啟動**登錄並啟動傳送埠。  
  
#### <a name="create-a-file-receive-port"></a>建立檔案接收埠  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**接收埠**。  
  
2.  以滑鼠右鍵按一下接收埠] 資料夾，然後按一下 [**新增**，**單向接收埠**以顯示 [接收埠屬性] 對話方塊。  
  
3.  輸入一個值**名稱**欄位，例如**TIBCOEMSOneWayFileRP**，然後按一下**確定**。  
  
#### <a name="create-a-file-receive-location"></a>建立檔案接收位置  
  
1.  為檔案接收位置建立一個資料夾來監視，例如 C:\Filesource。  
  
2.  以滑鼠右鍵按一下新的接收埠，然後按一下 **新增**，**接收位置**顯示**接收位置屬性**對話方塊。  
  
3.  輸入一個值**名稱**欄位，例如**TIBCOEMSOneWayFileRL**。  
  
4.  選取**檔案**從清單中的可用配接器的**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。  
  
5.  輸入您稍早建立的資料夾位置**接收資料夾**屬性，然後按一下**確定**。  
  
6.  選取**XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。  
  
7.  以滑鼠右鍵按一下接收位置，然後按一下**啟用**。  
  
#### <a name="generate-a-document-instance-from-the-adapter-schema"></a>從配接器結構描述產生文件執行個體  
  
1.  以滑鼠右鍵按一下方案總管 中的 Schema.xsd，然後按一下**屬性**。  
  
2.  在 [屬性] 視窗中，按一下以選取**輸出執行個體檔案名稱**選項在**一般**類別目錄。  
  
3.  按一下省略符號按鈕 （…） 以顯示**選取輸出檔案**對話方塊。  
  
4.  指定的資料夾和輸出檔案執行個體名稱，例如**C:\instance.xml**按一下**儲存**。  
  
    > [!NOTE]
    >  請勿在這裡指定剛才針對檔案接收位置指定的資料夾位置。  
  
5.  以滑鼠右鍵按一下方案總管 中的 Schema.xsd，然後按一下**產生執行個體**產生文件執行個體中指定的位置。  
  
#### <a name="modify-the-generated-document-instance"></a>修改產生的文件執行個體  
  
1.  在文字編輯器 (如 [記事本]) 中開啟產生的文件執行個體，然後編輯文件執行個體的內容，以確保資料會在 TIBCO 系統中產生唯一的記錄。 例如，下列程式碼顯示這個資料檔案的第一個部分：  
  
    ```  
    <ns0:Root xmlns:ns0="http://TibcoEMSOne_WaySend.TibcoEMSOneWaySendSchema">  
      <Name>Punya Palit</Name>  
      <MailAddress>Prose Ware, Inc.</MailAddress>  
    </ns0:Root>  
    ```  
  
2.  儲存已修改的文件執行個體。  
  
#### <a name="build-and-deploy-the-project"></a>建置和部署專案  
  
1.  以滑鼠右鍵按一下方案總管 中的 OneWaySend 專案，然後按一下**屬性**啟動專案的專案設計工具。  
  
2.  按一下**部署** 索引標籤。  
  
3.  輸入適當的值**伺服器**屬性和**組態資料庫**下的屬性**BizTalk 群組**類別目錄。  
  
4.  以滑鼠右鍵按一下方案總管 中的 OneWaySend 專案，然後按一下**部署**建置專案並部署組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。  
  
#### <a name="bind-and-enlist-the-orchestration"></a>繫結和登錄協調流程  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。  
  
2.  按一下**重新整理**中 MMC 工具列或按下按鈕**F5**重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。  
  
3.  按兩下協調流程以顯示**協調流程屬性**對話方塊。  
  
4.  按一下**繫結**以顯示協調流程繫結選項 對話方塊的左窗格中。  
  
5.  指定適當的繫結選項值，例如：  
  
    |**參數**|**值**|  
    |-------------------|---------------|  
    |Host|BizTalkServerApplication|  
    |FileReceivePort|TIBCOEMSOneWayFileRP|  
    |TibcoEMSOneWaySendPort|TIBCOEMSOneWaySP|  
  
6.  按一下 [確定]。  
  
#### <a name="start-the-orchestration"></a>啟動協調流程  
  
-   在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，以滑鼠右鍵按一下協調流程，然後按一下**啟動**登錄並啟動協調流程。  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a>將文件執行個體拖放到檔案接收位置所監視的資料夾  
  
-   將稍早建立的文件執行個體複製到應用程式所監視的檔案接收資料夾。  
  
#### <a name="verify-that-the-tibco-system-is-updated"></a>確認 TIBCO 系統已更新  
  
-   使用 TIBCO Web 介面，確認已從 XML 檔案中的資料建立記錄。  
  
 如果文件執行個體處理成功，則會發生以下一系列的事件：  
  
1.  檔案配接器從資料夾擷取到檔案，並將其發佈到 MessageBox 做為 BizTalk 訊息。  
  
2.  協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程執行個體，然後將訊息傳送至這個協調流程執行個體。  
  
3.  協調流程執行個體使用指定的協調流程中的邏輯處理訊息，並將訊息發佈回 MessageBox。  
  
4.  TIBCO 傳送埠訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會將訊息傳送至 TIBCO 傳送埠。  
  
5.  傳送埠將訊息交給 BizTalk Adapter for TIBCO Enterprise Message Service。  
  
6.  BizTalk Adapter for TIBCO Enterprise Message Service 將訊息傳送至 TIBCO 系統。  
  
## <a name="see-also"></a>請參閱  
 [教學課程： 使用 BizTalk Adapter for TIBCO Enterprise Message Service 來接收資料](../core/tutorial-us-the-biztalk-adapter-for-tibco-message-service-to-receive-data.md)   
 [教學課程： 使用 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md)   
 [快速入門](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)