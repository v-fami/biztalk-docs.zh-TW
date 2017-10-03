---
title: "疑難排解 BizTalk Server 移轉 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6eddc0a-2403-4bcd-9327-23f51ce7d57b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dcdb53c7123b4ffaa2294db080e1efc4fb4eb65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-server-migration"></a><span data-ttu-id="ebf76-102">疑難排解 BizTalk Server 移轉</span><span class="sxs-lookup"><span data-stu-id="ebf76-102">Troubleshooting BizTalk Server Migration</span></span>
<span data-ttu-id="ebf76-103">本節針對將 BizTalk 應用程式從 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 或 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 移轉至 [!INCLUDE[prague](../includes/prague-md.md)] 時發生的常見問題，集中提供相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="ebf76-103">This section provides a centralized location for information about common problems encountered while migrating BizTalk applications from [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 to [!INCLUDE[prague](../includes/prague-md.md)].</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="ebf76-104">已知問題</span><span class="sxs-lookup"><span data-stu-id="ebf76-104">Known Issues</span></span>  
  
#### <a name="custom-applications-might-not-work-while-upgrading"></a><span data-ttu-id="ebf76-105">升級時自訂應用程式可能無法運作</span><span class="sxs-lookup"><span data-stu-id="ebf76-105">Custom applications might not work while upgrading</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="ebf76-106">問題</span><span class="sxs-lookup"><span data-stu-id="ebf76-106">Problem</span></span>  
 <span data-ttu-id="ebf76-107">從 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 或 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 升級到 [!INCLUDE[prague](../includes/prague-md.md)] 時，部分自訂應用程式可能無法運作。</span><span class="sxs-lookup"><span data-stu-id="ebf76-107">While upgrading from [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 to [!INCLUDE[prague](../includes/prague-md.md)], some custom applications might not work.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="ebf76-108">原因</span><span class="sxs-lookup"><span data-stu-id="ebf76-108">Cause</span></span>  
 <span data-ttu-id="ebf76-109">所有 BizTalk Managed 程式碼元件都在 CLR 4.0 上執行。</span><span class="sxs-lookup"><span data-stu-id="ebf76-109">All the BizTalk managed code components run on CLR 4.0.</span></span> <span data-ttu-id="ebf76-110">因為這些元件都是針對 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 來編譯，它們需要組態檔才能在 CLR 4.0 中執行。</span><span class="sxs-lookup"><span data-stu-id="ebf76-110">As these components are compiled against [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], they need a config file to run in CLR 4.0.</span></span>  
  
##### <a name="solution"></a><span data-ttu-id="ebf76-111">方案</span><span class="sxs-lookup"><span data-stu-id="ebf76-111">Solution</span></span>  
 <span data-ttu-id="ebf76-112">若要解決此問題，請更新組態檔。</span><span class="sxs-lookup"><span data-stu-id="ebf76-112">To resolve this issue, update the config file.</span></span>  
  
```  
<configuration>  
<startup useLegacyV2RuntimeActivationPolicy="true">  
<supportedRuntime version="v4.0" />  
</startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebf76-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebf76-113">See Also</span></span>  
 [<span data-ttu-id="ebf76-114">疑難排解</span><span class="sxs-lookup"><span data-stu-id="ebf76-114">Troubleshooting</span></span>](../core/troubleshooting.md)