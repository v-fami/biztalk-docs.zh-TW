---
title: "GetServiceContractCallPoint |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be03d100-0cba-4b80-8056-b582a2cd74ce
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e291bcf733129991f6d3b5000ca8e9bc1353057
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getservicecontractcallpoint"></a><span data-ttu-id="693c3-102">GetServiceContractCallPoint</span><span class="sxs-lookup"><span data-stu-id="693c3-102">GetServiceContractCallPoint</span></span>
<span data-ttu-id="693c3-103">將目前服務合約呼叫點推至堆疊上。</span><span class="sxs-lookup"><span data-stu-id="693c3-103">Pushes the name of the current service contract call point onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="693c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="693c3-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name="GetServiceContractCallPoint" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="693c3-105">參數</span><span class="sxs-lookup"><span data-stu-id="693c3-105">Parameters</span></span>  
 <span data-ttu-id="693c3-106">無。</span><span class="sxs-lookup"><span data-stu-id="693c3-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="693c3-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="693c3-107">Pushed Value</span></span>  
 <span data-ttu-id="693c3-108">包含目前合約呼叫點的字串。</span><span class="sxs-lookup"><span data-stu-id="693c3-108">String containing the current contract call point.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="693c3-109">備註</span><span class="sxs-lookup"><span data-stu-id="693c3-109">Remarks</span></span>  
 <span data-ttu-id="693c3-110">Windows Communication Framework 服務可在服務合約存留期間的不同點來攔截。</span><span class="sxs-lookup"><span data-stu-id="693c3-110">A Windows Communication Framework service can be intercepted at different points in the lifetime of the service contract.</span></span> <span data-ttu-id="693c3-111">這些位置是由 `System.BizTalk.Bam.Interceptors.Wcf.ContractCallPoint` 列舉定義：</span><span class="sxs-lookup"><span data-stu-id="693c3-111">These locations are defined by the `System.BizTalk.Bam.Interceptors.Wcf.ContractCallPoint` enumeration:</span></span>  
  
|<span data-ttu-id="693c3-112">合約呼叫點</span><span class="sxs-lookup"><span data-stu-id="693c3-112">Contract call point</span></span>|<span data-ttu-id="693c3-113">說明</span><span class="sxs-lookup"><span data-stu-id="693c3-113">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="693c3-114">ClientReply</span><span class="sxs-lookup"><span data-stu-id="693c3-114">ClientReply</span></span>|<span data-ttu-id="693c3-115">用戶端回覆呼叫點。</span><span class="sxs-lookup"><span data-stu-id="693c3-115">Client reply call point.</span></span>|  
|<span data-ttu-id="693c3-116">ClientRequest</span><span class="sxs-lookup"><span data-stu-id="693c3-116">ClientRequest</span></span>|<span data-ttu-id="693c3-117">用戶端要求呼叫點。</span><span class="sxs-lookup"><span data-stu-id="693c3-117">Client request call point.</span></span>|  
|<span data-ttu-id="693c3-118">ClientFault</span><span class="sxs-lookup"><span data-stu-id="693c3-118">ClientFault</span></span>|<span data-ttu-id="693c3-119">用戶端錯誤點。</span><span class="sxs-lookup"><span data-stu-id="693c3-119">Client fault point.</span></span>|  
|<span data-ttu-id="693c3-120">ServiceReply</span><span class="sxs-lookup"><span data-stu-id="693c3-120">ServiceReply</span></span>|<span data-ttu-id="693c3-121">服務回覆呼叫點。</span><span class="sxs-lookup"><span data-stu-id="693c3-121">Service reply call point.</span></span>|  
|<span data-ttu-id="693c3-122">ServiceRequest</span><span class="sxs-lookup"><span data-stu-id="693c3-122">ServiceRequest</span></span>|<span data-ttu-id="693c3-123">服務要求呼叫點。</span><span class="sxs-lookup"><span data-stu-id="693c3-123">Service request call point.</span></span>|  
|<span data-ttu-id="693c3-124">ServiceFault</span><span class="sxs-lookup"><span data-stu-id="693c3-124">ServiceFault</span></span>|<span data-ttu-id="693c3-125">服務錯誤點。</span><span class="sxs-lookup"><span data-stu-id="693c3-125">Service fault point.</span></span>|  
|<span data-ttu-id="693c3-126">CallbackRequest</span><span class="sxs-lookup"><span data-stu-id="693c3-126">CallbackRequest</span></span>|<span data-ttu-id="693c3-127">回呼要求呼叫點。</span><span class="sxs-lookup"><span data-stu-id="693c3-127">Callback request call point.</span></span>|  
|<span data-ttu-id="693c3-128">CallbackReply</span><span class="sxs-lookup"><span data-stu-id="693c3-128">CallbackReply</span></span>|<span data-ttu-id="693c3-129">回呼回覆呼叫點。</span><span class="sxs-lookup"><span data-stu-id="693c3-129">Callback reply call point.</span></span>|  
|<span data-ttu-id="693c3-130">CallbackFault</span><span class="sxs-lookup"><span data-stu-id="693c3-130">CallbackFault</span></span>|<span data-ttu-id="693c3-131">回呼錯誤點。</span><span class="sxs-lookup"><span data-stu-id="693c3-131">Callback fault point.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="693c3-132">範例</span><span class="sxs-lookup"><span data-stu-id="693c3-132">Example</span></span>  
 <span data-ttu-id="693c3-133">下列範例包含事件篩選器運算式，這是設定來尋找用戶端回覆狀態中的特定作業 ("Receive")。</span><span class="sxs-lookup"><span data-stu-id="693c3-133">The following sample contains an event filter expression configured to find a specific operation ("Receive") in the client reply state.</span></span> <span data-ttu-id="693c3-134">這是使用包括 `GetOperationName`、`GetServiceContractCallPoint` 和邏輯運算等運算組合所完成。</span><span class="sxs-lookup"><span data-stu-id="693c3-134">This is done by using a combination of operations including `GetOperationName`, `GetServiceContractCallPoint`, and logical operations.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Receive</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wcf:Operation Name="GetServiceContractCallPoint" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ClientReply</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a><span data-ttu-id="693c3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="693c3-135">See Also</span></span>  
 [<span data-ttu-id="693c3-136">Windows Communication Foundation 中的作業</span><span class="sxs-lookup"><span data-stu-id="693c3-136">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)