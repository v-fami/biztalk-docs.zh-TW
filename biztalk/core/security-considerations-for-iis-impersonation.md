---
title: IIS 模擬的安全性考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d10f460-29cf-49dc-9eef-b72bde4580cd
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fdafc8668e5143cc43064690f7a14736fec4869
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269182"
---
# <a name="security-considerations-for-iis-impersonation"></a><span data-ttu-id="39b4f-102">IIS 模擬的安全性考量</span><span class="sxs-lookup"><span data-stu-id="39b4f-102">Security Considerations for IIS Impersonation</span></span>
<span data-ttu-id="39b4f-103">若要使用 BAM[!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)]攔截器，透過 IIS 模擬，請依照下列中的指導方針[如何判斷和設定事件寫入者角色活動](../core/how-to-determine-and-set-event-writer-roles-for-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="39b4f-103">To use the BAM [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] interceptor with IIS impersonation, follow the guidelines in [How to Determine and Set Event Writer Roles for Activities](../core/how-to-determine-and-set-event-writer-roles-for-activities.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="39b4f-104">您必須是「BizTalk 應用程式使用者」群組的成員。</span><span class="sxs-lookup"><span data-stu-id="39b4f-104">You must be a member of the BizTalk Application Users group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39b4f-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39b4f-105">See Also</span></span>  
 [<span data-ttu-id="39b4f-106">BAM 攔截器的安全性考量</span><span class="sxs-lookup"><span data-stu-id="39b4f-106">Security Considerations for BAM Interceptors</span></span>](../core/security-considerations-for-bam-interceptors.md)