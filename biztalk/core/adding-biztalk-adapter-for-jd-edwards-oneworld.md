---
title: 新增 BizTalk Adapter for JD Edwards OneWorld |Microsoft Docs
description: 將 JD Edwards OneWorld 新增至 BizTalk 管理、 建立傳送埠、 設定傳輸屬性中，和 BizTalk Server 中使用 JD Edwards OneWorld 配接器時，使用 XMLReceive 和 XMLTransmit 管線
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03126f4e-9156-4c0c-ab5c-0627f0c05263
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: decababef3ece92c99687a4019b15625b1b4c6b7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981391"
---
# <a name="configure-jd-edwards-enterpriseone-artifacts-in-biztalk-administration"></a>在 BizTalk 管理中設定 JD Edwards EnterpriseOne 成品
Microsoft BizTalk Adapter for JD Edwards OneWorld 包含 [接收處理常式] 和 [傳送處理常式] 資料夾。 [傳送處理常式] 資料夾包含 BizTalkServerApplication。 BizTalk Adapter for JD Edwards OneWorld 是可建立的；它會在與 BizTalk Server 相同的程序中執行，而且不會在外掛式主控件程序中執行。  

## <a name="add-the-adapter-to-biztalk-administration"></a>將配接器新增至 BizTalk 管理 

1.  開啟**BizTalk Server 管理**，展開**BizTalk Server 管理**，展開**BizTalk 群組**，然後展開**平台設定**.  
  
2.  以滑鼠右鍵按一下**配接器**，選取**新增**，然後選取**配接器**。  
  
3.  輸入配接器的名稱。 例如，輸入`JDEOneWorld`。  
  
4.  選取  **jdeoneworld**從**配接器**清單，然後選取**確定**。  

  
### <a name="check-if-the-adapter-is-working"></a>檢查配接器是否正常運作 
 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以確認配接器藉由查看正確運作**邏輯系統**視窗。 在初次安裝時，因為您尚未建立與伺服器系統的連線，也尚未建立任何邏輯系統，所以這個視窗會是空的。  
  
 
1. 在 [ **BizTalk Server 管理]**，展開**平台設定**，展開**配接器**，然後選取 **[jdeoneworld]**。  
  
2. 在 [詳細資料] 窗格中，以滑鼠右鍵按一下**BizTalkServerApplication**，然後選取**屬性**。  
  
3. 選取 [**屬性**] 索引標籤。  
  
4. 設定 SQL 連線參數。  
  
   -   **定義 SQL 資料庫參數-** 的 SQL Server 名稱和資料庫是您在安裝期間設定。 您可以在這個文字區域中重新定義此配接器的伺服器與資料庫。  
  
5. 選取 **關閉**以結束**邏輯系統**視窗。  
  
    下一個步驟是要使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 來新增邏輯系統。  

## <a name="create-the-send-port"></a>建立傳送埠  
  
1.  在 [ **BizTalk Server 管理]**，展開**BizTalk 群組**，展開**應用程式**，然後展開您的應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態請求-回應傳送埠**。  
  
    > [!NOTE]
    >  您也可以使用**靜態單向連接埠**。  
  
3.  在 **傳送埠屬性**，選取**名稱**欄位，並輸入傳送埠名稱。 例如，輸入**SendToJDE**。  
  
4.  在 **型別**下拉式清單中，選取**jdeoneworld**。  
  
5.  在  **URI**下拉式清單中，選取 傳送處理常式。  
  
6.  選取 [確定]。 

## <a name="configure-the-transport-properties"></a>設定傳輸屬性
「JD Edwards OneWorld 傳輸屬性系統定義」用於設計和執行階段登入。 您要設定這些認證以在設計階段瀏覽 JD Edwards OneWorld 商務功能，並在執行階段進行呼叫。  
  
 當與 JD Edwards OneWorld 建立連線時，參數會傳送到連線物件 (使用者、密碼、環境)。 它會傳回一個 JD Edwards OneWorld 應用程式商務函數。 企業/應用程式伺服器名稱與服務接聽的已定義 TCP/IP 連接埠會進一步定義認證。  
  
 企業伺服器名稱和連接埠會讀取名為 jdeinterop.ini 的檔案。 這些值必須是相同的系統定義的設定中。  
  
> [!NOTE]
>  所有項目均區分大小寫。  
  
### <a name="set-the-properties"></a>設定屬性  
 在 [**傳輸屬性**] 對話方塊中，您設定專屬於伺服器系統與您嘗試存取之物件的連接和認證參數。  
  
1.  提供認證。 您可以使用下列其中一種方法來存取 JD Edwards OneWorld 系統：  
  
    -   登入認證 （密碼、 使用者名稱）： 如果您使用這個方法時，請移至步驟 5。  
  
    -   單一登入。  
  
2.  若要使用單一登入 (SSO)，請選取 **[是]** 中**使用 SSO**。  
  
     如需如何設定 SSO 的詳細資訊，請參閱[配接器中的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)  
  
3.  在清單中選取分支機構應用程式。  
  
     企業單一登入工具建立的分支機構應用程式代表一個應用程式 (例如 JD Edwards OneWorld)。 Microsoft BizTalk Adapter for JD Edwards OneWorld 會使用應用程式使用者的認證。 這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 認證資料庫中擷取所得。 這些認證就是啟動 BizTalk Server 專案之應用程式使用者的認證。  
  
     如需詳細資訊，請參閱 <<c0> [ 建立分支機構應用程式](../core/creating-affiliate-applications3.md)。  
  
4.  依序展開**JD Edwards OneWorld 系統**節點，然後輸入所有必要的連接資訊至 JD Edwards OneWorld 伺服器。  
  
     ![](../core/media/jdedadapter-02-jdesystem.gif "JDEdAdapter_02_JDESystem")  
  
     在設定連線參數後，您可以瀏覽 JD Edwards OneWorld 系統。 如需詳細資訊，請參閱 <<c0> [ 匯入 JD Edwards OneWorld 結構描述至 BizTalk Server 專案](../core/importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects.md)。  
  
5.  輸入值，在表示的呼叫，例如 200，數目**同時呼叫數目上限**它是否必要。  
  
     `Max Concurrent Calls`參數可讓您最佳化組態。 在輸送量超過後端處理能力時，可以使用這個參數來啟動訊息多載保護。 預設值為 -1，表示呼叫沒有上限。  
  
     當 BizTalk Server 將訊息提交到傳輸配接器時，會先收到來自配接器的批次。 它會在批次上叫用 `TransmitMessage` 以傳輸每個訊息。 完成傳輸時，BizTalk Server 會在批次上叫用 `Done`，這時配接器就會開始將訊息傳輸至後端。 如果 BizTalk Server 在叫用 `Done` 之前取得多個批次，可能永遠不會叫用。 藉由設定批次中的訊息數目上限，您便可以控制送到後端的訊息。  
  
     此參數的變更會在 1 分鐘內生效；BizTalk Server 必須擷取儲存在 SQL 資料庫中的配接器組態變更。  
  
6.  選取  **是** for**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。  
  
     例如，您希望處理程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。  
  
    > [!NOTE]
    >  這個 browsingagent.exe 要等到您結束目前的瀏覽工作階段才會重新整理。 例如，您必須先結束**產生的新增項目**瀏覽工作階段並重新進入，才能更新 browsingagent.exe。  
  
7.  提供所有必要的資訊後，按一下**套用**，然後按一下**確定**以採用連線資訊。  
  
     您必須為 BizTalk Adapter for JD Edwards OneWorld 設定連線參數，才能存取 JD Edwards OneWorld。  
  
### <a name="adapter-required-properties"></a>配接器必要屬性  
 如果沒有在 [控制台] 中設定全域環境變數，您可以在此區段中設定。  
  
|參數|描述|  
|---------------|-----------------|  
|`Host`|輸入主控件伺服器電腦名稱的名稱 (例如`actsvr1`); 或電腦的 IP 位址 (例如`123.456.0.789`)。|  
|JAVA_HOME|輸入 JDK 安裝的完整路徑。|  
|JDE Edwards 環境|在 JD Edwards OneWorld 中，輸入環境的名稱，例如`DV7333`。<br /><br /> DV7333 是開發環境的一般名稱，PY7333 常見於原型環境，PD7333 常見於實際執行環境。|  
|JDEdwards JAR 檔案|輸入每個 JAR 檔案的完整路徑與檔案名稱：<br /><br /> -Connector.jar<br />-Kernel.jar<br />-JDEJAccess.jar<br />-JDEActionalInterop.jar<br /><br /> 每個 JAR 檔案都必須以分號 (;) 分隔，且不得包含空格。 例如：<br /><br /> `<drive>\Connector.jar;<drive>\Kernel.jar;`|  
|[密碼]|輸入指定使用者的密碼。|  
|通訊埠|輸入會交換資料的連接埠號碼 (例如`6009`)。|  
|使用者名稱|輸入將用來登入 JD Edwards OneWorld 系統的 JD Edwards OneWorld 使用者名稱。|  

## <a name="use-the-xmltransmit-and-xmlreceive-pipelines"></a>使用 XMLTransmit 和 XMLReceive 管線
Microsoft BizTalk Adapter for JD Edwards OneWorld 要求您選取 XMLTransmit 和 XMLReceive 傳送與接收管線。  
  
1.  在 [ **BizTalk Server 管理]**，展開**應用程式**，然後展開您的應用程式。  
  
2.  選取 **傳送埠**，以滑鼠右鍵按一下您的傳送埠，然後選取**屬性**。  
  
3.  在 **傳送埠屬性**，執行下列動作：  
  
    1.  選取傳送管線，從**傳送管線**下拉式清單。  
  
    2.  選取接收管線，從**接收管線**下拉式清單。  
  
4.  選取 [確定]。  

## <a name="next-steps"></a>後續的步驟
[將配接器結構描述匯入 Visual Studio](importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects.md)  
[使用訊息內容屬性](using-message-context-properties2.md)