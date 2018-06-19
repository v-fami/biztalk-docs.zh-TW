---
title: 使用 Siebel 配接器的效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance counters, troubleshooting
- troubleshooting, performance counters
- performance counters, using
ms.assetid: 7930e8f6-5099-4a9c-b38a-13c9902635a6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bebbd605df52e023c78112b78ad51db13d896cc7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962476"
---
# <a name="use-performance-counters-with-the-siebel-adapter"></a>使用 Siebel 配接器的效能計數器
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]用戶端可以用於量測計的配接器效能的效能計數器。 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式會建立效能計數器分類"[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]」 以及 Adapter Pack 安裝。  
  
## <a name="the-lob-time-cumulative-performance-counter"></a>LOB （累加） Time 效能計數器  
 **BizTalk.NET Adapter for Siebel**類別目錄具有一個效能計數器稱為 「 LOB 時間 （累計） 」。 此效能計數器代表的時間，以毫秒為單位，完成配接器起始的動作所需的 LOB 用戶端程式庫。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]建立特定的 Siebel 伺服器名稱的每個動作的效能計數器的執行個體。 在下列模式中建立執行個體：  
  
```  
<process id>:<app domain id>:<endpoint id>:<action id>  
```  
  
 如果是[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，結束點識別碼是 Siebel 伺服器連線 URI 中所指定的名稱。 動作識別碼可能是由執行任何動作[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]登入、 登出、 中繼資料，例如\<商務元件名稱\>。\<作業\>，\<商務服務名稱\>。\<商務服務方法\>。 如果先前的命名慣例的名稱超過 127 個字元會導致動作識別碼會顯示以下列格式：  
  
```  
:::<action id>  
```  
  
 如果`:::<action id>`也超過 127 個字元，修剪到 127 個字元。  
  
 效能計數器會初始化只在配接器對 Siebel 系統的第一個呼叫之後。 此外， **InstanceLifetime**效能計數器的屬性設定為 '處理序 」，這表示效能計數器不再存在時建立計數器在程式終止。 
  
> [!NOTE]
>  LOB 的時間 （累計） 效能計數器的有效位數為 16 毫秒。  
  
## <a name="enabling-performance-counters"></a>啟用效能計數器  
 您可以啟用或停用的繫結屬性設定的效能計數器**EnablePerformanceCounters**。 設定**EnablePerformanceCounters**內容繫結至**True**來啟用效能計數器。 若要停用效能計數器，請設定**EnablePerformanceCounters**至**False**。 根據預設， **EnablePerformanceCounters**設**False**。  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a>效能計數器和 WCF LOB 配接器 SDK  
 值變更**EnablePerformanceCounters**繫結屬性變更為對應的效能計數器的值[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 此外，繫結屬性的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的而針對[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]是動態的。 因此，如果有兩個執行個體[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]AppDomain 中的繫結和**EnablePerformanceCounters**繫結屬性設定為**True**中其中一個和**False**中，配接器專屬的效能計數器會是啟用其中一及其他停用。 不過，因為繫結屬性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是靜態的它將可設為**True**或**False**，取決於上次指定哪些值。  
  
## <a name="see-also"></a>請參閱  
[Siebel 配接器進行疑難排解](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)