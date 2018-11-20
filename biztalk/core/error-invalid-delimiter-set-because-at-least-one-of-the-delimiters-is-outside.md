---
title: 無效的分隔符號集，因為至少其中一個分隔符號是允許的範圍之外 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1286559-765b-4728-945d-cf3386e1ba06
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebda7e3ebfe2adc0084b672a2f66ed1ad639c943
ms.sourcegitcommit: c3070a7a3f332857357f056dc632829b43869c17
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2018
ms.locfileid: "51630363"
---
# <a name="invalid-delimiter-set-because-at-least-one-of-the-delimiters-is-outside-the-allowed-range"></a>無效的分隔符號集，因為至少其中一個分隔符號是在允許的範圍之外
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------|
|  產品名稱   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| 產品版本 |                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    事件識別碼     |                                                   -                                                    |
|  事件來源   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI         |
|    元件    |                                               將 EDI 引擎                                               |
|  符號名稱  |                                          DelimiterOutOfRange                                           |
|  訊息文字   | 無效的分隔符號集{0}，其中至少一個分隔符號是允許的 0 到 127 的範圍之外 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中的一或多個分隔符號中的 ASCII 字元的值範圍以外設定。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定交換中的每個分隔符號為 ASCII 字元集，，，然後重新傳送交換。
