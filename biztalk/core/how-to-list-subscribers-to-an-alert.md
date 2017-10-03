---
title: "如何列出警示的訂閱者 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- alerts, listing subscribers
- managing [BAM], listing alert subscribers
- subscriptions, listing subscribers
ms.assetid: 760cc88f-896d-43a3-a4af-b2a836190276
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d62f962847cf0e48929e11040bf1de226d567b6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-subscribers-to-an-alert"></a><span data-ttu-id="cfab8-102">如何列出警示的訂閱者</span><span class="sxs-lookup"><span data-stu-id="cfab8-102">How to List Subscribers to an Alert</span></span>
<span data-ttu-id="cfab8-103">系統管理員使用**get 訂閱**命令，列出所有的訂閱者至指定的警示。</span><span class="sxs-lookup"><span data-stu-id="cfab8-103">Administrators use the **get-subscriptions** command to list all of the subscribers to a specified alert.</span></span>  
  
### <a name="to-list-subscribers-to-an-alert"></a><span data-ttu-id="cfab8-104">列出警示的訂閱者</span><span class="sxs-lookup"><span data-stu-id="cfab8-104">To list subscribers to an alert</span></span>  
  
1.  <span data-ttu-id="cfab8-105">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="cfab8-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="cfab8-106">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="cfab8-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="cfab8-107">型別**bm get 訂閱-檢視：\<檢視名稱 >-警示：\<警示名稱 >**。</span><span class="sxs-lookup"><span data-stu-id="cfab8-107">Type **bm get-subscriptions -View:\<view name> -Alert:\<alert name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cfab8-108">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="cfab8-108">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="cfab8-109">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="cfab8-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfab8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfab8-110">See Also</span></span>  
 <span data-ttu-id="cfab8-111">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="cfab8-111">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="cfab8-112">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="cfab8-112">BAM Management Utility</span></span>](../core/bam-management-utility.md)