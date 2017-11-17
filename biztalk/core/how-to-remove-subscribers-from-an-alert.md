---
title: "如何從警示移除訂閱者 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subscriptions, subscribers
- managing [BAM], deleting alert subscibers
- alerts, subscribers
ms.assetid: d5571863-26e3-4c1b-991f-538cd1fef347
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92855ecc4e4e5ad2f7932327de7da8e19a80d490
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-subscribers-from-an-alert"></a><span data-ttu-id="1e23f-102">如何從警示移除訂閱者</span><span class="sxs-lookup"><span data-stu-id="1e23f-102">How to Remove Subscribers from an Alert</span></span>
<span data-ttu-id="1e23f-103">系統管理員使用**移除訂用帳戶**命令，以從警示移除指定的使用者做為訂閱者。</span><span class="sxs-lookup"><span data-stu-id="1e23f-103">Administrators use the **remove-subscription** command to remove the specified user as a subscriber from an alert.</span></span>  
  
### <a name="to-remove-subscribers-from-an-alert"></a><span data-ttu-id="1e23f-104">若要從警示移除訂閱者</span><span class="sxs-lookup"><span data-stu-id="1e23f-104">To remove subscribers from an alert</span></span>  
  
1.  <span data-ttu-id="1e23f-105">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="1e23f-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="1e23f-106">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="1e23f-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="1e23f-107">型別**bm 移除訂用帳戶的檢視：\<檢視名稱 >-警示：\<警示名稱 >-AccountName:\<帳戶名稱 >**。</span><span class="sxs-lookup"><span data-stu-id="1e23f-107">Type **bm remove-subscription -View:\<view name> -Alert:\<alert name> -AccountName:\<account name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1e23f-108">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="1e23f-108">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="1e23f-109">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="1e23f-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e23f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e23f-110">See Also</span></span>  
 <span data-ttu-id="1e23f-111">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="1e23f-111">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="1e23f-112">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="1e23f-112">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="1e23f-113">如何新增訂閱者至警示</span><span class="sxs-lookup"><span data-stu-id="1e23f-113">How to Add Subscribers to an Alert</span></span>](../core/how-to-add-subscribers-to-an-alert.md)