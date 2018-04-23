---
title: 設定 FileAct 和互動配接器 |Microsoft 文件
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
ms.openlocfilehash: ca2bc3aa739bf6914ea9943d84d58d44b1506323
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="configure-the-fileact-and-interact-adapter"></a><span data-ttu-id="9701b-102">設定 FileAct 和互動配接器</span><span class="sxs-lookup"><span data-stu-id="9701b-102">Configure the FileAct and InterAct Adapter</span></span>
<span data-ttu-id="9701b-103">設定所使用的不同成品[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]執行階段。</span><span class="sxs-lookup"><span data-stu-id="9701b-103">Configure the different artifacts used by the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] runtime.</span></span> 

  
## <a name="prerequisites"></a><span data-ttu-id="9701b-104">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="9701b-104">Prerequisites</span></span>  
   
-   <span data-ttu-id="9701b-105">安裝 [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9701b-105">Install the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]</span></span>
  
-   <span data-ttu-id="9701b-106">成員的身分登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組</span><span class="sxs-lookup"><span data-stu-id="9701b-106">Sign in as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group</span></span>
  
-   <span data-ttu-id="9701b-107">確認 SQL Server 正在執行</span><span class="sxs-lookup"><span data-stu-id="9701b-107">Confirm SQL Server is running</span></span>
  
## <a name="step-1-configure-the-fileact-and-interact-adapter"></a><span data-ttu-id="9701b-108">步驟 1： 設定 FileAct 和 InterAct 配接器</span><span class="sxs-lookup"><span data-stu-id="9701b-108">Step 1: Configure the FileAct and InterAct adapter</span></span>  
  
1.  <span data-ttu-id="9701b-109">在**Microsoft BizTalk FileAct 與互動的介面卡設定**精靈，請移至**概觀**。</span><span class="sxs-lookup"><span data-stu-id="9701b-109">In the **Microsoft BizTalk FileAct and InterAct Adapter Configuration** wizard, go to **Overview**.</span></span> <span data-ttu-id="9701b-110">在左窗格中，選取**執行階段**來設定配接器執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="9701b-110">In the left pane, select **Runtime** to configure the runtime components of the adapters.</span></span>  
  
2.  <span data-ttu-id="9701b-111">在**執行階段組態**下**帳戶**，選取省略符號 […]，輸入 COM plus 儲存與轉送模式的組態。</span><span class="sxs-lookup"><span data-stu-id="9701b-111">In **Runtime Configuration**, under **Account**, select the ellipsis […] to enter the COM plus configuration for the Store and Forward mode.</span></span>  
  
3.  <span data-ttu-id="9701b-112">在**使用者認證**，輸入使用者名稱 (在*網域 \ 使用者名稱*格式) 和 COM plus 組態中所使用之帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="9701b-112">In **User Credentials**, enter the user name (in the *domain\user name* format) and password for the account used in the COM plus configuration.</span></span> <span data-ttu-id="9701b-113">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9701b-113">Select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9701b-114">A**使用者認證**會出現警告，如果您輸入的帳戶具有比建議使用較高的權限。</span><span class="sxs-lookup"><span data-stu-id="9701b-114">A **User Credentials** warning appears if the account you entered has higher privileges than are recommended.</span></span> <span data-ttu-id="9701b-115">選取**是**才能繼續。</span><span class="sxs-lookup"><span data-stu-id="9701b-115">Select **Yes** to continue.</span></span>
  
4.  <span data-ttu-id="9701b-116">選取**套用組態**FileAct 和互動的介面卡套用 COM plus 組態。</span><span class="sxs-lookup"><span data-stu-id="9701b-116">Select **Apply configuration** to apply the COM plus configuration to the FileAct and InterAct Adapter.</span></span>  
  
5.  <span data-ttu-id="9701b-117">在**摘要**、 檢閱，並選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9701b-117">In the **Summary**, review, and select **Next**.</span></span>  
  
6.  <span data-ttu-id="9701b-118">完成設定時，檢閱元件的清單。</span><span class="sxs-lookup"><span data-stu-id="9701b-118">When the configuration completes, review the list of components.</span></span> <span data-ttu-id="9701b-119">核取記號表示已成功設定元件。</span><span class="sxs-lookup"><span data-stu-id="9701b-119">A check mark means that the component is configured successfully.</span></span> <span data-ttu-id="9701b-120">"X"表示該元件的問題。</span><span class="sxs-lookup"><span data-stu-id="9701b-120">An "X" means that there is a problem with that component.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9701b-121">使用**Logfile**連結，即可檢視設定事件。</span><span class="sxs-lookup"><span data-stu-id="9701b-121">Use the **Logfile** link to view the configuration events.</span></span>  
  
7.  <span data-ttu-id="9701b-122">選取**完成**以完成設定。</span><span class="sxs-lookup"><span data-stu-id="9701b-122">Select **Finish** to complete the configuration.</span></span> <span data-ttu-id="9701b-123">**概觀**顯示執行階段元件的目前組態狀態。</span><span class="sxs-lookup"><span data-stu-id="9701b-123">The **Overview** shows the current configuration status for the Runtime components.</span></span>  

<span data-ttu-id="9701b-124">接下來，建立執行這些配接器的主控件和主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="9701b-124">Next, create the host and host instances to run these adapters.</span></span>

## <a name="step-2-create-the-host-and-host-instances"></a><span data-ttu-id="9701b-125">步驟 2： 建立主控件和主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="9701b-125">Step 2: Create the host and host instances</span></span>

<span data-ttu-id="9701b-126">我們建議您建立 FileAct 配接器專用的主機和 InterAct 配接器是個別的專用的主機。</span><span class="sxs-lookup"><span data-stu-id="9701b-126">We recommend that you create a dedicated host for the FileAct adapter and a separate dedicated host for the InterAct adapter.</span></span> <span data-ttu-id="9701b-127">每個配接器，建立至少一個主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="9701b-127">For each adapter, create at least one host instance.</span></span>  

<span data-ttu-id="9701b-128">[管理 BizTalk 主控件和主控件執行個體](../../core/managing-biztalk-hosts-and-host-instances.md)列出的步驟建立主控件和主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="9701b-128">[Managing BizTalk Hosts and Host Instances](../../core/managing-biztalk-hosts-and-host-instances.md) list the steps to create hosts and host instances.</span></span> 

<span data-ttu-id="9701b-129">建立之後下, 一個步驟是加入的傳送處理常式，並使用用戶端的訊息交易夥伴建立 SWIFT 聯盟閘道 (SAG) 中。</span><span class="sxs-lookup"><span data-stu-id="9701b-129">Once created, the next step is to add the send handler, and use the Client Message Partner you created in the SWIFT Alliance Gateway (SAG).</span></span>

## <a name="step-3-create-the-send-handler"></a><span data-ttu-id="9701b-130">步驟 3： 建立傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="9701b-130">Step 3: Create the send handler</span></span>

<span data-ttu-id="9701b-131">使用 FileAct 和 InterAct 傳送處理常式屬性為 傳送連接埠組態值，如果屬性未設定在個別 FileAct 或互動的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="9701b-131">You use the FileAct and InterAct send handler properties as the send port configuration values, if the properties are not set on the individual FileAct or InterAct send port.</span></span> 
  
1.  <span data-ttu-id="9701b-132">在**BizTalk Server 管理**主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="9701b-132">In the **BizTalk Server Administration** console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="9701b-133">選取**FileAct**或**互動**配接器。</span><span class="sxs-lookup"><span data-stu-id="9701b-133">Select the **FileAct** or **InterAct** adapter.</span></span> <span data-ttu-id="9701b-134">在右窗格中，按兩下傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="9701b-134">In the right pane, double-click the send handler.</span></span>  
  
3.  <span data-ttu-id="9701b-135">在**主機名稱**下拉式清單中，選取您在上一節中建立的主控件。</span><span class="sxs-lookup"><span data-stu-id="9701b-135">In the **Host name** drop-down list, select the host you created in the previous section.</span></span> <span data-ttu-id="9701b-136">然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="9701b-136">Then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="9701b-137">在**傳輸屬性**，選取**引數**屬性，並輸入下列引數為：</span><span class="sxs-lookup"><span data-stu-id="9701b-137">In the **Transport Properties**, select the **Argument** property, and enter the following argument as:</span></span>  
  
     `-SagMessagePartner <Client Message Partner created in SAG\>`
  
    > [!NOTE]
    >  <span data-ttu-id="9701b-138">取代 <`Client Message Partner created in SAG`> 用戶端訊息夥伴的名稱。</span><span class="sxs-lookup"><span data-stu-id="9701b-138">Replace <`Client Message Partner created in SAG`> with the name of the client message partner.</span></span> <span data-ttu-id="9701b-139">保留預設值為密碼編譯模式、 FACrypto 模式和記錄訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="9701b-139">Leave the default values for the Crypto Mode, FACrypto Mode, and LogMessages properties.</span></span>  
  
5.  <span data-ttu-id="9701b-140">選取**確定**以儲存變更，然後關閉 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="9701b-140">Select **OK** to save your changes, and then to close the properties window.</span></span> 
  
6.  <span data-ttu-id="9701b-141">在下**平台設定**，選取**主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="9701b-141">Under **Platform Settings**, select **Host Instances**.</span></span>  
  
7. <span data-ttu-id="9701b-142">重新啟動主控件執行個體：</span><span class="sxs-lookup"><span data-stu-id="9701b-142">Restart the host instances:</span></span> 

  - <span data-ttu-id="9701b-143">FileAct 主控件執行個體，以滑鼠右鍵按一下和**重新啟動**</span><span class="sxs-lookup"><span data-stu-id="9701b-143">Right-click the FileAct host instance, and **Restart**</span></span>
  - <span data-ttu-id="9701b-144">以滑鼠右鍵按一下互動的主控件執行個體，和**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="9701b-144">Right-click the InterAct host instance, and **Restart**.</span></span>  

<span data-ttu-id="9701b-145">接下來，輸入伺服器訊息夥伴 SWIFTNet paramfile 中的啟用 FileAct 和 InterAct 接收配接器。</span><span class="sxs-lookup"><span data-stu-id="9701b-145">Next, enter the server message partners in the SWIFTNet paramfile to enable the FileAct and InterAct receive adapters.</span></span>
  
## <a name="step-4-configure-the-swiftnet-param-file"></a><span data-ttu-id="9701b-146">步驟 4： 設定 SWIFTNet param 檔案</span><span class="sxs-lookup"><span data-stu-id="9701b-146">Step 4: Configure the SWIFTNet param file</span></span>

<span data-ttu-id="9701b-147">若要啟用 FileAct 和 InterAct 接收配接器初始化為值，必須輸入 SWIFTNet paramfile SAG 中建立的協力廠商伺服器訊息。</span><span class="sxs-lookup"><span data-stu-id="9701b-147">To enable the FileAct and InterAct receive adapters to initialize with the values, the Server message partners created in SAG must be entered in the SWIFTNet paramfile.</span></span> <span data-ttu-id="9701b-148">Paramfile 通常位於`c:\SWIFTAlliance\RA\<remote access instance name\>\cfg\paramfile`。</span><span class="sxs-lookup"><span data-stu-id="9701b-148">The paramfile is typically located in `c:\SWIFTAlliance\RA\<remote access instance name\>\cfg\paramfile`.</span></span> <span data-ttu-id="9701b-149">設定 paramfile 之後，請啟動**SnlReceiver.exe**。</span><span class="sxs-lookup"><span data-stu-id="9701b-149">After you configure the paramfile, start **SnlReceiver.exe**.</span></span>  
  
1. <span data-ttu-id="9701b-150">開啟**SWIFTNet paramfile**。</span><span class="sxs-lookup"><span data-stu-id="9701b-150">Open the **SWIFTNet paramfile**.</span></span> <span data-ttu-id="9701b-151">在以標記的位置 」 “\*\*\*” 「 新增下列。</span><span class="sxs-lookup"><span data-stu-id="9701b-151">In the location marked with "\*\*\*" add the following.</span></span> <span data-ttu-id="9701b-152">請注意，`AdapterType`值可以是`Interact`或`Fileact`。</span><span class="sxs-lookup"><span data-stu-id="9701b-152">Note that the `AdapterType` value can be `Interact` or `Fileact`.</span></span>  
  
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
    >  <span data-ttu-id="9701b-153">SNLreceiver 前，啟用接收埠的配接器會使用 （FileAct 或互動）。</span><span class="sxs-lookup"><span data-stu-id="9701b-153">Before you start SNLreceiver, enable the receive ports for the adapter you are using (FileAct or InterAct).</span></span>  
  
2. <span data-ttu-id="9701b-154">啟動和停止 SnlReceiver.exe:</span><span class="sxs-lookup"><span data-stu-id="9701b-154">Start and stop SnlReceiver.exe:</span></span>

    1.  <span data-ttu-id="9701b-155">在桌面上，選取**遠端 API**圖示以開啟 遠端應用程式開發介面的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9701b-155">On the desktop, select the **Remote API** icon to open the Remote API command prompt.</span></span>  
  
    2.  <span data-ttu-id="9701b-156">在命令提示字元中，輸入`Swiftnet start`。</span><span class="sxs-lookup"><span data-stu-id="9701b-156">At the command prompt, type `Swiftnet start`.</span></span> <span data-ttu-id="9701b-157">選取 ENTER 開始 SnlReceiver.exe。</span><span class="sxs-lookup"><span data-stu-id="9701b-157">Select ENTER to start SnlReceiver.exe.</span></span>  
  
    3.  <span data-ttu-id="9701b-158">在命令提示字元中，輸入`Swiftnet stop`。</span><span class="sxs-lookup"><span data-stu-id="9701b-158">At the command prompt, type `Swiftnet stop`.</span></span> <span data-ttu-id="9701b-159">選取 ENTER，以停止 SnlReceiver.exe。</span><span class="sxs-lookup"><span data-stu-id="9701b-159">Select ENTER to stop SnlReceiver.exe.</span></span>  

  
<span data-ttu-id="9701b-160">接下來，更新檔案**autoexec.bat**設定 SWIFT 環境變數。</span><span class="sxs-lookup"><span data-stu-id="9701b-160">Next, update the file **autoexec.bat** to set the SWIFT environment variables.</span></span>

## <a name="step-5-update-autoexecbat-to-configure-the-receive-adapters"></a><span data-ttu-id="9701b-161">若要設定的接收配接器的步驟 5： 更新 autoexec.bat</span><span class="sxs-lookup"><span data-stu-id="9701b-161">Step 5: Update autoexec.bat to configure the receive adapters</span></span>

<span data-ttu-id="9701b-162">更新**autoexec.bat**安裝所在的電腦上設定環境變數 SWIFT 檔案[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]接收配接器。</span><span class="sxs-lookup"><span data-stu-id="9701b-162">Update the **autoexec.bat** file to set the SWIFT environment variables on the computer where you installed the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] receive adapters.</span></span> <span data-ttu-id="9701b-163">環境變數會從已安裝的路徑中，接收配接器的系統產生`c:\SWIFTAlliance`與名為接收配接器的執行個體**Ra1**。</span><span class="sxs-lookup"><span data-stu-id="9701b-163">The environment variables are generated from the system that has the receive adapter installed in the path `c:\SWIFTAlliance` with an instance of the receive adapter named **Ra1**.</span></span> <span data-ttu-id="9701b-164">更新您的設定適當的 SWIFT 的環境變數。</span><span class="sxs-lookup"><span data-stu-id="9701b-164">Update the SWIFT environment variables appropriately for your configuration.</span></span>  
  
 <span data-ttu-id="9701b-165">Autoexe.bat 檔案的範例如下：</span><span class="sxs-lookup"><span data-stu-id="9701b-165">The following is a sample of the autoexe.bat file:</span></span>
  
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
  
## <a name="see-some-examples"></a><span data-ttu-id="9701b-166">請參閱一些範例</span><span class="sxs-lookup"><span data-stu-id="9701b-166">See some examples</span></span>
<span data-ttu-id="9701b-167">FileAct 和 InterAct 訊息的範例，請參閱[範例進行互動，而且 FileAct 訊息](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="9701b-167">For examples of FileAct and InterAct messages, see [Sample InterAct and FileAct Messages](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9701b-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9701b-168">See Also</span></span>  

[<span data-ttu-id="9701b-169">安裝 FileAct 和 InterAct 配接器</span><span class="sxs-lookup"><span data-stu-id="9701b-169">Install the FileAct and InterAct Adapter</span></span>](../../adapters-and-accelerators/fileact-interact/install-the-fileact-and-interact-adapter.md)  
[<span data-ttu-id="9701b-170">解除安裝 FileAct 和 InterAct 配接器</span><span class="sxs-lookup"><span data-stu-id="9701b-170">Uninstall or repair the FileAct and InterAct adapter</span></span>](../../adapters-and-accelerators/fileact-interact/uninstall-or-repair-the-fileact-and-interact-adapter.md)  
[<span data-ttu-id="9701b-171">閱讀安裝已知問題</span><span class="sxs-lookup"><span data-stu-id="9701b-171">Read the installation known issues</span></span>](../../adapters-and-accelerators/fileact-interact/read-the-installation-known-issues.md)
