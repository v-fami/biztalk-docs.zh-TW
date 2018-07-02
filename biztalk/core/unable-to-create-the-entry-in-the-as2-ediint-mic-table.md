---
title: 無法在 AS2 EDIINT MIC 表格中建立項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1c75d70-e39e-4465-b32b-db646c059c9b
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d0a9cf5f472a449d8632553ec41738c7e4ebd9f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970447"
---
# <a name="unable-to-create-the-entry-in-the-as2-ediint-mic-table"></a>無法在 AS2 EDIINT MIC 表格中建立項目
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                               |
| 產品版本 |                                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                           |
|    事件識別碼     |                                                                                       -                                                                                       |
|  事件來源   |                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                             |
|    元件    |                                                                                  AS2 引擎                                                                                   |
|  符號名稱  |                                                                        AS2MicDataStoreCreateEntryError                                                                        |
|  訊息文字   | 無法在 AS2 EDIINT MIC 表格中建立項目。 這可能因重複的 AS2-From、as2-以和 MessageID 組合寫入至資料表。  錯誤： {0} |
  
## <a name="explanation"></a>說明  
 此錯誤表示資料庫連接問題或資料庫資料表中存在索引鍵的資料列。 完整的錯誤訊息應該提供插入作業的失敗原因的相關資訊。 MDN 收到之後 （不論成功或失敗），以便在收到 MDN 之後，應該永遠不會發生此錯誤，則會移除資料表中的項目。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請檢查完整的錯誤訊息，如需插入作業失敗的原因。 在 SQL 中，在 EDIINT_MIC 資料表中，判斷是否有重複的 AS2-從和 AS2-MessageID 來組合。 如果是的話，請將它們移除。