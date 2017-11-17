---
title: "使用 Siebel 配接器的效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters, troubleshooting
- troubleshooting, performance counters
- performance counters, using
ms.assetid: 7930e8f6-5099-4a9c-b38a-13c9902635a6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2540801af6c30632250602b45c21e7b57cd2bc22
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="use-performance-counters-with-the-siebel-adapter"></a><span data-ttu-id="5bd2a-102">使用 Siebel 配接器的效能計數器</span><span class="sxs-lookup"><span data-stu-id="5bd2a-102">Use Performance Counters with the Siebel adapter</span></span>
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]<span data-ttu-id="5bd2a-103">用戶端可以用於量測計的配接器效能的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-103"> clients can use the performance counters to gauge the performance of the adapters.</span></span> <span data-ttu-id="5bd2a-104">[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類"[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]」 以及 Adapter Pack 安裝。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category "[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]" along with the Adapter Pack installation.</span></span>  
  
## <a name="the-lob-time-cumulative-performance-counter"></a><span data-ttu-id="5bd2a-105">LOB （累加） Time 效能計數器</span><span class="sxs-lookup"><span data-stu-id="5bd2a-105">The LOB Time (Cumulative) Performance Counter</span></span>  
 <span data-ttu-id="5bd2a-106">**BizTalk.NET Adapter for Siebel**類別目錄具有一個效能計數器稱為 「 LOB 時間 （累計） 」。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-106">The **BizTalk .NET Adapter for Siebel** category has one performance counter called "LOB Time (Cumulative)".</span></span> <span data-ttu-id="5bd2a-107">此效能計數器代表的時間，以毫秒為單位，完成配接器起始的動作所需的 LOB 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-107">This performance counter denotes the time, in milliseconds, that the LOB client library takes to complete an action that the adapter initiates.</span></span> <span data-ttu-id="5bd2a-108">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]建立特定的 Siebel 伺服器名稱的每個動作的效能計數器的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-108">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] creates an instance of the performance counter for each action, for a specific Siebel server name.</span></span> <span data-ttu-id="5bd2a-109">在下列模式中建立執行個體：</span><span class="sxs-lookup"><span data-stu-id="5bd2a-109">The instances are created in the following pattern:</span></span>  
  
```  
<process id>:<app domain id>:<endpoint id>:<action id>  
```  
  
 <span data-ttu-id="5bd2a-110">如果是[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，結束點識別碼是 Siebel 伺服器連線 URI 中所指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-110">In case of the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], the endpoint id is the name of the Siebel server, as specified in the connection URI.</span></span> <span data-ttu-id="5bd2a-111">動作識別碼可能是由執行任何動作[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]登入、 登出、 中繼資料，例如\<商務元件名稱 >。\<作業 >，\<商務服務名稱 >。\<商務服務方法 >。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-111">The action id could be any action performed by the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] such as Login, Logoff, Metadata, \<business component name>.\<operation>, \<business service name>.\<business service method>.</span></span> <span data-ttu-id="5bd2a-112">如果先前的命名慣例的名稱超過 127 個字元會導致動作識別碼會顯示以下列格式：</span><span class="sxs-lookup"><span data-stu-id="5bd2a-112">If the preceding naming convention results in a name that exceeds 127 characters only the action ID is displayed in the following format:</span></span>  
  
```  
:::<action id>  
```  
  
 <span data-ttu-id="5bd2a-113">如果`:::<action id>`也超過 127 個字元，修剪到 127 個字元。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-113">If `:::<action id>` also exceeds 127 characters, it is trimmed down to 127 characters.</span></span>  
  
 <span data-ttu-id="5bd2a-114">效能計數器會初始化只在配接器對 Siebel 系統的第一個呼叫之後。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-114">The performance counter is initialized only after the adapter makes the first call to the Siebel system.</span></span> <span data-ttu-id="5bd2a-115">此外， **InstanceLifetime**效能計數器的屬性設定為 '處理序 」，這表示效能計數器不再存在時建立計數器在程式終止。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-115">Also, the **InstanceLifetime** property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="5bd2a-116">LOB 的時間 （累計） 效能計數器的有效位數為 16 毫秒。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-116">The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="5bd2a-117">啟用效能計數器</span><span class="sxs-lookup"><span data-stu-id="5bd2a-117">Enabling Performance Counters</span></span>  
 <span data-ttu-id="5bd2a-118">您可以啟用或停用的繫結屬性設定的效能計數器**EnablePerformanceCounters**。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-118">The performance counters can be enabled or disabled by setting the binding property **EnablePerformanceCounters**.</span></span> <span data-ttu-id="5bd2a-119">設定**EnablePerformanceCounters**內容繫結至**True**來啟用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-119">Set **EnablePerformanceCounters** binding property to **True** to enable performance counters.</span></span> <span data-ttu-id="5bd2a-120">若要停用效能計數器，請設定**EnablePerformanceCounters**至**False**。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-120">To disable performance counters, set **EnablePerformanceCounters** to **False**.</span></span> <span data-ttu-id="5bd2a-121">根據預設， **EnablePerformanceCounters**設**False**。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-121">By default, **EnablePerformanceCounters** is set to **False**.</span></span>  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="5bd2a-122">效能計數器和 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="5bd2a-122">Performance Counters and the WCF LOB Adapter SDK</span></span>  
 <span data-ttu-id="5bd2a-123">值變更**EnablePerformanceCounters**繫結屬性變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-123">Changing the value of the **EnablePerformanceCounters** binding property changes the value of the corresponding performance counter for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="5bd2a-124">此外，繫結屬性的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是動態的。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-124">Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is dynamic.</span></span> <span data-ttu-id="5bd2a-125">因此，如果有兩個執行個體[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]AppDomain 中的繫結和**EnablePerformanceCounters**繫結屬性設定為**True**中其中一個和**False**中，配接器專屬的效能計數器會是啟用其中一及其他停用。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-125">Hence, if there are two instances of the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding in the AppDomain, and the **EnablePerformanceCounters** binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other.</span></span> <span data-ttu-id="5bd2a-126">不過，因為繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它將可設為**True**或**False**，取決於上次指定哪些值。</span><span class="sxs-lookup"><span data-stu-id="5bd2a-126">However, because the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False**, depending on what value was specified last.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd2a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bd2a-127">See Also</span></span>  
[<span data-ttu-id="5bd2a-128">Siebel 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="5bd2a-128">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)