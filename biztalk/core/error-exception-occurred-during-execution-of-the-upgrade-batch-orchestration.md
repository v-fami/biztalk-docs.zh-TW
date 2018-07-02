---
title: 在執行升級批次協調流程期間發生例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2221a498-98aa-43ab-bc4e-34dcbd92dcf0
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a12c1a116a0f7d35f6fbc7d2250c48f224081fae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981343"
---
# <a name="an-exception-has-occurred-during-the-execution-of-the-upgrade-batch-orchestration"></a>在執行升級批次協調流程期間發生例外狀況
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                       |
|-----------------|-------------------------------------------------------------------------------------------------------|
|  產品名稱   |          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| 產品版本 |                      [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    事件識別碼     |                                                   -                                                   |
|  事件來源   |                                          BizTalk Server EDI                                           |
|    元件    |                                            批次引擎                                            |
|  符號名稱  |                                     ExceptionOccuredDuringUpgrade                                     |
|  訊息文字   | 在升級批次協調流程執行期間發生例外狀況。 ErrorMessage = {0} |
  
## <a name="explanation"></a>說明  
 錯誤/警告/資訊事件表示，升級批次協調流程可能無法正確進行處理訊息因為訊息 欄位中指定的錯誤情況。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，判斷錯誤狀況是從 [訊息] 欄位、 解決錯誤，然後重新提交訊息。