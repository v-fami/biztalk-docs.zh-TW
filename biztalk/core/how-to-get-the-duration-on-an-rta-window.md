---
title: "如何取得 RTA 視窗的持續時間 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], aggregations
- aggregations [BAM], time intervals
- managing [BAM], time intervals
- Get-RTAWindow command [BAM]
ms.assetid: 4e7ad0fd-e7ed-47f7-9435-ef01bbe17afa
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bb930c3e9d252a23653f0464e1adaa1e18b4f45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-get-the-duration-on-an-rta-window"></a><span data-ttu-id="b88e9-102">如何取得 RTA 視窗上的持續時間</span><span class="sxs-lookup"><span data-stu-id="b88e9-102">How to Get the Duration on an RTA Window</span></span>
<span data-ttu-id="b88e9-103">系統管理員使用**get rtawindow**命令，以取得指定之即時彙總 (RTA) 的持續時間。</span><span class="sxs-lookup"><span data-stu-id="b88e9-103">Administrators use the **get-rtawindow** command to get the duration for the specified real-time aggregation (RTA).</span></span> <span data-ttu-id="b88e9-104">這個命令會傳回持續時間的長度以及測量持續時間所用的單位。</span><span class="sxs-lookup"><span data-stu-id="b88e9-104">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
### <a name="to-get-the-duration-on-an-aggregation"></a><span data-ttu-id="b88e9-105">若要取得彙總的持續時間</span><span class="sxs-lookup"><span data-stu-id="b88e9-105">To get the duration on an aggregation</span></span>  
  
1.  <span data-ttu-id="b88e9-106">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b88e9-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b88e9-107">瀏覽至資料夾 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="b88e9-107">Navigate to the folder [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="b88e9-108">型別**bm get rtawindow-檢視：\<檢視名稱 >-活動：\<活動名稱 >-Rta:\<RTA 名稱 >**。</span><span class="sxs-lookup"><span data-stu-id="b88e9-108">Type **bm get-rtawindow -View:\<view name> -Activity:\<activity name> -Rta:\<RTA name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b88e9-109">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="b88e9-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="b88e9-110">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="b88e9-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b88e9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b88e9-111">See Also</span></span>  
 <span data-ttu-id="b88e9-112">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="b88e9-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="b88e9-113">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="b88e9-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="b88e9-114">如何設定 RTA 視窗的持續時間</span><span class="sxs-lookup"><span data-stu-id="b88e9-114">How to Set the Duration on an RTA Window</span></span>](../core/how-to-set-the-duration-on-an-rta-window.md)