---
title: "EDI 合作對象的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86475960-cdb2-4b39-817a-b5d834f498a9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fddda6dd62e8e3bd2d38574343b7fcb0e0d76f89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-parties"></a><span data-ttu-id="15013-102">EDI 合作對象的已知問題</span><span class="sxs-lookup"><span data-stu-id="15013-102">Known Issues with EDI Parties</span></span>
<span data-ttu-id="15013-103">本節主題說明 EDI 合作對象和夥伴協議管理員的已知問題。</span><span class="sxs-lookup"><span data-stu-id="15013-103">This section contains topics that describe known issues with EDI parties and the Partner Agreement Manager.</span></span>  
  
## <a name="a-cache-refresh-period-delays-availability-of-a-changed-party-property"></a><span data-ttu-id="15013-104">快取重新整理週期延遲了已變更之合作對象屬性的可用時間</span><span class="sxs-lookup"><span data-stu-id="15013-104">A Cache Refresh Period Delays Availability of a Changed Party Property</span></span>  
 <span data-ttu-id="15013-105">如果您在 PAM 中變更合作對象或全域屬性，必須等到每隔 15 分鐘的快取重新整理之後或是 BizTalk 服務重新啟動之後，才能在 BizTalk 執行階段中使用這些屬性。</span><span class="sxs-lookup"><span data-stu-id="15013-105">If you change a party or global property in PAM, the properties will be available to the BizTalk Runtime after the cache refreshes every fifteen minutes or after a restart of the BizTalk Service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15013-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15013-106">See Also</span></span>  
 <span data-ttu-id="15013-107">[設定 EDI 通知](../core/configuring-edi-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="15013-107">[Configuring EDI Acknowledgments](../core/configuring-edi-acknowledgments.md) </span></span>  
 <span data-ttu-id="15013-108">[中協議 EDI 處理的角色](../core/the-role-of-agreements-in-edi-processing.md) </span><span class="sxs-lookup"><span data-stu-id="15013-108">[The Role of Agreements in EDI Processing](../core/the-role-of-agreements-in-edi-processing.md) </span></span>  
 <span data-ttu-id="15013-109">[設定 EDI 屬性](../core/configuring-edi-properties.md) </span><span class="sxs-lookup"><span data-stu-id="15013-109">[Configuring EDI Properties](../core/configuring-edi-properties.md) </span></span>  
 [<span data-ttu-id="15013-110">設定全域或後援協議屬性</span><span class="sxs-lookup"><span data-stu-id="15013-110">Configuring Global or Fallback Agreement Properties</span></span>](../core/configuring-global-or-fallback-agreement-properties.md)