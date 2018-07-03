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
# <a name="use-performance-counters-with-the-sql-adapter"></a>使用 SQL 配接器的效能計數器
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] 用戶端可用來量測計的配接器效能的效能計數器。 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類"[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]」 以及 Adapter Pack 安裝。  
  
## <a name="the-lob-time-cumulative-performance-counter"></a>LOB 的時間 （累計） 效能計數器  
 **BizTalk.NET 配接器 sql**類別都有一個效能計數器稱為 「 LOB 時間 （累計） 」。 此效能計數器代表的時間，以毫秒為單位，完成配接器起始的動作所需的 SQL Server 用戶端程式庫。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]建立的每個動作，針對特定的 SQL Server 執行個體和資料庫名稱的效能計數器執行個體。 建立執行個體中以下列模式：  
  
```  
<processId>:<appDomainId>:<endpointId>:<actionId>  
```  
  
 `<endpointId>`做為衍生`<sql_server_name>, <instance_name>, <database_name>`。  
  
 \<ActionId\>衍生以下列方式：  
  
- 針對開啟連接，指定動作識別碼會是 [開啟]。  
  
- 若為輸入的作業，指定動作識別碼會是"Inbound"。  
  
- 為輸出的作業，指定動作識別碼會是正在叫用作業的動作具有"/"底線"_"取代。 此外，指定動作識別碼前面會加上"ExecuteScalar 」、 「 ExecuteReader"或"ExecuteNonQuery 」 根據配接器在內部使用的 SQL Server 資料庫上執行作業的方法。 例如，配接器會在內部使用**ExecuteReader** SQL Server 中執行預存程序的方法。 因此，您也可以指定動作識別碼，如預存程序，MyProcedure，將會：  
  
  ```  
  ExecuteReader_Procedure_dbo_MyProcedure  
  ```  

  配接器對元件的 SQL Server 資料庫的第一個呼叫之後，只初始化效能計數器。 此外， [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx)的效能計數器的屬性設定為 'Process'，這表示，效能計數器就會消失只要建立計數器在程式終止。
  
> [!NOTE]
>  LOB 的時間 （累計） 」 效能計數器的有效位數是 16 毫秒。  
  
## <a name="enabling-performance-counters"></a>啟用效能計數器  
 可以啟用或停用的繫結屬性設定的效能計數器**EnablePerformanceCounters**。 若要啟用效能計數器，請設定**EnablePerformanceCounters**屬性來繫結 **，則為 True**。 若要停用效能計數器，請設定**EnablePerformanceCounters**要**False**。 根據預設，此屬性設為**False**。 如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a>效能計數器和 WCF LOB 配接器 SDK  
 變更的值**EnablePerformanceCounters**繫結屬性也會變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 此外，繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是動態的。 因此，如果有兩個執行個體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結應用程式定義域，而**EnablePerformanceCounters**繫結屬性設定為 **，則為 True**其中一和**False**中，配接器特有的效能計數器會會啟用下列其中一及其他停用。 不過，因為繫結屬性，如[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它會設定 **，則為 True**或**False**根據上一次指定哪些值。  
  
## <a name="see-also"></a>另請參閱  
[SQL 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)