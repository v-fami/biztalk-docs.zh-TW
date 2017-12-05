---
title: "教學課程： 將資料寫入至 PeopleSoft Enterprise 使用 BizTalk Adapter for PeopleSoft Enterprise |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837dd4db-576d-41c1-9fe8-e1e46861270b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b38c1f5a0bd442404e832274d13ace2b0660c2e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-peoplesoft-enterprise-to-write-data-to-peoplesoft-enterprise"></a>教學課程： 將資料寫入至 PeopleSoft Enterprise 使用 BizTalk Adapter for PeopleSoft Enterprise
BizTalk Adapter for PeopleSoft Enterprise 可用來將資料寫入至 PeopleSoft 系統，以接收來自交易夥伴或內部應用程式的資訊。 這個逐步解說將說明此功能的 SDK 範例。  
  
## <a name="prerequisites"></a>必要條件  
  
-   Java 2 平台上必須安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk Adapter for PeopleSoft Enterprise 上執行。  
  
-   PeopleSoft Java Object Adapter JAR 檔案， **psjoa.jar**應複製到可存取的資料夾[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk Adapter for PeopleSoft Enterprise 上執行。  
  
-   執行 BizTalk Adapter for PeopleSoft Enterprise 的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上必須已安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會收取資料夾從某個 XML 檔案、 將該檔案傳送至協調流程，並再使用 BizTalk Adapter for PeopleSoft Enterprise 從 XML 檔案中的資料在 PeopleSoft 系統中建立的記錄。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 以 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 設計的這個範例，其建立的目的在示範將 BizTalk Adapter for PeopleSoft Enterprise 與 BizTalk 協調流程搭配使用的基本功能。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這個範例位於下列資料夾：  
  
 \Program Files\Microsoft BizTalk Adapters for enterprise \Sdk\PeopleSoftOneWaySend  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|**執行階段專案檔案名稱**|**執行階段專案檔案描述**|  
|----------------------------------|------------------------------------------|  
|OneWaySend.btproj，<br /><br /> OneWaySend.sln|應用程式的專案和方案檔。|  
|LOCATIONService.xsd、<br /><br /> LOCATIONService_1.xsd、<br /><br /> LOCATIONService_2.xsd|這個應用程式的結構描述檔案。 **注意：**使用原先建立在專案中的配接器結構描述檔案**新增配接器中繼資料精靈**。 如需 [新增配接器中繼資料精靈] 的詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的「如何將配接器中繼資料新增至 BizTalk 專案」主題。|  
|PeopleSoftOneWaySend.odx|這個應用程式使用的協調流程。|  
|PeopleSoftOneWaySend.snk|強式命名金鑰檔。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
  
#### <a name="create-a-new-instance-of-the-peoplesoft-enterprise-adapter"></a>建立 PeopleSoft Enterprise 配接器的新執行個體  
  
1.  啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。 按一下**啟動**，**所有程式**， [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]， **BizTalk Server 管理**。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 **配接器**。  
  
3.  以滑鼠右鍵按一下**配接器**指向**新增**，**配接器...** 若要顯示**配接器屬性**對話方塊。  
  
4.  輸入一個值**名稱**欄位，例如**PeopleSoft**。  
  
5.  選取**PeopleSoft enterprise （)**從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。  
  
#### <a name="create-a-biztalk-send-port"></a>建立 BizTalk 傳送埠  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。  
  
2.  以滑鼠右鍵按一下**傳送埠**指向**新增**，**靜態單向傳送埠**顯示**傳送埠屬性**對話方塊。  
  
3.  輸入一個值**名稱**欄位，例如**PeopleSoftOneWaySP**。  
  
4.  從使用中的配接器清單中選取 PeopleSoft 配接器**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。  
  
    > [!NOTE]
    >  這個值是在建立 PeopleSoft Enterprise 配接器時指定了名稱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
5.  輸入下列值**配接器必要屬性**:  
  
    |**屬性**|**值**|  
    |------------------|---------------|  
    |應用程式伺服器路徑|PeopleSoft 伺服器的機器與連接埠位置，例如 //PSServer:8888。 **注意：**如果未指定連接埠號碼，會使用預設連接埠 9000，因此在您上面的範例可以輸入 //PSServer 值如果 PeopleSoft 伺服器使用預設的連接埠值 9000。|  
    |JAVA_HOME|與 Java 2 平台 SDK 檔案相關聯之主目錄的路徑，例如 C:\j2sdk1.4.2_08|  
    |密碼|連接至 PeopleSoft 系統時使用的密碼。|  
    |PeopleSoft 8.x JAR 檔案|PeopleSoft Java Object Adapter JAR 檔案位置， **psjoa.jar**，例如 C:\JARS\psjoa.jar。|  
    |使用者名稱|用於連接至 PeopleSoft 系統的使用者名稱。|  
  
6.  按一下 **[確定]**。  
  
7.  選取**XML 傳輸**管線就會從管線中可用的清單**傳送管線**下拉式清單中，按一下 **確定**。  
  
8.  以滑鼠右鍵按一下傳送埠，然後按一下**啟動**登錄並啟動傳送埠。  
  
#### <a name="create-a-file-receive-port"></a>建立檔案接收埠  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**接收埠**。  
  
2.  以滑鼠右鍵按一下接收埠] 資料夾，然後按一下 [**新增**，**單向接收埠**以顯示 [接收埠屬性] 對話方塊。  
  
3.  輸入一個值**名稱**欄位，例如**PeopleSoftOneWayFileRP**，然後按一下**確定**。  
  
#### <a name="create-a-file-receive-location"></a>建立檔案接收位置  
  
1.  建立要由檔案接收位置監視的資料夾，例如 C:\Filesource。  
  
2.  以滑鼠右鍵按一下新的接收埠，然後按一下 **新增**，**接收位置**顯示**接收位置屬性**對話方塊。  
  
3.  輸入一個值**名稱**欄位，例如**PeopleSoftOneWayFileRL**。  
  
4.  選取**檔案**從清單中的可用配接器的**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。  
  
5.  輸入您稍早建立的資料夾位置**接收資料夾**屬性，然後按一下**確定**。  
  
6.  選取**XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。  
  
7.  以滑鼠右鍵按一下接收位置，然後按一下**啟用**。  
  
#### <a name="modify-the-adapter-schema-target-namespace-property"></a>修改配接器結構描述目標命名空間屬性  
  
1.  啟動 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 並開啟 OneWaySend.sln。 按一下**檔案**，**開啟**，**專案/方案...** 若要顯示**開啟專案**對話方塊。  
  
2.  瀏覽到 OneWaySend.sln 檔案，請按一下以選取此檔案，然後按一下**開啟**來開啟包含範例專案的方案。  
  
3.  按一下**檢視**功能表，然後選取**方案總管 中**以顯示 方案總管。  
  
4.  按兩下 [方案總管] 中的 LOCATIONService_1.xsd 檔案加以開啟。  
  
5.  以滑鼠右鍵按一下**結構描述**的 LOCATIONService_1.xsd，然後選取節點**屬性**功能表選項以顯示結構描述的屬性。  
  
6.  編輯**目標命名空間**屬性，以使用適當的值做為配接器名稱，例如**目標命名空間**屬性應該讀取，如下所示：  
  
    ```  
    http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]  
    ```  
  
     其中*PeopleSoft*是 PeopleSoft 配接器的名稱，如 BizTalk 管理主控台中所示。  
  
    > [!IMPORTANT]
    >  如果設定的值為**目標命名空間**不符合輸入文件執行個體處理時，會發生路由失敗，然後輸入文件執行個體中指定的命名空間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
#### <a name="generate-a-document-instance-from-the-adapter-schema"></a>從配接器結構描述產生文件執行個體  
  
1.  按兩下**LOCATIONService_1.xsd**結構描述編輯器中開啟該檔案 [方案總管] 中。  
  
2.  以滑鼠右鍵按一下**\<結構描述\>**節點在結構描述編輯器 中，按一下**屬性**顯示節點的屬性。  
  
3.  選取**CreateEx**從清單中的可用節點**根參考**下拉式方塊。 這應完成，以便在產生範例文件執行個體時將會產生從**CreateEx**結構描述節點。  
  
4.  以滑鼠右鍵按一下 [方案總管] 中的 LOCATIONService_1.xsd，然後按一下**屬性**。  
  
5.  在 [屬性] 視窗中，按一下以選取**輸出執行個體檔案名稱**選項在**一般**> 一節。  
  
6.  按一下省略符號按鈕 （…） 以顯示**選取輸出檔案**對話方塊。  
  
7.  指定的資料夾和輸出檔案執行個體名稱，例如**C:\instance.xml**按一下**儲存**。  
  
    > [!NOTE]
    >  請勿在這裡指定剛才針對檔案接收位置指定的資料夾位置。  
  
8.  以滑鼠右鍵按一下 [方案總管] 中的 LOCATIONService_1.xsd，然後按一下**產生執行個體**產生文件執行個體中指定的位置。  
  
9. 以滑鼠右鍵按一下**\<結構描述\>**節點在結構描述編輯器 中，按一下**屬性**顯示節點的屬性。  
  
10. 選取 (**預設)**從清單中的可用節點**根參考**下拉式方塊。  
  
#### <a name="modify-the-generated-document-instance"></a>修改產生的文件執行個體  
  
1.  在文字編輯器 (如 [記事本]) 中開啟產生的文件執行個體，然後編輯文件執行個體的內容，以確保這些欄位中的資料會在 PeopleSoft 系統中產生唯一的記錄，例如，底下的 XML 檔案描述記錄中定義位置的欄位：  
  
    ```  
    <ns0:CreateEx xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
      <ns0:SETID>SHARE</ns0:SETID>  
      <ns0:LOCATION>9991</ns0:LOCATION>  
      <ns0:interactiveMode>true</ns0:interactiveMode>  
       <ns0:properties>  
        <ns0:LOCATION_TBL_sequence>  
          <ns0:LOCATION_TBL>  
            <ns0:COUNTRY>USA</ns0:COUNTRY>  
            <ns0:DESCR>Adapter Test</ns0:DESCR>  
            <ns0:EFFDT>2006-05-31</ns0:EFFDT>  
            <ns0:EFF_STATUS>A</ns0:EFF_STATUS>  
            <ns0:SETID>SHARE</ns0:SETID>  
          </ns0:LOCATION_TBL>  
        </ns0:LOCATION_TBL_sequence>  
      </ns0:properties>  
    </ns0:CreateEx>  
    ```  
  
    > [!NOTE]
    >  在上述範例*PeopleSoft*是配接器的實際名稱的預留位置，如 BizTalk 管理主控台中所示。  
  
2.  儲存已修改的文件執行個體。  
  
#### <a name="build-and-deploy-the-project"></a>建置和部署專案  
  
1.  以滑鼠右鍵按一下方案總管 中的 OneWaySend 專案，然後按一下**屬性**為啟動專案設計工具。  
  
2.  按一下**部署** 索引標籤。  
  
3.  輸入適當的值**伺服器**屬性和**組態資料庫**下的屬性**BizTalk 群組**。  
  
4.  以滑鼠右鍵按一下方案總管 中的 OneWaySend 專案，然後按一下**部署**建置專案並部署組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。  
  
#### <a name="bind-and-enlist-the-orchestration"></a>繫結和登錄協調流程  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。  
  
2.  按一下**重新整理**中 MMC 工具列或按下按鈕**F5**重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。  
  
3.  按兩下協調流程以顯示**協調流程屬性**對話方塊。  
  
4.  按一下**繫結**以顯示協調流程繫結選項 對話方塊的左窗格中。  
  
5.  指定適當的繫結選項值，例如：  
  
    |**參數**|**值**|  
    |-------------------|---------------|  
    |Host|BizTalkServerApplication|  
    |FileReceivePort|PeopleSoftOneWayFileRP|  
    |PeopleSoftOneWaySendPort|PeopleSoftOneWaySP|  
  
6.  按一下 [確定]。  
  
#### <a name="start-the-orchestration"></a>啟動協調流程  
  
-   在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，以滑鼠右鍵按一下協調流程，然後按一下**啟動**登錄並啟動協調流程。  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a>將文件執行個體拖放到檔案接收位置所監視的資料夾  
  
-   將稍早建立的文件執行個體複製到檔案接收位置依設定要監視的資料夾。  
  
#### <a name="verify-that-the-peoplesoft-system-is-updated"></a>確認 PeopleSoft 系統更新  
  
-   若要確認記錄已經建立的 XML 檔案中的資料使用 PeopleSoft web 介面。  
  
 如果文件執行個體處理成功，則會發生以下一系列的事件：  
  
1.  檔案配接器從資料夾擷取到檔案，並將其發佈到 MessageBox 做為 BizTalk 訊息。  
  
2.  協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程執行個體，然後將訊息傳送至這個協調流程執行個體。  
  
3.  協調流程執行個體使用指定的協調流程中的邏輯處理訊息，並將訊息發佈回 MessageBox。  
  
4.  PeopleSoft 傳送埠訂閱這個發佈訊息，因此 BizTalk 傳訊引擎將訊息傳送至 PeopleSoft 傳送埠。  
  
5.  傳送埠將訊息交給 BizTalk Adapter for PeopleSoft Enterprise。  
  
6.  BizTalk Adapter for PeopleSoft Enterprise 會叫用 CreateEx 方法，以建立使用 XML 檔案中的資料記錄。  
  
## <a name="see-also"></a>請參閱  
 [教學課程：使用 BizTalk Adapter for PeopleSoft Enterprise](../core/tutorials-using-biztalk-adapter-for-peoplesoft-enterprise.md)