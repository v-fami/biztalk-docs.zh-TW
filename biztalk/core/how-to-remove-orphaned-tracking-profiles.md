---
title: 如何移除被遺棄的追蹤設定檔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, tracking profiles
- tracking profiles, orphans
- tracking profiles, activities
- tracking profiles, deleting
- activities, tracking profiles
ms.assetid: e8923dab-5d02-41a3-840b-104b20624e6c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33ddea8751a017db21306c06cdcca5929de641ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255398"
---
# <a name="how-to-remove-orphaned-tracking-profiles"></a><span data-ttu-id="59f22-102">如何移除被遺棄的追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="59f22-102">How to Remove Orphaned Tracking Profiles</span></span>
<span data-ttu-id="59f22-103">追蹤設定檔會與活動相關聯。</span><span class="sxs-lookup"><span data-stu-id="59f22-103">Tracking profiles are associated with an activity.</span></span> <span data-ttu-id="59f22-104">如果活動已解除部署，關聯的追蹤設定檔可能會被遺棄，表示那些追蹤設定檔不再與活動相關聯。</span><span class="sxs-lookup"><span data-stu-id="59f22-104">If an activity is undeployed, the associated tracking profiles can become orphaned, which means they are no longer associated with an activity.</span></span> <span data-ttu-id="59f22-105">您可以使用下列程序移除追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="59f22-105">You can use the following procedure to remove the tracking profile.</span></span>  
  
### <a name="to-remove-an-orphaned-tracking-profile"></a><span data-ttu-id="59f22-106">移除被遺棄的追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="59f22-106">To remove an orphaned tracking profile</span></span>  
  
1.  <span data-ttu-id="59f22-107">重新部署 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="59f22-107">Redeploy the BAM definition.</span></span> <span data-ttu-id="59f22-108">如需部署 BAM 定義的相關資訊，請參閱[如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md)。</span><span class="sxs-lookup"><span data-stu-id="59f22-108">For information about deploying BAM definitions, see [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).</span></span>  
  
2.  <span data-ttu-id="59f22-109">使用追蹤設定檔編輯器 (TPE) 移除追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="59f22-109">Use the Tracking Profile Editor (TPE) to remove the tracking profile.</span></span> <span data-ttu-id="59f22-110">移除追蹤設定檔的詳細資訊，請參閱[如何套用和移除追蹤設定檔](../core/how-to-apply-and-remove-a-tracking-profile.md)。</span><span class="sxs-lookup"><span data-stu-id="59f22-110">For information about removing tracking profiles, see [How to Apply and Remove a Tracking Profile](../core/how-to-apply-and-remove-a-tracking-profile.md).</span></span>  
  
3.  <span data-ttu-id="59f22-111">解除部署 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="59f22-111">Undeploy the BAM definition.</span></span> <span data-ttu-id="59f22-112">如需移除 BAM 定義的資訊，請參閱[如何移除 BAM 定義](../core/how-to-remove-bam-definitions.md)。</span><span class="sxs-lookup"><span data-stu-id="59f22-112">For information about removing BAM definitions, see [How to Remove BAM Definitions](../core/how-to-remove-bam-definitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f22-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59f22-113">See Also</span></span>  
 <span data-ttu-id="59f22-114">[追蹤設定檔編輯器](../core/tracking-profile-editor.md) </span><span class="sxs-lookup"><span data-stu-id="59f22-114">[Tracking Profile Editor](../core/tracking-profile-editor.md) </span></span>  
 [<span data-ttu-id="59f22-115">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="59f22-115">BAM Management Utility</span></span>](../core/bam-management-utility.md)