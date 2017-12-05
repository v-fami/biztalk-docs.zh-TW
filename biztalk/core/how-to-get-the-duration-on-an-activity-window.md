---
title: "如何取得活動視窗的持續時間 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], time intervals
- managing [BAM], time intervals
- Get-ActivityWindow command [BAM]
ms.assetid: d70f6767-f6f7-4ecf-ad9d-4a9d8c76edea
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37c5bb2c60133d19887e157f8e06633527e0fa11
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-get-the-duration-on-an-activity-window"></a><span data-ttu-id="f632b-102">如何取得活動視窗的持續時間</span><span class="sxs-lookup"><span data-stu-id="f632b-102">How to Get the Duration on an Activity Window</span></span>
<span data-ttu-id="f632b-103">系統管理員使用**get activitywindow**命令，以取得指定之活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="f632b-103">Administrators use the **get-activitywindow** command to get the duration for the specified activity.</span></span> <span data-ttu-id="f632b-104">這個命令會傳回持續時間的長度以及測量持續時間所用的單位。</span><span class="sxs-lookup"><span data-stu-id="f632b-104">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
### <a name="to-get-the-duration-on-an-activity"></a><span data-ttu-id="f632b-105">若要取得活動的持續時間</span><span class="sxs-lookup"><span data-stu-id="f632b-105">To get the duration on an activity</span></span>  
  
1.  <span data-ttu-id="f632b-106">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f632b-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="f632b-107">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="f632b-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="f632b-108">輸入 bm get activitywindow-活動：\<活動名稱\>。</span><span class="sxs-lookup"><span data-stu-id="f632b-108">Type  bm get-activitywindow -Activity:\<activity name\>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f632b-109">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="f632b-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="f632b-110">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f632b-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f632b-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="f632b-111">See Also</span></span>  
 <span data-ttu-id="f632b-112">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="f632b-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="f632b-113">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="f632b-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="f632b-114">如何設定活動視窗的持續時間</span><span class="sxs-lookup"><span data-stu-id="f632b-114">How to Set the Duration on an Activity Window</span></span>](../core/how-to-set-the-duration-on-an-activity-window.md)