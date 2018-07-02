---
title: 不是唯一分隔符號，區段和元件分隔符號相同 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 13c41899-02af-4678-a4ad-f3dc48c1fdfb
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6068b13502b8893fd5065957b6dd73072236126
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983775"
---
# <a name="delimiters-are-not-unique-segment-and-component-separators-are-the-same"></a>不是唯一分隔符號，區段和元件分隔符號相同
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |        不是唯一分隔符號，區段和元件分隔符號相同        |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，EDI 傳送管線無法處理外寄交換因為區段結束字元或元件分隔符號相同的值。 在 X12 交換，區段結束字元是最後一個字元位置的 ISA 區段中的字元，元件分隔符號是 ISA16 欄位中的字元。 在 EDIFACT 交換，區段結束字元是 una6 欄位中的字元，和元件分隔符號是 UNA1 欄位中的字元。 具有相同值的兩個分隔符號可能會發生 （但會導致錯誤狀況） 在保留批次案例中，或如果交換是透過通過傳輸接收，然後挑選最多的傳送埠即 MessageBox 中的 XML 檔案。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，區段結束字元或交換中的元件分隔符號的值變更，然後再重新送出交換。