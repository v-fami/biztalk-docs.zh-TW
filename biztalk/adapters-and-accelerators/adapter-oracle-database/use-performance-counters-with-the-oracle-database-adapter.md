---
title: 使用效能計數器與 Oracle 資料庫配接器 |Microsoft 文件
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
ms.openlocfilehash: ce36fe948daeb89d8fc248dbe33191aa69cdd9ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215182"
---
# <a name="use-performance-counters-with-the-oracle-database-adapter"></a>使用效能計數器，與 Oracle 資料庫配接器
Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]用戶端可以使用效能計數器來測量配接器的效能。 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類**BizTalk.NET Adapter for Oracle DB**以及安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
  
## <a name="lob-time-cumulative-performance-counter"></a>LOB （累加） Time 效能計數器  
 **BizTalk.NET Adapter for Oracle DB**類別目錄具有一個效能計數器稱為 「 LOB 時間 （累計） 」。 此效能計數器代表的時間，以毫秒為單位，完成配接器起始的動作所需的 LOB 用戶端程式庫。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]建立效能計數器的執行個體中的任何下列模式：  
  
```  
<process id>:<app domain id>:<oracle data source>:<string>  
```  
  
 其中可以是 「 字串 」:  
  
-   C  
  
-   Connection.Close  
  
-   中繼資料  
  
-   訊息的動作。 例如，如果動作是`http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert`字串將會 SCOTT。Table.EMP.Insert。  
  
 與連線 URI 中指定相同 Oracle 資料來源。  
  
 效能計數器會初始化只在配接器對 Oracle 資料庫的第一個呼叫之後。 此外，效能計數器的 InstanceLifetime 屬性會設定為 '處理序 」，這表示效能計數器不再存在時建立計數器在程式終止。 如需有關`InstanceLifetime property`，請參閱[http://go.microsoft.com/fwlink/p/?LinkId=104181](http://go.microsoft.com/fwlink/p/?LinkId=104181)。  
  
> [!NOTE]
>  LOB 的時間 （累計） 效能計數器的有效位數為 16 毫秒。  
  
## <a name="enabling-performance-counters"></a>啟用效能計數器  
 您可以啟用或停用的繫結屬性設定的效能計數器**EnablePerformanceCounters**。 若要啟用效能計數器， **EnablePerformanceCounters**內容繫結至**True**。 若要停用效能計數器，請設定**EnablePerformanceCounters**至**False**。 根據預設， **EnablePerformanceCounters**設**False**。  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a>效能計數器和 WCF LOB 配接器 SDK  
 值變更**EnablePerformanceCounters**也繫結屬性變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 此外，繫結屬性的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是動態的。 因此，如果有兩個執行個體[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]AppDomain 中的繫結和**EnablePerformanceCounters**繫結屬性設定為**True**中其中一個和**False**中，配接器專屬的效能計數器會是啟用其中一及其他停用。 不過，因為繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它將可設為**True**或**False**根據上一次指定哪些值。  
  
## <a name="see-also"></a>另請參閱  
[Oracle 資料庫配接器進行疑難排解](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)