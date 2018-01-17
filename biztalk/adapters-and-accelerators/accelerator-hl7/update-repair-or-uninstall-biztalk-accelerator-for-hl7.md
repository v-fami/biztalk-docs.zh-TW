---
title: "更新、 修復或解除安裝 BizTalk Accelerator for HL7 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2fc84d2-1262-4a6e-ae9c-488a00ab4099
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5b4fa1dba322e830114a76a0ca69134edbb1d06
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="update-repair-or-uninstall-biztalk-accelerator-for-hl7"></a><span data-ttu-id="297c5-102">更新、 修復或解除安裝 BizTalk Accelerator for HL7</span><span class="sxs-lookup"><span data-stu-id="297c5-102">Update, repair, or uninstall BizTalk Accelerator for HL7</span></span>

<span data-ttu-id="297c5-103">變更、 修復或解除安裝[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="297c5-103">Change, repair or uninstall the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="297c5-104">確定要解除安裝[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]再解除安裝[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="297c5-104">Be sure to uninstall [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] before uninstalling [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]<span data-ttu-id="297c5-105">無法解除安裝，如果[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]不會再安裝。</span><span class="sxs-lookup"><span data-stu-id="297c5-105"> cannot be uninstalled if [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is no longer installed.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="297c5-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="297c5-106">Prerequisites</span></span>
* <span data-ttu-id="297c5-107">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="297c5-107">Sign in using an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  

* <span data-ttu-id="297c5-108">此使用者帳戶也必須是 Administrators 群組的成員上[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]儲存 BizTalk Accelerator for HL7 資料。</span><span class="sxs-lookup"><span data-stu-id="297c5-108">This user account must also be a member of the Administrators group on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] that stores the BizTalk Accelerator for HL7 data.</span></span>  
    
## <a name="update-an-existing-installation"></a><span data-ttu-id="297c5-109">更新現有的安裝</span><span class="sxs-lookup"><span data-stu-id="297c5-109">Update an existing installation</span></span>

> [!NOTE]
>  <span data-ttu-id="297c5-110">當您修改您的安裝[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]，端對端教學課程不會自動執行。</span><span class="sxs-lookup"><span data-stu-id="297c5-110">When you modify your installation of [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)], the End-to-End Tutorial does not automatically run.</span></span> 
> 
> <span data-ttu-id="297c5-111">若要執行本教學課程，並確認已正確執行修改過的安裝，執行本教學課程以手動方式從***\<磁碟機\>*** **\Program Files\Microsoft BizTalk \<版本\>Accelerator for HL7\SDK\End 端對端教學課程**資料夾。</span><span class="sxs-lookup"><span data-stu-id="297c5-111">To run the tutorial and verify that the modified installation executed correctly, run the tutorial manually from the ***\<drive\>*** **\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial** folder.</span></span>
  
1. <span data-ttu-id="297c5-112">執行[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe**身為系統管理員</span><span class="sxs-lookup"><span data-stu-id="297c5-112">Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe** as an administrator</span></span> 
  
2.  <span data-ttu-id="297c5-113">在 [歡迎使用] 頁面上，選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="297c5-113">On the welcome page, select **Next**.</span></span>  
  
3.  <span data-ttu-id="297c5-114">在**程式維護**，選取**修改**，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="297c5-114">In **Program Maintenance**, select **Modify**, and then select **Next**.</span></span>  
  
4.  <span data-ttu-id="297c5-115">在**自訂安裝程式**、 選取您想要安裝的功能、 清除功能您不想，，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="297c5-115">In **Custom Setup**, select the features that you want to install, clear the features you don't want, and then select **Next**.</span></span>  
  
5.  <span data-ttu-id="297c5-116">在 [摘要] 選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="297c5-116">In the summary, select **Next**.</span></span>  
  
6.  <span data-ttu-id="297c5-117">選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="297c5-117">Select **Install**.</span></span>  
  
7. <span data-ttu-id="297c5-118">完成後，請選取 [完成]。</span><span class="sxs-lookup"><span data-stu-id="297c5-118">When complete, select **Finish**.</span></span>  

## <a name="repair-an-existing-installation"></a><span data-ttu-id="297c5-119">修復現有安裝</span><span class="sxs-lookup"><span data-stu-id="297c5-119">Repair an existing installation</span></span>
<span data-ttu-id="297c5-120">[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]精靈會修正遺失或損毀的檔案、 捷徑或登錄項目，修復安裝。</span><span class="sxs-lookup"><span data-stu-id="297c5-120">The [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] Wizard repairs an installation by fixing missing or corrupt files, shortcuts, or registry entries.</span></span>  
  
1. <span data-ttu-id="297c5-121">執行[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe**以系統管理員身分。</span><span class="sxs-lookup"><span data-stu-id="297c5-121">Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe** as administrator.</span></span>  
  
2.  <span data-ttu-id="297c5-122">在 [歡迎使用] 頁面上，選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="297c5-122">On the welcome page, select **Next**.</span></span>  
  
3.  <span data-ttu-id="297c5-123">在**程式維護**，選取**修復**，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="297c5-123">In **Program Maintenance**, select **Repair**, and then select **Next**.</span></span>  
  
4.  <span data-ttu-id="297c5-124">在**記錄服務帳戶**，重新輸入使用者帳戶，並選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="297c5-124">In **Logging Service Account**, re-enter the user account, and then select **OK**.</span></span>  
  
4.  <span data-ttu-id="297c5-125">如果出現提示**帳戶名稱已被授與登入為服務右**，然後選取**確定**繼續。</span><span class="sxs-lookup"><span data-stu-id="297c5-125">If prompted **The account name has been granted logon as a service right**, then select **OK** to continue.</span></span>  
  
5.  <span data-ttu-id="297c5-126">當準備好修復時，選取**安裝**。</span><span class="sxs-lookup"><span data-stu-id="297c5-126">When ready to repair, select **Install**.</span></span>  
  
6. <span data-ttu-id="297c5-127">完成時，選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="297c5-127">When completed, select **Finish**.</span></span> 

  
## <a name="uninstall-btahl7"></a><span data-ttu-id="297c5-128">解除安裝 BTAHL7</span><span class="sxs-lookup"><span data-stu-id="297c5-128">Uninstall BTAHL7</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="297c5-129">如果沒有接收位置或使用 MLLP 傳輸類型的傳送埠，BTAHL7 安裝程式不會移除 MLLP 配接器在解除安裝 BTAHL7 期間。</span><span class="sxs-lookup"><span data-stu-id="297c5-129">If there is a receive location or send port using the MLLP transport type, the BTAHL7 setup does not remove the MLLP adapter during the uninstall of BTAHL7.</span></span> <span data-ttu-id="297c5-130">解除安裝之前，移除所有接收位置或傳送埠使用 MLLP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="297c5-130">Before you uninstall, remove all receive locations or send ports using the MLLP transport.</span></span> <span data-ttu-id="297c5-131">或者，您也可以將傳輸類型 mllp 變更為另一種類型。</span><span class="sxs-lookup"><span data-stu-id="297c5-131">Or, change the transport type from MLLP to another type.</span></span> <span data-ttu-id="297c5-132">然後，解除安裝將會移除 MLLP 配接器。</span><span class="sxs-lookup"><span data-stu-id="297c5-132">Then, the uninstall will remove the MLLP adapter.</span></span>  
      
1.  <span data-ttu-id="297c5-133">開啟 [程式和功能]。</span><span class="sxs-lookup"><span data-stu-id="297c5-133">Open **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="297c5-134">選取[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]，然後選取**解除安裝**。</span><span class="sxs-lookup"><span data-stu-id="297c5-134">Select [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], and then select **Uninstall**.</span></span>  
  
4.  <span data-ttu-id="297c5-135">選取**是**如果要求確認。</span><span class="sxs-lookup"><span data-stu-id="297c5-135">Select **Yes** if asked to confirm.</span></span> 
  
5.  <span data-ttu-id="297c5-136">完成時，選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="297c5-136">When completed, select **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="297c5-137">BTAHL7 不會自動解除安裝[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]成品和組件。</span><span class="sxs-lookup"><span data-stu-id="297c5-137">BTAHL7 does not automatically uninstall [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] artifacts and assemblies.</span></span>  
  

  
## <a name="troubleshooting-installation-issues"></a><span data-ttu-id="297c5-138">疑難排解安裝問題</span><span class="sxs-lookup"><span data-stu-id="297c5-138">Troubleshooting Installation Issues</span></span>  
 <span data-ttu-id="297c5-139">如果伺服器是無法驗證使用者是否為[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員，請解除安裝 BTAHL7 會傳回下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="297c5-139">If the server is unable to validate whether the user is a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrator, uninstalling BTAHL7 returns the following error:</span></span> 
 
 `Fatal error during uninstallation`  
  
<span data-ttu-id="297c5-140">若要繼續解除安裝，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="297c5-140">To continue with uninstallation, do the following:</span></span>  
  
1.  <span data-ttu-id="297c5-141">以本機系統管理員身分登入伺服器。</span><span class="sxs-lookup"><span data-stu-id="297c5-141">Sign in to the server as a local administrator.</span></span>  
  
2.  <span data-ttu-id="297c5-142">解除安裝 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="297c5-142">Uninstall [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="297c5-143">解除安裝 [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="297c5-143">Uninstall [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="297c5-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="297c5-144">See Also</span></span>  
[<span data-ttu-id="297c5-145">安裝或升級 Microsoft BizTalk Accelerator for HL7</span><span class="sxs-lookup"><span data-stu-id="297c5-145">Install or upgrade Microsoft BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/install-or-upgrade-microsoft-biztalk-accelerator-for-hl7.md)