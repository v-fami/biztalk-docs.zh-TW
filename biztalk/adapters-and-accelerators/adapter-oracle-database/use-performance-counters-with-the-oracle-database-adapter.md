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
# <a name="use-performance-counters-with-the-oracle-database-adapter"></a>使用 Oracle 資料庫配接器的效能計數器
Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]用戶端可以使用效能計數器來量測計的配接器的效能。 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類**BizTalk.NET 配接器，適用於 Oracle DB**以及安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
  
## <a name="lob-time-cumulative-performance-counter"></a>LOB 時間 （累計） 」 效能計數器  
 **BizTalk.NET 配接器，適用於 Oracle DB**類別都有一個效能計數器稱為 「 LOB 時間 （累計） 」。 此效能計數器代表時間 （毫秒），完成配接器起始的動作所花的 LOB 用戶端程式庫。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]建立效能計數器執行個體中的任何下列模式：  
  
```  
<process id>:<app domain id>:<oracle data source>:<string>  
```  
  
 其中可以是"string":  
  
- C  
  
- Connection.Close  
  
- 中繼資料  
  
- 訊息的動作。 例如，如果動作是`http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert`則字串會 SCOTT。Table.EMP.Insert。  
  
  相同的連線 URI 中指定 Oracle 資料來源。  
  
  配接器對 Oracle 資料庫的第一個呼叫之後，只初始化效能計數器。 此外，InstanceLifetime 的效能計數器設定為 'Process'，這表示，效能計數器就會消失只要建立計數器在程式終止。 如需詳細資訊`InstanceLifetime property`，請參閱 < [ http://go.microsoft.com/fwlink/p/?LinkId=104181 ](http://go.microsoft.com/fwlink/p/?LinkId=104181)。  
  
> [!NOTE]
>  LOB 的時間 （累計） 」 效能計數器的有效位數是 16 毫秒。  
  
## <a name="enabling-performance-counters"></a>啟用效能計數器  
 可以啟用或停用的繫結屬性設定的效能計數器**EnablePerformanceCounters**。 若要啟用效能計數器，請設定**EnablePerformanceCounters**屬性來繫結 **，則為 True**。 若要停用效能計數器，請設定**EnablePerformanceCounters**要**False**。 根據預設， **EnablePerformanceCounters**設為**False**。  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a>效能計數器和 WCF LOB 配接器 SDK  
 變更的值**EnablePerformanceCounters**繫結屬性也會變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 此外，繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是動態的。 因此，如果有兩個執行個體[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結在 AppDomain 中，而**EnablePerformanceCounters**繫結屬性設定為 **，則為 True**其中一和**False**中，配接器特有的效能計數器會會啟用下列其中一及其他停用。 不過，因為繫結屬性，如[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它會設定 **，則為 True**或**False**根據上一次指定哪些值。  
  
## <a name="see-also"></a>另請參閱  
[Oracle 資料庫配接器進行疑難排解](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)