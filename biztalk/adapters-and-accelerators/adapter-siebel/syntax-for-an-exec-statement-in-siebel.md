---
title: Siebel 的 EXEC 陳述式的語法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EXEC statement, syntax for
- Data Provider for Siebel, EXEC statement
ms.assetid: c5534102-bf37-4b39-83ab-e09483744c4d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4db9ca810860ea64ffa474725dc485fecfaa5e78
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963076"
---
# <a name="syntax-for-an-exec-statement-in-siebel"></a>Siebel 中 EXEC 陳述式語法
使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，ADO.NET 用戶端也可以執行 EXEC 作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 EXEC 陳述式的語法為：  
  
```  
EXEC  
<Business Service name>.<Business Service method>  
<value 1..n>,  
@parameter 1..n [OUTPUT],  
@parameter 1..n = <value>  
  
```  
  
 在上述語法中，`\<value 1..n\>`代表一組未命名的參數。 這些是硬式編碼值。 它們通常代表在參數中。  它們也可能代表 INOUT 參數。 不過，如果 INOUT 參數使用硬式編碼值，該參數相關聯的輸出值無法擷取在 EXEC 陳述式執行之後。  
  
 `@parameter 1..n`語法代表一組具名參數，它可以是 IN、 INOUT、 參數或 OUT 參數。 輸出參數後面必須接著**輸出**關鍵字。  
  
> [!NOTE]
>  **輸出**關鍵字只能用於與 OUT 參數，而不是使用 INOUT 參數。  
  
 若要指定參數值的內嵌，使用`@parameter 1..n = <value>`語法。  
  
 所有參數必須都是以逗號分隔。  
  
 EXEC 陳述式的範例如下：  
  
```  
EXEC ExtractDataService.Echo @In, @InOut, @Out OUTPUT  
  
EXEC ExtractDataService.Echo 'InputValue', @InOut, @Out OUTPUT  
  
EXEC ExtractDataService.Echo @InOut, @Out OUTPUT, @In='InputValue'  
  
EXEC ExtractDataService.Echo 'InputValue', @Out OUTPUT, @InOut='InputValue'  
  
```  
  
> [!NOTE]
>  每個參數名稱 (例如`@In`在上述範例中) 必須符合對應的引數名稱，在 Siebel 商務服務方法。  
  
## <a name="see-also"></a>請參閱  
 [使用 .NET Framework Data Provider for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)