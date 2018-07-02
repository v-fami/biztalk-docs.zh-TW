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
# <a name="configure-the-fileact-and-interact-adapter"></a><span data-ttu-id="2adf0-102">設定 FileAct 和 InterAct 配接器</span><span class="sxs-lookup"><span data-stu-id="2adf0-102">Configure the FileAct and InterAct Adapter</span></span>
<span data-ttu-id="2adf0-103">設定所使用的不同成品[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]執行階段。</span><span class="sxs-lookup"><span data-stu-id="2adf0-103">Configure the different artifacts used by the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] runtime.</span></span> 

  
## <a name="prerequisites"></a><span data-ttu-id="2adf0-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="2adf0-104">Prerequisites</span></span>  
   
- <span data-ttu-id="2adf0-105">安裝 [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2adf0-105">Install the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]</span></span>
  
- <span data-ttu-id="2adf0-106">成員的身分登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組</span><span class="sxs-lookup"><span data-stu-id="2adf0-106">Sign in as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group</span></span>
  
- <span data-ttu-id="2adf0-107">確認 SQL Server 正在執行</span><span class="sxs-lookup"><span data-stu-id="2adf0-107">Confirm SQL Server is running</span></span>
  
## <a name="step-1-configure-the-fileact-and-interact-adapter"></a><span data-ttu-id="2adf0-108">步驟 1： 設定 FileAct 和 InterAct 配接器</span><span class="sxs-lookup"><span data-stu-id="2adf0-108">Step 1: Configure the FileAct and InterAct adapter</span></span>  
  
1.  <span data-ttu-id="2adf0-109">在  **Microsoft BizTalk FileAct 和互動的配接器組態**精靈中，移至**概觀**。</span><span class="sxs-lookup"><span data-stu-id="2adf0-109">In the **Microsoft BizTalk FileAct and InterAct Adapter Configuration** wizard, go to **Overview**.</span></span> <span data-ttu-id="2adf0-110">在左窗格中，選取**執行階段**設定配接器執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="2adf0-110">In the left pane, select **Runtime** to configure the runtime components of the adapters.</span></span>  
  
2.  <span data-ttu-id="2adf0-111">在 **執行階段組態**下方**帳戶**，選取省略符號 [...]，輸入 COM plus 存放與轉寄 」 模式的組態。</span><span class="sxs-lookup"><span data-stu-id="2adf0-111">In **Runtime Configuration**, under **Account**, select the ellipsis […] to enter the COM plus configuration for the Store and Forward mode.</span></span>  
  
3.  <span data-ttu-id="2adf0-112">在 **使用者認證**，輸入使用者名稱 (在*網域 \ 使用者名稱*格式) 和 COM plus 組態中所使用之帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="2adf0-112">In **User Credentials**, enter the user name (in the *domain\user name* format) and password for the account used in the COM plus configuration.</span></span> <span data-ttu-id="2adf0-113">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="2adf0-113">Select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2adf0-114">A**使用者認證**如果您輸入的帳戶有較高的權限比建議會出現警告。</span><span class="sxs-lookup"><span data-stu-id="2adf0-114">A **User Credentials** warning appears if the account you entered has higher privileges than are recommended.</span></span> <span data-ttu-id="2adf0-115">選取 **是**以繼續。</span><span class="sxs-lookup"><span data-stu-id="2adf0-115">Select **Yes** to continue.</span></span>
  
4.  <span data-ttu-id="2adf0-116">選取 **套用設定**將套用於 COM plus 設定 FileAct 和互動的介面卡。</span><span class="sxs-lookup"><span data-stu-id="2adf0-116">Select **Apply configuration** to apply the COM plus configuration to the FileAct and InterAct Adapter.</span></span>  
  
5.  <span data-ttu-id="2adf0-117">在 [**摘要**檢閱，然後選取**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2adf0-117">In the **Summary**, review, and select **Next**.</span></span>  
  
6.  <span data-ttu-id="2adf0-118">完成設定時，檢閱元件的清單。</span><span class="sxs-lookup"><span data-stu-id="2adf0-118">When the configuration completes, review the list of components.</span></span> <span data-ttu-id="2adf0-119">核取記號表示已成功設定元件。</span><span class="sxs-lookup"><span data-stu-id="2adf0-119">A check mark means that the component is configured successfully.</span></span> <span data-ttu-id="2adf0-120">"X"表示該元件的問題。</span><span class="sxs-lookup"><span data-stu-id="2adf0-120">An "X" means that there is a problem with that component.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2adf0-121">使用**Logfile**連結，即可檢視設定事件。</span><span class="sxs-lookup"><span data-stu-id="2adf0-121">Use the **Logfile** link to view the configuration events.</span></span>  
  
7.  <span data-ttu-id="2adf0-122">選取 **完成**以完成設定。</span><span class="sxs-lookup"><span data-stu-id="2adf0-122">Select **Finish** to complete the configuration.</span></span> <span data-ttu-id="2adf0-123">**概觀**顯示執行階段元件的目前組態狀態。</span><span class="sxs-lookup"><span data-stu-id="2adf0-123">The **Overview** shows the current configuration status for the Runtime components.</span></span>  

<span data-ttu-id="2adf0-124">接下來，建立要執行這些配接器的主控件和主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="2adf0-124">Next, create the host and host instances to run these adapters.</span></span>

## <a name="step-2-create-the-host-and-host-instances"></a><span data-ttu-id="2adf0-125">步驟 2： 建立主應用程式和主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="2adf0-125">Step 2: Create the host and host instances</span></span>

<span data-ttu-id="2adf0-126">我們建議您建立 FileAct 配接器專用的主機和 InterAct 配接器的個別專用的主機。</span><span class="sxs-lookup"><span data-stu-id="2adf0-126">We recommend that you create a dedicated host for the FileAct adapter and a separate dedicated host for the InterAct adapter.</span></span> <span data-ttu-id="2adf0-127">每個配接器，建立至少一個主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="2adf0-127">For each adapter, create at least one host instance.</span></span>  

<span data-ttu-id="2adf0-128">[管理 BizTalk 主控件和主控件執行個體](../../core/managing-biztalk-hosts-and-host-instances.md)列出的步驟建立主控件和主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="2adf0-128">[Managing BizTalk Hosts and Host Instances](../../core/managing-biztalk-hosts-and-host-instances.md) list the steps to create hosts and host instances.</span></span> 

<span data-ttu-id="2adf0-129">建立之後下, 一個步驟是新增的傳送處理常式，並使用用戶端的訊息交易夥伴建立 SWIFT Alliance 閘道 (SAG) 中。</span><span class="sxs-lookup"><span data-stu-id="2adf0-129">Once created, the next step is to add the send handler, and use the Client Message Partner you created in the SWIFT Alliance Gateway (SAG).</span></span>

## <a name="step-3-create-the-send-handler"></a><span data-ttu-id="2adf0-130">步驟 3： 建立傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="2adf0-130">Step 3: Create the send handler</span></span>

<span data-ttu-id="2adf0-131">您在使用 FileAct 和 InterAct 傳送處理常式屬性為 傳送埠組態值，如果個別 FileAct 上未設定屬性或 InterAct 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="2adf0-131">You use the FileAct and InterAct send handler properties as the send port configuration values, if the properties are not set on the individual FileAct or InterAct send port.</span></span> 
  
1. <span data-ttu-id="2adf0-132">在  **BizTalk Server 管理**主控台中，展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="2adf0-132">In the **BizTalk Server Administration** console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2. <span data-ttu-id="2adf0-133">選取  **FileAct**或是**InterAct**配接器。</span><span class="sxs-lookup"><span data-stu-id="2adf0-133">Select the **FileAct** or **InterAct** adapter.</span></span> <span data-ttu-id="2adf0-134">在右窗格中，按兩下傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="2adf0-134">In the right pane, double-click the send handler.</span></span>  
  
3. <span data-ttu-id="2adf0-135">在 **主機名稱**下拉式清單中，選取您在上一節中建立的主控件。</span><span class="sxs-lookup"><span data-stu-id="2adf0-135">In the **Host name** drop-down list, select the host you created in the previous section.</span></span> <span data-ttu-id="2adf0-136">然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2adf0-136">Then select **Properties**.</span></span>  
  
4. <span data-ttu-id="2adf0-137">在 **傳輸屬性**，選取**引數**屬性，並輸入下列引數為：</span><span class="sxs-lookup"><span data-stu-id="2adf0-137">In the **Transport Properties**, select the **Argument** property, and enter the following argument as:</span></span>  
  
    `-SagMessagePartner <Client Message Partner created in SAG\>`
  
   > [!NOTE]
   >  <span data-ttu-id="2adf0-138">取代 <`Client Message Partner created in SAG`> 的用戶端訊息的夥伴名稱。</span><span class="sxs-lookup"><span data-stu-id="2adf0-138">Replace <`Client Message Partner created in SAG`> with the name of the client message partner.</span></span> <span data-ttu-id="2adf0-139">保留的密碼編譯模式、 FACrypto 模式和記錄訊息屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="2adf0-139">Leave the default values for the Crypto Mode, FACrypto Mode, and LogMessages properties.</span></span>  
  
5. <span data-ttu-id="2adf0-140">選取 **確定**以儲存變更，然後關閉 屬性 視窗。</span><span class="sxs-lookup"><span data-stu-id="2adf0-140">Select **OK** to save your changes, and then to close the properties window.</span></span> 
  
6. <span data-ttu-id="2adf0-141">底下**平台設定**，選取**主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="2adf0-141">Under **Platform Settings**, select **Host Instances**.</span></span>  
  
7. <span data-ttu-id="2adf0-142">重新啟動主控件執行個體：</span><span class="sxs-lookup"><span data-stu-id="2adf0-142">Restart the host instances:</span></span> 

   - <span data-ttu-id="2adf0-143">FileAct 主控件執行個體，以滑鼠右鍵按一下並**重新啟動**</span><span class="sxs-lookup"><span data-stu-id="2adf0-143">Right-click the FileAct host instance, and **Restart**</span></span>
   - <span data-ttu-id="2adf0-144">以滑鼠右鍵按一下互動的主控件執行個體，並**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="2adf0-144">Right-click the InterAct host instance, and **Restart**.</span></span>  

<span data-ttu-id="2adf0-145">接下來，輸入 SWIFTNet paramfile 中的伺服器訊息合作夥伴，若要啟用 FileAct 和 InterAct 接收配接器。</span><span class="sxs-lookup"><span data-stu-id="2adf0-145">Next, enter the server message partners in the SWIFTNet paramfile to enable the FileAct and InterAct receive adapters.</span></span>
  
## <a name="step-4-configure-the-swiftnet-param-file"></a><span data-ttu-id="2adf0-146">步驟 4： 設定 SWIFTNet 參數檔案</span><span class="sxs-lookup"><span data-stu-id="2adf0-146">Step 4: Configure the SWIFTNet param file</span></span>

<span data-ttu-id="2adf0-147">若要啟用 FileAct 和 InterAct 接收配接器初始化的值，必須輸入 SWIFTNet paramfile SAG 中建立的協力廠商伺服器訊息。</span><span class="sxs-lookup"><span data-stu-id="2adf0-147">To enable the FileAct and InterAct receive adapters to initialize with the values, the Server message partners created in SAG must be entered in the SWIFTNet paramfile.</span></span> <span data-ttu-id="2adf0-148">通常位於 paramfile `c:\SWIFTAlliance\RA\<remote access instance name\>\cfg\paramfile`。</span><span class="sxs-lookup"><span data-stu-id="2adf0-148">The paramfile is typically located in `c:\SWIFTAlliance\RA\<remote access instance name\>\cfg\paramfile`.</span></span> <span data-ttu-id="2adf0-149">設定 paramfile 後，開始**SnlReceiver.exe**。</span><span class="sxs-lookup"><span data-stu-id="2adf0-149">After you configure the paramfile, start **SnlReceiver.exe**.</span></span>  
  
1. <span data-ttu-id="2adf0-150">開啟**SWIFTNet paramfile**。</span><span class="sxs-lookup"><span data-stu-id="2adf0-150">Open the **SWIFTNet paramfile**.</span></span> <span data-ttu-id="2adf0-151">在以標記的位置 」 “\*\*\*” 「 新增下列。</span><span class="sxs-lookup"><span data-stu-id="2adf0-151">In the location marked with "\*\*\*" add the following.</span></span> <span data-ttu-id="2adf0-152">請注意，`AdapterType`值可以是`Interact`或`Fileact`。</span><span class="sxs-lookup"><span data-stu-id="2adf0-152">Note that the `AdapterType` value can be `Interact` or `Fileact`.</span></span>  
  
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
>  <span data-ttu-id="2adf0-153">在開始 SNLreceiver 之前，啟用接收埠配接器會使用 （FileAct 或互動）。</span><span class="sxs-lookup"><span data-stu-id="2adf0-153">Before you start SNLreceiver, enable the receive ports for the adapter you are using (FileAct or InterAct).</span></span>  
  
2. <span data-ttu-id="2adf0-154">啟動和停止 SnlReceiver.exe:</span><span class="sxs-lookup"><span data-stu-id="2adf0-154">Start and stop SnlReceiver.exe:</span></span>

    1.  <span data-ttu-id="2adf0-155">在桌面上，選取**遠端 API**圖示以開啟遠端 API 的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="2adf0-155">On the desktop, select the **Remote API** icon to open the Remote API command prompt.</span></span>  
  
    2.  <span data-ttu-id="2adf0-156">在命令提示字元中，輸入`Swiftnet start`。</span><span class="sxs-lookup"><span data-stu-id="2adf0-156">At the command prompt, type `Swiftnet start`.</span></span> <span data-ttu-id="2adf0-157">選取 enter 鍵以啟動 SnlReceiver.exe。</span><span class="sxs-lookup"><span data-stu-id="2adf0-157">Select ENTER to start SnlReceiver.exe.</span></span>  
  
    3.  <span data-ttu-id="2adf0-158">在命令提示字元中，輸入`Swiftnet stop`。</span><span class="sxs-lookup"><span data-stu-id="2adf0-158">At the command prompt, type `Swiftnet stop`.</span></span> <span data-ttu-id="2adf0-159">選取 enter 鍵以停止 SnlReceiver.exe。</span><span class="sxs-lookup"><span data-stu-id="2adf0-159">Select ENTER to stop SnlReceiver.exe.</span></span>  

  
<span data-ttu-id="2adf0-160">接下來，更新檔案**autoexec.bat**設定 SWIFT 環境變數。</span><span class="sxs-lookup"><span data-stu-id="2adf0-160">Next, update the file **autoexec.bat** to set the SWIFT environment variables.</span></span>

## <a name="step-5-update-autoexecbat-to-configure-the-receive-adapters"></a><span data-ttu-id="2adf0-161">若要設定的接收配接器的步驟 5： 更新 autoexec.bat</span><span class="sxs-lookup"><span data-stu-id="2adf0-161">Step 5: Update autoexec.bat to configure the receive adapters</span></span>

<span data-ttu-id="2adf0-162">更新**autoexec.bat**安裝所在的電腦上設定 SWIFT 環境變數檔案[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]接收配接器。</span><span class="sxs-lookup"><span data-stu-id="2adf0-162">Update the **autoexec.bat** file to set the SWIFT environment variables on the computer where you installed the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] receive adapters.</span></span> <span data-ttu-id="2adf0-163">從已安裝的路徑中，接收配接器的系統產生的環境變數`c:\SWIFTAlliance`名為接收配接器的執行個體**Ra1**。</span><span class="sxs-lookup"><span data-stu-id="2adf0-163">The environment variables are generated from the system that has the receive adapter installed in the path `c:\SWIFTAlliance` with an instance of the receive adapter named **Ra1**.</span></span> <span data-ttu-id="2adf0-164">更新您的設定適當的 SWIFT 的環境變數。</span><span class="sxs-lookup"><span data-stu-id="2adf0-164">Update the SWIFT environment variables appropriately for your configuration.</span></span>  
  
 <span data-ttu-id="2adf0-165">Autoexe.bat 檔案範例如下：</span><span class="sxs-lookup"><span data-stu-id="2adf0-165">The following is a sample of the autoexe.bat file:</span></span>
  
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
  
## <a name="see-some-examples"></a><span data-ttu-id="2adf0-166">查看一些範例</span><span class="sxs-lookup"><span data-stu-id="2adf0-166">See some examples</span></span>
<span data-ttu-id="2adf0-167">例如 FileAct 和 InterAct 訊息的詳細資訊，請參閱[範例 InterAct 和 FileAct 訊息](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="2adf0-167">For examples of FileAct and InterAct messages, see [Sample InterAct and FileAct Messages](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2adf0-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2adf0-168">See Also</span></span>  

[<span data-ttu-id="2adf0-169">安裝 FileAct 和 InterAct 配接器</span><span class="sxs-lookup"><span data-stu-id="2adf0-169">Install the FileAct and InterAct Adapter</span></span>](../../adapters-and-accelerators/fileact-interact/install-the-fileact-and-interact-adapter.md)  
[<span data-ttu-id="2adf0-170">解除安裝 FileAct 和 InterAct 配接器</span><span class="sxs-lookup"><span data-stu-id="2adf0-170">Uninstall or repair the FileAct and InterAct adapter</span></span>](../../adapters-and-accelerators/fileact-interact/uninstall-or-repair-the-fileact-and-interact-adapter.md)  
[<span data-ttu-id="2adf0-171">閱讀安裝已知問題</span><span class="sxs-lookup"><span data-stu-id="2adf0-171">Read the installation known issues</span></span>](../../adapters-and-accelerators/fileact-interact/read-the-installation-known-issues.md)
