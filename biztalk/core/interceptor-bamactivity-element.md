---
title: "攔截器 BamActivity 項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dee61b4-83cd-4a22-b8a6-1c1a7ea3648b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd43869922e46187c8b2e06155d525e428edd905
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-bamactivity-element"></a><span data-ttu-id="90917-102">攔截器 BamActivity 項目</span><span class="sxs-lookup"><span data-stu-id="90917-102">Interceptor BamActivity Element</span></span>
<span data-ttu-id="90917-103">**BamActivity**項目會定義單一 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="90917-103">The **BamActivity** element defines a single BAM activity.</span></span>  
  
## <a name="format"></a><span data-ttu-id="90917-104">格式</span><span class="sxs-lookup"><span data-stu-id="90917-104">Format</span></span>  
 <span data-ttu-id="90917-105">`BamActivity`元素包含**名稱**屬性，而且包含一或多個`OnEvent`項目。</span><span class="sxs-lookup"><span data-stu-id="90917-105">The `BamActivity` element includes a **Name** attribute and contains one or more `OnEvent` elements.</span></span>  
  
```  
<ic:BamActivity Name="PurchaseOrder">  
  <!-- One or more OnEvent elements -->  
</ic:BamActivity>   
```  
  
### <a name="attributes"></a><span data-ttu-id="90917-106">屬性</span><span class="sxs-lookup"><span data-stu-id="90917-106">Attributes</span></span>  
  
|<span data-ttu-id="90917-107">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="90917-107">Attribute name</span></span>|<span data-ttu-id="90917-108">Description</span><span class="sxs-lookup"><span data-stu-id="90917-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="90917-109">名稱</span><span class="sxs-lookup"><span data-stu-id="90917-109">Name</span></span>|<span data-ttu-id="90917-110">BAM 活動的使用者定義名稱。</span><span class="sxs-lookup"><span data-stu-id="90917-110">User-defined name of the BAM activity.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="90917-111">範例</span><span class="sxs-lookup"><span data-stu-id="90917-111">Example</span></span>  
 <span data-ttu-id="90917-112">下面例子包含的是具有單一 OnEvent 之 "MyOrderWorkflow" 的示範 BamActivity。</span><span class="sxs-lookup"><span data-stu-id="90917-112">The following example contains a sample BamActivity for "MyOrderWorkflow" with a single OnEvent.</span></span>  
  
```  
<ic:BamActivity Name="MyOrderWorkflow">  
  <ic:OnEvent Name="MyActivityEvent"  Source="OrderWorkflow">  
    …  
  </ic:OnEvent>  
</ic:BamActivity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="90917-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90917-113">See Also</span></span>  
 <span data-ttu-id="90917-114">[攔截器 EventSource 項目](../core/interceptor-eventsource-element.md) </span><span class="sxs-lookup"><span data-stu-id="90917-114">[Interceptor EventSource Element](../core/interceptor-eventsource-element.md) </span></span>  
 [<span data-ttu-id="90917-115">攔截器 OnEvent 項目</span><span class="sxs-lookup"><span data-stu-id="90917-115">Interceptor OnEvent Element</span></span>](../core/interceptor-onevent-element.md)