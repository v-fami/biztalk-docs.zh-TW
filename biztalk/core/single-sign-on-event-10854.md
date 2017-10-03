---
title: "單一登入： 事件 10854 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8faed9d-5c7e-4b99-bcd9-ea5f670d5e72
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42f9e9e761689b2ed21ec37acdbb8a63f1f88070
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10854"></a>單一登入： 事件 10854
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10854|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|ENTSSO_E_INVALID_STRING_FORMAT|  
|訊息文字|字串格式不正確。 這個函式。|  
  
## <a name="explanation"></a>說明  
 字串格式不正確。 這個函式。  
  
## <a name="user-action"></a>使用者動作  
 正確的密碼字串的格式如下所述。  
  
 VT_BSTR 類型的屬性  
  
 分隔符號是/（斜線）  
  
 dc = 預設案例中 (沒有作業-不執行任何動作)  
  
 範例： dc /  
  
 （無變化-'Cat' 至 'Cat'）  
  
 uc = 大寫  
  
 範例： uc /  
  
 （將密碼變更為大寫-'Cat' 至 'CAT'）  
  
 lc = 小寫  
  
 範例： lc /  
  
 （將密碼變更為小寫的 'Cat' 至 'cat'）  
  
 rc = 移除字元-後面接著後面接著字元的計數  
  
 範例： rc/2 / #@/  
  
 (移除字元 '#' 和 '@' 從密碼-'C@t#' 至 'Ct')  
  
 sc = 的替代的替代字元後面接著字元-後面接著後面接著要取代的字元計數  
  
 範例： sc/3/abc/def /  
  
 (移除的字元 'a'、 'b' 和 'c' 取代密碼與使用具有 '、 'e' 和 'f' 分別)  
  
 （' 數據機用作 ' 'Cdt'）  
  
 ps = 從開始時間-後面接著計數 （最小密碼長度），後面接著單一填補字元板  
  
 範例： ps/8 / #/  
  
 （如果密碼不是在至少 8 字元長度，然後從直到 '#' 字元開頭的填補都是總 8 個字元）  
  
 （' 數據機用作 ' '###Cat'）  
  
 pe = 從端-後面接著計數 （最小密碼長度），後面接著單一填補字元板  
  
 範例： pe/10 / $/  
  
 （如果密碼不是在至少 10 個字元長度，則以字元 '$' 直到結尾處的填補都是總 10 個字元）  
  
 （' 數據機用作 ' 'Cat$ $$'）  
  
 tr = 截斷-後面計數-字串長度限制  
  
 範例： tr/11 /  
  
 ('Cat123456789' 至 'Cat12345678');  
  
 語彙基元字串的順序進行處理。  
  
 範例：  
  
 uc/rc/1/（& s) / sc/2 / #$/-/ ps/8/&/tr/32 /