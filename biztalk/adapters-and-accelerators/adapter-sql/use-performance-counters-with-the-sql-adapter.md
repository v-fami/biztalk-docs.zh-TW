---
title: 使用 SQL 配接器效能計數器 |Microsoft 文件
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
ms.openlocfilehash: 8f81189e34346d377686dac79b44e5a9b34889dc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965516"
---
# <a name="use-performance-counters-with-the-sql-adapter"></a>使用 SQL 配接器效能計數器
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]用戶端可以用於量測計的配接器效能的效能計數器。 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類"[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]」 以及 Adapter Pack 安裝。  
  
## <a name="the-lob-time-cumulative-performance-counter"></a>LOB （累加） Time 效能計數器  
 **BizTalk.NET Adapter for SQL**類別目錄具有一個效能計數器稱為 「 LOB 時間 （累計） 」。 此效能計數器代表的時間，以毫秒為單位，完成配接器起始的動作所需的 SQL Server 用戶端程式庫。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]建立特定的 SQL Server 執行個體和資料庫名稱的每個動作的效能計數器的執行個體。 在下列模式中建立執行個體：  
  
```  
<processId>:<appDomainId>:<endpointId>:<actionId>  
```  
  
 `<endpointId>`做為衍生`<sql_server_name>, <instance_name>, <database_name>`。  
  
 \<ActionId\>衍生以下列方式：  
  
-   針對開啟連接，動作識別碼會是 「 開啟 」。  
  
-   輸入的作業動作識別碼會是 「 輸入 」。  
  
-   對於傳出的作業動作識別碼是所叫用作業的動作與"/"由底線"_"取代。 此外，動作識別碼前面會加上"ExecuteScalar"、"ExecuteReader，"或"ExecuteNonQuery"根據配接器在內部使用的 SQL Server 資料庫上執行作業的方法。 例如，配接器會在內部使用**ExecuteReader**方法才能執行 SQL Server 中的預存程序。 因此，將會是預存程序，MyProcedure，動作 ID:  
  
    ```  
    ExecuteReader_Procedure_dbo_MyProcedure  
    ```  

 效能計數器會初始化只在配接器對 SQL Server 資料庫的第一個呼叫之後。 此外， [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx)效能計數器的屬性設定為 '處理序 」，這表示效能計數器不再存在時建立計數器在程式終止。
  
> [!NOTE]
>  LOB 的時間 （累計） 效能計數器的有效位數為 16 毫秒。  
  
## <a name="enabling-performance-counters"></a>啟用效能計數器  
 您可以啟用或停用的繫結屬性設定的效能計數器**EnablePerformanceCounters**。 若要啟用效能計數器， **EnablePerformanceCounters**內容繫結至**True**。 若要停用效能計數器，請設定**EnablePerformanceCounters**至**False**。 根據預設，此屬性設定為**False**。 如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a>效能計數器和 WCF LOB 配接器 SDK  
 值變更**EnablePerformanceCounters**也繫結屬性變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 此外，繫結屬性的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是動態的。 因此，如果有兩個執行個體[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]應用程式定義域中的繫結和**EnablePerformanceCounters**繫結屬性設定為**True**中其中一個和**False**中，配接器專屬的效能計數器會是啟用其中一及其他停用。 不過，因為繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它將可設為**True**或**False**根據上一次指定哪些值。  
  
## <a name="see-also"></a>請參閱  
[SQL 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)