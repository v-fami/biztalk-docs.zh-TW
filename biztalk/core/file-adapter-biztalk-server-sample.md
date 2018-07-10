---
title: File 配接器 （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, File adapters
- File adapters, examples
ms.assetid: d59cecb4-6353-44d5-b8d6-316446758536
caps.latest.revision: 46
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 251d527549100c88dc038ffed839ab98e92a3358
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007719"
---
# <a name="file-adapter-biztalk-server-sample"></a>File 配接器 （BizTalk Server 範例）
File 配接器範例是以 Microsoft Visual C#.NET 來使用 Microsoft BizTalk Server。 此範例提供可建置動態或靜態配接器的程式碼。  不過，下列程序僅概述靜態配接器。 靜態配接器具有一組靜態結構描述，且沒有自訂使用者介面。 動態配接器具有自訂使用者介面，並且可能有一組動態結構描述。 靜態和動態配接器都使用「新增配接器精靈」將結構描述新增至 BizTalk 專案。  

> [!NOTE]
>  File 配接器範例不是原生 FILE 配接器隨附於 BizTalk Server 相同。 因此，使用此範例選取傳輸類型時，請選取「靜態」，不要選取 FILE。  

 具有自訂使用者介面並且可能有一組動態結構描述的動態配接器，在配接器管理方面將需要額外的程式碼。 若要進一步了解使用動態結構描述集，請參閱[動態設計階段配接器組態](../core/dynamic-design-time-adapter-configuration.md)。  

## <a name="what-this-sample-does"></a>此範例的用途  
 此範例配接器會從檔案資料夾複製檔案，並當做訊息提交至 BizTalk，或者從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 取得訊息並放置在檔案資料夾中。 它提供可建置動態或靜態配接器的程式碼；不過，下列程序僅概述靜態配接器。 靜態配接器具有一組靜態結構描述，且沒有自訂使用者介面。 動態配接器具有自訂使用者介面，並且可能有一組動態結構描述。 靜態和動態配接器都使用「新增配接器精靈」將結構描述新增至 BizTalk 專案。  

 您可以將範例 FILE 配接器當做範本，建立其他自訂配接器。  

## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*Samples Path*\>**\AdaptersDevelopment\File Adapter**  

> [!NOTE]
>  預設位置\<*範例路徑*\>會 *%programfiles%* \Microsoft BizTalk Server\SDK\Samples 時執行 32 位元的電腦上安裝 BizTalk ServerWindows 版本。 預設位置\<*範例路徑*\>會*ProgramFiles(x86) %* \Microsoft BizTalk Server\SDK\Samples 時執行 64 位的電腦上安裝 BizTalk Server位元版本的 Windows。 若要判斷與相關聯的值 *%programfiles%* 或是*ProgramFiles(x86) %* 環境變數類型**echo %programfiles%** 或**echo %ProgramFiles(x86) %** 在命令提示字元並按 ENTER 鍵。 如果在 64 位元作業系統上執行此範例中，您必須將任何的.reg 檔案中的所有參考都變更 **%programfiles%** 要**ProgramFiles(x86) %** 之前執行.reg 檔案。  

 下表顯示此範例中的檔案，並說明其用途。  

|\File Adapter 檔案|描述|  
|--------------------------|-----------------|  
|\BizTalk Project 檔案|包含配接器控管專案，可用來測試範例配接器。|  
|\Design Time 檔案|包含設計階段和管理專案 (AdapterManagement.csproj)。|  
|\Runtime 檔案|包含執行階段檔案複製接收和傳輸專案 (DotNetFile.csproj)。|  
|DynamicAdapterManagement.reg|註冊範例動態配接器。|  
|Instance.xml|透過 FILE 配接器傳遞的範例檔案。|  
|StaticAdapterManagement.reg|註冊範例靜態配接器。|  

|\BizTalk Project\Adapter Harness 檔案|描述|  
|----------------------------------------------|-----------------|  
|AdapterHarness.odx、AdapterHarness.sln、AdapterHarnessProject.btproj|提供適用於 BizTalk 專案的專案、解決方案和相關檔案。|  
|mySchema.xsd|提供控管協調流程所預期的 Instance.xml 結構描述 (來自配接器的接收部分)，以及由協調流程傳遞到配接器的傳送部分的 Instance.xml 結構描述。|  

|\Design Time\Adapter Management 檔案|描述|  
|---------------------------------------------|-----------------|  
|AdapterManagement.cs、AdapterManagement.csproj、AdapterManagement.sln|適用於配接器設計階段的專案、解決方案和相關檔案。|  
|AssemblyInfo.cs|包含此範例的組件資訊。|  
|CategorySchema2.xml|範例配接器不使用。|  
|CategorySchema.xml|包含靜態配接器的服務組織樹狀結構。|  
|DotNetFileResource.resx|包含資源。|  
|ReceiveHandler.xsd、ReceiveLocation.xsd|包含接收端處理常式和結束點自訂屬性結構描述|  
|service1.wsdl|包含配接器的作業定義。|  
|TransmitHandler.xsd、TransmitLocation.xsd|包含傳輸端處理常式和結束點自訂屬性結構描述|  

|                                                                                                                                                             \Runtime 檔案                                                                                                                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DotNetFile.csproj、DotNetFile.sln,<br /><br /> AssemblyInfo.cs、<br /><br /> DotNetFileExceptions.cs、DotNetFileProperties.cs、DotNetFileReceiver.cs、DotNetFileReceiverEndPoint.cs、DotNetFileTransmitter.cs、<br /><br /> DotNetFileTransmitterEndpoint.cs、<br /><br /> DotNetFileAsyncTransmitterBatch.cs、<br /><br /> BatchMessage.cs | 適用於執行階段檔案複製傳送和接收配接器的檔案。 您可以修改並以新名稱儲存這些檔案，做為自訂元件。<br /><br /> DotNetFile.csproj 和 DotNetFile.sln 是專案與方案檔。<br /><br /> AssemblyInfo.cs 包含此範例的組件資訊。<br /><br /> DotNetFileReceiver.cs 會從接收位置讀取檔案，並將檔案提交至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。<br /><br /> DotNetFileExceptions.cs 會在處理訊息期間實作程式碼以處理例外狀況<br /><br /> DotNetFileProperties.cs 包含接收和傳送作業的通用屬性<br /><br /> BatchMessage.cs 會實作批次訊息處理。<br /><br /> DotNetFileReceiverEndPoint.cs 是對應至接收位置/URI 的類別。  它會為新訊息輪詢指定資料夾<br /><br /> DotNetFileTransmitter.cs 是 DotNetFile 傳送配接器的單一類別。 傳遞到此配接器不同傳送埠的所有訊息都會經過這個類別<br /><br /> DotNetFileTransmitterEndpoint.cs 會處理傳輸訊息。 |

|\SDK\Samples\AdaptersDevelopment\BaseAdapter\v1.0.2 檔案|描述|  
|--------------------------------------------------------------------|-----------------|  
|Adapter.cs、AdapterException.cs、AsyncTransmitter.cs、batch.cs、ConfigProperties.cs、ControlledTermination.cs、IManageEndpoints.cs、Receiver.cs、ReceiverEndpoint.cs|提供組成 Base 配接器的類別。 您可以使用這些類別來建立自己的配接器。|  

## <a name="how-to-use-this-sample"></a>如何使用此範例  
 將範例 FILE 配接器當做範本，建立其他自訂配接器。  

## <a name="building-this-sample"></a>建置此範例  

> [!IMPORTANT]
>  如果 BizTalk 安裝是 64 位元，或安裝位置已有修改，則需要隨之變更 OutboundAssemblyPath、InboundAssemblyPath、AdapterMgmtAssemblyPath。  

 使用下列程序建置和初始化 FILE 配接器範例。  

#### <a name="to-create-a-strong-name-key-for-the-dotnetfileadapter-projects-and-the-base-adapter-project"></a>為 DotNetFileAdapter 專案和 Base 配接器專案建立強式名稱金鑰  

1.  開始**Visual Studio 命令提示字元**。  

    > [!NOTE]
    >  以系統管理員身分執行命令提示字元。  

2.  變更目前的目錄\<*範例路徑*\>**\AdaptersDevelopment\BaseAdapter\v1.0.2**目錄。  

3.  在命令提示字元中，輸入**sn – k BaseAdapter.snk**然後按 ENTER 鍵。 這個 .snk 檔案可能因為先前已執行過其他範例而存在。 如果檔案已經存在，您可以直接執行步驟 4 並略過這個步驟。  

4.  變更目前的目錄\<*範例路徑*\>\\**AdaptersDevelopment\File Adapter\Runtime**目錄。  

5.  在命令提示字元中，輸入**sn – k DotNetFileAdapter.snk**然後按 ENTER 鍵。  

6.  在命令提示字元中，輸入**結束**然後按 ENTER 關閉命令提示字元視窗。  

#### <a name="to-build-the-receiver-run-time-project"></a>建置接收器執行階段專案  

1.  按一下 **開始**，指向**所有程式**，指向**附屬應用程式**，然後按一下**Windows 檔案總管**。  

2.  瀏覽至\<*範例路徑*\>**"\AdaptersDevelopment\File Adapter\Runtime 」** 目錄，然後再按兩下**DotNetFile.sln**.  

3.  若要重新建置配接器接收器執行階段專案，在 [方案總管] 中，以滑鼠右鍵按一下**DotNetFile**，然後按一下**重建**。  

4.  從**檔案**功能表上，按一下**結束**以關閉 Visual Studio。  

#### <a name="to-build-the-adapter-design-time-project"></a>建置配接器執行階段專案  

1.  在 Windows 檔案總管中，瀏覽至\<*範例路徑*\>**"\AdaptersDevelopment\File Adapter\Design Time\Adapter Management"** 目錄，然後再按兩下**AdapterManagement.sln**。  

2.  在 [方案總管] 中，以滑鼠右鍵按一下**AdapterManagement**，然後按一下**重建**。  

3.  從**檔案**功能表上，按一下**結束**以關閉 Visual Studio。  

#### <a name="to-register-the-sample-static-adapter"></a>註冊範例靜態配接器  

1. 在 Windows 檔案總管中，瀏覽至\<*範例路徑*\>**"\AdaptersDevelopment\File 配接器"** 目錄。  

2. 若要將範例配接器新增至登錄中，按兩下**StaticAdapterManagement.reg**。  

   > [!NOTE]
   >  StaticAdapterManagement.reg 包括硬式編碼路徑 C:\Program Files\Microsoft BizTalk Server\\。 如果您未安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 %ProgramFiles%\Microsoft BizTalk 目錄下，如果您是從 BizTalk Server 2009 或 BizTalk Server 2006 R2 中，升級您的 BizTalk Server 安裝，或如果您正在執行的電腦上安裝 BizTalk Server64 位元版本的 Windows，您必須將檔案 StaticAdapterManagement.reg 修改為適當的路徑。 根據預設，BizTalk Server 會安裝到 %programfiles(x86) %\Microsoft 執行 Windows 64 位元版本的電腦上的 BizTalk Server\ 目錄。 請將與 "InboundAssemblyPath"、"OutboundAssemblyPath" 和 "AdapterMgmtAssemblyPath" 值關聯的路徑更新為指向所指定檔案的正確位置。  
   > 
   > [!IMPORTANT]
   >  如果您在 64 位元電腦上安裝 BizTalk，可將所有 HKEY_CLASSES_ROOT\CLSID\ 登錄項目執行個體都變更為 hkey_classes_root\wow6432node\clsid \ 中**StaticAdapterManagement.reg**登錄檔。  

3. 在 **登錄編輯程式**  對話方塊中，按一下**是**以將範例配接器新增至登錄，然後按一下**確定**。  

4. 若要在關閉 Windows 檔案總管中，**檔案**功能表上，按一下**關閉**。  

#### <a name="to-install-the-sample-static-adapter"></a>安裝範例靜態配接器  

1. 按一下 **開始**，選取**所有程式**，選取[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後選取**BizTalk Server 管理**。  

2. 在 BizTalk Server 管理主控台中，按一下以展開**BizTalk Server 管理**，按一下以展開**BizTalk 群組**，然後按一下以展開**平台設定**.  

3. 以滑鼠右鍵按一下**配接器**，按一下**新增**，然後按一下**配接器**。  

4. 在 **新增配接器**對話方塊方塊中，執行下列動作。  


   |  使用   |                      以進行此動作                       |
   |-------------|-------------------------------------------------------|
   |  **名稱**   |                   型別**靜態**。                    |
   | **配接器** | 選取 [ **Static dotnetfile]** 從下拉式清單。 |
   | **註解** |               型別**範例配接器**。                |


5. 按一下 [確定] 。  

    靜態配接器現在會出現在 [BizTalk 管理主控台] 右邊視窗的配接器清單中。  

#### <a name="to-stop-and-restart-the-host-instance"></a>停止並重新啟動主控件執行個體  

1. 按一下 **開始**，選取**所有程式**，選取[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後選取**BizTalk Server 管理**。  

2. 在 BizTalk Server 管理主控台中，按一下以展開**BizTalk Server 管理]**，按一下以展開**BizTalk 群組**，按一下以展開**平台設定**按一下 [**主控件執行個體**。 在右窗格中選取 BizTalkServerApplication。  

3. 在 [結果] 窗格中，以滑鼠右鍵按一下主控件執行個體 （通常是電腦名稱），，然後按一下**重新啟動**。  

### <a name="running-this-sample"></a>執行此範例  

##### <a name="to-run-the-file-adapter-sample"></a>執行 FILE 配接器範例  

1. 按一下 **開始**，指向**所有程式**，指向**附屬應用程式**，然後按一下**Windows 檔案總管**。  

2. 在 BizTalk Server 安裝磁碟機上建立下列資料夾：  

   -   *\<drive\>*:**\Temp**  

   -   *\<drive\>*:**\Temp\Send**  

   -   *\<drive\>*:**\Temp\Receive**  

3. 若要在關閉 Windows 檔案總管中，**檔案**功能表上，按一下**關閉**。  

4. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  

5. 以滑鼠右鍵按一下**BizTalk Server 管理**節點，然後選取**連接到現有的群組**。  

6. 在 **連接到現有的 BizTalk Server 組態資料庫**對話方塊方塊中，執行下列動作。  

   > [!NOTE]
   >  「BizTalk 管理」資料庫也稱為「BizTalk 組態」資料庫。  

   |    使用    |                                                                                    以進行此動作                                                                                     |
   |----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **[SQL Server]** |                                                                              型別 **。** (句點)。                                                                               |
   |  **[資料庫備份]**  | 選取由組態精靈建立的 BizTalk 管理資料庫名稱。 「 組態精靈 」 所使用的預設資料庫名稱是**BizTalkMgmtDb**。 |


7. 按一下 [確定] 。  

8. 依序展開**BizTalk 群組 [*伺服器名稱*]** 節點中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**應用程式**節點，展開**BizTalk Application 1**節點。  

9. 以滑鼠右鍵按一下**傳送埠**節點，然後再按一下**新增**，選取**靜態單向傳送埠**，然後按一下**確定**。  

10. 在 **傳送埠屬性**對話方塊中，選取**一般**，並執行下列動作。  


    |      使用      |                                                                                                                                                                                   以進行此動作                                                                                                                                                                                   |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |      **名稱**      |                                                                                                                                                                             型別**AdapterSend**。                                                                                                                                                                              |
    | **傳輸類型** | 選取 **靜態**從下拉式清單，然後按一下**設定**。<br /><br /> -在**Directory**方塊中，輸入 ***\<磁碟機\>*:\Temp\Send**。<br />-在**檔案模式**方塊中，選取**CreateNew**。<br />-在**檔名**方塊中，輸入 **%MessageID%.xml**。<br />-按一下**確定**。<br />- **URI**欄位應該會顯示 ***\<磁碟機\>*:\Temp\Send\\%MessageID%.xml**。 |
    | **傳送管線**  |                                                                                                                                   選取  **PassThruTransmit (Microsoft.BizTalk.DefaultPipelines.PassThruTransmit)**，然後按一下**確定**。                                                                                                                                    |


11. 底下**BizTalk Application 1**  節點按一下**接收埠**，然後選取**新增 / 單向接收埠**。  

12. 中**建立新接收埠**對話方塊中，於**指定的接收埠類型**方塊中，選取**單向接收埠**從下拉式清單，然後再按  **確定**。  

13. 中**接收埠屬性**對話方塊中，於**名稱**方塊中，輸入**AdapterReceive**，然後按一下 **確定**。  

14. 底下**BizTalk Application 1**以滑鼠右鍵按一下節點**接收位置**，然後選取**新增 / 單向接收位置**。  

15. 在 **選取接收埠**對話方塊中，選取**AdapterReceive**然後按一下 **確定**。  

16. 在 **接收位置屬性**對話方塊方塊中，執行下列動作。  


    |       使用       |                                                                                                                                                                                               以進行此動作                                                                                                                                                                                                |
    |----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |       **名稱**       |                                                                                                                                                                                     型別**AdapterReceiveLocation**                                                                                                                                                                                     |
    |  **傳輸類型**  |                                                                                                                                                  選取 **靜態**從下拉式清單和點擊**設定**來存取這些其餘屬性。                                                                                                                                                  |
    |       **URI**        | -按一下省略符號按鈕 (**...**).<br />-在**數字的檔案在批次**方塊中，輸入**20**。<br />-在**Directory**方塊中，輸入 ***\<磁碟機\>*:\Temp\Receive**。<br />-確定**檔案遮罩**屬性設定為 **\*.xml**。<br />-在**輪詢間隔**方塊中，輸入**5**，然後按一下**確定**。<br />-確定**URI**標籤包含 ***\<磁碟機\>*:\Temp\Receive\\\*.xml**。 |
    | **接收處理常式**  |                                                                                                                                                                      選取  **BizTalkServerApplication**從下拉式清單。                                                                                                                                                                       |
    | **接收管線** |                                                                                                                                                                             選取  **XMLReceive**從下拉式清單。                                                                                                                                                                              |


17. 按一下 [確定] 。  

     請繼續進行*建置、 部署和繫結範例配接器*。  

### <a name="building-deploying-and-binding-the-sample-adapter"></a>建置、部署和繫結範例配接器  
 在配接器可以使用之前，您必須先建置專案、將協調流程繫結至連接埠以及登錄配接器。  

##### <a name="to-create-a-strong-name-key-for-the-static-adapter"></a>建立靜態配接器的強式名稱金鑰  

1.  開始**Visual Studio 命令提示字元**。  

2.  在命令提示字元中，變更目前的目錄\<*範例路徑*\>**\AdaptersDevelopment\File Adapter\BizTalk Project\Adapter 控管**目錄。  

3.  在命令提示字元中，輸入**sn – k AdapterHarness.snk**，然後按下 enter。  

4.  按一下 [確定] 。  

##### <a name="to-build-the-adapter-harness-project"></a>建置配接器控管專案  

-   在 [方案總管] 中，以滑鼠右鍵按一下 **[adapterharnessproject]**，然後按一下**重建**。  

##### <a name="to-deploy-the-adapter-harness-project"></a>部署配接器控管專案  

1.  在 [方案總管] 中，當重新建置專案之後，按一下滑鼠右鍵 **[adapterharnessproject]**，然後按一下**部署**。  

2.  在 BizTalk Server 管理主控台 中，選取的專案，您已部署，然後按一下**重新整理**。  

##### <a name="to-bind-the-orchestration-with-the-ports"></a>將協調流程繫結至連接埠  

1. 在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台] 底下的適當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式中，展開**協調流程**節點。  

2. 以滑鼠右鍵按一下**AdapterHarness.AdapterHarnessType**，然後按一下**繫結**。  

3. 在 **連接埠繫結內容-AdapterHarness.AdapterHarnessType-Binding Configurations**對話方塊方塊中，執行下列動作。  


   |          使用          |                     以進行此動作                     |
   |----------------------------|----------------------------------------------------|
   | **AdapterFileReceivePort** | 選取  **AdapterReceive**從下拉式清單。 |
   |  **AdapterFileSendPort**   |  選取  **AdapterSend**從下拉式清單。   |


4. 在左窗格中，按一下**主機**。  

5. 在 **主機**方塊中，選取**BizTalkServerApplication**從下拉式清單中，然後按一下**確定**。  

   請繼續進行*管理範例配接器*。  

### <a name="administering-the-sample-adapter"></a>管理範例配接器  
 請在 [BizTalk 管理主控台] 中完成範例配接器的管理工作。  

##### <a name="to-administer-the-file-adapter-sample"></a>管理 FILE 配接器範例  

1. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  

2. 在左窗格中，按一下以展開**應用程式**，按一下以展開**BizTalk Application 1**，然後按一下**接收位置**。  

3. 請確定**AdapterReceive**狀態**已啟用**。  

    如果狀態不是**Enabled**，以滑鼠右鍵按一下**AdapterReceive**在右窗格中，然後按一下**啟用**。  

4. 在左窗格中，按一下**協調流程**，並確定**AdapterHarness.AdapterHarnessType**會**已登錄**。 以滑鼠右鍵按一下**AdapterHarness.AdapterHarnessType**，然後按一下**登錄**(如果 AdapterHarness.AdapterHarnessType 已經登錄，**登錄**功能表選項無法使用）。  

5. 以滑鼠右鍵按一下**AdapterHarness.AdapterHarnessType** ，然後選取**開始**。 此協調流程的狀態應該變更為**執行**。  

   請繼續進行*測試範例配接器*。  

### <a name="testing-the-sample-adapter"></a>測試範例配接器  
 部署範例配接器之後，您必須停止並重新啟動主控件執行個體。 請務必先測試範例配接器，再運用到實際執行的環境中。  

##### <a name="to-stop-and-restart-the-host-instance"></a>停止並重新啟動主控件執行個體  

1.  在 [ **BizTalk Server 管理]** 主控台中，按一下以展開**BizTalk Server 管理]**，按一下以展開**BizTalk 群組**，按一下以展開**平台設定**，按一下 [**主控件執行個體**。 在右窗格中選取 BizTalkServerApplication。  

2.  主控件執行個體 （通常是電腦名稱），以滑鼠右鍵按一下，然後按一下**停止**。  

     主控件執行個體狀態會變更為**已停止**。  

3.  以滑鼠右鍵按一下主控件執行個體，然後按一下**啟動**。  

     主控件執行個體狀態會變更為**執行**。  

##### <a name="to-test-the-sample-static-adapter-runtime"></a>測試範例靜態配接器執行階段  

1.  在 Windows 檔案總管中，瀏覽至\<*範例路徑*\>**\AdaptersDevelopment\File 配接器**目錄，並將 InstanceXML.xml 檔案到您的剪貼簿。  

2.  瀏覽至*\<磁碟機\>*:**\Temp\Receive**並將 Instance.xml 檔案貼到資料夾。  

     如果傳輸和接收配接器使用，則檔案應該從*\<磁碟機\>*:**\Temp\Receive**資料夾*\<磁碟機\>* :**\Temp\Send**資料夾。  

##### <a name="to-test-the-sample-add-adapter-wizard-functionality-for-the-sample-static-adapter"></a>測試範例靜態配接器的範例新增配接器精靈功能  

1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在方案總管] 中，以滑鼠右鍵按一下 **[adapterharnessproject]**，指向**新增**，然後按一下 **新增產生的項目**。  

2. 在 **新增產生的項目-adapterharnessproject**  對話方塊中，按一下**新增配接器中繼資料**，然後按一下 **開啟**。  

    已註冊的配接器清單便會出現。  

3. 選取  **Static dotnetfile**，然後按一下**下一步**。  

    配接器所公開的服務組織便會出現。  

4. 依序展開**服務組織**，**美國衛生保健**，然後按一下**系統管理**。  

    請注意，**資格**顯示方式和其他節點。 **資格**是您可以選取 [服務] 節點。 其他節點是組織節點，沒有說明任何特定的服務。  

5. 選取 **資格**節點，然後再按一下**完成**。  

    BizTalk 會將 .odx 檔案和 .xsd 檔案匯入專案。  

    現在，您可以在 BizTalk 專案中，使用排程中的配接器所匯入的結構描述、PortTypes、Operations 和 MessageTypes。  

## <a name="classes-or-methods-used-in-this-sample"></a>在此範例中使用的類別或方法  
 介面： IBaseMessage、 IPropertyBag、 IBTTransportProxy  

 類別 （來自 Base 配接器）： AsyncTransmitterEndpoint、 AsyncTransmitter、 BatchMessage、 ControlledTermination、 ReceiverEndpoint、 DotNetFileCommonProperties、 BatchOperationType  

### <a name="comments"></a>註解  
 完成範例配接器之後, 您可以修改範例配接器建立自訂靜態或動態配接器的詳細資訊，請參閱[配接器設計階段組態](../core/adapter-design-time-configuration.md)。  

## <a name="see-also"></a>另請參閱  
 [配接器範例-用法](../core/adapter-samples-usage.md)   
 [註冊配接器](../core/registering-an-adapter.md)