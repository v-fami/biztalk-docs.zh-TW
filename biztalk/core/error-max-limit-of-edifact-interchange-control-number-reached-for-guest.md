---
title: Guest 設定的已達到可接受 Edifact 交換控制編號的最高上限 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5d2dcc0-61fd-47c9-9339-8a85319c5398
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dc8110f9aa9a48e098f970383b65266cc544c19
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241526"
---
# <a name="max-limit-of-acceptable-edifact-interchange-control-number-has-reached-for-guest-settings"></a>Guest 設定的已達到可接受 Edifact 交換控制編號的最高上限
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|GlobalEdifactUnbNumberError|  
|訊息文字|Guest 設定的已達到可接受 Edifact 交換控制編號的最高上限。 瀏覽到全域組態接收者角色畫面，欄位 UNB 5 在夥伴協議管理員 中，重設計數器|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄交換的交換控制編號，在通用設定，特別是參考編號欄位 UNB5.2，在指定的 ISA13 欄位中，因此大於允許的最大值。 交換控制編號允許的最大值取決於 UNB5 中三個欄位的值。 字元數上限為 14 個欄位 UNB5.2，13 for UNB5.1 中的前置詞和 13 for UNB5.3，在後置詞結合的所有三個欄位 14 中的參考編號。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設的交換控制編號，參考編號欄位 (UNB5.2)，如下所示：  
  
1.  在 EDI 全域屬性 對話方塊中，開啟 UNB 區段定義頁面。  
  
2.  按一下 UNB5 欄位相關聯的編輯欄位。  
  
3.  新的值設定交換控制編號 （UNB5.2 中的參考編號） 的中間欄位的欄位具有可接受數。