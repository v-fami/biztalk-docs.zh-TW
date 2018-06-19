---
title: 如何設定 RTA 視窗的持續時間 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [BAM], aggregations
- aggregations [BAM], time intervals
- Set-RTAWindow command [BAM]
- managing [BAM], time intervals
ms.assetid: 3042c3f5-be0f-48fb-9831-daa4868b90fe
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb8b43fc846835ab8f24f664d4af54ab99b88576
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971356"
---
# <a name="how-to-set-the-duration-on-an-rta-window"></a><span data-ttu-id="95ca1-102">如何設定 RTA 視窗的持續時間</span><span class="sxs-lookup"><span data-stu-id="95ca1-102">How to Set the Duration on an RTA Window</span></span>
<span data-ttu-id="95ca1-103">系統管理員使用**組 rtawindow**命令設定指定之即時彙總 (RTA) 的持續時間。</span><span class="sxs-lookup"><span data-stu-id="95ca1-103">Administrators use the **set-rtawindow** command to set the duration for the specified real-time aggregation (RTA).</span></span>  
  
### <a name="to-set-the-duration-on-an-aggregation"></a><span data-ttu-id="95ca1-104">設定彙總的持續時間</span><span class="sxs-lookup"><span data-stu-id="95ca1-104">To set the duration on an aggregation</span></span>  
  
1.  <span data-ttu-id="95ca1-105">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="95ca1-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="95ca1-106">在命令提示字元中，輸入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，以瀏覽至追蹤資料夾。</span><span class="sxs-lookup"><span data-stu-id="95ca1-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="95ca1-107">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="95ca1-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="95ca1-108">型別**bm 組 rtawindow-檢視：\<檢視名稱\>-活動：\<活動名稱\>-Name:\<RTA 名稱\>-TimeLength:\<整數\>-TimeUnit： 日 &#124;小時 &#124;分鐘**。</span><span class="sxs-lookup"><span data-stu-id="95ca1-108">Type **bm set-rtawindow -View:\<view name\> -Activity:\<activity name\> -Name:\<RTA name\> -TimeLength:\<integer number\> -TimeUnit:Day&#124;Hour&#124;Minute**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="95ca1-109">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="95ca1-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="95ca1-110">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="95ca1-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ca1-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="95ca1-111">See Also</span></span>  
 <span data-ttu-id="95ca1-112">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="95ca1-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="95ca1-113">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="95ca1-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="95ca1-114">如何取得 RTA 視窗的持續時間</span><span class="sxs-lookup"><span data-stu-id="95ca1-114">How to Get the Duration on an RTA Window</span></span>](../core/how-to-get-the-duration-on-an-rta-window.md)