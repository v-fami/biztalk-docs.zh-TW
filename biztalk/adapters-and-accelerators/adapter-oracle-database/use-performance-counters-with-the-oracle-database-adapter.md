---
title: 使用 Oracle 資料庫配接器的效能計數器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance counters, using
- performance counter, LOB Time Cumulative
- performance counters, enabling
- performance counters, and the WCF LOB Adapter SDK
ms.assetid: beb80896-7594-411e-a83c-169d5278e2ce
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb1137487a87532f015bd9edbf20b95b5e493e77
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978543"
---
# <a name="use-performance-counters-with-the-oracle-database-adapter"></a><span data-ttu-id="da2e5-102">使用 Oracle 資料庫配接器的效能計數器</span><span class="sxs-lookup"><span data-stu-id="da2e5-102">Use performance counters with the Oracle Database adapter</span></span>
<span data-ttu-id="da2e5-103">Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]用戶端可以使用效能計數器來量測計的配接器的效能。</span><span class="sxs-lookup"><span data-stu-id="da2e5-103">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] clients can use performance counters to gauge the performance of the adapters.</span></span> <span data-ttu-id="da2e5-104">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類**BizTalk.NET 配接器，適用於 Oracle DB**以及安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="da2e5-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category **BizTalk .NET Adapter for Oracle DB** along with installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span>  
  
## <a name="lob-time-cumulative-performance-counter"></a><span data-ttu-id="da2e5-105">LOB 時間 （累計） 」 效能計數器</span><span class="sxs-lookup"><span data-stu-id="da2e5-105">LOB Time (Cumulative) Performance Counter</span></span>  
 <span data-ttu-id="da2e5-106">**BizTalk.NET 配接器，適用於 Oracle DB**類別都有一個效能計數器稱為 「 LOB 時間 （累計） 」。</span><span class="sxs-lookup"><span data-stu-id="da2e5-106">The **BizTalk .NET Adapter for Oracle DB** category has one performance counter called the “LOB Time (Cumulative).”</span></span> <span data-ttu-id="da2e5-107">此效能計數器代表時間 （毫秒），完成配接器起始的動作所花的 LOB 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="da2e5-107">This performance counter denotes the time, in milliseconds, that the LOB client library takes to complete an action that the adapter initiates.</span></span> <span data-ttu-id="da2e5-108">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]建立效能計數器執行個體中的任何下列模式：</span><span class="sxs-lookup"><span data-stu-id="da2e5-108">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] creates an instance of the performance counter in any of the following patterns:</span></span>  
  
```  
<process id>:<app domain id>:<oracle data source>:<string>  
```  
  
 <span data-ttu-id="da2e5-109">其中可以是"string":</span><span class="sxs-lookup"><span data-stu-id="da2e5-109">Where "string" could be:</span></span>  
  
- <span data-ttu-id="da2e5-110">C</span><span class="sxs-lookup"><span data-stu-id="da2e5-110">Connection.Open</span></span>  
  
- <span data-ttu-id="da2e5-111">Connection.Close</span><span class="sxs-lookup"><span data-stu-id="da2e5-111">Connection.Close</span></span>  
  
- <span data-ttu-id="da2e5-112">中繼資料</span><span class="sxs-lookup"><span data-stu-id="da2e5-112">Metadata</span></span>  
  
- <span data-ttu-id="da2e5-113">訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="da2e5-113">Message action.</span></span> <span data-ttu-id="da2e5-114">例如，如果動作是`http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert`則字串會 SCOTT。Table.EMP.Insert。</span><span class="sxs-lookup"><span data-stu-id="da2e5-114">For example, if the action is `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert` then the string will be SCOTT.Table.EMP.Insert.</span></span>  
  
  <span data-ttu-id="da2e5-115">相同的連線 URI 中指定 Oracle 資料來源。</span><span class="sxs-lookup"><span data-stu-id="da2e5-115">The Oracle data source is the same as specified in the connection URI.</span></span>  
  
  <span data-ttu-id="da2e5-116">配接器對 Oracle 資料庫的第一個呼叫之後，只初始化效能計數器。</span><span class="sxs-lookup"><span data-stu-id="da2e5-116">The performance counter is initialized only after the adapter makes the first call to the Oracle database.</span></span> <span data-ttu-id="da2e5-117">此外，InstanceLifetime 的效能計數器設定為 'Process'，這表示，效能計數器就會消失只要建立計數器在程式終止。</span><span class="sxs-lookup"><span data-stu-id="da2e5-117">Also, the InstanceLifetime property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates.</span></span> <span data-ttu-id="da2e5-118">如需詳細資訊`InstanceLifetime property`，請參閱 < [ http://go.microsoft.com/fwlink/p/?LinkId=104181 ](http://go.microsoft.com/fwlink/p/?LinkId=104181)。</span><span class="sxs-lookup"><span data-stu-id="da2e5-118">For more information about the `InstanceLifetime property`, see [http://go.microsoft.com/fwlink/p/?LinkId=104181](http://go.microsoft.com/fwlink/p/?LinkId=104181).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da2e5-119">LOB 的時間 （累計） 」 效能計數器的有效位數是 16 毫秒。</span><span class="sxs-lookup"><span data-stu-id="da2e5-119">The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="da2e5-120">啟用效能計數器</span><span class="sxs-lookup"><span data-stu-id="da2e5-120">Enabling Performance Counters</span></span>  
 <span data-ttu-id="da2e5-121">可以啟用或停用的繫結屬性設定的效能計數器**EnablePerformanceCounters**。</span><span class="sxs-lookup"><span data-stu-id="da2e5-121">The performance counters can be enabled or disabled by setting the binding property **EnablePerformanceCounters**.</span></span> <span data-ttu-id="da2e5-122">若要啟用效能計數器，請設定**EnablePerformanceCounters**屬性來繫結 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="da2e5-122">To enable performance counters, set the **EnablePerformanceCounters** binding property to **True**.</span></span> <span data-ttu-id="da2e5-123">若要停用效能計數器，請設定**EnablePerformanceCounters**要**False**。</span><span class="sxs-lookup"><span data-stu-id="da2e5-123">To disable performance counters, set **EnablePerformanceCounters** to **False**.</span></span> <span data-ttu-id="da2e5-124">根據預設， **EnablePerformanceCounters**設為**False**。</span><span class="sxs-lookup"><span data-stu-id="da2e5-124">By default, **EnablePerformanceCounters** is set to **False**.</span></span>  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="da2e5-125">效能計數器和 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="da2e5-125">Performance Counters and the WCF LOB Adapter SDK</span></span>  
 <span data-ttu-id="da2e5-126">變更的值**EnablePerformanceCounters**繫結屬性也會變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="da2e5-126">Changing the value of the **EnablePerformanceCounters** binding property also changes the value of the corresponding performance counter for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="da2e5-127">此外，繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是動態的。</span><span class="sxs-lookup"><span data-stu-id="da2e5-127">Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is dynamic.</span></span> <span data-ttu-id="da2e5-128">因此，如果有兩個執行個體[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結在 AppDomain 中，而**EnablePerformanceCounters**繫結屬性設定為 **，則為 True**其中一和**False**中，配接器特有的效能計數器會會啟用下列其中一及其他停用。</span><span class="sxs-lookup"><span data-stu-id="da2e5-128">Therefore, if there are two instances of the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding in the AppDomain, and the **EnablePerformanceCounters** binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other.</span></span> <span data-ttu-id="da2e5-129">不過，因為繫結屬性，如[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它會設定 **，則為 True**或**False**根據上一次指定哪些值。</span><span class="sxs-lookup"><span data-stu-id="da2e5-129">However, because the binding property for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False** depending on what value was specified last.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da2e5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da2e5-130">See Also</span></span>  
[<span data-ttu-id="da2e5-131">Oracle 資料庫配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="da2e5-131">Troubleshoot the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)