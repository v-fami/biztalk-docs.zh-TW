---
title: 單一登入： 事件 10854 |Microsoft Docs
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
ms.openlocfilehash: d1f89ef2727933e72de1e9d759bd91dc507a0954
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994401"
---
# <a name="single-sign-on-event-10854"></a>單一登入： 事件 10854
## <a name="details"></a>詳細資料  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  產品名稱   |                 企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    事件識別碼     |                           10854                            |
|  事件來源   |                           ENTSSO                           |
|    元件    |                            不適用                             |
|  符號名稱  |               ENTSSO_E_INVALID_STRING_FORMAT               |
|  訊息文字   |     字串格式不正確。 此函式。      |
  
## <a name="explanation"></a>說明  
 字串格式不正確。 此函式。  
  
## <a name="user-action"></a>使用者動作  
 正確的密碼字串的格式如下所述。  
  
 將 VT_BSTR 類型的屬性  
  
 分隔符號是/（斜線）  
  
 dc = 預設案例中 (沒有作業-不執行任何動作)  
  
 範例： dc /  
  
 （無變更-'Cat' 到 'Cat'）  
  
 uc = 大寫  
  
 範例： uc /  
  
 （將密碼變更為大寫-'Cat' 到 'CAT'）  
  
 lc = 小寫  
  
 範例： lc /  
  
 （將密碼變更為小寫的 'Cat' 到 'cat'）  
  
 rc = 移除字元-後面接著字元的計數  
  
 範例： rc/2 / #@/  
  
 (移除的字元 '#' 和 '@' 的密碼-'C@t#' 到 'Ct')  
  
 sc = 的替代替代字元後面接著字元-後面接著要取代的字元計數  
  
 範例： sc/3/abc/def /  
  
 (移除的字元 'a'、 'b'，但 'c' 的密碼與取代使用 '，'e' 和 'f' 分別)  
  
 (以 'Cdt' 為 ' cat')  
  
 ps = 面板從開始時間-後面接著單一的填補字元的計數 （最小密碼長度）  
  
 範例： ps/8 / #/  
  
 （如果密碼不是在最少 8 字元長度，然後從該處之前的字元 '#' 開頭的板都是總 8 個字元）  
  
 (以 '###Cat' 為 ' cat')  
  
 pe = 面板從結尾-後面接著單一的填補字元的計數 （最小密碼長度）  
  
 範例： pe/10 / $/  
  
 （如果密碼不是在至少 10 個字元長度，則直到字元 '$' 結尾的板都是總計的 10 個字元）  
  
 (以 'Cat$ $$' 為 ' cat')  
  
 tr = 截斷-後面計數-字串的長度限制  
  
 範例： tr/11 /  
  
 ('Cat123456789' 到 'Cat12345678');  
  
 權杖會在字串中的順序處理。  
  
 範例  
  
 uc/rc/1/（& s) / sc/2 / #$，/ ps/8/&/tr/32 /