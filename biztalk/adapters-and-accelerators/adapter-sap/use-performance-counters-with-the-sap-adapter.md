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
# <a name="use-performance-counters-with-the-sap-adapter"></a>使用 SAP 配接器的效能計數器
Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]用戶端可以使用效能計數器來量測計的配接器的效能。 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類 」[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]"沿著安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
  
## <a name="lob-time-cumulative-performance-counter"></a>LOB 時間 （累計） 」 效能計數器  
 **適用於 SAP 的 BizTalk.NET Adapter**類別都有一個效能計數器稱為 「 LOB 時間 （累計） 」。 此效能計數器代表時間 （毫秒），完成配接器起始的動作所花的 LOB 用戶端程式庫。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]建立效能計數器執行個體中以下列模式：  
  
```  
<process id>:<app domain id>:<endpoint id>:<action id>  
```  
  
 可能的結束點 ID:  
  
- 針對從配接器對 SAP 系統 （輸出） 的呼叫  
  
  -   A\<應用程式伺服器主機\>，\<系統編號\>  
  
  -   B\<訊息伺服器主機\>，\<R3NAME\>  
  
  -   D、\<目的地\>  
  
- 對配接器從 SAP 系統的呼叫 （輸入）  
  
  -   我\<閘道器主機\>，\<閘道伺服器\>  
  
  -   識別碼、\<目的地\>  
  
  指定動作識別碼可能是：  
  
- \<RFC 名稱\>（如 RFC 呼叫）  
  
- T，則\<RFC 名稱\>（適用於 tRFC 呼叫）  
  
  配接器對 SAP 系統的第一個呼叫之後，只初始化效能計數器。 此外， [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx)的效能計數器的屬性設定為 'Process'，這表示，效能計數器就會消失只要建立計數器在程式終止。
  
> [!NOTE]
>  LOB 的時間 （累計） 」 效能計數器的有效位數是 16 毫秒。  
  
## <a name="enabling-performance-counters"></a>啟用效能計數器  
 可以啟用或停用的繫結屬性設定的效能計數器*EnablePerformanceCounters*。 若要啟用效能計數器，請設定*EnablePerformanceCounters*屬性來繫結 **，則為 True**。 若要停用效能計數器，請設定*EnablePerformanceCounters*要**False**。 根據預設， *EnablePerformanceCounters*設為**False**。  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a>效能計數器和 WCF LOB 配接器 SDK  
 變更的值*EnablePerformanceCounters*繫結屬性也會變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 此外，繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是動態的。 因此，如果有兩個執行個體[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結在 AppDomain 中，而*EnablePerformanceCounters*繫結屬性設定為 **，則為 True**其中一和**False**中，配接器特有的效能計數器會會啟用下列其中一及其他停用。 不過，因為繫結屬性，如[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它會設定 **，則為 True**或**False**根據上一次指定哪些值。  
  
## <a name="see-also"></a>另請參閱  

[SAP 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)