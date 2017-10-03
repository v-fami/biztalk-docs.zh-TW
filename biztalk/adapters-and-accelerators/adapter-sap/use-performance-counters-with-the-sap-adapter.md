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
ms.openlocfilehash: 5da387377f6201b518d3c5fdf37dabb872bcf600
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="use-performance-counters-with-the-sap-adapter"></a>SAP 配接器搭配使用效能計數器
Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]用戶端可以使用效能計數器來測量配接器的效能。 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類"[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]"沿著安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
  
## <a name="lob-time-cumulative-performance-counter"></a>LOB （累加） Time 效能計數器  
 **BizTalk.NET 配接器適用於 SAP**類別目錄具有一個效能計數器稱為 「 LOB 的時間 （累計） 」。 此效能計數器代表的時間，以毫秒為單位，完成配接器起始的動作所需的 LOB 用戶端程式庫。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]建立效能計數器的執行個體中的下列模式：  
  
```  
<process id>:<app domain id>:<endpoint id>:<action id>  
```  
  
 可能的結束點識別碼：  
  
-   針對從配接器對 SAP 系統 （輸出） 的呼叫  
  
    -   A、\<主應用程式伺服器 >，\<系統編號 >  
  
    -   B\<訊息伺服器主機 >，\<R3NAME >  
  
    -   D、\<目的地 >  
  
-   對從 SAP 系統的配接器呼叫 （輸入）  
  
    -   我，\<閘道器主機 >，\<閘道伺服器 >  
  
    -   識別碼、\<目的地 >  
  
 動作識別碼可能是：  
  
-   \<RFC 名稱 > （針對 RFC 呼叫）  
  
-   T，\<RFC 名稱 > （適用於 tRFC 呼叫）  
  
 效能計數器會初始化只在配接器對 SAP 系統的第一個呼叫之後。 此外， [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx)效能計數器的屬性設定為 '處理序 」，這表示效能計數器不再存在時建立計數器在程式終止。
  
> [!NOTE]
>  LOB 的時間 （累計） 效能計數器的有效位數為 16 毫秒。  
  
## <a name="enabling-performance-counters"></a>啟用效能計數器  
 您可以啟用或停用的繫結屬性設定的效能計數器*EnablePerformanceCounters*。 若要啟用效能計數器， *EnablePerformanceCounters*內容繫結至**True**。 若要停用效能計數器，請設定*EnablePerformanceCounters*至**False**。 根據預設， *EnablePerformanceCounters*設**False**。  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a>效能計數器和 WCF LOB 配接器 SDK  
 值變更*EnablePerformanceCounters*也繫結屬性變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 此外，繫結屬性的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是動態的。 因此，如果有兩個執行個體[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]AppDomain 中的繫結和*EnablePerformanceCounters*繫結屬性設定為**True**中其中一個和**False**中，配接器專屬的效能計數器會是啟用其中一及其他停用。 不過，因為繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它將可設為**True**或**False**根據上一次指定哪些值。  
  
## <a name="see-also"></a>另請參閱  

[SAP 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)