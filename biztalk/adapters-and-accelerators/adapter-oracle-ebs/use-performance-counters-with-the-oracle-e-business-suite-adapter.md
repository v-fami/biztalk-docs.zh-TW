---
title: 使用效能計數器與 Oracle E-business Suite 介面卡 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7d722b7-8343-4956-81ed-acd5a463a9b1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf2a9f345745c18ca03086833fffe3553e96cece
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216070"
---
# <a name="use-performance-counters-with-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="56081-102">使用效能計數器與 Oracle E-business Suite 介面卡</span><span class="sxs-lookup"><span data-stu-id="56081-102">Use Performance Counters with the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="56081-103">Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]用戶端可以使用效能計數器來測量配接器的效能。</span><span class="sxs-lookup"><span data-stu-id="56081-103">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] clients can use performance counters to gauge the performance of the adapters.</span></span> <span data-ttu-id="56081-104">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類**BizTalk.NET Adapter for Oracle E-business Suite**以及安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="56081-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category **BizTalk .NET Adapter for Oracle E-Business Suite** along with installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span>  
  
## <a name="lob-time-cumulative-performance-counter"></a><span data-ttu-id="56081-105">LOB （累計） Time 效能計數器</span><span class="sxs-lookup"><span data-stu-id="56081-105">LOB Time (Cumulative) performance counter</span></span>  
 <span data-ttu-id="56081-106">**BizTalk.NET Adapter for Oracle E-business Suite**類別目錄具有一個效能計數器稱為 「 LOB 時間 （累計） 」。</span><span class="sxs-lookup"><span data-stu-id="56081-106">The **BizTalk .NET Adapter for Oracle E-Business Suite** category has one performance counter called the “LOB Time (Cumulative).”</span></span> <span data-ttu-id="56081-107">此效能計數器代表的時間，以毫秒為單位，完成配接器起始的動作所需的 LOB 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="56081-107">This performance counter denotes the time, in milliseconds, that the LOB client library takes to complete an action that the adapter initiates.</span></span> <span data-ttu-id="56081-108">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]建立效能計數器的執行個體中的任何下列模式：</span><span class="sxs-lookup"><span data-stu-id="56081-108">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] creates an instance of the performance counter in any of the following patterns:</span></span>  
  
```  
<process id>:<app domain id>:<oracle data source>:<string>  
```  
  
 <span data-ttu-id="56081-109">其中可以是 「 字串 」:</span><span class="sxs-lookup"><span data-stu-id="56081-109">Where "string" could be:</span></span>  
  
-   <span data-ttu-id="56081-110">C</span><span class="sxs-lookup"><span data-stu-id="56081-110">Connection.Open</span></span>  
  
-   <span data-ttu-id="56081-111">Connection.Close</span><span class="sxs-lookup"><span data-stu-id="56081-111">Connection.Close</span></span>  
  
-   <span data-ttu-id="56081-112">中繼資料</span><span class="sxs-lookup"><span data-stu-id="56081-112">Metadata</span></span>  
  
-   <span data-ttu-id="56081-113">訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="56081-113">Message action.</span></span> <span data-ttu-id="56081-114">例如，如果動作是`InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE`字串將會 InterfaceTables.Insert.FND.APPS.MS_SAMPLE_EMPLOYEE。</span><span class="sxs-lookup"><span data-stu-id="56081-114">For example, if the action is `InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE` then the string will be InterfaceTables.Insert.FND.APPS.MS_SAMPLE_EMPLOYEE.</span></span>  
  
 <span data-ttu-id="56081-115">與連線 URI 中指定相同 Oracle 資料來源。</span><span class="sxs-lookup"><span data-stu-id="56081-115">The Oracle data source is the same as specified in the connection URI.</span></span>  
  
 <span data-ttu-id="56081-116">效能計數器會初始化只在配接器對 Oracle 資料庫的第一個呼叫之後。</span><span class="sxs-lookup"><span data-stu-id="56081-116">The performance counter is initialized only after the adapter makes the first call to the Oracle database.</span></span> <span data-ttu-id="56081-117">此外，效能計數器的 InstanceLifetime 屬性會設定為 '處理序 」，這表示效能計數器不再存在時建立計數器在程式終止。</span><span class="sxs-lookup"><span data-stu-id="56081-117">Also, the InstanceLifetime property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="56081-118">LOB 的時間 （累計） 效能計數器的有效位數為 16 毫秒。</span><span class="sxs-lookup"><span data-stu-id="56081-118">The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="56081-119">啟用效能計數器</span><span class="sxs-lookup"><span data-stu-id="56081-119">Enabling Performance Counters</span></span>  
 <span data-ttu-id="56081-120">您可以啟用或停用的繫結屬性設定的效能計數器**EnablePerformanceCounters**。</span><span class="sxs-lookup"><span data-stu-id="56081-120">The performance counters can be enabled or disabled by setting the binding property **EnablePerformanceCounters**.</span></span> <span data-ttu-id="56081-121">若要啟用效能計數器， **EnablePerformanceCounters**內容繫結至**True**。</span><span class="sxs-lookup"><span data-stu-id="56081-121">To enable performance counters, set the **EnablePerformanceCounters** binding property to **True**.</span></span> <span data-ttu-id="56081-122">若要停用效能計數器，請設定**EnablePerformanceCounters**至**False**。</span><span class="sxs-lookup"><span data-stu-id="56081-122">To disable performance counters, set **EnablePerformanceCounters** to **False**.</span></span> <span data-ttu-id="56081-123">根據預設， **EnablePerformanceCounters**設**False**。</span><span class="sxs-lookup"><span data-stu-id="56081-123">By default, **EnablePerformanceCounters** is set to **False**.</span></span>  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="56081-124">效能計數器和 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="56081-124">Performance Counters and the WCF LOB Adapter SDK</span></span>  
 <span data-ttu-id="56081-125">值變更**EnablePerformanceCounters**也繫結屬性變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="56081-125">Changing the value of the **EnablePerformanceCounters** binding property also changes the value of the corresponding performance counter for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="56081-126">此外，繫結屬性的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是動態的。</span><span class="sxs-lookup"><span data-stu-id="56081-126">Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is dynamic.</span></span> <span data-ttu-id="56081-127">因此，如果有兩個執行個體[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]AppDomain 中的繫結和**EnablePerformanceCounters**繫結屬性設定為**True**中其中一個和**False**中，配接器專屬的效能計數器會是啟用其中一及其他停用。</span><span class="sxs-lookup"><span data-stu-id="56081-127">Therefore, if there are two instances of the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding in the AppDomain, and the **EnablePerformanceCounters** binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other.</span></span> <span data-ttu-id="56081-128">不過，因為繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它將可設為**True**或**False**根據上一次指定哪些值。</span><span class="sxs-lookup"><span data-stu-id="56081-128">However, because the binding property for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False** depending on what value was specified last.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56081-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56081-129">See Also</span></span>  
[<span data-ttu-id="56081-130">配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="56081-130">Troubleshooting the adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)