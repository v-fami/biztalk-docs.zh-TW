---
title: 如何取得活動視窗的持續時間 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities [BAM], time intervals
- managing [BAM], time intervals
- Get-ActivityWindow command [BAM]
ms.assetid: d70f6767-f6f7-4ecf-ad9d-4a9d8c76edea
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e562e1580f616d8298b07c17a950edecc7f2c13e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993543"
---
# <a name="how-to-get-the-duration-on-an-activity-window"></a><span data-ttu-id="dd6f1-102">如何取得活動視窗的持續時間</span><span class="sxs-lookup"><span data-stu-id="dd6f1-102">How to Get the Duration on an Activity Window</span></span>
<span data-ttu-id="dd6f1-103">系統管理員可以使用**get activitywindow**命令來取得指定之活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="dd6f1-103">Administrators use the **get-activitywindow** command to get the duration for the specified activity.</span></span> <span data-ttu-id="dd6f1-104">這個命令會傳回持續時間的長度以及測量持續時間所用的單位。</span><span class="sxs-lookup"><span data-stu-id="dd6f1-104">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
### <a name="to-get-the-duration-on-an-activity"></a><span data-ttu-id="dd6f1-105">若要取得活動的持續時間</span><span class="sxs-lookup"><span data-stu-id="dd6f1-105">To get the duration on an activity</span></span>  
  
1. <span data-ttu-id="dd6f1-106">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="dd6f1-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="dd6f1-107">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="dd6f1-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3. <span data-ttu-id="dd6f1-108">輸入 bm get activitywindow-活動：\<活動名稱\>。</span><span class="sxs-lookup"><span data-stu-id="dd6f1-108">Type  bm get-activitywindow -Activity:\<activity name\>.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="dd6f1-109">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="dd6f1-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4. <span data-ttu-id="dd6f1-110">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="dd6f1-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd6f1-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd6f1-111">See Also</span></span>  
 <span data-ttu-id="dd6f1-112">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="dd6f1-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="dd6f1-113">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="dd6f1-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="dd6f1-114">如何設定活動視窗的持續時間</span><span class="sxs-lookup"><span data-stu-id="dd6f1-114">How to Set the Duration on an Activity Window</span></span>](../core/how-to-set-the-duration-on-an-activity-window.md)