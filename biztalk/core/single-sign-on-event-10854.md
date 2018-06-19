---
title: 單一登入： 事件 10854 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d8faed9d-5c7e-4b99-bcd9-ea5f670d5e72
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42f9e9e761689b2ed21ec37acdbb8a63f1f88070
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22277574"
---
# <a name="single-sign-on-event-10854"></a>單一登入： 事件 10854
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|제품 이름|Enterprise Single Sign-On|  
|제품 버전|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10854|  
|事件來源|ENTSSO|  
|구성 요소|해당 사항 없음|  
|符號名稱|ENTSSO_E_INVALID_STRING_FORMAT|  
|訊息文字|這個函式的字串格式無效。|  
  
## <a name="explanation"></a>說明  
 這個函式的字串格式無效。  
  
## <a name="user-action"></a>使用者動作  
 正確的密碼字串的格式如下所述︰  
  
 VT_BSTR 類型屬性  
  
 分隔符號是/（斜線）  
  
 dc = 預設的情況 (沒有作業需要執行任何動作)  
  
 範例︰ dc /  
  
 （沒有變更為 「 貓 」 到 「 貓 」）  
  
 uc = 大寫  
  
 範例︰ uc /  
  
 （將密碼變更為大寫的 「 貓 」 到 「 貓 」）  
  
 lc = 小寫  
  
 範例︰ lc /  
  
 （將密碼變更為小寫的 「 貓 」 到 「 貓 」）  
  
 rc = 移除字元-後面接著字元的計數  
  
 範例： rc/2 / #@/  
  
 (移除字元 '#' 和 '@' 從密碼-'C@t#' 至 'Ct')  
  
 sc = 的替代替代字元後面接著字元-後面接著要取代的字元計數  
  
 範例︰ sc/3/abc/def /  
  
 (移除的字元 'a'、 'b' 和 'c' 的密碼與取代從與有 '、 'e' 和 'f' 分別)  
  
 （以 'Cdt' 為 「 貓 」）  
  
 ps = 從開始時間-後面接著計數 （最小密碼長度），後面接著單一填補字元輸入板  
  
 範例︰ ps/8 / #/  
  
 （如果在找不到密碼長度，然後從一開始，直到 '#' 字元輸入板中的至少 8 個字元都是總 8 個字元）  
  
 （以 '###Cat' 為 「 貓 」）  
  
 pe = 從結尾-後面接著計數 （最小密碼長度），後面接著單一填補字元輸入板  
  
 範例︰ pe/10 / $/  
  
 （如果密碼不是在至少 10 個字元長度，則直到 '$' 字元開頭的填補是總數的 10 個字元）  
  
 （以 '$$$ 貓 」 為 「 貓 」）  
  
 tr = 截斷-後面計數字串的長度限制  
  
 範例︰ tr/11 /  
  
 ('Cat123456789' 到 'Cat12345678');  
  
 在字串中的順序進行處理的語彙基元。  
  
 範例：  
  
 uc/rc/1/（& s) / sc/2 / #$/-/ ps/8/&/tr/32 /