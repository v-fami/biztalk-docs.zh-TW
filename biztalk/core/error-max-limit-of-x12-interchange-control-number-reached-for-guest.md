---
title: X12 交換控制編號已達到 Guest 設定的可接受的最高上限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9737053d-6065-4c88-8dfa-5f69b48e0e82
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1145573dc5aec674e79cef960c4737ddfe6d5e9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005951"
---
# <a name="max-limit-of-acceptable-x12-interchange-control-number-has-reached-for-guest-settings"></a>X12 交換控制編號已達到 Guest 設定的可接受的最高上限
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                             |
| 產品版本 |                                                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                         |
|    事件識別碼     |                                                                                                     -                                                                                                      |
|  事件來源   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                           |
|    元件    |                                                                                                 將 EDI 引擎                                                                                                 |
|  符號名稱  |                                                                                          GlobalX12IsaNumberError                                                                                           |
|  訊息文字   | 可接受的 X12 交換控制編號已達到 Guest 設定的最大限制。 瀏覽至全域組態接收者角色畫面，在夥伴協議 管理員中的欄位 ISA 13，重設計數器 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為全域設定中指定的 [ISA13] 欄位中的交換控制編號大於允許的最大值。 交換控制編號的字元數目上限是 9 個。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設交換控制編號，如下所示：  
  
1.  在 [EDI 全域屬性] 對話方塊中，開啟 [ISA 區段定義] 頁面。  
  
2.  按一下 [ISA13] 欄位相關聯的編輯欄位。  
  
3.  使欄位具有一個可接受的數字，則您可以設為新值的交換控制編號。