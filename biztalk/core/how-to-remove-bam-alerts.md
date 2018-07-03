---
title: 如何移除 BAM 警示 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions], deleting alerts
- Remove-Alerts command [BAM]
- alerts, deleting
ms.assetid: 9deb0ab2-a22f-477d-af31-35410d04fc6c
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4d55456a78c126eec3d14c3b26852d488da3b5b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991215"
---
# <a name="how-to-remove-bam-alerts"></a><span data-ttu-id="cd30f-102">如何移除 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="cd30f-102">How to Remove BAM Alerts</span></span>
<span data-ttu-id="cd30f-103">系統管理員可以使用**移除警示**命令來移除指定的檢視中的所有警示。</span><span class="sxs-lookup"><span data-stu-id="cd30f-103">Administrators use the **remove-alerts** command to remove all the alerts from a specified view.</span></span>  
  
### <a name="to-remove-bam-alerts"></a><span data-ttu-id="cd30f-104">移除 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="cd30f-104">To remove BAM alerts</span></span>  
  
1. <span data-ttu-id="cd30f-105">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="cd30f-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="cd30f-106">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="cd30f-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3. <span data-ttu-id="cd30f-107">型別**bm 移除警示-檢視：\<檢視表名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="cd30f-107">Type **bm remove-alerts -View:\<view name\>**.</span></span>  
  
4. <span data-ttu-id="cd30f-108">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="cd30f-108">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd30f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd30f-109">See Also</span></span>  
 <span data-ttu-id="cd30f-110">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="cd30f-110">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="cd30f-111">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="cd30f-111">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="cd30f-112">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="cd30f-112">BAM Management Utility</span></span>](../core/bam-management-utility.md)