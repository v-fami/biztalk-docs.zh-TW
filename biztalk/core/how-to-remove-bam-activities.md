---
title: 如何移除 BAM 活動 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions], deleting activities
- activities [BAM], deleting
- deleting, activities [BAM]
- Remove-Activity command [BAM]
ms.assetid: 6c4643dc-84df-487d-aad0-590d1a6a5107
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a45201791912e960976d2e7820ae5421ebefe411
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972759"
---
# <a name="how-to-remove-bam-activities"></a><span data-ttu-id="2e67c-102">如何移除 BAM 活動</span><span class="sxs-lookup"><span data-stu-id="2e67c-102">How to Remove BAM Activities</span></span>
<span data-ttu-id="2e67c-103">系統管理員可以使用**移除活動**命令，從 BAM 主要匯入資料庫移除指定的活動。</span><span class="sxs-lookup"><span data-stu-id="2e67c-103">Administrators use the **remove-activity** command to remove the specified activity from the BAM Primary Import database.</span></span>  
  
### <a name="to-remove-a-bam-activity"></a><span data-ttu-id="2e67c-104">移除 BAM 活動</span><span class="sxs-lookup"><span data-stu-id="2e67c-104">To remove a BAM activity</span></span>  
  
1. <span data-ttu-id="2e67c-105">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="2e67c-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="2e67c-106">瀏覽至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2e67c-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
3. <span data-ttu-id="2e67c-107">型別**bm 移除活動-名稱：\<活動名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="2e67c-107">Type **bm remove-activity -Name:\<activity name\>**.</span></span>  
  
4. <span data-ttu-id="2e67c-108">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="2e67c-108">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e67c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e67c-109">See Also</span></span>  
 <span data-ttu-id="2e67c-110">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="2e67c-110">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="2e67c-111">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="2e67c-111">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="2e67c-112">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="2e67c-112">BAM Management Utility</span></span>](../core/bam-management-utility.md)