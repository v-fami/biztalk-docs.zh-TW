---
title: 如何復原 BAM 入口網站 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a5df99-6d03-4f1f-8540-1700d3a0b9db
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 781191047e0ee99b0000c7b773d46aa035a7e1d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254598"
---
# <a name="how-to-recover-the-bam-portal"></a><span data-ttu-id="9e06c-102">如何復原 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="9e06c-102">How to Recover the BAM Portal</span></span>
<span data-ttu-id="9e06c-103">如果您使用商務活動監控 (BAM)，您必須復原 BAM 入口網站的復原一部分您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9e06c-103">If you are using Business Activity Monitoring (BAM), you must recover the BAM portal as a part of recovering your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="9e06c-104">如果您未使用 BAM，則此程序是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="9e06c-104">If you are not using BAM, this procedure is optional.</span></span>  
  
 <span data-ttu-id="9e06c-105">復原 BAM 入口網站組態的程序的差異您使用的 IIS 版本而定。</span><span class="sxs-lookup"><span data-stu-id="9e06c-105">The procedure for recovering the BAM portal configuration differs considerably depending on which version of IIS you are using.</span></span> <span data-ttu-id="9e06c-106">當您還原適用於 IIS 7 設定時，您會使用**Appcmd.exe**，而且您還原整個預設網站上，而不只是 BAM 入口網站的組態。</span><span class="sxs-lookup"><span data-stu-id="9e06c-106">When you restore the configuration for IIS 7, you use **Appcmd.exe**, and you restore the configuration for the entire default Web site, not just the BAM portal.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9e06c-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="9e06c-107">Prerequisites</span></span>  
 <span data-ttu-id="9e06c-108">您必須以「系統管理員」群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="9e06c-108">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
### <a name="to-recover-the-bam-portal-configuration-iis-70"></a><span data-ttu-id="9e06c-109">若要復原 BAM 入口網站組態 (IIS 7.0)</span><span class="sxs-lookup"><span data-stu-id="9e06c-109">To recover the BAM portal configuration (IIS 7.0)</span></span>  
  
1.  <span data-ttu-id="9e06c-110">在 執行 對話方塊中，開啟 方塊中，輸入下列命令： `runas /user:` *computername*`\`*accountname* `cmd`，然後按一下 **確定**或按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="9e06c-110">On the Run dialog, in the Open box, type the following: `runas /user:`*computername*`\`*accountname* `cmd`, and then click **OK** or press **Enter**.</span></span>  
  
     <span data-ttu-id="9e06c-111">*Accountname*必須是本機電腦上 administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="9e06c-111">*Accountname* must be a member of the administrators group on the local computer.</span></span>  
  
2.  <span data-ttu-id="9e06c-112">出現提示時，輸入的密碼*accountname*，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="9e06c-112">When prompted, type the password for *accountname*, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="9e06c-113">型別`cd %windir%\system32\inetsrv`，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="9e06c-113">Type `cd %windir%\system32\inetsrv`, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="9e06c-114">型別`appcmd restore backup “` *backupname*`”`，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="9e06c-114">Type `appcmd restore backup “`*backupname*`”`, and then press **Enter**.</span></span>  
  
     <span data-ttu-id="9e06c-115">*Backupname*是您先前使用建立的備份名稱**Appcmd.exe**。</span><span class="sxs-lookup"><span data-stu-id="9e06c-115">*Backupname* is the name of a backup you previously created using **Appcmd.exe**.</span></span> <span data-ttu-id="9e06c-116">此備份必須存在於 **%windir%\system32\inetsrv\backup**目錄。</span><span class="sxs-lookup"><span data-stu-id="9e06c-116">This backup must exist in the **%windir%\system32\inetsrv\backup** directory.</span></span> <span data-ttu-id="9e06c-117">備份無法用於還原不同電腦上建立的密碼。</span><span class="sxs-lookup"><span data-stu-id="9e06c-117">The backup cannot be used to restore passwords created on a different computer.</span></span> <span data-ttu-id="9e06c-118">如果 BAMAppPool 設定為預設值以外的身分識別執行**NetworkService**帳戶，您必須分別進行設定的帳戶和密碼下, 一個步驟中所述。</span><span class="sxs-lookup"><span data-stu-id="9e06c-118">If the BAMAppPool is configured to run under an identity other than the default **NetworkService** account, you must configure the account and password separately, as described in the next step.</span></span>  
  
5.  <span data-ttu-id="9e06c-119">使用**網際網路資訊服務 (IIS) 管理員**，選取**應用程式集區**中**連線**窗格。</span><span class="sxs-lookup"><span data-stu-id="9e06c-119">Using the **Internet Information Services (IIS) Manager**, select **Application Pools** in the **Connections** pane.</span></span>  
  
6.  <span data-ttu-id="9e06c-120">在**應用程式集區**] 窗格中，以滑鼠右鍵按一下**BAMAppPool**，然後按一下 [**進階設定**</span><span class="sxs-lookup"><span data-stu-id="9e06c-120">In the **Application Pools** pane, right-click the **BAMAppPool**, then click **Advanced Settings**</span></span>  
  
7.  <span data-ttu-id="9e06c-121">在**進階設定**s 對話方塊中，向下捲動至**處理序模型**> 一節。</span><span class="sxs-lookup"><span data-stu-id="9e06c-121">In the **Advanced Setting**s dialog, scroll down to the **Process Model** section.</span></span> <span data-ttu-id="9e06c-122">按一下**識別**方塊。</span><span class="sxs-lookup"><span data-stu-id="9e06c-122">Click the **Identity** box.</span></span> <span data-ttu-id="9e06c-123">這會導致出現方塊右邊的省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="9e06c-123">This will cause an ellipses button to appear on the right side of the box.</span></span> <span data-ttu-id="9e06c-124">按一下**省略符號** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9e06c-124">Click the **ellipses** button.</span></span>  
  
8.  <span data-ttu-id="9e06c-125">在**應用程式集區識別** 對話方塊中，按一下 **自訂帳戶**按鈕，然後按一下**設定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9e06c-125">In the **Application Pool Identity** dialog, click the **Custom account** button, then click the **Set** button.</span></span>  
  
9. <span data-ttu-id="9e06c-126">在**設定認證**對話方塊方塊中，輸入您想要用於 BAMAppPool 的密碼與帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="9e06c-126">In the **Set Credentials** dialog box, enter the account name and password you want to use for the BAMAppPool.</span></span> <span data-ttu-id="9e06c-127">帳戶名稱應該輸入為*電腦名稱*`\`*accountname*，或*網域*`\`*accountname*.</span><span class="sxs-lookup"><span data-stu-id="9e06c-127">The account name should be entered as *computer name*`\`*accountname*, or *domain*`\`*accountname*.</span></span> <span data-ttu-id="9e06c-128">按一下**確定**關閉**設定認證**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9e06c-128">Click **OK** to close the **Set Credentials** dialog.</span></span>  
  
10. <span data-ttu-id="9e06c-129">按一下**確定**關閉**應用程式集區識別**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9e06c-129">Click **OK** to close the **Application Pool Identity** dialog.</span></span>  
  
11. <span data-ttu-id="9e06c-130">按一下**確定**關閉**進階設定**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9e06c-130">Click **OK** to close the **Advanced Settings** dialog.</span></span>  
  
12. <span data-ttu-id="9e06c-131">確認**BAMAppPool**應用程式集區的清單中選取。</span><span class="sxs-lookup"><span data-stu-id="9e06c-131">Verify that the **BAMAppPool** is selected in the list of application pools.</span></span> <span data-ttu-id="9e06c-132">在**動作**] 右邊的窗格**網際網路資訊服務 (IIS) 管理員**畫面上，於**應用程式集區工作**，按一下 [**啟動**.</span><span class="sxs-lookup"><span data-stu-id="9e06c-132">In the **Actions** pane on the right of the **Internet Information Services (IIS) Manager** screen, under **Application Pool Tasks**, click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e06c-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e06c-133">See Also</span></span>  
 <span data-ttu-id="9e06c-134">[復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="9e06c-134">[Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span></span>  
 [<span data-ttu-id="9e06c-135">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="9e06c-135">BAM Portal</span></span>](../core/bam-portal.md)