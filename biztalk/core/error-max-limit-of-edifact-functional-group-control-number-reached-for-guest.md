---
title: "Guest 設定的已達到可接受的 Edifact 功能群組控制編號的最高上限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93ea1bd6-8c39-4d11-81a5-75d4a861e041
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 736b191628807bf7ed0af647e83fb3665d4f2d65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-functional-group-control-number-has-reached-for-guest-settings"></a>Guest 設定的 Edifact 功能群組控制編號已達到可接受的最高上限
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|GlobalEdifactUngNumberError|  
|訊息文字|Guest 設定的 Edifact 功能群組控制編號已達到可接受的最高上限。 請瀏覽到全域組態 receiver 角色畫面中，夥伴協議管理員的 [UNG 5] 欄位，以重設計數器|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理外寄交換，因為全域設定中指定之 UGN5 欄位的群組控制編號，特別是欄位 UNG5.2 中的參考編號，大於允許的最大值。 群組控制編號允許的最大值取決於 UNG5 中三個欄位的值。 最大字元數是參考編號欄位 UNG5.2，13 for UNG5.1 中的前置詞和 13 for UNG5.3，在後置詞結合的所有三個欄位 14 中 14。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設的群組控制編號，參考編號欄位 (UNG5.2)，如下所示：  
  
1.  開啟 [EDI 全域屬性] 對話方塊中的 [UNG 和 UNH 區段定義] 頁面。  
  
2.  按一下 UNG5 欄位相關聯的編輯欄位。  
  
3.  新的值設定的群組控制編號 （UNG5.2 中的參考編號） 的中間欄位的欄位具有可接受數。