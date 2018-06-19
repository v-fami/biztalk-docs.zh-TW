---
title: 如何設定活動視窗的持續時間 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Set-ActivityWindow command [BAM]
- activities [BAM], time intervals
- managing [BAM], time intervals
ms.assetid: e39c315e-f215-4f81-9774-cf7aedf6ba33
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66ef0c7200c69cd69a72a5743ca8f14a8950b17d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972036"
---
# <a name="how-to-set-the-duration-on-an-activity-window"></a><span data-ttu-id="09c25-102">如何設定活動視窗的持續時間</span><span class="sxs-lookup"><span data-stu-id="09c25-102">How to Set the Duration on an Activity Window</span></span>
<span data-ttu-id="09c25-103">系統管理員使用**組 activitywindow**命令設定指定之活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="09c25-103">Administrators use the **set-activitywindow** command to set the duration for the specified activity.</span></span>  
  
### <a name="to-set-the-duration-on-an-activity"></a><span data-ttu-id="09c25-104">設定活動的持續時間</span><span class="sxs-lookup"><span data-stu-id="09c25-104">To set the duration on an activity</span></span>  
  
1.  <span data-ttu-id="09c25-105">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="09c25-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="09c25-106">在命令提示字元中，輸入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，以瀏覽至追蹤資料夾。</span><span class="sxs-lookup"><span data-stu-id="09c25-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="09c25-107">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="09c25-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="09c25-108">型別**bm 組 activitywindow-活動：\<活動名稱\>-TimeLength:\<整數\>-TimeUnit： 月份 &#124; 天 &#124;小時 &#124;分鐘**。</span><span class="sxs-lookup"><span data-stu-id="09c25-108">Type **bm set-activitywindow -Activity:\<activity name\> -TimeLength:\<integer number\> -TimeUnit:Month&#124;Day&#124;Hour&#124;Minute**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09c25-109">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="09c25-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="09c25-110">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="09c25-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c25-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="09c25-111">See Also</span></span>  
 <span data-ttu-id="09c25-112">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="09c25-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="09c25-113">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="09c25-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="09c25-114">如何取得活動視窗的持續時間</span><span class="sxs-lookup"><span data-stu-id="09c25-114">How to Get the Duration on an Activity Window</span></span>](../core/how-to-get-the-duration-on-an-activity-window.md)