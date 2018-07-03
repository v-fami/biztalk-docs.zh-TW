---
title: 教學課程： 使用 BizTalk Adapter for PeopleSoft Enterprise 從 PeopleSoft Enterprise 中擷取資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c173fa4c-911e-4fa3-813f-e8f36b0049a5
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9728e642a1ad9e03e550a652757d33038cbab79d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993423"
---
# <a name="tutorial-using-the-biztalk-adapter-for-peoplesoft-enterprise-to-retrieve-data-from-peoplesoft-enterprise"></a>教學課程：使用 BizTalk Adapter for PeopleSoft Enterprise 從 PeopleSoft Enterprise 中擷取資料
BizTalk Adapter for PeopleSoft Enterprise 可用來對 PeopleSoft 系統執行查詢，並傳回查詢的結果。 這個逐步解說將說明此功能的 SDK 範例。  

## <a name="prerequisites"></a>必要條件  

- 執行 BizTalk Adapter for PeopleSoft Enterprise Geis 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上必須已安裝 Java 2 平台。  

- PeopleSoft Java Object Adapter JAR 檔案中， **psjoa.jar**應複製到可存取的資料夾[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上執行 BizTalk Adapter for PeopleSoft Enterprise。  

- 執行 BizTalk Adapter for PeopleSoft Enterprise 的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上必須已安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。  

## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會從某個資料夾收取某個 XML 檔案、將該檔案傳送至協調流程，然後使用 BizTalk Adapter for PeopleSoft Enterprise 對 PeopleSoft 系統執行查詢。 查詢的結果會寫入至 XML 檔案。  

## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 以 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 設計的這個範例，其建立的目的在示範將 BizTalk Adapter for PeopleSoft Enterprise 與 BizTalk 協調流程搭配使用的基本功能。  

## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這個範例位於下列資料夾：  

 \Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Sdk\PeopleSoftTwoWaySend  

 下表顯示此範例中的檔案，並描述其用途。  


|                               **執行階段專案檔案名稱**                                |                                                                                                                                                                           **執行階段專案檔案描述**                                                                                                                                                                            |
|-------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                       TwoWaySend.btproj、<br /><br /> TwoWaySend.sln                       |                                                                                                                                                                      應用程式的專案和方案檔。                                                                                                                                                                      |
| LOCATIONService.xsd、<br /><br /> LOCATIONService_1.xsd、<br /><br /> LOCATIONService_2.xsd | 這個應用程式的結構描述檔案。 **注意︰** 專案中的配接器結構描述檔案最初建立使用**新增配接器中繼資料精靈**。 如需 [新增配接器中繼資料精靈] 的詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的「如何將配接器中繼資料新增至 BizTalk 專案」主題。 |
|                                 PeopleSoftTwoWaySend.odx                                  |                                                                                                                                                                        這個應用程式使用的協調流程。                                                                                                                                                                         |
|                                 PeopleSoftTwoWaySend.snk                                  |                                                                                                                                                                                強式命名金鑰檔。                                                                                                                                                                                |

## <a name="how-to-use-this-sample"></a>如何使用此範例  

#### <a name="create-a-new-instance-of-the-peoplesoft-enterprise-adapter"></a>建立 PeopleSoft Enterprise 配接器的新執行個體  

1. 啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。 按一下 **開始**，**程式**， **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]， **BizTalk Server 管理**。  

2. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 [ **配接器**。  

3. 以滑鼠右鍵按一下**配接器**，指向**新增**，**配接器**以顯示**配接器屬性**對話方塊。  

4. 輸入的值**名稱**欄位，例如**PeopleSoft**。  

5. 選取**PeopleSoft enterprise （)** 從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。  

#### <a name="create-a-solicit-response-biztalk-send-port"></a>建立請求-回應 BizTalk 傳送埠  

1. 在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。  

2. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，**靜態請求-回應傳送埠**以顯示**傳送埠屬性**對話方塊。  

3. 輸入的值**名稱**欄位，例如**PeopleSoftTwoWaySP**。  

4. 從可用配接器清單中選取 PeopleSoft 配接器**型別**下拉式清單方塊，然後按一下**設定** 按鈕以顯示配接器**傳輸屬性** 對話方塊。  

   > [!NOTE]
   >  這個值是在管理主控台中建立 PeopleSoft Enterprise 配接器時指定的名稱。  

5. 輸入下列值**配接器必要屬性**:  


   |       **屬性**       |                                                                                                                                        **ReplTest1**                                                                                                                                         |
   |--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | 應用程式伺服器路徑  | PeopleSoft 伺服器的機器與連接埠位置，例如 //PSServer:8888。 **注意：** 以便在上面的範例可以輸入 //PSServer 值如果 PeopleSoft 伺服器使用預設的連接埠值 9000，如果您未指定連接埠號碼，使用預設連接埠 9000。 |
   |        JAVA_HOME         |                                                                                          與 Java 2 平台 SDK 檔案相關聯之主目錄的路徑，例如 C:\j2sdk1.4.2_08                                                                                          |
   |         [密碼]         |                                                                                                                 連接至 PeopleSoft 系統時使用的密碼。                                                                                                                  |
   | PeopleSoft 8.x JAR 檔案 |                                                                                          PeopleSoft Java Object Adapter JAR 檔案中，位置**psjoa.jar**，例如 C:\JARS\psjoa.jar。                                                                                          |
   |        [使用者名稱]         |                                                                                                                    用於連接至 PeopleSoft 系統的使用者名稱。                                                                                                                     |


6. 按一下 [確定] 。  

7. 選取  **XMLTransmit**從清單中可用的管線的管線**傳送管線**下拉式清單。  

8. 選取  **XMLReceive**從清單中可用的管線的管線**接收管線**下拉式清單中，按一下 **確定**。  

9. 以滑鼠右鍵按一下傳送埠，然後按一下 **啟動**登錄並啟動傳送埠。  

#### <a name="create-a-one-way-biztalk-send-port"></a>建立單向 BizTalk 傳送埠  

1. 建立傳送埠所要使用的目標資料夾，例如 C:\Files\Out。  

2. 在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。  

3. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，**靜態單向傳送埠**以顯示**傳送埠屬性**對話方塊。  

4. 輸入的值**名稱**欄位，例如**PeopleSoftTwoWayFileSP**。  

5. 選取 **檔案**從清單中的可用配接器**型別**下拉式清單方塊，然後按一下**設定** 按鈕以顯示配接器**傳輸屬性** 對話方塊。  

6. 輸入您稍早建立的資料夾的位置**目的地資料夾**屬性，然後按一下**確定**。  

7. 選取  **XMLTransmit**從清單中可用的管線的管線**傳送管線**下拉式清單中，按一下 **確定**。  

8. 以滑鼠右鍵按一下傳送埠，然後按一下 **啟動**登錄並啟動傳送埠。  

#### <a name="create-a-file-receive-port"></a>建立檔案接收埠  

1. 在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**接收埠**。  

2. 以滑鼠右鍵按一下接收埠 資料夾，然後按一下**的新**，**單向接收埠**以顯示 接收埠屬性 對話方塊。  

3. 輸入的值**名稱**欄位，例如**PeopleSoftTwoWayFileRP**，然後按一下**確定**。  

#### <a name="create-a-file-receive-location"></a>建立檔案接收位置  

1.  建立要由檔案接收位置監視的資料夾，例如 C:\Files\In。  

2.  以滑鼠右鍵按一下新的接收埠，然後按一下**的新**，**接收位置**以顯示**接收位置屬性**對話方塊。  

3.  輸入的值**名稱**欄位，例如**PeopleSoftTwoWayFileRL**。  

4.  選取 **檔案**從清單中的可用配接器**型別**下拉式清單方塊，然後按一下**設定** 按鈕以顯示配接器**傳輸屬性** 對話方塊。  

5.  輸入您稍早建立的資料夾的位置**接收資料夾**屬性，然後按一下**確定**。  

6.  選取  **XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。  

7.  以滑鼠右鍵按一下接收位置，然後按一下 **啟用**。  

#### <a name="modify-the-adapter-schema-target-namespace-property"></a>修改配接器結構描述目標命名空間屬性  

1. 啟動 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 並開啟 TwoWaySend.sln。 按一下 **檔案**，**開放**，**專案/方案**以顯示**開啟專案**對話方塊。  

2. 瀏覽到 TwoWaySend.sln 檔案，請按一下以選取此檔案，然後按一下**開啟**來開啟包含範例專案的方案。  

3. 按一下 [**檢視**功能表，然後選取**方案總管] 中**以顯示 [方案總管]。  

4. 按兩下 [方案總管] 中的 LOCATIONService_1.xsd 檔案加以開啟。  

5. 以滑鼠右鍵按一下**結構描述**節點的 LOCATIONService_1.xsd，然後選取**屬性**功能表選項以顯示結構描述的屬性。  

6. 編輯**目標命名空間**屬性，以使用適當的值做為配接器名稱，例如**目標命名空間**屬性應該讀取，如下所示：  

   ```  
   http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]  
   ```  

    何處*PeopleSoft*是 PeopleSoft 配接器的名稱中所示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

   > [!IMPORTANT]
   >  如果設定的值，如**目標命名空間**不符合輸入文件執行個體中指定，則處理輸入文件執行個體時，會發生路由失敗的命名空間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  

#### <a name="generate-a-document-instance-from-the-adapter-schema"></a>從配接器結構描述產生文件執行個體  

1.  按兩下**LOCATIONService_1.xsd**結構描述編輯器中開啟檔案的方案總管 中。  

2.  以滑鼠右鍵按一下**\<結構描述\>** 節點在結構描述編輯器，然後按一下 **屬性**顯示節點的屬性。  

3.  選取 **取得**從清單中的可用節點**根參考**下拉式方塊。 這應該如此一來，當您產生範例文件執行個體時它會從**取得**的結構描述的節點。  

4.  以滑鼠右鍵按一下**LOCATIONService_1.xsd**在 [方案總管]，然後按一下**屬性**顯示在 [屬性] 視窗中的屬性。  

5.  在 [屬性] 視窗中，按一下以選取**輸出執行個體檔案名稱**選項。  

6.  按一下省略符號按鈕 （...） 以顯示**選取輸出檔案**對話方塊。  

7.  指定的資料夾，然後輸出檔案執行個體名稱，例如**C:\instance.xml**然後按一下**儲存**。  

    > [!NOTE]
    >  請勿在這裡指定剛才針對檔案接收位置指定的資料夾位置。  

8.  以滑鼠右鍵按一下 方案總管 中的 LOCATIONService_1.xsd，然後按一下 **產生的執行個體**產生文件執行個體中指定的位置。  

9. 以滑鼠右鍵按一下**\<結構描述\>** 節點在結構描述編輯器，然後按一下 **屬性**以顯示節點的屬性。  

10. 選取 (**預設值)** 從清單中的可用節點**根參考**下拉式方塊。  

#### <a name="modify-the-generated-document-instance"></a>修改產生的文件執行個體  

1.  在文字編輯器 (如 [記事本]) 中開啟產生的文件執行個體，然後編輯文件執行個體的內容，以確保這些欄位中的資料會傳回現有的記錄：  

    ```  
    <ns0:Get xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
    <ns0:SETID>SHARE</ns0:SETID>  
    <ns0:LOCATION>WFKLOC</ns0:LOCATION>  
    <ns0:getHistory>true</ns0:getHistory>  
    </ns0:Get>  
    ```  

    > [!NOTE]
    >  在上述範例*PeopleSoft*是配接器的實際名稱的預留位置，「 BizTalk 管理主控台中所示。 *共用*並*WFKLOC*都是用來識別特定資料錄 PeopleSoft 系統中值的預留位置。  

2.  儲存已修改的文件執行個體。  

#### <a name="build-and-deploy-the-project"></a>建置和部署專案  

1. 以滑鼠右鍵按一下方案總管] 中的 TwoWaySend 專案，然後按一下 [**屬性**來顯示專案的專案設計工具。  

2. 按一下 **部署**專案設計工具中的索引標籤。  

3. 輸入適當的值，如**伺服器**屬性並**組態資料庫**下的屬性**BizTalk 群組**。  

4. 以滑鼠右鍵按一下方案總管] 中的 TwoWaySend 專案，然後按一下 [ **Deploy**以建置專案並部署組件，以[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。  

#### <a name="bind-and-enlist-the-orchestration"></a>繫結和登錄協調流程  

1. 在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。  

2. 按一下 **重新整理**按鈕[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台工具列或按下**F5**若要重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。  

3. 按兩下協調流程，以顯示**協調流程屬性**對話方塊。  

4. 按一下 [**繫結**以顯示協調流程繫結選項] 對話方塊的左窗格中。  

5. 指定適當的繫結選項值，例如：  


   |      **參數**      |        **ReplTest1**         |
   |-------------------------|--------------------------|
   |          Host           | BizTalkServerApplication |
   |     FileReceivePort     |  PeopleSoftTwoWayFileRP  |
   | PeopleSoftTwoWaySend678 |    PeopleSoftTwoWaySP    |
   |      ResponsePort       |  PeopleSoftTwoWayFileSP  |


6. 按一下 [確定]。  

#### <a name="start-the-orchestration"></a>啟動協調流程  

- 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下協調流程，然後按一下**啟動**登錄並啟動協調流程。  

#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a>將文件執行個體拖放到檔案接收位置所監視的資料夾  

-   將稍早建立的文件執行個體複製到檔案接收位置依設定要監視的資料夾。  

#### <a name="verify-that-the-document-instance-was-processed-by-the-biztalk-adapter-for-peoplesoft-enterprise"></a>確認文件執行個體已由 BizTalk Adapter for PeopleSoft Enterprise 進行處理  

- 開啟檔案傳送埠進行傳送時依設定要使用的目標資料夾，然後確認已產生輸出文件。 此檔案應包含 BizTalk Adapter for PeopleSoft Enterprise 處理查詢的結果。  

  如果文件執行個體處理成功，則會發生以下一系列的事件：  

1.  檔案配接器從資料夾擷取到檔案，並將其發佈到 MessageBox 做為 BizTalk 訊息。  

2.  協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程的執行個體，然後將訊息傳送至這個協調流程執行個體。  

3.  協調流程執行個體將訊息發佈回 MessageBox。  

4.  請求-回應傳送埠訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會將訊息傳送至 PeopleSoft 傳送埠。  

5.  傳送埠將訊息交給 BizTalk Adapter for PeopleSoft Enterprise。  

6.  BizTalk Adapter for PeopleSoft Enterprise 使用輸入檔中定義的參數，對 PeopleSoft 系統執行 Get 陳述式。  

7.  BizTalk Adapter for PeopleSoft Enterprise 傳回 Get 陳述式的結果，做為協調流程中「請求-回應」連接埠的回應訊息。  

8.  協調流程將結果集發佈至 MessageBox。  

9. 檔案傳送埠訂閱這個訊息，因此 BizTalk 會將訊息傳送至檔案配接器。  

10. 檔案配接器將包含結果集的訊息寫入至指定的輸出資料夾。  

## <a name="see-also"></a>另請參閱  
 [教學課程：使用 BizTalk Adapter for PeopleSoft Enterprise](../core/tutorials-using-biztalk-adapter-for-peoplesoft-enterprise.md)