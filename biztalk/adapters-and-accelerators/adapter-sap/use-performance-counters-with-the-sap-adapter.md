---
title: "使用效能計數器，與 SAP 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters, using
- troubleshooting, using performance counters
ms.assetid: 2749add3-31f1-47ff-b3b4-ef46c76fa533
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbc7ed347bc81a8a00ff7faa826bd48203c47e63
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="use-performance-counters-with-the-sap-adapter"></a><span data-ttu-id="0b398-102">SAP 配接器搭配使用效能計數器</span><span class="sxs-lookup"><span data-stu-id="0b398-102">Use Performance Counters with the SAP adapter</span></span>
<span data-ttu-id="0b398-103">Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]用戶端可以使用效能計數器來測量配接器的效能。</span><span class="sxs-lookup"><span data-stu-id="0b398-103">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] clients can use performance counters to gauge the performance of the adapters.</span></span> <span data-ttu-id="0b398-104">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類"[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]"沿著安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b398-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category "[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]" along installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span>  
  
## <a name="lob-time-cumulative-performance-counter"></a><span data-ttu-id="0b398-105">LOB （累加） Time 效能計數器</span><span class="sxs-lookup"><span data-stu-id="0b398-105">LOB Time (Cumulative) Performance Counter</span></span>  
 <span data-ttu-id="0b398-106">**BizTalk.NET 配接器適用於 SAP**類別目錄具有一個效能計數器稱為 「 LOB 的時間 （累計） 」。</span><span class="sxs-lookup"><span data-stu-id="0b398-106">The **BizTalk .NET Adapter for SAP** category has one performance counter called the "LOB Time (Cumulative)".</span></span> <span data-ttu-id="0b398-107">此效能計數器代表的時間，以毫秒為單位，完成配接器起始的動作所需的 LOB 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="0b398-107">This performance counter denotes the time, in milliseconds, that the LOB client library takes to complete an action that the adapter initiates.</span></span> <span data-ttu-id="0b398-108">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]建立效能計數器的執行個體中的下列模式：</span><span class="sxs-lookup"><span data-stu-id="0b398-108">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] creates an instance of the performance counter in the following pattern:</span></span>  
  
```  
<process id>:<app domain id>:<endpoint id>:<action id>  
```  
  
 <span data-ttu-id="0b398-109">可能的結束點識別碼：</span><span class="sxs-lookup"><span data-stu-id="0b398-109">The endpoint ID could be:</span></span>  
  
-   <span data-ttu-id="0b398-110">針對從配接器對 SAP 系統 （輸出） 的呼叫</span><span class="sxs-lookup"><span data-stu-id="0b398-110">For calls from the adapter to the SAP system (outbound)</span></span>  
  
    -   <span data-ttu-id="0b398-111">A、\<應用程式伺服器主機\>，\<系統編號\></span><span class="sxs-lookup"><span data-stu-id="0b398-111">A,\<application server host\>,\<system number\></span></span>  
  
    -   <span data-ttu-id="0b398-112">B\<訊息伺服器主機\>，\<R3NAME\></span><span class="sxs-lookup"><span data-stu-id="0b398-112">B,\<message server host\>,\<R3NAME\></span></span>  
  
    -   <span data-ttu-id="0b398-113">D、\<目的地\></span><span class="sxs-lookup"><span data-stu-id="0b398-113">D,\<destination\></span></span>  
  
-   <span data-ttu-id="0b398-114">對從 SAP 系統的配接器呼叫 （輸入）</span><span class="sxs-lookup"><span data-stu-id="0b398-114">For calls from the SAP system to the adapter (inbound)</span></span>  
  
    -   <span data-ttu-id="0b398-115">我，\<閘道器主機\>，\<閘道伺服器\></span><span class="sxs-lookup"><span data-stu-id="0b398-115">I,\<gateway host\>,\<gateway server\></span></span>  
  
    -   <span data-ttu-id="0b398-116">識別碼、\<目的地\></span><span class="sxs-lookup"><span data-stu-id="0b398-116">ID,\<destination\></span></span>  
  
 <span data-ttu-id="0b398-117">動作識別碼可能是：</span><span class="sxs-lookup"><span data-stu-id="0b398-117">The action ID could be:</span></span>  
  
-   <span data-ttu-id="0b398-118">\<RFC 名稱\>（適用於 RFC 呼叫）</span><span class="sxs-lookup"><span data-stu-id="0b398-118">\<RFC name\> (for an RFC call)</span></span>  
  
-   <span data-ttu-id="0b398-119">T，\<RFC 名稱\>（適用於 tRFC 呼叫）</span><span class="sxs-lookup"><span data-stu-id="0b398-119">T,\<RFC name\> (for a tRFC call)</span></span>  
  
 <span data-ttu-id="0b398-120">效能計數器會初始化只在配接器對 SAP 系統的第一個呼叫之後。</span><span class="sxs-lookup"><span data-stu-id="0b398-120">The performance counter is initialized only after the adapter makes the first call to the SAP system.</span></span> <span data-ttu-id="0b398-121">此外， [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx)效能計數器的屬性設定為 '處理序 」，這表示效能計數器不再存在時建立計數器在程式終止。</span><span class="sxs-lookup"><span data-stu-id="0b398-121">Also, the [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx) property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="0b398-122">LOB 的時間 （累計） 效能計數器的有效位數為 16 毫秒。</span><span class="sxs-lookup"><span data-stu-id="0b398-122">The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="0b398-123">啟用效能計數器</span><span class="sxs-lookup"><span data-stu-id="0b398-123">Enabling Performance Counters</span></span>  
 <span data-ttu-id="0b398-124">您可以啟用或停用的繫結屬性設定的效能計數器*EnablePerformanceCounters*。</span><span class="sxs-lookup"><span data-stu-id="0b398-124">The performance counters can be enabled or disabled by setting the binding property *EnablePerformanceCounters*.</span></span> <span data-ttu-id="0b398-125">若要啟用效能計數器， *EnablePerformanceCounters*內容繫結至**True**。</span><span class="sxs-lookup"><span data-stu-id="0b398-125">To enable performance counters, set the *EnablePerformanceCounters* binding property to **True**.</span></span> <span data-ttu-id="0b398-126">若要停用效能計數器，請設定*EnablePerformanceCounters*至**False**。</span><span class="sxs-lookup"><span data-stu-id="0b398-126">To disable performance counters, set *EnablePerformanceCounters* to **False**.</span></span> <span data-ttu-id="0b398-127">根據預設， *EnablePerformanceCounters*設**False**。</span><span class="sxs-lookup"><span data-stu-id="0b398-127">By default, *EnablePerformanceCounters* is set to **False**.</span></span>  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="0b398-128">效能計數器和 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="0b398-128">Performance Counters and the WCF LOB Adapter SDK</span></span>  
 <span data-ttu-id="0b398-129">值變更*EnablePerformanceCounters*也繫結屬性變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b398-129">Changing the value of the *EnablePerformanceCounters* binding property also changes the value of the corresponding performance counter for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="0b398-130">此外，繫結屬性的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是動態的。</span><span class="sxs-lookup"><span data-stu-id="0b398-130">Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is dynamic.</span></span> <span data-ttu-id="0b398-131">因此，如果有兩個執行個體[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]AppDomain 中的繫結和*EnablePerformanceCounters*繫結屬性設定為**True**中其中一個和**False**中，配接器專屬的效能計數器會是啟用其中一及其他停用。</span><span class="sxs-lookup"><span data-stu-id="0b398-131">Hence, if there are two instances of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding in the AppDomain, and the *EnablePerformanceCounters* binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other.</span></span> <span data-ttu-id="0b398-132">不過，因為繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它將可設為**True**或**False**根據上一次指定哪些值。</span><span class="sxs-lookup"><span data-stu-id="0b398-132">However, because the binding property for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False** depending on what value was specified last.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b398-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="0b398-133">See Also</span></span>  

[<span data-ttu-id="0b398-134">SAP 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="0b398-134">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)