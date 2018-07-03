---
title: 無法從交換 (R2) 中讀取分隔符號集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17bdd32e-d43f-4f59-af27-5d3054fd5432
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 778bfa7c417776e5baa78a6103e1075c7ccac27b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996271"
---
# <a name="delimiter-set-could-not-be-read-from-the-interchange-r2"></a>無法從交換 (R2) 中讀取分隔符號集
## <a name="details"></a>詳細資料  

|                 |                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                     |
| 產品版本 |                                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                 |
|    事件識別碼     |                                                             -                                                             |
|  事件來源   |                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                   |
|    元件    |                                                        將 EDI 引擎                                                         |
|  符號名稱  |                                                             -                                                             |
|  訊息文字   | 無法從交換中讀取分隔符號集。 從根節點遺失屬性 DelimiterSetSerializedData。 |

## <a name="explanation"></a>說明  
 此錯誤表示交換不包含分隔符號設定的值。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  

- 加入分隔符號設定的值交換，如下所示：  

  1.  開啟訊息。  

  2.  決定是否在交換沒有 UNA 區段。 如果沒有 UNA 區段，請要求合作夥伴將與交換的 UNA 區段。  

- 輸入分隔符號值至 EfactDelimiters 管線屬性中，如下所示：  

  1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，以滑鼠右鍵按一下使用您要設定屬性之管線的接收位置或傳送埠。 按一下 **[屬性]**。  

  2. 按一下要設定屬性之管線旁邊的省略符號按鈕 (?。  

  3. 輸入 UNA 分隔符號為逗號分隔清單 （UNA1、 UNA2、 UNA3、 UNA4、 UNA5，與 UNA6），變更所需的預設值。 預設值如下所示： 0x3A、 0x2B，0x2C、 0x3F，0x20，0x27。  

  4. 按一下 [確定] 。
