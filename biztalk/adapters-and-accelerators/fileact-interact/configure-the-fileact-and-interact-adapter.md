---
title: 設定 FileAct 和 InterAct 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d3876ff-e8e4-47f4-9ca8-d4dad419ed67
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d62e4cf0896e755a0ec8ece00d6a2140210b463
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974599"
---
# <a name="configure-the-fileact-and-interact-adapter"></a>設定 FileAct 和 InterAct 配接器
設定所使用的不同成品[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]執行階段。 

  
## <a name="prerequisites"></a>必要條件  
   
- 安裝 [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]
  
- 成員的身分登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組
  
- 確認 SQL Server 正在執行
  
## <a name="step-1-configure-the-fileact-and-interact-adapter"></a>步驟 1： 設定 FileAct 和 InterAct 配接器  
  
1.  在  **Microsoft BizTalk FileAct 和互動的配接器組態**精靈中，移至**概觀**。 在左窗格中，選取**執行階段**設定配接器執行階段元件。  
  
2.  在 **執行階段組態**下方**帳戶**，選取省略符號 [...]，輸入 COM plus 存放與轉寄 」 模式的組態。  
  
3.  在 **使用者認證**，輸入使用者名稱 (在*網域 \ 使用者名稱*格式) 和 COM plus 組態中所使用之帳戶的密碼。 選取 [確定]。  
  
    > [!NOTE]
    >  A**使用者認證**如果您輸入的帳戶有較高的權限比建議會出現警告。 選取 **是**以繼續。
  
4.  選取 **套用設定**將套用於 COM plus 設定 FileAct 和互動的介面卡。  
  
5.  在 [**摘要**檢閱，然後選取**下一步]**。  
  
6.  完成設定時，檢閱元件的清單。 核取記號表示已成功設定元件。 "X"表示該元件的問題。  
  
    > [!NOTE]
    >  使用**Logfile**連結，即可檢視設定事件。  
  
7.  選取 **完成**以完成設定。 **概觀**顯示執行階段元件的目前組態狀態。  

接下來，建立要執行這些配接器的主控件和主控件執行個體。

## <a name="step-2-create-the-host-and-host-instances"></a>步驟 2： 建立主應用程式和主控件執行個體

我們建議您建立 FileAct 配接器專用的主機和 InterAct 配接器的個別專用的主機。 每個配接器，建立至少一個主控件執行個體。  

[管理 BizTalk 主控件和主控件執行個體](../../core/managing-biztalk-hosts-and-host-instances.md)列出的步驟建立主控件和主控件執行個體。 

建立之後下, 一個步驟是新增的傳送處理常式，並使用用戶端的訊息交易夥伴建立 SWIFT Alliance 閘道 (SAG) 中。

## <a name="step-3-create-the-send-handler"></a>步驟 3： 建立傳送處理常式

您在使用 FileAct 和 InterAct 傳送處理常式屬性為 傳送埠組態值，如果個別 FileAct 上未設定屬性或 InterAct 傳送埠。 
  
1. 在  **BizTalk Server 管理**主控台中，展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。  
  
2. 選取  **FileAct**或是**InterAct**配接器。 在右窗格中，按兩下傳送處理常式。  
  
3. 在 **主機名稱**下拉式清單中，選取您在上一節中建立的主控件。 然後選取**屬性**。  
  
4. 在 **傳輸屬性**，選取**引數**屬性，並輸入下列引數為：  
  
    `-SagMessagePartner <Client Message Partner created in SAG\>`
  
   > [!NOTE]
   >  取代 <`Client Message Partner created in SAG`> 的用戶端訊息的夥伴名稱。 保留的密碼編譯模式、 FACrypto 模式和記錄訊息屬性的預設值。  
  
5. 選取 **確定**以儲存變更，然後關閉 屬性 視窗。 
  
6. 底下**平台設定**，選取**主控件執行個體**。  
  
7. 重新啟動主控件執行個體： 

   - FileAct 主控件執行個體，以滑鼠右鍵按一下並**重新啟動**
   - 以滑鼠右鍵按一下互動的主控件執行個體，並**重新啟動**。  

接下來，輸入 SWIFTNet paramfile 中的伺服器訊息合作夥伴，若要啟用 FileAct 和 InterAct 接收配接器。
  
## <a name="step-4-configure-the-swiftnet-param-file"></a>步驟 4： 設定 SWIFTNet 參數檔案

若要啟用 FileAct 和 InterAct 接收配接器初始化的值，必須輸入 SWIFTNet paramfile SAG 中建立的協力廠商伺服器訊息。 通常位於 paramfile `c:\SWIFTAlliance\RA\<remote access instance name\>\cfg\paramfile`。 設定 paramfile 後，開始**SnlReceiver.exe**。  
  
1. 開啟**SWIFTNet paramfile**。 在以標記的位置 」 “***” 「 新增下列。 請注意，`AdapterType`值可以是`Interact`或`Fileact`。  
  
     ```spawn "snlreceiver -SagMessagePartner <Server MessagePartnerName\> -AdapterMode <AdapterType\>"```  
       
  
   ```  
    username:snlowner  
    subsystem_name:SampleSubsystem  
    #subsystem_group: SampleSubsystem  
    #subsystem_dependency:Support,Swarm  
    subsystem_nature:critical  
    subsystem_start:  
    ***  
    *END  
    subsystem_stop:  
    *KILL9:snlreceiver  
    *END  
    subsystem_status:  
    *NB:1:snlreceiver  
    *END  
    start_event:SNL001:subsystem SampleSubsystem is up  
    stop_event:SNL002:subsystem SampleSubsystem is down  
   ```  
  
> [!NOTE]
>  在開始 SNLreceiver 之前，啟用接收埠配接器會使用 （FileAct 或互動）。  
  
2. 啟動和停止 SnlReceiver.exe:

    1.  在桌面上，選取**遠端 API**圖示以開啟遠端 API 的命令提示字元。  
  
    2.  在命令提示字元中，輸入`Swiftnet start`。 選取 enter 鍵以啟動 SnlReceiver.exe。  
  
    3.  在命令提示字元中，輸入`Swiftnet stop`。 選取 enter 鍵以停止 SnlReceiver.exe。  

  
接下來，更新檔案**autoexec.bat**設定 SWIFT 環境變數。

## <a name="step-5-update-autoexecbat-to-configure-the-receive-adapters"></a>若要設定的接收配接器的步驟 5： 更新 autoexec.bat

更新**autoexec.bat**安裝所在的電腦上設定 SWIFT 環境變數檔案[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]接收配接器。 從已安裝的路徑中，接收配接器的系統產生的環境變數`c:\SWIFTAlliance`名為接收配接器的執行個體**Ra1**。 更新您的設定適當的 SWIFT 的環境變數。  
  
 Autoexe.bat 檔案範例如下：
  
```  
SET COMPUTERNAME=<Machine Name>  
SET GENLOG_DIR=C:\SWIFTAlliance\RA\Ra1\log  
SET GENUTIL_DIR=C:\SWIFTAlliance\RA\bin  
SET HOMEDRIVE=C:  
SET LOGONSERVER=\\SERVERNAME  
SET OSA_DIR=C:\SWIFTAlliance\RA\Ra1\log  
SET OSA_INSTANCE=Ra1  
SET PKIEXECDIR=C:\SWIFTAlliance\RA  
SET SAGRA_HOME=C:\SWIFTAlliance\RA  
SET SESSIONNAME=RDP-Tcp#1  
SET SLP_ENV=DEFAULT  
SET SLP_FILE=server.slp  
SET SNL_DOMAIN_NAME=Ra1  
SET SPK_DATA_DIR=C:\SWIFTAlliance\RA\data\pki  
SET SWNET_BIN_PATH=C:\SWIFTAlliance\RA\Ra1\bin  
SET SWNET_CFG_PATH=C:\SWIFTAlliance\RA\Ra1\cfg  
SET SWNET_HOME=C:\SWIFTAlliance\RA  
SET SWNET_HOST=HOSTNAME  
SET SWNET_INST=Ra1  
SET SWNET_LOG_PATH=C:\SWIFTAlliance\RA\Ra1\log  
SET SWNET_SLP_PATH=C:\SWIFTAlliance\RA\data\  
SET SWNET_VERSION=5.0.20  
SET SWTRACE=C:\SWIFTAlliance\RA\Ra1\log  
SET Path=%PATH%;C:\SWIFTAlliance\RA\bin  
SET Path=%PATH%;C:\SWIFTAlliance\RA\lib  
  
```  
  
## <a name="see-some-examples"></a>查看一些範例
例如 FileAct 和 InterAct 訊息的詳細資訊，請參閱[範例 InterAct 和 FileAct 訊息](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md)。  
  
## <a name="see-also"></a>另請參閱  

[安裝 FileAct 和 InterAct 配接器](../../adapters-and-accelerators/fileact-interact/install-the-fileact-and-interact-adapter.md)  
[解除安裝 FileAct 和 InterAct 配接器](../../adapters-and-accelerators/fileact-interact/uninstall-or-repair-the-fileact-and-interact-adapter.md)  
[閱讀安裝已知問題](../../adapters-and-accelerators/fileact-interact/read-the-installation-known-issues.md)
