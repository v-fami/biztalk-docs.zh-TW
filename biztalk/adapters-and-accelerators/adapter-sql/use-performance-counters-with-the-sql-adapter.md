---
title: 使用 SQL 配接器的效能計數器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae381b78-d89e-4cf2-810b-821e49422463
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb28399887452688e084f5f2858745958fd85991
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993751"
---
# <a name="use-performance-counters-with-the-sql-adapter"></a><span data-ttu-id="42211-102">使用 SQL 配接器的效能計數器</span><span class="sxs-lookup"><span data-stu-id="42211-102">Use Performance Counters with the SQL adapter</span></span>
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]<span data-ttu-id="42211-103"> 用戶端可用來量測計的配接器效能的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="42211-103"> clients can use the performance counters to gauge the performance of the adapters.</span></span> <span data-ttu-id="42211-104">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類"[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]」 以及 Adapter Pack 安裝。</span><span class="sxs-lookup"><span data-stu-id="42211-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category "[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]" along with the Adapter Pack installation.</span></span>  
  
## <a name="the-lob-time-cumulative-performance-counter"></a><span data-ttu-id="42211-105">LOB 的時間 （累計） 效能計數器</span><span class="sxs-lookup"><span data-stu-id="42211-105">The LOB Time (Cumulative) Performance Counter</span></span>  
 <span data-ttu-id="42211-106">**BizTalk.NET 配接器 sql**類別都有一個效能計數器稱為 「 LOB 時間 （累計） 」。</span><span class="sxs-lookup"><span data-stu-id="42211-106">The **BizTalk .NET Adapter for SQL** category has one performance counter called "LOB Time (Cumulative)".</span></span> <span data-ttu-id="42211-107">此效能計數器代表的時間，以毫秒為單位，完成配接器起始的動作所需的 SQL Server 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="42211-107">This performance counter denotes the time, in milliseconds, that the SQL Server client library takes to complete an action that the adapter initiates.</span></span> <span data-ttu-id="42211-108">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]建立的每個動作，針對特定的 SQL Server 執行個體和資料庫名稱的效能計數器執行個體。</span><span class="sxs-lookup"><span data-stu-id="42211-108">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] creates an instance of the performance counter for each action, for a specific SQL Server instance and database name.</span></span> <span data-ttu-id="42211-109">建立執行個體中以下列模式：</span><span class="sxs-lookup"><span data-stu-id="42211-109">The instances are created in the following pattern:</span></span>  
  
```  
<processId>:<appDomainId>:<endpointId>:<actionId>  
```  
  
 <span data-ttu-id="42211-110">`<endpointId>`做為衍生`<sql_server_name>, <instance_name>, <database_name>`。</span><span class="sxs-lookup"><span data-stu-id="42211-110">The `<endpointId>` is derived as `<sql_server_name>, <instance_name>, <database_name>`.</span></span>  
  
 <span data-ttu-id="42211-111">\<ActionId\>衍生以下列方式：</span><span class="sxs-lookup"><span data-stu-id="42211-111">The \<actionId\> is derived in the following manner:</span></span>  
  
- <span data-ttu-id="42211-112">針對開啟連接，指定動作識別碼會是 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="42211-112">For opening a connection, the action ID is “Open”.</span></span>  
  
- <span data-ttu-id="42211-113">若為輸入的作業，指定動作識別碼會是"Inbound"。</span><span class="sxs-lookup"><span data-stu-id="42211-113">For inbound operations, the action ID is “Inbound”.</span></span>  
  
- <span data-ttu-id="42211-114">為輸出的作業，指定動作識別碼會是正在叫用作業的動作具有"/"底線"_"取代。</span><span class="sxs-lookup"><span data-stu-id="42211-114">For outbound operations, the action ID is the action of the operation being invoked, with “/” replaced by an underscore “_”.</span></span> <span data-ttu-id="42211-115">此外，指定動作識別碼前面會加上"ExecuteScalar 」、 「 ExecuteReader"或"ExecuteNonQuery 」 根據配接器在內部使用的 SQL Server 資料庫上執行作業的方法。</span><span class="sxs-lookup"><span data-stu-id="42211-115">Also, the action ID is prefixed with the “ExecuteScalar”, “ExecuteReader”, or “ExecuteNonQuery” depending on the method that the adapter internally uses to perform the operation on the SQL Server database.</span></span> <span data-ttu-id="42211-116">例如，配接器會在內部使用**ExecuteReader** SQL Server 中執行預存程序的方法。</span><span class="sxs-lookup"><span data-stu-id="42211-116">For example, the adapter internally uses the **ExecuteReader** method to execute a stored procedure in SQL Server.</span></span> <span data-ttu-id="42211-117">因此，您也可以指定動作識別碼，如預存程序，MyProcedure，將會：</span><span class="sxs-lookup"><span data-stu-id="42211-117">So, the action ID for the stored procedure, MyProcedure, will be:</span></span>  
  
  ```  
  ExecuteReader_Procedure_dbo_MyProcedure  
  ```  

  <span data-ttu-id="42211-118">配接器對元件的 SQL Server 資料庫的第一個呼叫之後，只初始化效能計數器。</span><span class="sxs-lookup"><span data-stu-id="42211-118">The performance counter is initialized only after the adapter makes the first call to the SQL Server database.</span></span> <span data-ttu-id="42211-119">此外， [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx)的效能計數器的屬性設定為 'Process'，這表示，效能計數器就會消失只要建立計數器在程式終止。</span><span class="sxs-lookup"><span data-stu-id="42211-119">Also, the [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx) property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="42211-120">LOB 的時間 （累計） 」 效能計數器的有效位數是 16 毫秒。</span><span class="sxs-lookup"><span data-stu-id="42211-120">The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="42211-121">啟用效能計數器</span><span class="sxs-lookup"><span data-stu-id="42211-121">Enabling Performance Counters</span></span>  
 <span data-ttu-id="42211-122">可以啟用或停用的繫結屬性設定的效能計數器**EnablePerformanceCounters**。</span><span class="sxs-lookup"><span data-stu-id="42211-122">The performance counters can be enabled or disabled by setting the binding property **EnablePerformanceCounters**.</span></span> <span data-ttu-id="42211-123">若要啟用效能計數器，請設定**EnablePerformanceCounters**屬性來繫結 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="42211-123">To enable performance counters, set the **EnablePerformanceCounters** binding property to **True**.</span></span> <span data-ttu-id="42211-124">若要停用效能計數器，請設定**EnablePerformanceCounters**要**False**。</span><span class="sxs-lookup"><span data-stu-id="42211-124">To disable performance counters, set **EnablePerformanceCounters** to **False**.</span></span> <span data-ttu-id="42211-125">根據預設，此屬性設為**False**。</span><span class="sxs-lookup"><span data-stu-id="42211-125">By default, the property is set to **False**.</span></span> <span data-ttu-id="42211-126">如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="42211-126">For more information about this binding property, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="42211-127">效能計數器和 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="42211-127">Performance Counters and the WCF LOB Adapter SDK</span></span>  
 <span data-ttu-id="42211-128">變更的值**EnablePerformanceCounters**繫結屬性也會變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42211-128">Changing the value of the **EnablePerformanceCounters** binding property also changes the value of the corresponding performance counter for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="42211-129">此外，繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是動態的。</span><span class="sxs-lookup"><span data-stu-id="42211-129">Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is dynamic.</span></span> <span data-ttu-id="42211-130">因此，如果有兩個執行個體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結應用程式定義域，而**EnablePerformanceCounters**繫結屬性設定為 **，則為 True**其中一和**False**中，配接器特有的效能計數器會會啟用下列其中一及其他停用。</span><span class="sxs-lookup"><span data-stu-id="42211-130">Hence, if there are two instances of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding in the application domain, and the **EnablePerformanceCounters** binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other.</span></span> <span data-ttu-id="42211-131">不過，因為繫結屬性，如[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它會設定 **，則為 True**或**False**根據上一次指定哪些值。</span><span class="sxs-lookup"><span data-stu-id="42211-131">However, because the binding property for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False** depending on what value was specified last.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42211-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42211-132">See Also</span></span>  
[<span data-ttu-id="42211-133">SQL 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="42211-133">Troubleshoot the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)