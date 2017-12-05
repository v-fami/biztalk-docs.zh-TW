---
title: "如何復原 BizTalk 群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1010e55-7e3d-4565-8604-ea652ea4da8c
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: deaf3ddae7d7351d53c5cd46b7d48633e0271a3d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-recover-the-biztalk-group"></a><span data-ttu-id="b7182-102">如何復原 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="b7182-102">How to Recover the BizTalk Group</span></span>
<span data-ttu-id="b7182-103">在系統復原程序中，您必須將 BizTalk Server 重新加入現有的 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="b7182-103">You must rejoin the BizTalk Server to an existing BizTalk group as part of the system recovery process.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b7182-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="b7182-104">Prerequisites</span></span>  
 <span data-ttu-id="b7182-105">您必須以「系統管理員」群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="b7182-105">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
 <span data-ttu-id="b7182-106">如果您要復原的是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition，必須下載能夠協助復原伺服器的指令碼。</span><span class="sxs-lookup"><span data-stu-id="b7182-106">If you are recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition, you must download a script that facilitates recovery of the server.</span></span> <span data-ttu-id="b7182-107">下載[RestoreConfig.vbe](http://go.microsoft.com/fwlink/?LinkID=195799)。</span><span class="sxs-lookup"><span data-stu-id="b7182-107">Download [RestoreConfig.vbe](http://go.microsoft.com/fwlink/?LinkID=195799).</span></span>  
  
### <a name="to-recover-the-biztalk-group-standard-edition"></a><span data-ttu-id="b7182-108">復原 BizTalk 群組 (Standard Edition)</span><span class="sxs-lookup"><span data-stu-id="b7182-108">To recover the BizTalk group (Standard Edition)</span></span>  
  
1.  <span data-ttu-id="b7182-109">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b7182-109">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b7182-110">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="b7182-110">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="b7182-111">**RestoreConfig.vbe***\<SavedConfigXML  \>*</span><span class="sxs-lookup"><span data-stu-id="b7182-111">**RestoreConfig.vbe**  *\<SavedConfigXML\>*</span></span>  
  
     <span data-ttu-id="b7182-112">其中 *\<SavedConfigXML\>* 是完整路徑和儲存的組態檔的檔名。</span><span class="sxs-lookup"><span data-stu-id="b7182-112">Where *\<SavedConfigXML\>* is the full path and filename of the saved configuration file.</span></span>  
  
     <span data-ttu-id="b7182-113">上述命令應該會結束且不顯示任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7182-113">The above should exit without displaying any errors.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7182-114">若要復原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]64 位元電腦上的 Standard Edition，您必須執行**RestoreConfig.vbe**從 32 位元命令提示字元，它可以更新 32 位元登錄。</span><span class="sxs-lookup"><span data-stu-id="b7182-114">To recover [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition on a 64-bit computer, you must run **RestoreConfig.vbe** from the 32-bit command prompt so that it can update the 32-bit registry.</span></span> <span data-ttu-id="b7182-115">若要開啟 32 位元命令提示字元，請按一下**啟動**，按一下**執行**，型別**c:\windows\syswow64\cmd.exe**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b7182-115">To open the 32-bit command prompt, click **Start**, click **Run**, type **c:\windows\syswow64\cmd.exe**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7182-116">失敗電腦的名稱會包含在儲存的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="b7182-116">The name of the computer that failed is contained in the saved configuration file.</span></span> <span data-ttu-id="b7182-117">您要還原至的電腦必須具有該相同名稱。</span><span class="sxs-lookup"><span data-stu-id="b7182-117">The name of the computer that you are restoring onto must have that same name.</span></span> <span data-ttu-id="b7182-118">您必須在具有該名稱的電腦上執行上述指令碼。</span><span class="sxs-lookup"><span data-stu-id="b7182-118">You must run the script above on a computer with that name.</span></span> <span data-ttu-id="b7182-119">不過，您可以在儲存的組態檔中變更失敗電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7182-119">You can, however, change the name of the computer that failed in the saved configuration file.</span></span> <span data-ttu-id="b7182-120">如果這樣做，您就可以在具有不同名稱的電腦上執行上述指令碼。</span><span class="sxs-lookup"><span data-stu-id="b7182-120">If you do so, you can run the script above onto a computer with a different name.</span></span>  
  
### <a name="to-recover-the-biztalk-group-developer-edition-or-enterprise-edition"></a><span data-ttu-id="b7182-121">復原 BizTalk 群組 (Developer Edition 或 Enterprise Edition)</span><span class="sxs-lookup"><span data-stu-id="b7182-121">To recover the BizTalk group (Developer Edition or Enterprise Edition)</span></span>  
  
1.  <span data-ttu-id="b7182-122">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 組態**。</span><span class="sxs-lookup"><span data-stu-id="b7182-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="b7182-123">在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，在主控台樹狀目錄中，按一下**群組**。</span><span class="sxs-lookup"><span data-stu-id="b7182-123">In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], in the console tree, click **Group**.</span></span>  
  
3.  <span data-ttu-id="b7182-124">在 [詳細資料] 窗格中，選取**加入現有的 BizTalk 群組**，然後指定適當的遠端 BizTalk 管理 (BizTalkMgmtDb) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b7182-124">In the details pane, select **Join an existing BizTalk Group**, and then specify the appropriate remote BizTalk Management (BizTalkMgmtDb) database.</span></span>  
  
4.  <span data-ttu-id="b7182-125">按一下 [套用組態]。</span><span class="sxs-lookup"><span data-stu-id="b7182-125">Click **Apply Configuration**.</span></span>  
  
5.  <span data-ttu-id="b7182-126">按一下**檔案**，然後按一下 **結束**。</span><span class="sxs-lookup"><span data-stu-id="b7182-126">Click **File**, and then click **Exit**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7182-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7182-127">See Also</span></span>  
 [<span data-ttu-id="b7182-128">復原執行 BizTalk Server 的電腦</span><span class="sxs-lookup"><span data-stu-id="b7182-128">Recovering a Computer Running BizTalk Server</span></span>](../core/recovering-a-computer-running-biztalk-server.md)