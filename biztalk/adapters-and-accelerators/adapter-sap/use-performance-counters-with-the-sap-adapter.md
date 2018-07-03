---
title: 使用 SAP 配接器的效能計數器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance counters, using
- troubleshooting, using performance counters
ms.assetid: 2749add3-31f1-47ff-b3b4-ef46c76fa533
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7818f5f5cf24bd1d4e58da2c24691813fc2b761f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991455"
---
# <a name="use-performance-counters-with-the-sap-adapter"></a><span data-ttu-id="e9db1-102">使用 SAP 配接器的效能計數器</span><span class="sxs-lookup"><span data-stu-id="e9db1-102">Use Performance Counters with the SAP adapter</span></span>
<span data-ttu-id="e9db1-103">Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]用戶端可以使用效能計數器來量測計的配接器的效能。</span><span class="sxs-lookup"><span data-stu-id="e9db1-103">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] clients can use performance counters to gauge the performance of the adapters.</span></span> <span data-ttu-id="e9db1-104">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類 」[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]"沿著安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e9db1-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category "[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]" along installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span>  
  
## <a name="lob-time-cumulative-performance-counter"></a><span data-ttu-id="e9db1-105">LOB 時間 （累計） 」 效能計數器</span><span class="sxs-lookup"><span data-stu-id="e9db1-105">LOB Time (Cumulative) Performance Counter</span></span>  
 <span data-ttu-id="e9db1-106">**適用於 SAP 的 BizTalk.NET Adapter**類別都有一個效能計數器稱為 「 LOB 時間 （累計） 」。</span><span class="sxs-lookup"><span data-stu-id="e9db1-106">The **BizTalk .NET Adapter for SAP** category has one performance counter called the "LOB Time (Cumulative)".</span></span> <span data-ttu-id="e9db1-107">此效能計數器代表時間 （毫秒），完成配接器起始的動作所花的 LOB 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="e9db1-107">This performance counter denotes the time, in milliseconds, that the LOB client library takes to complete an action that the adapter initiates.</span></span> <span data-ttu-id="e9db1-108">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]建立效能計數器執行個體中以下列模式：</span><span class="sxs-lookup"><span data-stu-id="e9db1-108">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] creates an instance of the performance counter in the following pattern:</span></span>  
  
```  
<process id>:<app domain id>:<endpoint id>:<action id>  
```  
  
 <span data-ttu-id="e9db1-109">可能的結束點 ID:</span><span class="sxs-lookup"><span data-stu-id="e9db1-109">The endpoint ID could be:</span></span>  
  
- <span data-ttu-id="e9db1-110">針對從配接器對 SAP 系統 （輸出） 的呼叫</span><span class="sxs-lookup"><span data-stu-id="e9db1-110">For calls from the adapter to the SAP system (outbound)</span></span>  
  
  -   <span data-ttu-id="e9db1-111">A\<應用程式伺服器主機\>，\<系統編號\></span><span class="sxs-lookup"><span data-stu-id="e9db1-111">A,\<application server host\>,\<system number\></span></span>  
  
  -   <span data-ttu-id="e9db1-112">B\<訊息伺服器主機\>，\<R3NAME\></span><span class="sxs-lookup"><span data-stu-id="e9db1-112">B,\<message server host\>,\<R3NAME\></span></span>  
  
  -   <span data-ttu-id="e9db1-113">D、\<目的地\></span><span class="sxs-lookup"><span data-stu-id="e9db1-113">D,\<destination\></span></span>  
  
- <span data-ttu-id="e9db1-114">對配接器從 SAP 系統的呼叫 （輸入）</span><span class="sxs-lookup"><span data-stu-id="e9db1-114">For calls from the SAP system to the adapter (inbound)</span></span>  
  
  -   <span data-ttu-id="e9db1-115">我\<閘道器主機\>，\<閘道伺服器\></span><span class="sxs-lookup"><span data-stu-id="e9db1-115">I,\<gateway host\>,\<gateway server\></span></span>  
  
  -   <span data-ttu-id="e9db1-116">識別碼、\<目的地\></span><span class="sxs-lookup"><span data-stu-id="e9db1-116">ID,\<destination\></span></span>  
  
  <span data-ttu-id="e9db1-117">指定動作識別碼可能是：</span><span class="sxs-lookup"><span data-stu-id="e9db1-117">The action ID could be:</span></span>  
  
- <span data-ttu-id="e9db1-118">\<RFC 名稱\>（如 RFC 呼叫）</span><span class="sxs-lookup"><span data-stu-id="e9db1-118">\<RFC name\> (for an RFC call)</span></span>  
  
- <span data-ttu-id="e9db1-119">T，則\<RFC 名稱\>（適用於 tRFC 呼叫）</span><span class="sxs-lookup"><span data-stu-id="e9db1-119">T,\<RFC name\> (for a tRFC call)</span></span>  
  
  <span data-ttu-id="e9db1-120">配接器對 SAP 系統的第一個呼叫之後，只初始化效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e9db1-120">The performance counter is initialized only after the adapter makes the first call to the SAP system.</span></span> <span data-ttu-id="e9db1-121">此外， [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx)的效能計數器的屬性設定為 'Process'，這表示，效能計數器就會消失只要建立計數器在程式終止。</span><span class="sxs-lookup"><span data-stu-id="e9db1-121">Also, the [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx) property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="e9db1-122">LOB 的時間 （累計） 」 效能計數器的有效位數是 16 毫秒。</span><span class="sxs-lookup"><span data-stu-id="e9db1-122">The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="e9db1-123">啟用效能計數器</span><span class="sxs-lookup"><span data-stu-id="e9db1-123">Enabling Performance Counters</span></span>  
 <span data-ttu-id="e9db1-124">可以啟用或停用的繫結屬性設定的效能計數器*EnablePerformanceCounters*。</span><span class="sxs-lookup"><span data-stu-id="e9db1-124">The performance counters can be enabled or disabled by setting the binding property *EnablePerformanceCounters*.</span></span> <span data-ttu-id="e9db1-125">若要啟用效能計數器，請設定*EnablePerformanceCounters*屬性來繫結 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="e9db1-125">To enable performance counters, set the *EnablePerformanceCounters* binding property to **True**.</span></span> <span data-ttu-id="e9db1-126">若要停用效能計數器，請設定*EnablePerformanceCounters*要**False**。</span><span class="sxs-lookup"><span data-stu-id="e9db1-126">To disable performance counters, set *EnablePerformanceCounters* to **False**.</span></span> <span data-ttu-id="e9db1-127">根據預設， *EnablePerformanceCounters*設為**False**。</span><span class="sxs-lookup"><span data-stu-id="e9db1-127">By default, *EnablePerformanceCounters* is set to **False**.</span></span>  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="e9db1-128">效能計數器和 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="e9db1-128">Performance Counters and the WCF LOB Adapter SDK</span></span>  
 <span data-ttu-id="e9db1-129">變更的值*EnablePerformanceCounters*繫結屬性也會變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e9db1-129">Changing the value of the *EnablePerformanceCounters* binding property also changes the value of the corresponding performance counter for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="e9db1-130">此外，繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是動態的。</span><span class="sxs-lookup"><span data-stu-id="e9db1-130">Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is dynamic.</span></span> <span data-ttu-id="e9db1-131">因此，如果有兩個執行個體[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結在 AppDomain 中，而*EnablePerformanceCounters*繫結屬性設定為 **，則為 True**其中一和**False**中，配接器特有的效能計數器會會啟用下列其中一及其他停用。</span><span class="sxs-lookup"><span data-stu-id="e9db1-131">Hence, if there are two instances of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding in the AppDomain, and the *EnablePerformanceCounters* binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other.</span></span> <span data-ttu-id="e9db1-132">不過，因為繫結屬性，如[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它會設定 **，則為 True**或**False**根據上一次指定哪些值。</span><span class="sxs-lookup"><span data-stu-id="e9db1-132">However, because the binding property for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False** depending on what value was specified last.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9db1-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9db1-133">See Also</span></span>  

[<span data-ttu-id="e9db1-134">SAP 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="e9db1-134">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)