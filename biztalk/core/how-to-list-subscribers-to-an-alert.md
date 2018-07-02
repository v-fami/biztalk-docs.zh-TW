---
title: 如何列出警示的訂閱者 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- alerts, listing subscribers
- managing [BAM], listing alert subscribers
- subscriptions, listing subscribers
ms.assetid: 760cc88f-896d-43a3-a4af-b2a836190276
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae95582e2923c682a5d4138235029f21293fd847
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972647"
---
# <a name="how-to-list-subscribers-to-an-alert"></a><span data-ttu-id="552ad-102">如何列出警示的訂閱者</span><span class="sxs-lookup"><span data-stu-id="552ad-102">How to List Subscribers to an Alert</span></span>
<span data-ttu-id="552ad-103">系統管理員可以使用**取得訂用帳戶**命令，列出所有訂閱者指定的警示。</span><span class="sxs-lookup"><span data-stu-id="552ad-103">Administrators use the **get-subscriptions** command to list all of the subscribers to a specified alert.</span></span>  
  
### <a name="to-list-subscribers-to-an-alert"></a><span data-ttu-id="552ad-104">列出警示的訂閱者</span><span class="sxs-lookup"><span data-stu-id="552ad-104">To list subscribers to an alert</span></span>  
  
1. <span data-ttu-id="552ad-105">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="552ad-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="552ad-106">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="552ad-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3. <span data-ttu-id="552ad-107">型別**bm 取得訂用帳戶-檢視：\<檢視表名稱\>-警示：\<警示名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="552ad-107">Type **bm get-subscriptions -View:\<view name\> -Alert:\<alert name\>**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="552ad-108">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="552ad-108">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4. <span data-ttu-id="552ad-109">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="552ad-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="552ad-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="552ad-110">See Also</span></span>  
 <span data-ttu-id="552ad-111">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="552ad-111">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="552ad-112">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="552ad-112">BAM Management Utility</span></span>](../core/bam-management-utility.md)