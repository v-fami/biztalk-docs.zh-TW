---
title: "執行 JD Edwards OneWorld 範例查詢 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b060d383-a2df-472f-90cc-e79078b0bcfd
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58e06eb1b606217aea6fe5e40ac645a2eaf623c2
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="execute-a-jd-edwards-oneworld-sample-query"></a>執行 JD Edwards OneWorld 範例查詢
JD Edwards OneWorld (JDEOW) 系統是否可從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用 JD Edwards OneWorld 配接器的系統。 此配接器隨附於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。
  
 這是 JD Edwards OneWorld 實驗室工作的第二個部分。 在第一個部分 (實驗室 1) 中，您以手動方式存取的協助而 JD Edwards OneWorld 系統上的資料[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或其他 Microsoft 技術。 在這個部分 (實驗室 2) 中，您將建立 BizTalk 協調流程的一部分[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案。 您將使用 JD Edwards OneWorld 配接器從 JD Edwards OneWorld 系統取得資料的此協調流程上設定連接埠。  
  
## <a name="prerequisites"></a>必要條件  
  
-   Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]
  
-   Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 
  
-   JD Edwards OneWorld 用戶端軟體  
  
-   JD Edwards OneWorld 系統在另一部伺服器上的網路連線  
  
-   Microsoft BizTalk Adapters for Enterprise Applications  
  
> [!NOTE]
>  請參閱[安裝和設定為企業應用程式配接器](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md)JD Edwards、 PeopleSoft、 和 TIBCO 配接器的重要組態資訊。  
  
## <a name="lab-2---executing-a-jd-edwards-oneworld-sample-query"></a>實驗室 2 - 執行 JD Edwards OneWorld 範例查詢  
 在這個實驗室中，您將執行**取得**對 JD Edwards OneWorld 系統的作業。 也就是說，您將執行下列工作：  
  
-   確認 JD Edwards OneWorld 必要條件  
  
-   在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中設定 JD Edwards OneWorld 傳送埠  
  
-   建立 BizTalk 協調流程專案  
  
-   建置和部署專案  
  
-   測試應用程式並檢視 XML 輸出  
  
 您將會使用 JD Edwards OneWorld 配接器從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 存取 JD Edwards OneWorld 系統上的資料。  
  
 此配接器可用以使用協調流程執行的要求和回應，處理 JD Edwards OneWorld 物件。 對於結構描述物件，有許多方法可用。 這個實驗室會示範如何使用**Address Book MBF**方法。  
  
 執行服務要求之前，您必須針對特定 JD Edwards OneWorld 物件建立服務要求和回應結構描述。 新增產生的項目/新增配接器精靈會透過直接詢問 JD Edwards OneWorld 中的支援中繼資料物件，來建立這些結構描述。 此實驗室示範建立結構描述所需的步驟**Address Book MBF**方法和處理查詢。  
  
## <a name="step-1-verify-the-jd-edwards-oneworld-prerequisites"></a>步驟 1： 確認 JD Edwards OneWorld 必要條件  
 在您開始建立要與 JD Edwards OneWorld 配接器搭配使用的 BizTalk 專案之前，您必須確定已正確設定檔案和配接器，以便存取 JD Edwards OneWorld 系統。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上，JD Edwards OneWorld 配接器會利用 Java 介面與 JD Edwards OneWorld 系統通訊。    

1. 四個檔案所需的適當介面存取使用 JD Edwards OneWorld 配接器的 JD Edwards OneWorld 系統： Connector.jar、 Kernel.jar、 BTSLIBinterop.jar 及 JDEJAccess.jar。  
  
    -   Connector.jar 和 Kernel.jar 檔案來自 JD Edwards OneWorld 系統，可以向 JD Edwards OneWorld 系統管理員取得。 這些檔案都位於 C:\JDEOWJars 資料夾中。  
  
    -   BTSLIBinterop.jar 檔案是遵循配接器的《安裝指南》包含的指示後，由 JD Edwards OneWorld 系統所產生。 此檔案位於 C:\JDEOWJars 資料夾中。  
  
    -   JDEJAccess.jar 檔案是 JDEOW 配接器的一部分，因此會隨配接器的安裝而存在。 根據預設，它位於 C:\Program Files\Microsoft BizTalk Adapters for Enterprise applications\j.d.edwards。 Edwards OneWorld® \Classes 資料夾中。  
  
2. 確認 Connector.jar、 Kernel.jar，和 BTSLIBinterop.jar 檔案存在於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]C:\JDEOWJars 資料夾中的電腦。  
  
3. 確認 JDEJAccess.jar 檔案存在於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]C:\Program Files\Microsoft BizTalk Adapters for Enterprise applications\j.d.edwards 中的電腦。 Edwards OneWorld\Classes 資料夾。  
  
## <a name="step-2-configure-biztalk-send-ports"></a>步驟 2： 設定 BizTalk 傳送埠  
接下來，確認 JD Edwards OneWorld 配接器已安裝，且建立傳送埠。  

1.  開啟**BizTalk Server 管理**，依序展開**主控台根目錄**，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。  
  
    確認**JDE_OneWorld**列出配接器。 如果未安裝 JD Edwards OneWorld 配接器，請安裝 BizTalk Adapters for Enterprise Applications (請參閱稍早的「必要條件」一節)。 安裝配接器之後，以滑鼠右鍵按一下**配接器**，然後按一下**新增-配接器**安裝 JD Edwards OneWorld 配接器。 重新啟動主控件執行個體，這個值才會生效。  
  
2. 展開**應用程式**，然後展開**BizTalk Application 1**。  
  
3.  以滑鼠右鍵按一下**傳送埠**，按一下 **新增**，然後按一下**靜態請求-回應傳送埠**。這些欄位中輸入下列值：  
  
    1.  **名稱：**  `JDE_OneWorldPort`  
  
    2.  **類型：**  `JDE_OneWorld`  
  
    3.  **傳送處理常式：**  `BizTalkServerApplication`  
  
    4.  **傳送管線：**  `XMLTransmit`  
  
    5.  **接收管線：**  `XMLReceive`  
  
4.  按一下 [設定] ，然後輸入下列屬性值：  
  
    1.  **主機：** \<輸入 JDEOW 主控件名稱 >  
  
    2.  **JAVA_HOME:**`C:\j2sdk1.4.2_08`  
  
    3.  **JDEdwards 環境：** \<輸入 JDEOW 環境 >  
  
    4.  **JDEdwards JAR 檔案：** \<輸入 JAR 檔案的完整路徑 >  
  
         `C:\JDEOWJars\BTSLIBInterop.jar; C:\JDEOWJars\Connector.jar; C:\JDEOWJars\Kernel.jar;C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\J.D. Edwards OneWorld®\Classes\JDEJAccess.jar`  
  
    5.  **密碼：**使用下拉式清單，然後輸入 JD Edwards OneWorld 密碼。  
  
    6.  **連接埠：**  `6009`  
  
    7.  **使用者名稱：** \<輸入 JD Edwards 使用者名稱 >  
  
     ![](../core/media/jdeow-transportproperties-configurebutton.gif "JDEOW_TransportProperties_ConfigureButton")  
  
5.  選取**確定**關閉**傳送埠屬性**。  
  
## <a name="step-3-create-a-biztalk-orchestration-project"></a>步驟 3： 建立 BizTalk 協調流程專案  
接下來，建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，並在專案中，以處理之間的通訊設定協調流程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 JD Edwards OneWorld 系統。 您將新增傳送和接收埠、建置專案，然後部署專案。  

  
1.  開啟[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，並在 C:\LABS 資料夾中建立新的 BizTalk 專案。 在 [檔案]  功能表上，按一下 [新增] 。 [新增專案]  對話方塊隨即出現。 在 [傳送埠屬性]  區段下，選取 [空白 BizTalk Server 專案]  輸入`JDE_OW_Test`作為唯一的專案名稱，然後按一下**確定**。  
  
2.  在方案總管中，以滑鼠右鍵按一下專案，按一下 [新增] 及 [新增產生的項目] 。 在 [類別] 窗格中，選取**新增配接器中繼資料**，在 [範本] 窗格中，選取**新增配接器中繼資料**，然後按一下**新增**。  
  
3.  在 新增配接器精靈 中，選取  **JD Edwards OneWorld**配接器，選取**JDE_OneWorldPort**傳送您在先前程序中建立的連接埠，然後按一下**下一步**.  
  
     ![](../core/media/jdeow-addadapterwizardselectadapter.gif "JDEOW_AddAdapterWizardSelectAdapter")  
  
4.  在**選取要匯入服務**頁面上，開啟**JD Edwards OneWorld**。 系統隨即使用 BrowsingAgent 程式透過配接器聯繫 JDEOW 系統。 BrowsingAgent 會傳回下列服務。  
  
     ![](../core/media/jdeow-callbsfn.gif "JDEOW_CALLBSFN")  
  
5.  展開**[callbsfn]**向下捲動至**N0100041-Address Book MBF**。 選取 N0100041，然後按一下**完成**。  
  
6.  在 [方案總管] 中，沒有新的 BizTalk 協調流程含有兩個新的相關聯的結構描述檔案。 這些檔案是由 [新增配接器精靈] 所建立。 按兩下 BizTalk Orchestration.odx  檔案開啟協調流程。  
  
     ![](../core/media/jdeow-solution-explorer-jde-ow-test-schemas.gif "JDEOW_Solution_Explorer_JDE_OW_TEST_Schemas")  
  
 此協調流程接受做為從 JD Edwards OneWorld 系統的格式為 XML 檔案的 File 配接器的輸入。 協調流程會使用 JD Edwards OneWorld 配接器將 XML 檔案傳送至 JD Edwards OneWorld 系統。 JD Edwards OneWorld 會處理查詢，並且產生包含結果的輸出 XML 檔案。 此 XML 檔案會透過 JD Edwards OneWorld 配接器傳回至協調流程，然後 File 配接器會將 XML 檔案寫入至磁碟上的輸出位置。  
  
 若要完成協調流程，您需要建立及設定連接埠來接收和傳送 XML 檔案。 首先，設定 File 配接器要使用的接收埠，以將包含查詢的 XML 從磁碟輸入至協調流程。  
  
#### <a name="configure-a-receive-port-to-accept-the-input-xml-file"></a>設定接收埠以接受輸入的 XML 檔案  
  
1.  按兩下 BizTalk Orchestration.odx  檔案開啟協調流程。  
  
2.  在 BizTalk Orchestration.odx 檔內，以滑鼠右鍵按一下左連接埠介面，然後按一下**新設定連接埠**。 如此將啟動 [連接埠組態精靈]。 在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。  
  
3.  上**連接埠內容**頁面上，輸入`JDE_File_In`如**名稱**，然後按一下**下一步**。  
  
4.  在 [選取連接埠類型]  頁面上，選取 [建立新的連接埠類型] ，然後輸入或選取下列屬性值：  
  
     **連接埠類型名稱**:`JDE_FileIn_Port`  
  
     **通訊模式**： **單向**  
  
     **存取限制**： **內部 - 限制於此專案**  
  
5.  按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：  
  
     **連接埠通訊方向**： **我將總是在此連接埠接收訊息**  
  
     **連接埠繫結**： **稍後指定**  
  
6.  按 **[下一步]**，再按一下 **[完成]**。  
  
 接著，建立傳送/接收埠，以將包含查詢的初始 XML 輸入檔案傳送至 JD Edwards OneWorld 系統。 此連接埠也會接收 JD Edwards OneWorld 系統在收到呼叫後，所傳回之包含查詢結果的輸出 XML 檔案。  
  
#### <a name="configure-a-sendreceive-port-to-interface-with-jd-edwards-oneworld"></a>使用 JD Edwards OneWorld 設定介面傳送/接收埠  
  
1.  在 BizTalk Orchestration.odx 檔內，以滑鼠右鍵按一下右側連接埠介面，然後按一下**新設定連接埠**。 如此將啟動 [連接埠組態精靈]。 在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。  
  
2.  在 **[選取連接埠類型]** 頁面上，選取 **[使用現有連接埠類型]**。 在下**可用的連接埠類型**，選取**JD_OW_Test.N0100041**，然後按一下**下一步**。  
  
     ![](../core/media/a421358c-6e90-4fe0-b243-6beb1b51955a.gif "a421358c-6e90-4fe0-b243-6beb1b51955a")  
  
3.  選取下列屬性值：  
  
     **連接埠通訊方向**:**我要傳送要求並接收回應**  
  
     **連接埠繫結**： **稍後指定**  
  
4.  按 **[下一步]**，再按一下 **[完成]**。 您將會在連接埠介面上看到連接埠和可用的方法。  
  
 最後，設定 File 配接器要使用的傳送埠，以將包含查詢結果的 XML 輸出至磁碟。  
  
#### <a name="configure-a-send-port-to-output-the-xml-file-to-disk"></a>設定傳送埠輸出 XML 檔到磁碟  
  
1.  在 BizTalk Orchestration.odx 檔內，以滑鼠右鍵按一下左連接埠介面，然後按一下**新設定連接埠**。 如此將啟動 [連接埠組態精靈]。 在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。  
  
2.  上**連接埠內容**頁面上，輸入`JDE_FileOut`如**名稱**，然後按一下**下一步**。  
  
3.  在 [選取連接埠類型]  頁面上，選取 [建立新的連接埠類型] ，然後輸入或選取下列屬性值：  
  
     **連接埠類型名稱**:`JDE_FileOut_Port`  
  
     **通訊模式**： **單向**  
  
     **存取限制**： **內部 - 限制於此專案**  
  
4.  按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：  
  
     **連接埠通訊方向**： **我將總是在此連接埠傳送訊息**  
  
     **連接埠繫結**： **稍後指定**  
  
5.  按 **[下一步]**，再按一下 **[完成]**。  
  
 新的連接埠與 JD Edwards OneWorld 服務可用的方法，會顯示在連接埠介面上。 稍後您將指定的 JD Edwards OneWorld 配接器傳送和接收來自 JD Edwards OneWorld 系統的檔案。  
  
 **JDE_File_In**和**JDE_File_Out**您剛建立需要的連接埠關聯的訊息類型。  
  
#### <a name="assign-message-types-to-the-ports"></a>指派的連接埠的訊息類型  
  
1.  在左側連接埠介面上**JDE_File_In**通訊埠，請按一下**要求**。 在 [屬性] 視窗中，依序展開**訊息類型**，依序展開**多部分訊息**，然後按一下 **JDE_OW_TestAddressBookMasterMBF**。  
  
2.  在左側連接埠介面上**JDE_File_Out**通訊埠，請按一下**要求**。 在 [屬性] 視窗中，依序展開**訊息類型**，依序展開**多部分訊息**，然後按一下 **JDE_OW_TestAddressBookMasterMBFResponse**。  
  
 將兩個**傳送**圖形與兩個**接收**圖形至協調流程來連結至連接埠。  
  
#### <a name="add-send-and-receive-shapes"></a>新增傳送和接收圖形  
  
1.  從工具箱拖曳 **接收** 元件，緊解著將其放置於協調流程 (綠色圓形) 的開頭下方。 按一下**接收**圖形，然後在 [屬性] 視窗中，輸入`Get_File`如**名稱**，並設定**Activate**至`true`。 如此會在此接收埠收到內送文件時啟動協調流程。  
  
2.  拖曳**傳送**元件從工具箱拖曳並將它放在正下方**GetFileReceive**圖形。 按一下新**傳送**圖形，然後在 [屬性] 視窗中，輸入`SendToJDEOW`如**名稱**。  
  
3.  拖曳**接收**元件從工具箱拖曳並將它放在正下方**SendToJDEOWSend**圖形。 按一下**接收**圖形，然後在 [屬性] 視窗中，輸入`JDEOW_Resp`如**名稱**。  
  
4.  拖曳**傳送**元件從工具箱拖曳並將它放在正下方**JDEOW_RespReceive**圖形。 按一下新**傳送**圖形，然後在 [屬性] 視窗中，輸入`FileToDisk`如**名稱**。  
  
     ![](../core/media/jdeow-orchestration-multipartmessages.gif "JDEOW_Orchestration_MultiPartMessages")  
  
5.  連接**[jde_filein]**埠連接到**GetFileReceive**元件。  
  
6.  連接**JDE_FileOut**埠連接到**FileToDiskReceive**元件。  
  
7.  移至**協調流程檢視**展開**訊息**。 變更的識別項**Message_1**至`MsgToJDEOW`，以及**Message_2**至`JDEOW_Resp.`  
  
8.  反白顯示**SendToJDEOWSend**元件並設定其**訊息**屬性**MsgToJDEOW**。  
  
9. 反白顯示**JDEOW_RespReceive**元件並設定其**訊息**屬性**[jdeow_resp]**。  
  
10. 連接**[sendtojdeow]**至**要求**部分**JDE_OW_Port**連接埠。  
  
11. 連接**[jdeow_resp]**至**回應**部分**JDE_OW_Port**連接埠。  
  
     ![](../core/media/jdeow-portsurface-connectcomponentstoports.gif "JDEOW_PortSurface_ConnectComponentsToPorts")  
  
## <a name="step-4-build-and-deploy-the-project"></a>步驟 4： 建立和部署專案  
 現在 BizTalk 專案已完成，而且您可以建置並部署在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
1.  啟動**Visual Studio 命令提示字元**。  
  
2.  若要建置專案時，您會需要強式名稱金鑰檔。 在命令提示字元中，輸入下列命令以建立強式名稱金鑰檔：  
  
     **sn-k [labs.snk]**  
  
3.  在 [方案總管] 中，以滑鼠右鍵按一下**[jd_ow_test]**專案，然後再按一下**屬性**啟動專案的專案設計工具。  
  
4.  按一下 [ **簽署** ] 索引標籤。  
  
5.  選取 **[簽署組件]** 選項、按一下 **[選擇強式名稱金鑰檔]** 選項的下拉式清單，然後按一下 **[瀏覽]**。  
  
6.  瀏覽並選取金鑰檔： **[labs.snk]**，然後按一下 **[開啟]**。  
  
7.  按一下 [專案設計工具] 中的 **[部署]** 索引標籤。  
  
8.  設定**應用程式名稱**至`JDE_OW_Test`。  
  
9. 在 [方案總管] 中，以滑鼠右鍵按一下**JDE_OW_Test**專案，然後再按一下**建置。**  
  
     ![](../core/media/jdeow-buildcompleteoutput.gif "JDEOW_BuildCompleteOutput")  
  
10. 成功完成建置後，以滑鼠右鍵按一下**[XX_JD Edwards oneworldquery]**專案，然後再按一下**部署**。 在輸出視窗中會顯示下列輸出：  
  
     ![](../core/media/jdeow-deployoutput.gif "JDEOW_DeployOutput")  
  
## <a name="step-5-test-the-application-and-viewing-the-xml-output"></a>步驟 5： 測試應用程式並檢視 XML 輸出  
 現在您將測試所建立和部署的應用程式。 您會建立啟動協調流程處理序的 XML 檔案，然後設定在應用程式內接收和傳送 XML 檔案的資料夾。 設定應用程式之後，您將會執行它並檢視協調流程所傳回的 XML 檔案。  
  
#### <a name="generate-the-xml-file-for-the-query"></a>產生查詢的 XML 檔案  
  
1.  在 [方案總管] 中，按兩下**[n0100041service_n0100041.xsd]**開啟檔案。  
  
2.  以滑鼠右鍵按一下**[n0100041service_n0100041.xsd]** ，然後按一下**屬性**。 針對 **輸出執行個體檔案名稱** 輸入範例 XML 的下列路徑和檔案名稱：  
  
     `C:\LABS\JDE_OW_TEST\SAMPLE.XML`  
  
3.  按一下 **[確定].** 在 [屬性] 視窗中，選取**\<結構描述 >**並設定**根參考：**至`AddressBookMasterMBF`。 這會導致產生的 XML 只包含**查詢**xml。  
  
     ![](../core/media/jdeow-jde-ow-test-msvisualstudio-schemas.gif "JDEOW_JDE_OW_Test_MSVISUALSTUDIO_SCHEMAS")  
  
4.  以滑鼠右鍵按一下**[n0100041service_n0100041.xsd]** ，然後按一下**產生執行個體**。 這會產生**Sample.xml**檔案。 這個檔案將做為配接器的輸入，放置在接收位置以啟動協調流程處理序。  
  
#### <a name="configure-and-start-the-biztalk-application"></a>設定和啟動 BizTalk 應用程式  
  
1.  設定用於接收內送檔案及傳送外寄檔案的資料夾。 移至**C:\LABS\JDE_OW_Test**並建立兩個新子資料夾名為`FileIn`和`FileOut`。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**主控台根目錄**，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，展開**應用程式**。  
  
3.  以滑鼠右鍵按一下**JDE_OW_Test**，然後按一下**設定**。  
  
     ![](../core/media/jdeow-configureapplicationjde-ow-test.gif "JDEOW_ConfigureApplicationJDE_OW_Test")  
  
4.  選取 [Orchestration_1]  ，並按一下 [主機]  下拉式方塊。 選取 **BizTalkServerApplication**。  
  
5.  在下**接收埠**，按一下  **\<無 >**。 在下拉式清單中選取 [新增接收埠] 。  
  
6.  如**名稱**，型別`JDE_FileIn_Port`，然後按一下**確定**。 訊息方塊會出現，指出您需要指定接收位置。 按一下 [確定] 及 [新增] 。  
  
     ![](../core/media/jdeow-filein-port-receiveportproperties.gif "JDEOW_FileIn_Port_ReceivePortProperties")  
  
7.  輸入或選取屬性的下列值：  
  
     **名稱**: JDE_`FileInLoc`  
  
     **類型**： **檔案**  
  
     **接收處理常式**： **BizTalkServerApplication**  
  
     **接收管線**： **XMLReceive**  
  
     ![](../core/media/jdeow-filein-loc-receivelocationproperties.gif "JDEOW_FileIn_Loc_ReceiveLocationProperties")  
  
8.  按一下**設定**，型別`C:\LABS\JDE_OW_Test\FileIn`如**接收資料夾**，然後按一下**確定**三次。  
  
     ![](../core/media/jdeow-file-transport-properties-filein.gif "JDEOW_File_Transport_Properties_FileIn")  
  
9. 按一下**\<無 >**如**JDE_OW_Port**下拉式清單中。  
  
10. 選取**新傳送埠**然後選取或輸入下列值的屬性：  
  
     **名稱**:`JDE_OW_Port`  
  
     **型別**: **JDE_OneWorld**  
  
     **傳送處理常式**： **BizTalkServerApplication**  
  
     **管線**： **XMLTransmit** 和 **XMLReceive**  
  
11. 按一下 [設定] ，然後輸入下列屬性值：  
  
     **主機：** \<輸入 JDEOW 主控件名稱 >  
  
     **JAVA_HOME:**`C:\j2sdk1.4.2_08`  
  
     **JDEdwards 環境：** \<輸入 JDEOW 環境 >  
  
     **JDEdwards JAR 檔案：**<enter full path of JAR files>  
  
     `C:JDEOWJarsBTSLIBInterop.jar; C:JDEOWJarsConnector.jar; C:JDEOWJarsKernel.jar;C:Program FilesMicrosoft BizTalk Adapters for Enterprise ApplicationsJ.D. Edwards OneWorld®ClassesJDEJAccess.jar`  
  
     **密碼：**使用下拉式清單，然後輸入 JD Edwards OneWorld 密碼。  
  
     **連接埠：**  `6009`  
  
     **使用者名稱：**<enter your JD Edwards User Name>  
  
     ![](../core/media/jdeow-transportproperties-configurebutton2.gif "JDEOW_TransportProperties_ConfigureButton2")  
  
12. 按兩下 [確定]  關閉對話方塊。  
  
13. 在 設定 Applicationwindow 中，按一下  **\<無 >**如**JDE_FileOut**下拉式清單中。  
  
14. 選取 [新增傳送埠]  ，然後選取或輸入下列屬性值：  
  
     **名稱**:`FileOutPort`  
  
     **類型**： **檔案**  
  
     **傳送處理常式**： **BizTalkServerApplication**  
  
     **傳送管線**： **XMLTransmit**  
  
15. 按一下**設定**和型別`C:\Labs\JDE_OW_Test\FileOut`如**目的地資料夾。** 保留**%MessageID%.xml**如**檔案名稱**因為這會產生唯一的檔案，每個訊息。  
  
     ![](../core/media/jdeow-file-transport-properties-fileout.gif "JDEOW_File_Transport_Properties_FileOut")  
  
16. 按三下 [確定]  關閉對話方塊。  
  
17. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下滑鼠右鍵**JDE_OW_Test**應用程式，，然後按一下**啟動**。  
  
#### <a name="test-the-orchestration"></a>測試協調流程  
  
1.  在**C:\Labs\JDE_OW_Test**目錄**Sample.xml**檔案將會顯示為：  
  
     ![](../core/media/jdeow-samplexml-notepad-addressbookmastermbf.gif "JDEOW_SampleXML_Notepad_AddressBookMasterMBF")  
  
2.  編輯**Sample.xml**移除以外的所有內容檔案**cActionCode**和**mnAddressBookNumber**項目。  
  
     ![](../core/media/jdeow-samplexml-notepad-cactioncode.gif "JDEOW_SampleXML_Notepad_cActionCode")  
  
3.  如**cActionCode**項目插入字母`i`。  
  
4.  如**mnAddressBookNumber**插入數`500`。  
  
5.  儲存變更，並將檔案複製到**C:\Labs\JDE_OW_Test\FileIn**資料夾。 這是啟動協調流程程序的接收位置。  
  
6.  在幾秒鐘，XML 檔案應該會出現在**C:\Labs\JDE_OW_Test\FileOut**資料夾。 這包含所有記錄的位址是 500。  
  
     ![](../core/media/jdeow-xml-output-jde-callbsfn.gif "JDEOW_XML_Output_JDE_CALLBSFN")  
  
     這個傳回的記錄資料應符合針對在實驗室 1 中的 JD Edwards OneWorld 系統查詢所傳回的資料。 藉由比較您在實驗室 1 中取得的記錄，您可以確認**取得**方法運作正常。  
  
## <a name="summary"></a>摘要  
 在此實驗室中，您先確認了必要條件已正確設定，以便存取 JD Edwards OneWorld 系統。 之後，使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]來建立新的 BizTalk 專案包含協調流程。 您會設定 BizTalk 協調流程，以使用 JD Edwards OneWorld 配接器自 JD Edwards OneWorld 系統取得資料。 為了設定協調流程，您建立了傳送、接收與傳送/接收埠。 您的 JD Edwards OneWorld 配接器，繫結這些連接埠，並指派訊息到適當的連接埠。  
  
 當您完成 BizTalk 專案之後，您使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]建置和部署它。 然後設定新的應用程式，並加以執行，以從 JD Edwards OneWorld 系統取得資料。 為了確定應用程式正確運作，您將其輸出 XML 檔與實驗室 1 中自 JD Edwards OneWorld 系統中接收的檔案做比較。