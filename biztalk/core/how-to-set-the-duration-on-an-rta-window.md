---
title: 如何設定 RTA 視窗的持續時間 |Microsoft Docs
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
ms.openlocfilehash: 067e70ec9bff40e0b7dcee6152791f194a104218
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992271"
---
# <a name="how-to-set-the-duration-on-an-rta-window"></a><span data-ttu-id="c8141-102">如何設定 RTA 視窗的持續時間</span><span class="sxs-lookup"><span data-stu-id="c8141-102">How to Set the Duration on an RTA Window</span></span>
<span data-ttu-id="c8141-103">系統管理員可以使用**組 rtawindow**命令設定指定即時彙總 (RTA) 的持續時間。</span><span class="sxs-lookup"><span data-stu-id="c8141-103">Administrators use the **set-rtawindow** command to set the duration for the specified real-time aggregation (RTA).</span></span>  
  
### <a name="to-set-the-duration-on-an-aggregation"></a><span data-ttu-id="c8141-104">設定彙總的持續時間</span><span class="sxs-lookup"><span data-stu-id="c8141-104">To set the duration on an aggregation</span></span>  
  
1. <span data-ttu-id="c8141-105">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c8141-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="c8141-106">在命令提示字元中，輸入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，以瀏覽至追蹤資料夾。</span><span class="sxs-lookup"><span data-stu-id="c8141-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="c8141-107">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="c8141-107">Press **ENTER**.</span></span>  
  
3. <span data-ttu-id="c8141-108">型別**bm 組 rtawindow-檢視：\<檢視表名稱\>-活動：\<活動名稱\>-名稱：\<RTA 名稱\>-TimeLength:\<整數\>-TimeUnit： 天&#124;小時&#124;分鐘**。</span><span class="sxs-lookup"><span data-stu-id="c8141-108">Type **bm set-rtawindow -View:\<view name\> -Activity:\<activity name\> -Name:\<RTA name\> -TimeLength:\<integer number\> -TimeUnit:Day&#124;Hour&#124;Minute**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c8141-109">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="c8141-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4. <span data-ttu-id="c8141-110">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="c8141-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8141-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8141-111">See Also</span></span>  
 <span data-ttu-id="c8141-112">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="c8141-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="c8141-113">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="c8141-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="c8141-114">如何取得 RTA 視窗的持續時間</span><span class="sxs-lookup"><span data-stu-id="c8141-114">How to Get the Duration on an RTA Window</span></span>](../core/how-to-get-the-duration-on-an-rta-window.md)