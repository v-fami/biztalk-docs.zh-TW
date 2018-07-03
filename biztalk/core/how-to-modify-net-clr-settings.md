---
title: 如何修改.NET CLR 設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Bts10.settings.HostInstanceCLR
ms.assetid: 085743d8-27a6-4d8b-98c7-bb5b5c75848c
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afe3d54aa508d45211277377c2f2d8880c37044d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015151"
---
# <a name="how-to-modify-net-clr-settings"></a><span data-ttu-id="afb32-102">如何修改.NET CLR 設定</span><span class="sxs-lookup"><span data-stu-id="afb32-102">How to Modify .NET CLR Settings</span></span>
<span data-ttu-id="afb32-103">若要更新的 Windows 與 BizTalk 主控件執行個體相關聯的.NET 執行緒集區中可用的執行緒數目，您可以修改使用 BizTalk 設定儀表板，將適當的 Common Runtime Language (CLR) Hosting 值。</span><span class="sxs-lookup"><span data-stu-id="afb32-103">To update the number of Windows threads available in the .NET thread pool associated with an instance of a BizTalk host, you can modify the appropriate Common Runtime Language (CLR) Hosting values using the BizTalk Settings Dashboard.</span></span> <span data-ttu-id="afb32-104">本主題提供修改這些設定的逐步程序。</span><span class="sxs-lookup"><span data-stu-id="afb32-104">This topic provides the step-by-step procedure to modify these settings.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="afb32-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="afb32-105">Prerequisites</span></span>  
 <span data-ttu-id="afb32-106">若要執行此作業，您必須以 BizTalk Server Administrators 群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="afb32-106">To perform this operation, you must be logged on as a member of the BizTalk Server Administrators group.</span></span>  

### <a name="to-modify-the-net-clr-settings-of-a-host-instance"></a><span data-ttu-id="afb32-107">若要修改主控件執行個體的 .NET CLR 設定</span><span class="sxs-lookup"><span data-stu-id="afb32-107">To modify the .NET CLR settings of a host instance</span></span>  

1. <span data-ttu-id="afb32-108">在  **BizTalk Server 管理主控台**，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="afb32-108">In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.</span></span>  

2. <span data-ttu-id="afb32-109">在  **BizTalk 設定儀表板**對話方塊的 **主控件執行個體**索引標籤上，按一下  **.NET CLR**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="afb32-109">In the **BizTalk Settings Dashboard** dialog box, on the **Host Instance** tab, click the **.NET CLR** tab.</span></span>  

3. <span data-ttu-id="afb32-110">執行下列作業，按一下**套用**以套用所做的修改，並前進到另一個索引標籤。或按一下**確定**以套用所做的修改並結束 設定儀表板。</span><span class="sxs-lookup"><span data-stu-id="afb32-110">Do the following and click **Apply** to apply the modifications and proceed to another tab. Or click **OK** to apply the modifications and exit the Settings Dashboard.</span></span>  


   |     <span data-ttu-id="afb32-111">使用</span><span class="sxs-lookup"><span data-stu-id="afb32-111">Use this</span></span>      |                                                                                <span data-ttu-id="afb32-112">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="afb32-112">To do this</span></span>                                                                                | <span data-ttu-id="afb32-113">界限值</span><span class="sxs-lookup"><span data-stu-id="afb32-113">Boundary values</span></span> | <span data-ttu-id="afb32-114">預設值</span><span class="sxs-lookup"><span data-stu-id="afb32-114">Default value</span></span> | <span data-ttu-id="afb32-115">升級邏輯</span><span class="sxs-lookup"><span data-stu-id="afb32-115">Upgrade logic</span></span> |
   |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|---------------|---------------|
   | <span data-ttu-id="afb32-116">**主控件執行個體**</span><span class="sxs-lookup"><span data-stu-id="afb32-116">**Host Instance**</span></span> | <span data-ttu-id="afb32-117">從下拉式方塊選取 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦上執行中的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="afb32-117">From the drop-down box, select the running instance of a host on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime machine.</span></span> |        -        |       -       |       -       |

    <span data-ttu-id="afb32-118">**執行緒設定**</span><span class="sxs-lookup"><span data-stu-id="afb32-118">**Threading Settings**</span></span>  

   |<span data-ttu-id="afb32-119">使用</span><span class="sxs-lookup"><span data-stu-id="afb32-119">Use this</span></span>|<span data-ttu-id="afb32-120">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="afb32-120">To do this</span></span>|<span data-ttu-id="afb32-121">界限值</span><span class="sxs-lookup"><span data-stu-id="afb32-121">Boundary values</span></span>|<span data-ttu-id="afb32-122">預設值</span><span class="sxs-lookup"><span data-stu-id="afb32-122">Default value</span></span>|<span data-ttu-id="afb32-123">升級邏輯</span><span class="sxs-lookup"><span data-stu-id="afb32-123">Upgrade logic</span></span>|  
   |--------------|----------------|---------------------|-------------------|-------------------|  
   |<span data-ttu-id="afb32-124">**最大值。背景工作執行緒**</span><span class="sxs-lookup"><span data-stu-id="afb32-124">**Max. worker threads**</span></span>|<span data-ttu-id="afb32-125">指定 .NET CLR 工作者執行緒的最大數目。</span><span class="sxs-lookup"><span data-stu-id="afb32-125">Specify the maximum number of .NET CLR worker threads.</span></span>|<span data-ttu-id="afb32-126">[工作者執行緒數下限, 500]</span><span class="sxs-lookup"><span data-stu-id="afb32-126">[Min worker threads, 500]</span></span>|<span data-ttu-id="afb32-127">25</span><span class="sxs-lookup"><span data-stu-id="afb32-127">25</span></span>|<span data-ttu-id="afb32-128">將主控件執行個體登錄設定移轉至主控件執行個體設定，並忽略 Version、Flavor、Flags 和 MinCompletionPortThreads。</span><span class="sxs-lookup"><span data-stu-id="afb32-128">Migrate the host instance registry settings to host instance settings, ignore Version, Flavor, Flags, and MinCompletionPortThreads.</span></span>|  
   |<span data-ttu-id="afb32-129">**工作者執行緒數下限**</span><span class="sxs-lookup"><span data-stu-id="afb32-129">**Min. worker threads**</span></span>|<span data-ttu-id="afb32-130">指定 .NET CLR 工作者執行緒的最小數目。</span><span class="sxs-lookup"><span data-stu-id="afb32-130">Specify the minimum number of .NET CLR worker threads.</span></span>|<span data-ttu-id="afb32-131">[0, 500]</span><span class="sxs-lookup"><span data-stu-id="afb32-131">[0, 500]</span></span>|<span data-ttu-id="afb32-132">5</span><span class="sxs-lookup"><span data-stu-id="afb32-132">5</span></span>|<span data-ttu-id="afb32-133">將主控件執行個體登錄設定移轉至主控件執行個體設定，並忽略 Version、Flavor、Flags 和 MinCompletionPortThreads。</span><span class="sxs-lookup"><span data-stu-id="afb32-133">Migrate the host instance registry settings to host instance settings, ignore Version, Flavor, Flags, and MinCompletionPortThreads.</span></span>|  
   |<span data-ttu-id="afb32-134">**最大值。IO 執行緒**</span><span class="sxs-lookup"><span data-stu-id="afb32-134">**Max. IO threads**</span></span>|<span data-ttu-id="afb32-135">指定 IO 執行緒的最大數目。</span><span class="sxs-lookup"><span data-stu-id="afb32-135">Specify the maximum number of IO threads.</span></span>|<span data-ttu-id="afb32-136">[IO 執行緒數下限, 1000]</span><span class="sxs-lookup"><span data-stu-id="afb32-136">[Min IO threads, 1000]</span></span>|<span data-ttu-id="afb32-137">250</span><span class="sxs-lookup"><span data-stu-id="afb32-137">250</span></span>|<span data-ttu-id="afb32-138">將主控件執行個體登錄設定移轉至主控件執行個體設定，並忽略 Version、Flavor、Flags 和 MinCompletionPortThreads。</span><span class="sxs-lookup"><span data-stu-id="afb32-138">Migrate the host instance registry settings to host instance settings, ignore Version, Flavor, Flags, and MinCompletionPortThreads.</span></span>|  
   |<span data-ttu-id="afb32-139">**最小值。IO 執行緒**</span><span class="sxs-lookup"><span data-stu-id="afb32-139">**Min. IO threads**</span></span>|<span data-ttu-id="afb32-140">指定 IO 執行緒的最小數目。</span><span class="sxs-lookup"><span data-stu-id="afb32-140">Specify the minimum number of IO threads.</span></span>|<span data-ttu-id="afb32-141">[0, 1000]</span><span class="sxs-lookup"><span data-stu-id="afb32-141">[0, 1000]</span></span>|<span data-ttu-id="afb32-142">25</span><span class="sxs-lookup"><span data-stu-id="afb32-142">25</span></span>|<span data-ttu-id="afb32-143">將主控件執行個體登錄設定移轉至主控件執行個體設定，並忽略 Version、Flavor、Flags 和 MinCompletionPortThreads。</span><span class="sxs-lookup"><span data-stu-id="afb32-143">Migrate the host instance registry settings to host instance settings, ignore Version, Flavor, Flags, and MinCompletionPortThreads.</span></span>|  

    <span data-ttu-id="afb32-144">.NET CLR 設定是每一核心的 CPU。</span><span class="sxs-lookup"><span data-stu-id="afb32-144">.NET CLR Settings are per-core CPU.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="afb32-145">若要還原預設設定，請按一下**還原預設值**。</span><span class="sxs-lookup"><span data-stu-id="afb32-145">To restore the default settings, click **Restore Defaults**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="afb32-146">**背景工作執行緒**用來處理已排入佇列的工作項目和**I/O 執行緒**會處理已完成的非同步 I/O 要求 I/O 完成連接埠相關聯的專用的回呼執行緒。</span><span class="sxs-lookup"><span data-stu-id="afb32-146">**Worker threads** are used to handle queued work items and **I/O threads** are dedicated callback threads associated with an I/O completion port to handle a completed asynchronous I/O request.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="afb32-147">如果 BizTalk 從舊版中，於 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc$ 值升級*hostname*\CLR 主控登錄機碼將設定儀表板中。</span><span class="sxs-lookup"><span data-stu-id="afb32-147">If BizTalk is upgraded from a previous version, the values in the HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc$*hostname*\CLR Hosting registry key will be set in Settings Dashboard.</span></span>  

## <a name="see-also"></a><span data-ttu-id="afb32-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afb32-148">See Also</span></span>  
 [<span data-ttu-id="afb32-149">如何修改主控件執行個體設定</span><span class="sxs-lookup"><span data-stu-id="afb32-149">How to Modify Host Instance Settings</span></span>](../core/how-to-modify-host-instance-settings.md)