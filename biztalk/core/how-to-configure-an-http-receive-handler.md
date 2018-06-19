---
title: 如何設定 HTTP 接收處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- permissions, receive handlers
- configuring [HTTP adapters], permissions
- HTTP adapters, receive handlers
- receive handlers, permissions
- configuring [HTTP adapters], receive handlers
- permissions, HTTP adapters
- receive handlers, HTTP adapters
- HTTP adapters, permissions
ms.assetid: c295489e-dbbb-44f7-bddb-d3cdfe302cf5
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b199ac25fea412e9912e7989ff1f16e6e0e8d9d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007607"
---
# <a name="how-to-configure-an-http-receive-handler"></a><span data-ttu-id="2093b-102">如何設定 HTTP 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="2093b-102">How to Configure an HTTP Receive Handler</span></span>
<span data-ttu-id="2093b-103">使用下列程序可設定 HTTP 接收處理常式的屬性。</span><span class="sxs-lookup"><span data-stu-id="2093b-103">Use the following procedure to configure the properties for an HTTP receive handler.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2093b-104">每個主控件只能有一個關聯的接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="2093b-104">Each host can have only one receive handler associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2093b-105">HTTP 接收配接器在「BizTalk 外掛式主控件」執行個體的環境中執行。</span><span class="sxs-lookup"><span data-stu-id="2093b-105">The HTTP receive adapter runs in the context of a BizTalk Isolated Host instance.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2093b-106">在使用 HTTP 或 SOAP 配接器處理常式時，建議您在 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 或 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 電腦上安裝這些處理常式的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="2093b-106">When using HTTP or SOAP adapter handlers, it is recommended that you install the host instances for these handlers on Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] computers.</span></span>  
  
### <a name="to-configure-the-general-properties-for-an-http-receive-handler"></a><span data-ttu-id="2093b-107">設定 HTTP 接收處理常式的一般屬性</span><span class="sxs-lookup"><span data-stu-id="2093b-107">To configure the general properties for an HTTP receive handler</span></span>  
  
1.  <span data-ttu-id="2093b-108">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="2093b-108">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="2093b-109">在展開的配接器清單中，按一下  **HTTP**在右窗格中，以滑鼠右鍵按一下您想要設定，然後按一下 接收處理常式**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2093b-109">In the expanded adapter list, click **HTTP,** in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="2093b-110">在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的接收處理常式的主機。</span><span class="sxs-lookup"><span data-stu-id="2093b-110">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  
  
4.  <span data-ttu-id="2093b-111">按一下**屬性**存取**批次大小**屬性之 http 接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="2093b-111">Click **Properties** to access the **Batch size** property for the HTTP receive handler.</span></span>  
  
5.  <span data-ttu-id="2093b-112">輸入介於 1 到 256 值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2093b-112">Enter a value from 1 to 256 and click **OK**.</span></span>  
  
6.  <span data-ttu-id="2093b-113">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2093b-113">Click **OK**.</span></span>  
  
 <span data-ttu-id="2093b-114">BizTalk Server 的設計，有效地處理訊息批次，而非快速處理單一訊息。</span><span class="sxs-lookup"><span data-stu-id="2093b-114">BizTalk Server is designed to process batches of messages effectively and not to process a single message very quickly.</span></span> <span data-ttu-id="2093b-115">因此，如果此接收處理常式將會用於「雙向/要求-回應」接收位置，那麼您就可以依照下列步驟，將延遲降到最低：</span><span class="sxs-lookup"><span data-stu-id="2093b-115">So if this receive handler is going to be used for two way/request-response receive locations then you can minimize latency by following these steps:</span></span>  
  
-   <span data-ttu-id="2093b-116">設定**批次大小**屬性設為 1 的值。</span><span class="sxs-lookup"><span data-stu-id="2093b-116">Set the **Batch size** property to a value of 1.</span></span>  
  
-   <span data-ttu-id="2093b-117">減少**MaxReceiveInterval**值小於 100 的值從預設值 500 **Messaging Isolated]、 [XLANG/s，** 和**Messaging In-process**服務類別。</span><span class="sxs-lookup"><span data-stu-id="2093b-117">Reduce the **MaxReceiveInterval** value from the default value of 500 to a value less than 100 for the **Messaging Isolated, XLANG/s,** and **Messaging In-Process** service classes.</span></span>  <span data-ttu-id="2093b-118">變更**adm_ServiceClass** BizTalk 管理資料庫資料表，其中包含一筆記錄的每個服務類型。</span><span class="sxs-lookup"><span data-stu-id="2093b-118">Changes are made the **adm_ServiceClass** table of the BizTalk Management database, which contains one record for each of these service types.</span></span>  <span data-ttu-id="2093b-119">變更此設定，因為這是服務類型範圍變更時，請務必小心。</span><span class="sxs-lookup"><span data-stu-id="2093b-119">Use caution when changing this setting because this is a service-type-wide change.</span></span> <span data-ttu-id="2093b-120">此設定會指定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳訊代理程式向 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Messagebox 資料庫輪詢訊息的輪詢間隔上限 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="2093b-120">This setting specifies the maximum polling interval (in milliseconds) at which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] messaging agent polls the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Messagebox database for messages.</span></span>  <span data-ttu-id="2093b-121">節流控制器也會使用此設定，決定在特定的負載狀況下是否需要進行訊息節流。</span><span class="sxs-lookup"><span data-stu-id="2093b-121">It also is used by the throttle controller to decide whether message throttling is needed under certain load conditions.</span></span> <span data-ttu-id="2093b-122">如果有需要，節流控制器將會根據系統上的壓力狀況，以遞增的方式延遲訊息分派間隔。</span><span class="sxs-lookup"><span data-stu-id="2093b-122">If needed, the throttling controller will incrementally delay the message dispatch interval based upon stress conditions on the system.</span></span> <span data-ttu-id="2093b-123">在高輸送量系統中，將不會使用此設定。</span><span class="sxs-lookup"><span data-stu-id="2093b-123">In a high throughput system, this setting will not be used.</span></span>  <span data-ttu-id="2093b-124">然而一旦使用此值，時間間隔就會在 MaxReceiveInteral/10 與 MaxReceiveInterval 之間動態切換。</span><span class="sxs-lookup"><span data-stu-id="2093b-124">Once this values is used, however, the time interval will dynamically change between MaxReceiveInteral/10 and MaxReceiveInterval.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2093b-125">變更此設定會影響所有主機利用所建立的**主機類型**的**隔離**。</span><span class="sxs-lookup"><span data-stu-id="2093b-125">Changing this setting affects all hosts that are created with a **Host Type** of **Isolated**.</span></span>  
  
-   <span data-ttu-id="2093b-126">重新啟動與您所設定的任何 HTTP 接收函式相關聯的 IIS 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="2093b-126">Restart the IIS Application Pool(s) associated with any HTTP receive functions that you have configured.</span></span>  
  
 <span data-ttu-id="2093b-127">登入帳戶**BizTalkServerIsolatedHost**主控件執行個體必須具有讀取和寫入權限之暫存目錄的動態編譯 HTTP 所使用的程式碼後置檔案接收函式。</span><span class="sxs-lookup"><span data-stu-id="2093b-127">The logon account for the **BizTalkServerIsolatedHost** host instance must have Read and Write permissions to the temp directory or directories to dynamically compile the code-behind files used by the HTTP receive function.</span></span> <span data-ttu-id="2093b-128">使用下列程序授與權限。</span><span class="sxs-lookup"><span data-stu-id="2093b-128">Use the following procedure to grant permissions.</span></span>  
  
### <a name="to-grant-the-account-for-the-biztalkserverisolatedhost-host-instance-read-and-write-permissions-to-the-temp-directory-of-your-biztalk-server"></a><span data-ttu-id="2093b-129">授與 BizTalkServerIsolatedHost 主控件執行個體帳戶對於 BizTalk Server 暫存目錄的寫入和讀取權限</span><span class="sxs-lookup"><span data-stu-id="2093b-129">To grant the account for the BizTalkServerIsolatedHost host instance Read and Write permissions to the temp directory of your BizTalk server</span></span>  
  
1.  <span data-ttu-id="2093b-130">按一下**啟動**，按一下 **執行**，型別**CMD**，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="2093b-130">Click **Start**, click **Run**, type **CMD**, and press ENTER.</span></span>  
  
2.  <span data-ttu-id="2093b-131">在命令提示字元中，輸入**設定 TEMP**按下 ENTER，以顯示相關聯的目錄**TEMP**環境變數。</span><span class="sxs-lookup"><span data-stu-id="2093b-131">At the command prompt, type **set TEMP** and press ENTER to display the directory associated with the **TEMP** environment variable.</span></span>  
  
3.  <span data-ttu-id="2093b-132">在命令提示字元中，輸入**set TMP**按下 ENTER，以顯示相關聯的目錄**TMP**環境變數。</span><span class="sxs-lookup"><span data-stu-id="2093b-132">At the command prompt, type **set TMP** and press ENTER to display the directory associated with the **TMP** environment variable.</span></span>  
  
 <span data-ttu-id="2093b-133">授與指定的登入帳戶為帳戶**BizTalkServerIsolatedHost**裝載執行個體讀取和寫入權限相關聯之目錄的**TEMP**和**TMP**環境變數。</span><span class="sxs-lookup"><span data-stu-id="2093b-133">Grant the account that is specified as the logon account for the **BizTalkServerIsolatedHost** host instance Read and Write permissions to the directory or directories associated with the **TEMP** and **TMP** environment variables.</span></span> <span data-ttu-id="2093b-134">若要判斷登入帳戶**BizTalkServerIsolatedHost**執行個體，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，依序展開**主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerIsolatedHost**主機在右窗格中，執行個體，然後按**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2093b-134">To determine the logon account for the **BizTalkServerIsolatedHost** instance, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, expand **Host Instances**, right-click the **BizTalkServerIsolatedHost** host instance in the right pane, and then click **Properties**.</span></span> <span data-ttu-id="2093b-135">用於主控件執行個體的登入帳戶所列旁**登入**標籤。</span><span class="sxs-lookup"><span data-stu-id="2093b-135">The logon account used for the host instance is listed next to the **Logon** label.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2093b-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="2093b-136">See Also</span></span>  
 [<span data-ttu-id="2093b-137">設定 HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="2093b-137">Configuring the HTTP Adapter</span></span>](../core/configuring-the-http-adapter.md)