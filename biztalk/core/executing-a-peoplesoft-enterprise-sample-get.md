---
title: 執行 PeopleSoft Enterprise 範例 Get |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb54f14c-3fce-44d6-91bb-cb1ca38a20da
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29cf6bba03e6a43bb3fdedf0742741e48ac22dd6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="execute-a-peoplesoft-enterprise-sample-get"></a>執行 PeopleSoft Enterprise 的 Get 範例
您可以從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統使用 PeopleSoft 配接器存取 PeopleSoft 系統。 此配接器隨附於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。
  
 這是 PeopleSoft 實驗室工作的第二個部分。 在第一個部分 (實驗室 1) 中，您以手動方式存取及修改 PeopleSoft 系統的協助而資料[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或其他 Microsoft 技術。 在這個部分 (實驗室 2) 中，您將建立 BizTalk 協調流程的一部分[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案。 您將設定此協調流程上的連接埠，以使用 PeopleSoft 配接器自 PeopleSoft 系統取得資料。  
  
## <a name="prerequisites"></a>必要條件  
  
-   Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]
  
-   Microsoft BizTalk Adapters for Enterprise Applications  
  
-   Microsoft Visual Studio  
  
-   Sun Systems Java Development Kit (JDK) 1.4 (含) 以上版本  
  
> [!NOTE]
>  請參閱[安裝和設定為企業應用程式配接器](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md)JD Edwards、 PeopleSoft、 和 TIBCO 配接器的重要組態資訊。  
  
## <a name="lab-2---executing-a-peoplesoft-sample-get"></a>實驗室 2 - 執行 PeopleSoft 的 Get 範例  
 在這個實驗室中，您將針對 PeopleSoft 系統執行 **Get** 作業。 也就是說，您將執行下列工作：  
  
-   驗證 PeopleSoft 必要條件  
  
-   設定中的 PeopleSoft 傳送埠 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   建立 BizTalk 協調流程專案  
  
-   建置和部署專案  
  
-   測試應用程式並檢視 XML 輸出  
  
## <a name="procedures-for-lab-2--executing-a-peoplesoft-sample-get"></a>實驗室 2 程序 - 執行 PeopleSoft 的 Get 範例  
 PeopleSoft 系統的適當介面存取需要兩個檔案：PSJOA.JAR 和 GET_CI_INFO.PC。 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，PeopleSoft 配接器進行通訊與 PeopleSoft 系統使用 PeopleSoft Java 介面。 此介面是由 PSJOA.JAR 檔案所提供。 置入此檔案的副本[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]通常來自所存取之 PeopleSoft 伺服器系統的系統管理員。 在此實驗室中，一份 PSJOA。JAR 上的 C:\PSJars\Ver841\ 資料夾中有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 此檔案的位置是在 PeopleSoft 配接器組態屬性中所指定。  
  
 PeopleSoft 系統本身必須安裝自訂元件介面 (CI)。 這可讓配接器在配接器組態期間瀏覽 PeopleSoft 物件。 呼叫自訂元件介面 (從 [新增產生的項目] 步驟中) 可取得可存取 PeopleSoft 物件的清單。 這些物件會判斷提供給用戶端系統的 PeopleSoft 公開功能。  
  
 特別是自訂元件 GET_CI_INFO，必須在初始安裝期間安裝於 PeopleSoft 系統上。 您可以修改這個檔案以限制 GET_CI_INFO 所公開的項目 (預設會公開 PeopleSoft 系統內的所有元件介面)。 其來源位於下列預設位置中的 GET_CI_INFO 文字檔：  
  
 **Enterprise Applications\PeopleSoft Enterprise(r) \Config 的 C:\Program Files\Microsoft BizTalk 配接器**  
  
 提供有關安裝至 PeopleSoft GET_CI_INFO 元件介面的一般指示[安裝和設定為企業應用程式配接器](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md)。 這些指示適用於經驗豐富的 PeopleSoft 系統管理員。  
  
## <a name="step-1-confirm-the-peoplesoft-rerequisites"></a>步驟 1： 確認 PeopleSoft rerequisites  
 在您開始建立搭配 PeopleSoft 配接器使用的 BizTalk 專案之前，必須先確定所有事項都已正確設定，以便存取 PeopleSoft。  
  
1.  確認 PSJOA。JAR 檔案存在於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]的 C:\psjars\ver841 資料夾中的電腦。 (這個檔案可以位於另一個位置[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 在下方提供的組態中，會假設檔案是在這個位置。)  
  
2.  確認 get_ci_info.pc 檔案位於 C:\Program Files\Microsoft BizTalk Adapters，enterprise \Config 資料夾。  
  
3.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**管理**，依序展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。 請確定已安裝 PeopleSoft 配接器，並且出現在清單上。  
  
     如果未安裝 PeopleSoft 配接器，請安裝 BizTalk Adapters for Enterprise Applications (請參閱稍早的＜必要條件＞一節)。 安裝配接器之後，用滑鼠右鍵按一下 [配接器]  ，然後按一下 [新增 - 配接器]  安裝 PeopleSoft 配接器。 重新啟動主控件執行個體，這個值才會生效。  
  
## <a name="step-2-create-a-send-port-for-peoplesoft"></a>步驟 2： 建立 peoplesoft 傳送埠  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須有要用來與 PeopleSoft 系統通訊的傳送埠。 此傳送埠最終會繫結至協調流程的邏輯連接埠。  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**主控台根目錄**，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，展開**應用程式**，然後展開**BizTalk.EnterpriseApplication。**  
  
2.  用滑鼠右鍵按一下 [傳送埠] ，再按一下 [新增] ，然後選取 [靜態請求-回應傳送埠] 。 在 [傳送埠屬性]  對話方塊中輸入屬性的下列值：  
  
    1.  **名稱︰**  `PeopleSoftSamplePort`  
  
    2.  **類型︰**  `PeopleSoft`  
  
    3.  **傳送處理常式︰**  `BizTalkServerApplication`  
  
    4.  **傳送管線︰**  `XMLTransmit`  
  
    5.  **接收管線︰**  `XMLReceive`  
  
3.  按一下 [設定] ，然後輸入下列屬性值：  
  
    1.  **應用程式伺服器路徑**： **//Servername:9000**  
  
         Servername 是您的應用程式伺服器。 這是此 PeopleSoft 系統的特定伺服器名稱或 IP 位址以及連接埠號碼。  
  
    2.  **JAVA_HOME**： **C:\J2SDK1.4.2_08**  
  
         這個路徑是特定上的 Java SDK 安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
    3.  **密碼**:\<輸入您的 PeopleSoft 密碼\>  
  
    4.  **PeopleSoft 8.x JAR 檔案**： **C:\PSJARS\VER841\PSJOA.JAR**  
  
    5.  **使用者名稱：** \<輸入您的 PeopleSoft Userid>\>  
  
     ![](../core/media/7bf30707-c7c6-409f-af18-9c9dfeb0de58.gif "7bf30707-c7c6-409f-af18-9c9dfeb0de58")  
  
4.  按兩下 [確定]  關閉對話方塊。  
  
## <a name="step-3-create-a-biztalk-orchestration-project"></a>步驟 3： 建立 BizTalk 協調流程專案  
 現在您將建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]和處理之間的通訊專案中設定協調流程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 PeopleSoft 系統。 您將新增傳送和接收埠、建置專案，然後部署專案。  
  
1.  開啟[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]並在 C:\LABS 資料夾中建立新的 BizTalk 專案。 在 [檔案]  功能表上，按一下 [新增] 。 [新增專案]  對話方塊隨即出現。 在 [傳送埠屬性]  區段下，選取 [空白 BizTalk Server 專案]  。輸入 `PS_Test` 做為唯一的專案名稱，然後按一下 [確定] 使用的八個企業營運系統 (LOB) 配接器之一。  
  
2.  在方案總管中，以滑鼠右鍵按一下專案，按一下 [新增] 及 [新增產生的項目] 。 在 [類別]  窗格中選取 [新增配接器中繼資料]  ，在 [範本]  側選取 [新增配接器中繼資料]  ，然後按一下 [新增] 。  
  
3.  在 [新增配接器精靈] 中，選取 [PeopleSoft Enterprise]  配接器，選取您在先前程序中所建立的 [PeopleSoftSamplePort]  傳送埠，然後按 [下一步] 。  
  
     ![](../core/media/ed0dedc5-a8fb-444c-b884-e310cf56462c.gif "ed0dedc5-a8fb-444c-b884-e310cf56462c")  
  
4.  在 [選取要匯入服務]  頁面上，展開 [PeopleSoft] ，然後展開 [CI] 。  
  
     PeopleSoft 系統是由使用瀏覽代理程式的配接器所查核。 當您展開 [CI] 時，BrowsingAgent.exe 處理序會啟動 (您可以將其視為在工作管理員中執行) 並傳回如下圖所示的服務。  
  
     ![](../core/media/6988104c-6483-4df2-a637-3301628ea665.gif "6988104c-6483-4df2-a637-3301628ea665")  
  
    > [!NOTE]
    >  從您的 PeopleSoft 系統取得及顯示的 PeopleSoft 服務，可能與此處顯示的服務稍有不同。  
  
5.  向下捲動，選取 [位置] ，然後按一下 [完成] 。  
  
     ![](../core/media/0506affd-3caa-47cb-9c25-f49c8a0ad614.gif "0506affd-3caa-47cb-9c25-f49c8a0ad614")  
  
6.  在方案總管中，有新的 BizTalk 協調流程和兩個新的相關聯結構描述檔案。 這些檔案是由 [新增配接器精靈] 所建立。 按兩下 [BizTalk Orchestration.odx]  檔案開啟協調流程。  
  
     ![](../core/media/825c5690-78eb-4048-9a47-cd3fc7310b7b.gif "825c5690-78eb-4048-9a47-cd3fc7310b7b")  
  
 此協調流程以輸入形式接受 XML 檔案格式針對 PeopleSoft **Get** 方法格式化，以及將 XML 檔案傳送至 PeopleSoft 系統。 **Get** 方法會從 PeopleSoft 系統擷取位置資訊，並將它傳回至 BizTalk 協調流程。 協調流程會使用連接埠來協助與配接器和 PeopleSoft 系統的通訊。 您將在此處設定的連接埠是用於接收和傳送 XML 檔案。 外寄的 XML 檔案會告知 PeopleSoft 系統這是 **Get** 作業。 內送的 XML 檔案會將位置資訊傳回至協調流程。  
  
 若要完成協調流程，您需要建立及設定連接埠來接收和傳送 XML 檔案。 首先，設定可接受初始 XML 輸入檔案的新接收埠 (其中包含 **Get** 方法)，來啟動協調流程。  
  
#### <a name="configure-a-receive-port"></a>設定接收埠  
  
1.  在您上一個步驟中開啟的 BizTalk Orchestration.odx 檔案內，以滑鼠右鍵按一下左側連接埠介面，然後按一下 [新設定連接埠] 。 如此將啟動 [連接埠組態精靈]。 在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。  
  
2.  在 **[連接埠屬性]** 頁面上的 `FileIn` 中輸入 **[FileIn]**，然後按一下 [BizTalk Server 管理] 使用的八個企業營運系統 (LOB) 配接器之一。  
  
3.  在 [選取連接埠類型]  頁面上，選取 [建立新的連接埠類型] ，然後輸入或選取下列屬性值：  
  
     **連接埠類型名稱**: `FileInPort`  
  
     **通訊模式**： **單向**  
  
     **存取限制**： **內部 - 限制於此專案**  
  
4.  按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：  
  
     **連接埠通訊方向**： **我將總是在此連接埠接收訊息**  
  
     **連接埠繫結**： **稍後指定**  
  
5.  按 **[下一步]**，再按一下 **[完成]**。 您將使用 FILE 配接器，來接受此檔案為來自磁碟的輸入。  
  
 接下來，建立傳送埠以接受包含呼叫 PeopleSoft **Get** 方法所得位置的 XML 檔案。 協調流程會使用 FILE 配接器，經由此傳送埠將該 XML 檔案寫入磁碟。  
  
#### <a name="configure-a-send-port"></a>設定傳送埠  
  
1.  在 BizTalk Orchestration.odx 檔案內，以滑鼠右鍵按一下左側連接埠介面，然後按一下 [新設定連接埠] 。 如此將啟動 [連接埠組態精靈]。 在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。  
  
2.  在 **[連接埠屬性]** 頁面上的 `FileOut` 中輸入 **[FileIn]**，然後按一下 [BizTalk Server 管理] 使用的八個企業營運系統 (LOB) 配接器之一。  
  
3.  在 [選取連接埠類型]  頁面上，選取 [建立新的連接埠類型] ，然後輸入或選取下列屬性值：  
  
     **連接埠類型名稱**: `FileOutPort`  
  
     **通訊模式**： **單向**  
  
     **存取限制**： **內部 - 限制於此專案**  
  
4.  按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：  
  
     **連接埠通訊方向**： **我將總是在此連接埠傳送訊息**  
  
     **連接埠繫結**： **稍後指定**  
  
5.  按 **[下一步]**，再按一下 **[完成]**。  
  
 最後，建立傳送/接收埠，以將包含 **Get** 方法的初始 XML 輸入檔案傳送至 PeopleSoft 系統。 此連接埠也會接收包含 PeopleSoft 系統上 **Get** 方法呼叫所得位置資訊的 XML 檔案。  
  
#### <a name="configure-a-sendreceive-port"></a>設定傳送/接收埠  
  
1.  在 BizTalk Orchestration.odx 檔案內，以滑鼠右鍵按一下右側連接埠介面，然後按一下 [新設定連接埠] 。 如此將啟動 [連接埠組態精靈]。 在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。  
  
2.  在 **[連接埠屬性]** 頁面上的 `PeopleSoft_Port` 中輸入 **[FileIn]**，然後按一下 [BizTalk Server 管理] 使用的八個企業營運系統 (LOB) 配接器之一。  
  
3.  在 **[選取連接埠類型]** 頁面上，選取 **[使用現有連接埠類型]**。 針對 [可用的連接埠類型] ，選取 [PS_Test.LOCATION] ，然後按 [下一步] 。  
  
     ![](../core/media/d8b443ec-294d-4124-a29d-aeb42bbb107e.gif "d8b443ec-294d-4124-a29d-aeb42bbb107e")  
  
4.  按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：  
  
     **連接埠通訊方向**： **我將總是傳送要求並接收回應**  
  
     **連接埠繫結**： **稍後指定**  
  
5.  按 **[下一步]**，再按一下 **[完成]**。  
  
 在連接埠介面上顯示的是新的連接埠，以及 PeopleSoft 位置服務可用的方法。 稍後，您將會指定 PeopleSoft 配接器來傳送和接收來自 PeopleSoft 系統的檔案。  
  
 現在將兩個 **傳送** 圖形與兩個 **接收** 圖形插入協調流程，以連結至您剛才建立的連接埠。  
  
#### <a name="add-send-and-receive-shapes"></a>新增傳送和接收圖形  
  
1.  從工具箱拖曳 **接收** 元件，緊解著將其放置於協調流程 (綠色圓形) 的開頭下方。 按一下 **接收** 圖形，然後在 [屬性] 視窗中針對 [名稱] `FromDisk` 輸入 **[FileIn]**，並將 [啟動]  設為 `true`使用的八個企業營運系統 (LOB) 配接器之一。 如此會在此接收埠收到內送文件時啟動協調流程。  
  
2.  拖放到 **傳送** 元件從工具箱拖曳，把它放在正下方 **FromDiskReceive** 圖形。 按一下新 **傳送** 圖形，然後在 [屬性] 視窗中，輸入 `ToPS` 的 **名稱**。  
  
3.  拖放到 **接收** 元件從工具箱拖曳，把它放在正下方 **To_PS * * * 傳送** 圖形。 按一下  **接收** 圖形，然後在 屬性 視窗中，輸入 `FromPS` 的 **名稱**。  
  
4.  拖放到 **傳送** 元件從工具箱拖曳，把它放在正下方 **From_PSReceive** 圖形。 按一下新 **傳送** 圖形，然後在 [屬性] 視窗中，輸入 `ToDisk` 的 **名稱**。  
  
 您必須先定義要處理的訊息類型，才可以將這些圖形連接至邏輯連接埠。 配接器同時需要內送 (**要求** 方法) 訊息和外寄 (**回應** 方法) 訊息。 每個方法的訊息都不同。  
  
 在此協調流程中，您只會使用 **Get-Request** 和 **Get-Response** 訊息。 如果協調流程在更新資料，假設其使用 **UpdateEx** 方法，便會需要不同的要求/回應訊息。  
  
#### <a name="define-and-assign-messages-to-ports"></a>定義和指派訊息到連接埠  
  
1.  在左側連接埠介面上，按一下 [FileIn]  連接埠上的 [要求]  。 在 [屬性] 視窗中依序展開 [訊息類型] 和 [多部分訊息] ，然後按一下 [PS_Test.Get] 。  
  
2.  在左側連接埠介面上，按一下 [FileOut]  連接埠上的 [要求]  。 在 [屬性] 視窗中依序展開 [訊息類型] 及 [多部分訊息] ，然後按一下 [PS_Test.GetResponse] 。  
  
     ![](../core/media/6b844ca3-322a-47b3-8cfd-68652c950752.gif "6b844ca3-322a-47b3-8cfd-68652c950752")  
  
3.  選取 [FileIn]  連接埠，並將其外寄傳送箭頭拖曳至 **FromDisk** 圖形上的內送反向接收箭頭。  
  
4.  選取 [FileOut]  連接埠，並將其內送反向接收箭頭拖曳至 **ToDisk** 圖形上的外寄傳送箭頭。  
  
5.  將現有的泛型訊息名稱重新命名為更具描述性的名稱，以遵守良好的應用程式設計原則。 在方案總管中，按一下 [協調流程檢視]  索引標籤。在下**訊息**，變更的識別項**Message_1**至**PS_Msg**。 將 **Message_2** 的識別項變更為 [PS_Resp] 。  
  
     ![](../core/media/5ec92b81-4a55-4d44-a360-78a6aaa64255.gif "5ec92b81-4a55-4d44-a360-78a6aaa64255")  
  
     ![](../core/media/04b31c26-73a6-40a6-8d50-39c7c929d6a1.gif "04b31c26-73a6-40a6-8d50-39c7c929d6a1")  
  
6.  反白顯示 **To_PS** 傳送圖形並將其 **訊息** 屬性設為 [PS_Msg] 。  
  
7.  反白顯示 **From_PS** 接收圖形並將其 **訊息** 屬性設為 [PS_Resp] 。  
  
8.  將 **To_PS** 傳送圖形連接至 **PeopleSoft_Port** 連接埠上 **Get** 方法的 **要求** 部分。  
  
9. 將 **From_PS** 傳送圖形連接至 **PeopleSoft_Port** 連接埠上 **Get** 方法的 **回應** 部分。  
  
     ![](../core/media/d16e02bc-954c-4aa2-99d6-3fee1222c730.gif "d16e02bc-954c-4aa2-99d6-3fee1222c730")  
  
## <a name="step-4-build-and-deploy-the-project"></a>步驟 4： 建立和部署專案  
 現在 BizTalk 專案已完成，而且您可以建置並部署在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
1.  在 Visual Studio 中，指向**Visual Studio Tools**，然後選取 Visual Studio 命令提示字元 * *。  
  
2.  若要建置專案，您需要強式名稱金鑰檔。在命令提示字元中，輸入下列內容建立強式金鑰名稱檔：  
  
     **sn-k [labs.snk]**  
  
3.  在方案總管中，以滑鼠右鍵按一下 [PS_Test]  專案，再按一下 [屬性]  為專案啟動 [專案設計工具]。  
  
4.  按一下 [ **簽署** ] 索引標籤。  
  
5.  選取 **[簽署組件]** 選項、按一下 **[選擇強式名稱金鑰檔]** 選項的下拉式清單，然後按一下 **[瀏覽]**。  
  
6.  瀏覽並選取金鑰檔： **[labs.snk]**，然後按一下 **[開啟]**。  
  
7.  按一下 [專案設計工具] 中的 **[部署]** 索引標籤。  
  
8.  將 **應用程式名稱** 設為 `PS_Test`使用的八個企業營運系統 (LOB) 配接器之一。  
  
9. 在方案總管中，以滑鼠右鍵按一下 []  專案，然後按一下 [建置]   
  
10. 順利完成建置後，以滑鼠右鍵按一下 [PS_Test]  專案，然後按一下 [部署] 。  
  
## <a name="step-5-test-the-application-and-viewing-the-xml-output"></a>步驟 5： 測試應用程式並檢視 XML 輸出  
 現在您將測試所建立和部署的應用程式。 您會建立啟動協調流程處理序的 XML 檔案，然後設定在應用程式內接收和傳送 XML 檔案的資料夾。 設定應用程式之後，您將會執行它並檢視協調流程所傳回的 XML 檔案。  
  
#### <a name="generate-the-xml-file-for-the-query"></a>產生查詢的 XML 檔案  
  
1.  在方案總管中，按兩下 [LOCATIONService_LOCATION_x5d.xsd]  開啟檔案。  
  
2.  以滑鼠右鍵按一下 [LOCATIONService_LOCATION_x5d.xsd]  ，再按一下 [屬性] 。 針對 **輸出執行個體檔案名稱** 輸入範例 XML 的下列路徑和檔案名稱：  
  
     `C:\LABS\PS_TEST\SAMPLEQUERY.XML`  
  
3.  按一下 **[確定]**。 在 [屬性] 視窗中，選取**\<結構描述\>**並設定**根參考： 取得**。  
  
4.  以滑鼠右鍵按一下 [LOCATIONService_LOCATION_x5d.xsd]  ，再按一下 [產生執行個體] 。 這會產生 **SampleQuery.xml** 檔案。 這個檔案將做為配接器的輸入，放置在接收位置以啟動協調流程處理序。  
  
     ![](../core/media/ef65a96c-2daa-44db-ab95-d18b1fda934e.gif "ef65a96c-2daa-44db-ab95-d18b1fda934e")  
  
#### <a name="configure-and-start-the-biztalk-application"></a>設定和啟動 BizTalk 應用程式  
  
1.  設定用於接收內送檔案及傳送外寄檔案的資料夾。 移至 **C:\LABS\PS_TEST** ，然後建立名為 `FileIn` 和 `FileOut`使用的八個企業營運系統 (LOB) 配接器之一。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**主控台根目錄**，依序展開**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理**，依序展開**BizTalk 群組**，展開**應用程式**，以滑鼠右鍵按一下**PS_Test** ，然後按一下 **設定**。  
  
     ![](../core/media/e45f4c8b-fc8a-492a-9824-5232eb728d95.gif "e45f4c8b-fc8a-492a-9824-5232eb728d95")  
  
3.  選取 [Orchestration_1]  ，並按一下 [主機]  下拉式方塊。 選取 **[BizTalkServerApplication]**。  
  
4.  在下**接收埠**，按一下  **\<無\>**。 在下拉式清單中選取 [新增接收埠] 。  
  
5.  For **[FileIn]**輸入 `FileInPort`，然後按一下 [BizTalk Server 管理] 使用的八個企業營運系統 (LOB) 配接器之一。 訊息方塊會出現，指出您需要指定接收位置。 按一下 [確定] 及 [新增] 。  
  
     ![](../core/media/298638b6-0eb8-49c4-8a2e-485571d070cf.gif "298638b6-0eb8-49c4-8a2e-485571d070cf")  
  
6.  輸入或選取屬性的下列值：  
  
     **名稱**: `FileInLoc`  
  
     **類型**： **檔案**  
  
     **接收處理常式**： **BizTalkServerApplication**  
  
     **接收管線**： **XMLReceive**  
  
     ![](../core/media/613a5dbc-effe-4827-a72b-d16eef8d0e8a.gif "613a5dbc-effe-4827-a72b-d16eef8d0e8a")  
  
7.  按一下 [開始]  ，針對 [接收資料夾] `C:\LABS\PS_TEST\FILEIN` 中輸入 **C:\LABS\PS_TEST\FILEIN**，然後按一下 [BizTalk Server 管理]  。  
  
     ![](../core/media/513eebb0-58ca-4aaa-a33b-31700f9cf7a8.gif "513eebb0-58ca-4aaa-a33b-31700f9cf7a8")  
  
8.  按一下**\<無\>**如**PeopleSoft_Port**下拉式清單中。  
  
9. 選取 [新增傳送埠]  ，然後選取或輸入下列屬性值。  
  
     **名稱**: `PS_Test_Port`  
  
     **類型**： **PeopleSoft**  
  
     **傳送處理常式**： **BizTalkServerApplication**  
  
     **管線**： **XMLTransmit** 和 **XMLReceive**  
  
10. 按一下 [設定] ，然後輸入下列屬性值：  
  
    1.  **應用程式伺服器路徑**： **//Servername:9000**  
  
         Servername 是您的應用程式伺服器。 這是此 PeopleSoft 系統的特定伺服器名稱或 IP 位址以及連接埠號碼。  
  
    2.  **JAVA_HOME**： **C:\J2SDK1.4.2_08**  
  
         這個路徑是特定上的 Java SDK 安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
    3.  **密碼**:\<輸入您的 PeopleSoft 密碼\>  
  
    4.  **PeopleSoft 8.x JAR 檔案**： **C:\PSJARS\VER841\PSJOA.JAR**  
  
     **使用者名稱：** \<輸入您的 PeopleSoft Userid>\>  
  
11. 按兩下 [確定]  關閉對話方塊。  
  
12. 在 設定 Applicationwindow 中，按一下  **\<無\>**如**FileOut**下拉式清單中。  
  
13. 選取 [新增傳送埠]  ，然後選取或輸入下列屬性值：  
  
     **名稱**: `FileOutPort`  
  
     **類型**： **檔案**  
  
     **傳送處理常式**： **BizTalkServerApplication**  
  
     **傳送管線**： **XMLTransmit**  
  
14. 按一下  **設定** 和型別`C:\Labs\PS_Test\FileOut` 的 **目的地資料夾。** 保留 **%MessageID%.xml** 的 **檔案名稱** 因為這會產生唯一的檔案，為每個訊息。  
  
15. 按三下 [確定]  關閉對話方塊。  
  
16. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下滑鼠右鍵**PS_Test**應用程式，然後按一下**啟動**。  
  
     ![](../core/media/7bf30707-c7c6-409f-af18-9c9dfeb0de58.gif "7bf30707-c7c6-409f-af18-9c9dfeb0de58")  
  
#### <a name="test-the-orchestration"></a>測試協調流程  
  
1.  在 **C:\Labs\PS_Test** 目錄中，將 **Samplequery.xml** 檔案變更為下列所示：  
  
    ```  
    <ns0:Get xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
      <ns0:SETID>SHARE</ns0:SETID>  
      <ns0:LOCATION>AUS01</ns0:LOCATION>  
      <ns0:getHistory>true</ns0:getHistory>  
    </ns0:Get>  
    ```  
  
    > [!NOTE]
    >  **SHARE** 資料值將用在所有系統上。 不過，您將在使用在此 XML 檔案中的 **位置** 值必須存在您的系統上。 您已在實驗室 1 中發現這個原則。  
  
2.  儲存變更，並將檔案複製到 **C:\Labs\PS_Test\FileIn** 資料夾。 這是啟動協調流程處理序的 FileIn 接收位置。  
  
3.  XML 檔案很快就會出現在 **C:\Labs\PS_Test\FileOut** 資料夾中。 其中應包含來自位置為 AUS01 之記錄的資料。  
  
     ![](../core/media/1320ea3c-b2bc-4717-b200-c3c550079ccb.gif "1320ea3c-b2bc-4717-b200-c3c550079ccb")  
  
     這份傳回的記錄資料應符合針對 PeopleSoft 實驗室 1 中 PeopleSoft 系統的查詢所傳回的內容。 藉由比較值取得在實驗室 1 中，特別是**Address1**和**address2 一起顯示**到這裡所顯示的線條**\<位置： ADDRESS1\>**和**\<位置： address2 一起顯示\>**欄位，您可以確認**取得**方法運作正常。  
  
## <a name="summary"></a>摘要  
 在此實驗室中，您先確認了已正確設定必要條件，以便存取 PeopleSoft 系統。 之後，使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]來建立新的 BizTalk 專案包含協調流程。 您設定了此協調流程，以使用 PeopleSoft 配接器自 PeopleSoft 系統取得資料。 為了設定協調流程，您建立了傳送、接收與傳送/接收埠。 您將這些連接埠繫結至 PeopleSoft 配接器，並指派訊息到適當的連接埠。  
  
 當您完成 BizTalk 專案之後，您使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]建置和部署它。 然後設定了新的應用程式並加以執行，以從 PeopleSoft 系統取得資料。 為了確定應用程式正確運作，您將其輸出 XML 檔與在實驗室 1 中接收自 PeopleSoft 系統的檔案做比較。