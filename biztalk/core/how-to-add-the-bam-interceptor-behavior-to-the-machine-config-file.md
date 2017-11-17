---
title: "如何新增 BAM 攔截器行為至 Machine.config 檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea09925-264f-4976-8e34-f63bad70f886
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abc8845333389c95ea52d440437935d4c4867dc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-the-bam-interceptor-behavior-to-the-machineconfig-file"></a><span data-ttu-id="4101d-102">如何新增 BAM 攔截器行為至 Machine.config 檔</span><span class="sxs-lookup"><span data-stu-id="4101d-102">How to Add the BAM Interceptor Behavior to the Machine.config File</span></span>
<span data-ttu-id="4101d-103">若要在 BAM 中攔截資料，您必須將 BAM 攔截器行為新增至 Microsoft .NET machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="4101d-103">To intercept data in BAM, you must add the BAM interceptor behavior to the Microsoft .NET machine.config file.</span></span> <span data-ttu-id="4101d-104">執行這項作業的方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="4101d-104">You can do this in two ways:</span></span>  
  
-   <span data-ttu-id="4101d-105">手動編輯 machine.config 檔來加入此行為。</span><span class="sxs-lookup"><span data-stu-id="4101d-105">Manually edit the machine.config file to include the behavior.</span></span>  
  
-   <span data-ttu-id="4101d-106">使用 [服務組態編輯器] 加入此行為。</span><span class="sxs-lookup"><span data-stu-id="4101d-106">Use the Service Configuration Editor to include the behavior.</span></span>  
  
### <a name="to-manually-edit-the-machineconfig-file"></a><span data-ttu-id="4101d-107">手動編輯 machine.config 檔</span><span class="sxs-lookup"><span data-stu-id="4101d-107">To manually edit the machine.config file</span></span>  
  
1.  <span data-ttu-id="4101d-108">編輯位於 Microsoft .NET 組態資料夾中的 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="4101d-108">Edit the machine.config file located in the Microsoft .NET configuration folder.</span></span> <span data-ttu-id="4101d-109">若要這樣做，請按一下**啟動**，按一下 **執行**，輸入 c:\WINDOWS\Microsoft.NET\Framework\v4.0.30319\Config\machine.config，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4101d-109">To do this, click **Start**, click **Run**, type notepad c:\WINDOWS\Microsoft.NET\Framework\v4.0.30319\Config\machine.config, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="4101d-110">使用下列行為延伸模組更新 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="4101d-110">Update the machine.config file with the following behavior extensions.</span></span>  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="BAMEndPointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
3.  <span data-ttu-id="4101d-111">關閉並儲存 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="4101d-111">Close and save the machine.config file.</span></span>  
  
#### <a name="to-edit-the-machineconfig-file-using-the-service-configuration-editor"></a><span data-ttu-id="4101d-112">使用服務組態編輯器編輯 machine.config 檔</span><span class="sxs-lookup"><span data-stu-id="4101d-112">To edit the machine.config file using the Service Configuration Editor</span></span>  
  
1.  <span data-ttu-id="4101d-113">開啟 [服務組態編輯器]。</span><span class="sxs-lookup"><span data-stu-id="4101d-113">Open the Service Configuration Editor.</span></span> <span data-ttu-id="4101d-114">使用 服務組態編輯器的相關資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=83557](http://go.microsoft.com/fwlink/?LinkId=83557)。</span><span class="sxs-lookup"><span data-stu-id="4101d-114">For information about using the Service Configuration Editor, see [http://go.microsoft.com/fwlink/?LinkId=83557](http://go.microsoft.com/fwlink/?LinkId=83557).</span></span>  
  
2.  <span data-ttu-id="4101d-115">在樹狀檢視窗格中 (標示為**組態**)，展開節點樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="4101d-115">In the tree view pane (labeled **Configuration**), expand the node tree.</span></span> <span data-ttu-id="4101d-116">按一下**進階**資料夾中，按一下 **延伸**資料夾，然後再選取**行為項目延伸**項目。</span><span class="sxs-lookup"><span data-stu-id="4101d-116">Click the **Advanced** folder, click the **Extensions** folder, and then select the **behavior element extensions** element.</span></span>  
  
3.  <span data-ttu-id="4101d-117">建立新的行為項目延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4101d-117">Create a new behavior element extension.</span></span> <span data-ttu-id="4101d-118">按一下**新增**按鈕以開啟 [延伸模組組態項目編輯器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4101d-118">Click the **New** button to open the Extension Configuration Element Editor dialog box.</span></span> <span data-ttu-id="4101d-119">在**組態名稱**輸入行為，例如 BAMEndPointBehaviorExtension 的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="4101d-119">In **Configuration Name** enter a unique name for the behavior, for example BAMEndPointBehaviorExtension.</span></span>  
  
     <span data-ttu-id="4101d-120">![延伸模組組態元素編輯器](../core/media/00a053ba-1993-4e52-a336-e452cc60691c.gif "00a053ba-1993-4e52-a336-e452cc60691c")</span><span class="sxs-lookup"><span data-stu-id="4101d-120">![Extension Configuration Element Editor](../core/media/00a053ba-1993-4e52-a336-e452cc60691c.gif "00a053ba-1993-4e52-a336-e452cc60691c")</span></span>  
  
4.  <span data-ttu-id="4101d-121">按一下**類型**欄位，，然後按一下省略符號按鈕 (**...**) 按鈕來開啟 [行為延伸型別瀏覽器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4101d-121">Click the **Type** field, and then click the ellipsis button (**...**) button to open the Behavior Extension Type Browser dialog box.</span></span>  
  
5.  <span data-ttu-id="4101d-122">按一下 [全域組件快取] (GAC) 圖示，列出 GAC 中的 DLL。</span><span class="sxs-lookup"><span data-stu-id="4101d-122">Click the global assembly cache (GAC) icon to list the DLLs in GAC.</span></span>  
  
6.  <span data-ttu-id="4101d-123">選取 [Microsoft.BizTalk.Bam.Interceptors] 組件。</span><span class="sxs-lookup"><span data-stu-id="4101d-123">Select the Microsoft.BizTalk.Bam.Interceptors assembly.</span></span>  
  
7.  <span data-ttu-id="4101d-124">按一下**開啟**按紐選取組件，並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4101d-124">Click the **Open** button to select the assembly, and then close the dialog box.</span></span>  
  
     <span data-ttu-id="4101d-125">![Bejavopr 延伸模組型別瀏覽器](../core/media/0d525d4c-927c-42d6-96b7-0ebaf2691c6c.gif "0d525d4c-927c-42d6-96b7-0ebaf2691c6c")</span><span class="sxs-lookup"><span data-stu-id="4101d-125">![Bejavopr Extension Type Browser](../core/media/0d525d4c-927c-42d6-96b7-0ebaf2691c6c.gif "0d525d4c-927c-42d6-96b7-0ebaf2691c6c")</span></span>  
  
8.  <span data-ttu-id="4101d-126">在 [行為延伸模組型別瀏覽器] 對話方塊的 [型別名稱] 窗格中，按兩下 [Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior] 型別 (如下方畫面中反白顯示者)。</span><span class="sxs-lookup"><span data-stu-id="4101d-126">In the Type Name pane of the Behavior Extension Type Browser dialog box, double-click the Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior type (as highlighted in the following screen).</span></span>  
  
     <span data-ttu-id="4101d-127">![Bejavopr 延伸模組型別瀏覽器](../core/media/67186ad6-8802-4214-be46-11e50e4ff15d.gif "67186ad6-8802-4214-be46-11e50e4ff15d")</span><span class="sxs-lookup"><span data-stu-id="4101d-127">![Bejavopr Extension Type Browser](../core/media/67186ad6-8802-4214-be46-11e50e4ff15d.gif "67186ad6-8802-4214-be46-11e50e4ff15d")</span></span>  
  
     <span data-ttu-id="4101d-128">這樣做會開啟 [延伸模組組態項目編輯器]。</span><span class="sxs-lookup"><span data-stu-id="4101d-128">This opens the Extension Configuration Element Editor.</span></span>  
  
9. <span data-ttu-id="4101d-129">按一下**確定**關閉延伸模組組態項目編輯器對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4101d-129">Click **OK** to close the Extension Configuration Element Editor dialog box.</span></span>  
  
10. <span data-ttu-id="4101d-130">在 [服務組態編輯器] 的詳細資訊窗格中，確認顯示 BAMEndPointBehaviorExtension。</span><span class="sxs-lookup"><span data-stu-id="4101d-130">In the details pane of the Service Configuration Editor, verify that the BAMEndPointBehaviorExtension appears.</span></span>  
  
11. <span data-ttu-id="4101d-131">關閉 [服務組態編輯器]。</span><span class="sxs-lookup"><span data-stu-id="4101d-131">Close the Service Configuration Editor.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4101d-132">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4101d-132">Next Steps</span></span>  
 [<span data-ttu-id="4101d-133">如何設定 BAM WCF 攔截</span><span class="sxs-lookup"><span data-stu-id="4101d-133">How to Configure the BAM WCF Interception</span></span>](../core/how-to-configure-the-bam-wcf-interception.md)  
  
## <a name="see-also"></a><span data-ttu-id="4101d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4101d-134">See Also</span></span>  
 [<span data-ttu-id="4101d-135">設定 WCF 配接器攔截 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="4101d-135">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)