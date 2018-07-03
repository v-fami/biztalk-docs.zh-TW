---
title: Edifact 交換 Xml 序列化失敗，因為無效的結構，無 FunctionalGroup 或 ServiceSchema |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 530faadd-e301-4743-b4b3-b04ba7578f1d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 370b9844faaa46955f6e45bfcea78f6eba0f8cf9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003151"
---
# <a name="edifact-interchange-xml-serialization-failed-due-to-invalid-structure-no-functionalgroup-or-serviceschema"></a>Edifact 交換 Xml 序列化失敗，因為無效的結構，無 FunctionalGroup 或 ServiceSchema
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                              |
| 產品版本 |                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                          |
|    事件識別碼     |                                                                      -                                                                       |
|  事件來源   |                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                            |
|    元件    |                                                                  將 EDI 引擎                                                                  |
|  符號名稱  |                                                                      -                                                                       |
|  訊息文字   | Edifact 交換 Xml 序列化失敗，因為無效的結構。 尋找 FunctionalGroup 或 ServiceSchema UNZ，但是找不到。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理批次的 EDIFACT 交換因為交換 XML 檔案中未包含 TransactionSetGroup 或 FunctionalGroup 的標記時保留。  
  
 BizTalk 可處理的批次的交換時，會保留，交易集的群組或交換的 XML 檔案中的群組一組指定的 XML 標記。 群組一組指定的 FunctionalGroup 標記。 ServiceSchema 旗標會指出用於保留批次交換的控制結構描述。 如果您設定保留批次使用 接收管線，並通過傳輸的傳送管線，就會發生這個錯誤狀況。 標記會由接收管線設定，並移除的傳送管線。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定保留批次產生的 XML 檔有格式正確的 XML 結構 （適用於多個群組） 的 FunctionalGroup 標記和/或 ServiceSchema 標記 （用於保留批次交換的控制結構描述）。