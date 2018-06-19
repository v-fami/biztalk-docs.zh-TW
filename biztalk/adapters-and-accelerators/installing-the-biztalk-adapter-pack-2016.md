---
title: 安裝 BizTalk Adapter Pack 2016 |Microsoft 文件
description: 以無訊息模式安裝的 BAP 2016，32 位元與 64 位元、 標準或自訂安裝
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f3e1717-8063-4460-bfdc-a933cd58a5c1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7076b9c076b263a54a436c553b519671760ca473
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967788"
---
# <a name="install-the-biztalk-adapter-pack-2016"></a><span data-ttu-id="92759-103">安裝 BizTalk Adapter Pack 2016</span><span class="sxs-lookup"><span data-stu-id="92759-103">Install the BizTalk Adapter Pack 2016</span></span>
<span data-ttu-id="92759-104">安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]下列兩種方式：</span><span class="sxs-lookup"><span data-stu-id="92759-104">Install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in the following two ways:</span></span>  
  
-   <span data-ttu-id="92759-105">**以互動模式**： 執行安裝精靈</span><span class="sxs-lookup"><span data-stu-id="92759-105">**In interactive mode**: Run the setup wizard</span></span>  
  
-   <span data-ttu-id="92759-106">**以無訊息模式**： 使用命令列</span><span class="sxs-lookup"><span data-stu-id="92759-106">**In silent mode**: Use the command line</span></span>  
  
> [!IMPORTANT]
> - <span data-ttu-id="92759-107">您必須在您安裝的電腦上系統管理權限[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，不論您是否要安裝使用精靈或命令列。</span><span class="sxs-lookup"><span data-stu-id="92759-107">You must have administrative privileges on the computer where you install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], irrespective of whether you are installing using the wizard, or the command line.</span></span>  
> - <span data-ttu-id="92759-108">是確定所有[軟體必要條件](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md)會安裝，才能安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-108">Be sure all the [software prerequisites](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md) are installed before installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>

## <a name="typical-vs-custom-installation"></a><span data-ttu-id="92759-109">一般與自訂安裝</span><span class="sxs-lookup"><span data-stu-id="92759-109">Typical vs custom installation</span></span>  
<span data-ttu-id="92759-110">列出安裝類型，以及與每個選項一起安裝的功能：</span><span class="sxs-lookup"><span data-stu-id="92759-110">Lists the installation types, and the features that are installed with each option:</span></span>  
  
-   <span data-ttu-id="92759-111">**一般**和**完成**選項會安裝為配接器，與相關聯的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="92759-111">The **Typical** and **Complete** options install all the adapters, with the associated data providers.</span></span> <span data-ttu-id="92759-112">您沒有選擇特定的配接器的安裝的選項。</span><span class="sxs-lookup"><span data-stu-id="92759-112">You do not have the option of choosing a specific adapter to install.</span></span>  
  
-   <span data-ttu-id="92759-113">**自訂**選項會與相關聯的資料提供者安裝一或多個介面卡。</span><span class="sxs-lookup"><span data-stu-id="92759-113">The **Custom** option installs one or more adapters, with the associated data providers.</span></span> <span data-ttu-id="92759-114">您可以選擇要安裝哪一個配接器。</span><span class="sxs-lookup"><span data-stu-id="92759-114">You can choose which adapters to install.</span></span> <span data-ttu-id="92759-115">如果您選擇安裝資料提供者，您也必須安裝對應的配接器。</span><span class="sxs-lookup"><span data-stu-id="92759-115">If you choose to install a data provider, you must also install the corresponding adapter.</span></span> <span data-ttu-id="92759-116">不過，您可以安裝配接器，而不需要安裝對應的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="92759-116">However, you can install an adapter without installing the corresponding data provider.</span></span> <span data-ttu-id="92759-117">這樣做展開**ADO 提供者**節點，然後再選取您不想要安裝的提供者。</span><span class="sxs-lookup"><span data-stu-id="92759-117">Do this by expanding the **ADO Providers** node, and then selecting the providers that you don't want to install.</span></span> <span data-ttu-id="92759-118">請參閱**使用安裝精靈安裝**（在本主題中）。</span><span class="sxs-lookup"><span data-stu-id="92759-118">See **Install using the setup wizard** (in this topic).</span></span>  
  
     <span data-ttu-id="92759-119">例如，如果您安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，您也必須安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-119">For example, if you install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], you must also install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="92759-120">不過，您可以安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]而不需要安裝[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-120">However, you can install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] without installing the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].</span></span>  
  
## <a name="32-bit-and-64-bit-install-scenarios"></a><span data-ttu-id="92759-121">32 位元和 64 位元安裝案例</span><span class="sxs-lookup"><span data-stu-id="92759-121">32-bit and 64-bit install scenarios</span></span>
 <span data-ttu-id="92759-122">與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]適用於：</span><span class="sxs-lookup"><span data-stu-id="92759-122">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] can be used for:</span></span> 
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="92759-123">設計階段 （當產生作業的 LOB 應用程式上的中繼資料）</span><span class="sxs-lookup"><span data-stu-id="92759-123"> design time (when generating metadata for operations on LOB applications)</span></span>
  
-   <span data-ttu-id="92759-124">BizTalk Server 管理主控台設計階段 （適用於建立實體連接埠）</span><span class="sxs-lookup"><span data-stu-id="92759-124">BizTalk Server Administration console design time (for creating physical ports)</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="92759-125">BizTalk Server 管理主控台會以 32 位元 Microsoft Management Console (MMC) 應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="92759-125">BizTalk Server Administration console runs as a 32-bit Microsoft Management Console (MMC) application.</span></span>  
  
-   <span data-ttu-id="92759-126">BizTalk 執行階段 （傳送和接收訊息時從 LOB 應用程式）</span><span class="sxs-lookup"><span data-stu-id="92759-126">BizTalk run time (when sending and receiving messages from LOB applications)</span></span>

<span data-ttu-id="92759-127">您可以使用單一電腦的所有這些 taks，或使用不同的電腦。</span><span class="sxs-lookup"><span data-stu-id="92759-127">You can use a single computer for all these taks, or use different computers.</span></span> <span data-ttu-id="92759-128">因為同時[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]和 BizTalk MMC 是 32 位元處理程序，您必須安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]您完成設計階段工作的電腦上。</span><span class="sxs-lookup"><span data-stu-id="92759-128">Because both [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and BizTalk MMC are 32-bit processes, you must install the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] on the computer where you complete the design-time tasks.</span></span> 

### <a name="32-bit-install-scenario"></a><span data-ttu-id="92759-129">32 位元的安裝案例</span><span class="sxs-lookup"><span data-stu-id="92759-129">32-bit install scenario</span></span>
<span data-ttu-id="92759-130">每部電腦上安裝下列軟體。</span><span class="sxs-lookup"><span data-stu-id="92759-130">Install the following software on each computer.</span></span> <span data-ttu-id="92759-131">如果您使用單一電腦，必須在該電腦上安裝所有軟體。</span><span class="sxs-lookup"><span data-stu-id="92759-131">If you are using a single computer, all the software must be installed on that computer.</span></span> 
 
1. <span data-ttu-id="92759-132">安裝 32 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92759-132">Install 32-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</span></span>
2. <span data-ttu-id="92759-133">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-133">Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>
3. <span data-ttu-id="92759-134">安裝 32 位元 LOB 用戶端和其他所需的 Dll。</span><span class="sxs-lookup"><span data-stu-id="92759-134">Install 32-bit LOB client and other required DLLs.</span></span>  
  
### <a name="64-bit-install-scenarios"></a><span data-ttu-id="92759-135">64 位元的安裝案例</span><span class="sxs-lookup"><span data-stu-id="92759-135">64-bit install scenarios</span></span>
  
|<span data-ttu-id="92759-136">Visual Studio 設計階段的</span><span class="sxs-lookup"><span data-stu-id="92759-136">For Visual Studio design time</span></span>|<span data-ttu-id="92759-137">MMC 的 biztalk 設計階段</span><span class="sxs-lookup"><span data-stu-id="92759-137">For BizTalk MMC design time</span></span>|<span data-ttu-id="92759-138">Biztalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="92759-138">For BizTalk run time</span></span>|<span data-ttu-id="92759-139">Visual Studio 設計階段及/或 MMC BizTalk 設計階段 + BizTalk 執行階段</span><span class="sxs-lookup"><span data-stu-id="92759-139">For Visual Studio design time and/or BizTalk MMC design time + BizTalk run time</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="92759-140">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-140">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-141">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-141">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-142">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="92759-142">- Install 32-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="92759-143">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-143">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-144">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-144">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-145">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="92759-145">- Install 32-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="92759-146">**32 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="92759-146">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="92759-147">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-147">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-148">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-148">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-149">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="92759-149">- Install 32-bit LOB client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="92759-150">**64 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="92759-150">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="92759-151">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-151">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-152">安裝 64 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-152">- Install 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-153">-安裝 64 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="92759-153">- Install 64-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="92759-154">**32 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="92759-154">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="92759-155">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-155">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-156">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-156">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-157">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="92759-157">- Install 32-bit LOB client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="92759-158">**64 位元 BizTalk 處理序**:</span><span class="sxs-lookup"><span data-stu-id="92759-158">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="92759-159">安裝 64 位元[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-159">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-160">安裝 64 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-160">- Install 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-161">-安裝 64 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="92759-161">- Install 64-bit LOB client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="92759-162">安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-162">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="92759-163">-安裝 32 位元 LOB 用戶端和其他必要的 Dll。</span><span class="sxs-lookup"><span data-stu-id="92759-163">- Install 32-bit LOB client and other required DLLs.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="92759-164">任何在電腦上您要執行設計階段工作，使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk MMC 中，您必須安裝 32 位元或[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-164">On any computer where you want to do design-time tasks, using either [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] or BizTalk MMC, you must install the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>  
  
## <a name="install-using-the-setup-wizard"></a><span data-ttu-id="92759-165">使用安裝精靈安裝</span><span class="sxs-lookup"><span data-stu-id="92759-165">Install using the setup wizard</span></span>  
<span data-ttu-id="92759-166">若要安裝的步驟[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]在互動模式中。</span><span class="sxs-lookup"><span data-stu-id="92759-166">Steps to install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in interactive mode.</span></span>  
  
1.  <span data-ttu-id="92759-167">執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **setup.exe**。</span><span class="sxs-lookup"><span data-stu-id="92759-167">Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **setup.exe**.</span></span>  
  
2.  <span data-ttu-id="92759-168">選取**安裝 Microsoft BizTalk Adapter**。</span><span class="sxs-lookup"><span data-stu-id="92759-168">Select **Install Microsoft BizTalk Adapters**.</span></span> <span data-ttu-id="92759-169">在下一步 視窗中，會列出任何遺失的必要條件程式。</span><span class="sxs-lookup"><span data-stu-id="92759-169">In the next window, any missing prerequisite programs are listed.</span></span> <span data-ttu-id="92759-170">如果遺漏任何，然後選取 需要的程式，安裝程式會為您安裝它。</span><span class="sxs-lookup"><span data-stu-id="92759-170">If any are missing, then select the missing program, and setup installs it for you.</span></span> 

    <span data-ttu-id="92759-171">例如，選取**步驟 2： 安裝 Microsoft BizTalk Adapter Pack**或**步驟 3： 安裝 Microsoft BizTalk Adapter Pack (x64)**。</span><span class="sxs-lookup"><span data-stu-id="92759-171">For example, select **Step 2: Install Microsoft BizTalk Adapter Pack** or **Step 3: Install Microsoft BizTalk Adapter Pack (x64)**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92759-172">如果您要安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]上為虛擬機器，安裝精靈可能會顯示正在檢查可用磁碟空間的訊息。</span><span class="sxs-lookup"><span data-stu-id="92759-172">If you are installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] on a virtual machine, the setup wizard may display a message that it's checking for available disk space.</span></span> <span data-ttu-id="92759-173">如果沒有回應，或只坐在那裡，會出現此訊息，則我們建議您**以無訊息模式安裝**（在本主題中）。</span><span class="sxs-lookup"><span data-stu-id="92759-173">If this message appears to hang or just sit there, then we recommend you **Install in silent mode** (in this topic).</span></span>  
  
3.  <span data-ttu-id="92759-174">在 歡迎使用畫面上，選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="92759-174">On the Welcome screen, select **Next**.</span></span>  
  
4.  <span data-ttu-id="92759-175">接受使用者授權合約 (EULA)，然後再選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="92759-175">Accept the end-user license agreement (EULA), and then select **Next**.</span></span>  
  
5.  <span data-ttu-id="92759-176">在**選擇安裝類型**:</span><span class="sxs-lookup"><span data-stu-id="92759-176">In **Choose Setup Type**:</span></span>  
  
    -   <span data-ttu-id="92759-177">若要安裝最常見的功能，請選取**一般**。</span><span class="sxs-lookup"><span data-stu-id="92759-177">To install the most common features, select **Typical**.</span></span>  
  
    -   <span data-ttu-id="92759-178">若要選取您想要安裝的配接器，請選取**自訂**，然後繼續進行下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="92759-178">To select the adapters you want to install, select **Custom**, and then proceed to the next step.</span></span>  
  
    -   <span data-ttu-id="92759-179">若要安裝所有功能，請選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="92759-179">To install all the features, select **Complete**.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="92759-180">若要安裝與您的企業應用程式互動，請選取您使用的介面卡**自訂**安裝。</span><span class="sxs-lookup"><span data-stu-id="92759-180">To install only the adapter that you use to interface with your enterprise application, select the **Custom** installation.</span></span>  
  
6. <span data-ttu-id="92759-181">**需要**只有當您選擇自訂安裝。</span><span class="sxs-lookup"><span data-stu-id="92759-181">**Required** only if you chose the Custom installation.</span></span> <span data-ttu-id="92759-182">如果您選擇**一般**或**完成**安裝，然後略過此步驟中，並移至步驟 7。</span><span class="sxs-lookup"><span data-stu-id="92759-182">If you chose the **Typical** or **Complete** installation, then skip this step, and go to step 7.</span></span>  
  
    1.  <span data-ttu-id="92759-183">在**自訂安裝程式**，依序展開**基底介面卡**若要查看可用的介面卡。</span><span class="sxs-lookup"><span data-stu-id="92759-183">In **Custom Setup**, expand **Base Adapters** to see the available adapters.</span></span>  
  
    2.  <span data-ttu-id="92759-184">您不想為配接器，請選取介面卡旁的圖示，然後選取**整個功能將無法使用**。</span><span class="sxs-lookup"><span data-stu-id="92759-184">For the adapters that you don't want, select the icon next to the adapter, and then select **Entire feature will be unavailable**.</span></span>  
  
    3.  <span data-ttu-id="92759-185">展開**ADO 提供者**，然後選取您不想要安裝的提供者。</span><span class="sxs-lookup"><span data-stu-id="92759-185">Expand **ADO Providers**, and then select the providers that you don't want to install.</span></span>  
  
    4.  <span data-ttu-id="92759-186">選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="92759-186">Select **Next**.</span></span>  
  
7.  <span data-ttu-id="92759-187">選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="92759-187">Select **Install**.</span></span>  
  
8.  <span data-ttu-id="92759-188">在**客戶經驗改進計畫**，您可以選擇註冊。</span><span class="sxs-lookup"><span data-stu-id="92759-188">In **Customer Experience Improvement Program**, you can choose to enroll.</span></span> <span data-ttu-id="92759-189">如果您註冊時，您可以與 Microsoft 共用的下列資料：</span><span class="sxs-lookup"><span data-stu-id="92759-189">If you enroll, you can share the following data with Microsoft:</span></span>  
  
    -   <span data-ttu-id="92759-190">您要安裝的電腦硬體的相關資料[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-190">Data related to the computer hardware on which you are installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="92759-191">資料與企業應用程式版本，您正在使用[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-191">Data related to the enterprise application versions you are using with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>  
  
     <span data-ttu-id="92759-192">[CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699)提供詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="92759-192">[CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699) provides more information.</span></span>  
     
     <span data-ttu-id="92759-193">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="92759-193">Select **OK**.</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="92759-194">您隨時可以變更此設定處於修復模式，從執行安裝程式**程式**。</span><span class="sxs-lookup"><span data-stu-id="92759-194">You can always change this setting by running the Setup in Repair mode from **Programs**.</span></span>  
  
9. <span data-ttu-id="92759-195">選取 [完成]。</span><span class="sxs-lookup"><span data-stu-id="92759-195">Select **Finish**.</span></span>  
  
<a name="BKMK_SilentInst"></a>   
## <a name="install-in-silent-mode"></a><span data-ttu-id="92759-196">以無訊息模式安裝</span><span class="sxs-lookup"><span data-stu-id="92759-196">Install in silent mode</span></span>  
 <span data-ttu-id="92759-197">使用**msiexec**命令來執行無訊息安裝。</span><span class="sxs-lookup"><span data-stu-id="92759-197">Use the **msiexec** command to do a silent installation.</span></span> <span data-ttu-id="92759-198">Msiexec 命令的一部分，請輸入您想要安裝的個別元件。</span><span class="sxs-lookup"><span data-stu-id="92759-198">As part of the msiexec command, enter the individual components that you want to install.</span></span> <span data-ttu-id="92759-199">下表列出每個元件中的值[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92759-199">The following table lists the values for each component in the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="92759-200">若要安裝 （移除） 特定元件使用這些值。</span><span class="sxs-lookup"><span data-stu-id="92759-200">Use these values to install (or remove) specific components.</span></span> <span data-ttu-id="92759-201">若要安裝 （移除） 多個元件，您可以使用以逗號分隔這些值的組合。</span><span class="sxs-lookup"><span data-stu-id="92759-201">To install (or remove) more than one component, you can use a combination of these values separated by a comma.</span></span>  
  
|<span data-ttu-id="92759-202">元件名稱</span><span class="sxs-lookup"><span data-stu-id="92759-202">Component name</span></span>|<span data-ttu-id="92759-203">命令列屬性的對應值</span><span class="sxs-lookup"><span data-stu-id="92759-203">Corresponding value for command-line properties</span></span>|  
|---|---|  
|[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]|<span data-ttu-id="92759-204">DbFeature</span><span class="sxs-lookup"><span data-stu-id="92759-204">DbFeature</span></span>|  
|[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]|<span data-ttu-id="92759-205">OracleEBSFeature</span><span class="sxs-lookup"><span data-stu-id="92759-205">OracleEBSFeature</span></span>|  
|[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]|<span data-ttu-id="92759-206">SapBaseAdapterFeature</span><span class="sxs-lookup"><span data-stu-id="92759-206">SapBaseAdapterFeature</span></span>|  
|[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]|<span data-ttu-id="92759-207">SiebelBaseAdapterFeature</span><span class="sxs-lookup"><span data-stu-id="92759-207">SiebelBaseAdapterFeature</span></span>|  
|[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]|<span data-ttu-id="92759-208">SqlFeature</span><span class="sxs-lookup"><span data-stu-id="92759-208">SqlFeature</span></span>|  
|[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]|<span data-ttu-id="92759-209">SapAdoFeature</span><span class="sxs-lookup"><span data-stu-id="92759-209">SapAdoFeature</span></span><br /><br /> <span data-ttu-id="92759-210">**請注意**： 您必須提供此值，只有當您安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]也。</span><span class="sxs-lookup"><span data-stu-id="92759-210">**Note**: You must provide this value only if you are installing the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] also.</span></span>|  
|[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]|<span data-ttu-id="92759-211">SiebelAdoFeature</span><span class="sxs-lookup"><span data-stu-id="92759-211">SiebelAdoFeature</span></span><br /><br /> <span data-ttu-id="92759-212">**請注意**： 您必須提供此值，只有當您安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]也。</span><span class="sxs-lookup"><span data-stu-id="92759-212">**Note**: You must provide this value only if you are installing the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] also.</span></span>|  
|<span data-ttu-id="92759-213">所有元件</span><span class="sxs-lookup"><span data-stu-id="92759-213">All components</span></span>|<span data-ttu-id="92759-214">ALL</span><span class="sxs-lookup"><span data-stu-id="92759-214">ALL</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="92759-215">功能名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="92759-215">The feature names are case-sensitive.</span></span>  
  
 <span data-ttu-id="92759-216">下列步驟說明如何完成的無訊息安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]為不同的元件。</span><span class="sxs-lookup"><span data-stu-id="92759-216">The following steps show you how to complete a silent installation of [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] for different components.</span></span>  
  
### <a name="silent-mode-steps"></a><span data-ttu-id="92759-217">無訊息模式的步驟</span><span class="sxs-lookup"><span data-stu-id="92759-217">Silent mode steps</span></span>
  
1.  <span data-ttu-id="92759-218">開啟命令提示字元，並移至[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]根中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="92759-218">Open a command prompt, and go to the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] root in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span></span>  
  
2.  <span data-ttu-id="92759-219">執行下列命令，根據您想要安裝：</span><span class="sxs-lookup"><span data-stu-id="92759-219">Run the following commands based on what you want to install:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92759-220">若要執行無訊息安裝在 x64 架構的平台上，取代`AdaptersSetup.msi`與`AdaptersSetup64.msi`在下列命令。</span><span class="sxs-lookup"><span data-stu-id="92759-220">To do silent installation on an x64-based platform, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi` in the following commands.</span></span>  
  
    -   <span data-ttu-id="92759-221">若要執行完整安裝，安裝所有包括.NET Framework 資料提供者的介面卡，請輸入：</span><span class="sxs-lookup"><span data-stu-id="92759-221">To perform a complete installation, which installs all the adapters including the .NET Framework Data Providers, type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=ALL  
        ```  
  
    -   <span data-ttu-id="92759-222">只安裝[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="92759-222">To install only the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=DbFeature  
        ```  
  
    -   <span data-ttu-id="92759-223">只安裝[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="92759-223">To install only the [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=OracleEBSFeature  
        ```  
  
    -   <span data-ttu-id="92759-224">只安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="92759-224">To install only the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature  
        ```  
  
    -   <span data-ttu-id="92759-225">若要安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]連同[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="92759-225">To install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] along with [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature  
        ```  
  
    -   <span data-ttu-id="92759-226">只安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="92759-226">To install only the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature  
        ```  
  
    -   <span data-ttu-id="92759-227">若要安裝[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]連同[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="92759-227">To install the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] along with [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature,SiebelAdoFeature  
        ```  
  
    -   <span data-ttu-id="92759-228">只安裝[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]，類型：</span><span class="sxs-lookup"><span data-stu-id="92759-228">To install only the [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SqlFeature  
        ```  
  
    -   <span data-ttu-id="92759-229">若要安裝的所有基底介面卡，請輸入：</span><span class="sxs-lookup"><span data-stu-id="92759-229">To install all the base adapters, type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SiebelBaseAdapterFeature,DbFeature,OracleEBSFeature,SqlFeature  
        ```  
  
    -   <span data-ttu-id="92759-230">若要安裝兩個.NET Framework 資料提供者，請輸入：</span><span class="sxs-lookup"><span data-stu-id="92759-230">To install the two .NET Framework Data Providers, type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapAdoFeature,SiebelAdoFeature  
        ```  
  
    -   <span data-ttu-id="92759-231">以逗號分隔之元件的自訂安裝的任何類型。</span><span class="sxs-lookup"><span data-stu-id="92759-231">Any type of custom installation by separating the components by a comma.</span></span> <span data-ttu-id="92759-232">例如，若要安裝[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]與[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]，而[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]類型：</span><span class="sxs-lookup"><span data-stu-id="92759-232">For example, to install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] with the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], and the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature,SiebelBaseAdapterFeature  
        ```  
  
    -   <span data-ttu-id="92759-233">您也可以選擇的 CEIP 註冊為無訊息安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="92759-233">You can also opt to enroll for CEIP as part of the silent installation.</span></span> <span data-ttu-id="92759-234">類型：</span><span class="sxs-lookup"><span data-stu-id="92759-234">Type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn CEIP_OPTIN=true  
        ```  
  
         <span data-ttu-id="92759-235">根據預設選項是 false。</span><span class="sxs-lookup"><span data-stu-id="92759-235">By default the option is false.</span></span> 
  
        > [!IMPORTANT]
        >  <span data-ttu-id="92759-236">在安裝時[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]以無訊息模式的評估版，CEIP 的預設選項為 true。</span><span class="sxs-lookup"><span data-stu-id="92759-236">While installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] Evaluation version in silent mode, the default option for CEIP is true.</span></span>  
  
     <span data-ttu-id="92759-237">如需有關**msiexec**命令中，輸入`msiexec`命令列，然後按上`ENTER`。</span><span class="sxs-lookup"><span data-stu-id="92759-237">For more information about the **msiexec** command, type `msiexec` on the command line, and press `ENTER`.</span></span> <span data-ttu-id="92759-238">或移至[http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199)。</span><span class="sxs-lookup"><span data-stu-id="92759-238">Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span></span>
     
## <a name="known-install-issue"></a><span data-ttu-id="92759-239">已知的安裝問題</span><span class="sxs-lookup"><span data-stu-id="92759-239">Known install issue</span></span>
<span data-ttu-id="92759-240">安裝相關問題的完整清單，請參閱**疑難排解**每個配接器的主題。</span><span class="sxs-lookup"><span data-stu-id="92759-240">For a comprehensive list of installation-related issues, refer to **Troubleshooting** topics for each adapter.</span></span>  
  
<span data-ttu-id="92759-241">**在 64 位元電腦上的執行安裝程式可能會擲回錯誤存取結構描述檔案時發生**</span><span class="sxs-lookup"><span data-stu-id="92759-241">**Running setup on a 64-bit computer may throw an error while accessing schema file**</span></span>  
  
<span data-ttu-id="92759-242">[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝存取 Microsoft.Adapters 時擲回錯誤。*\<AdapterName\>*_schema.xml 檔案，但配接器的安裝會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="92759-242">The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] setup throws an error while accessing the Microsoft.Adapters.*\<AdapterName\>*_schema.xml file, but proceeds with the adapter installation.</span></span>  
  
<span data-ttu-id="92759-243">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="92759-243">**Cause**</span></span>  
  
<span data-ttu-id="92759-244">如果 32 位元和 64 位元版本的[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]已安裝的相同電腦上，目標結構描述所用的檔案都相同。</span><span class="sxs-lookup"><span data-stu-id="92759-244">If both 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] are installed on the same computer, the target schema file used by both is the same.</span></span> <span data-ttu-id="92759-245">如此一來，檔案安裝 32 位元[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]64 位元安裝程式會嘗試存取權限時，可能是由 IIS 所使用。</span><span class="sxs-lookup"><span data-stu-id="92759-245">As a result, the file installed by the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] might be in use by IIS when the 64-bit installer tries to access it.</span></span>  
  
<span data-ttu-id="92759-246">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="92759-246">**Resolution**</span></span>  
  
<span data-ttu-id="92759-247">手動複製 Microsoft.Adapters。 *\<AdapterName\>*_schema.xml 檔案從*C:\Program Files\Microsoft BizTalk Adapter Pack (x64) \IIS 結構描述*至*C:\Windows\System32\inetsrv\config\schema*。</span><span class="sxs-lookup"><span data-stu-id="92759-247">Manually copy the Microsoft.Adapters.*\<AdapterName\>*_schema.xml file from *C:\Program Files\Microsoft BizTalk Adapter Pack(x64)\IIS Schemas* to *C:\Windows\System32\inetsrv\config\schema*.</span></span> 
  
## <a name="next-step"></a><span data-ttu-id="92759-248">下一步</span><span class="sxs-lookup"><span data-stu-id="92759-248">Next step</span></span>
[<span data-ttu-id="92759-249">後續安裝步驟</span><span class="sxs-lookup"><span data-stu-id="92759-249">Post installation steps</span></span>](../adapters-and-accelerators/post-installation-steps-for-biztalk-adapter-pack-2016.md)