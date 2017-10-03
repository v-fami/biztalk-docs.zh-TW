---
title: "運算質類別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 029905e2-f01a-436a-b2ed-a364379c9cc5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89db4168af133e616f48ded54cce98cd54bb8ec8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="functoid-categories"></a>運算質類別
根據 BizTalk 運算質不同的使用目的，將它們分成不同的類別。 例如，資料庫運算質的設計為可在執行階段從資料庫擷取資料，而數學運算質則用於執行數學運算，等等。 在 BizTalk 對應工具中，運算質會依類別出現在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 工具箱中。 

## <a name="categories--description"></a>類別與描述
以下的表格顯示運算質類別、簡要描述類別並顯示每個類別中的運算質清單，包括其對應的參考頁面之連結。  
  
|運算質類別 <br/><br/> 類別描述|類別中的運算質|  
|---|---|  
|**進階** <br /><br /> 主要與迴圈記錄搭配使用。 也可以用於執行任意指令碼或編譯的程式碼。|Assert、 索引、 反覆項目、 迴圈、 大量複製 」、 「 Nil 值，記錄計數，指令碼、 表格擷取程式 」，表格迴圈 」、 「 值對應時，值對應 （簡維）|  
|**轉換** <br /><br /> 用以轉換成 ASCII 和從 ASCII 轉換，以及數字基數之間的轉換。|ASCII 到字元，字元到 ASCII，十六進位、 八進位|  
|**累計** <br /><br /> 用以執行迴圈記錄中的數學運算，例如平均值和串連。|累計平均]、 [累計串連、 累計最大值、 累計最小值和累計總和|  
|**資料庫** <br /><br /> 用以擷取資料庫的資料並用於目的執行個體訊息中。|資料庫查詢，傳回錯誤，格式訊息，取得應用程式識別碼、 取得應用程式值、 取得通用識別碼、 取得通用值、 移除應用程式識別碼，設定通用識別碼，值擷取程式 」|  
|**日期和時間** <br /><br /> 用以擷取目前的日期和時間，並計算差異時間。|新增天、 日期、 日期和時間、 時間|  
|**邏輯** <br /><br /> 用以執行各種邏輯運算，例如大於和存在。|等於、 大於、 大於或等於，IsNil，Less Than、 小於或等於邏輯 AND、 邏輯日期、 存在、 數字，邏輯不，邏輯 OR、 邏輯的字串、 不等於|  
|**數學** <br /><br /> 用以執行各種數學運算，例如加法和乘法。|絕對值，加法、 除法、 整數、 最大值、 乘法、 圓形、 平方根、 減法模數的最小值|  
|**科學記號** <br /><br /> 用以執行各種科學運算，例如對數和三角函數。|10 ^ n 反正切值、 指定基底的對數、 常用對數、 餘弦函數、 自然指數函式、 自然對數、 正弦、 正切函數，X ^ Y|  
|**字串** <br /><br /> 用以執行各種字串函數，例如修剪和串連。|小寫、 大小、 字串串連、 字串左邊擷取、 字串尋找字串、 字串左空白位置修剪、 字串，字串右空白位置修剪，預設為大寫|  
  
> [!NOTE]
>  運算質的用途通常可以從其名稱看出。  
  
> [!NOTE]
>  Microsoft 所隨附的所有運算質[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]皆為內嵌 C# 中，除了**資料庫**運算質。  
  
## <a name="see-also"></a>另請參閱  
 [基本運算質](../core/basic-functoids.md)   
 [進階運算質](../core/advanced-functoids.md)