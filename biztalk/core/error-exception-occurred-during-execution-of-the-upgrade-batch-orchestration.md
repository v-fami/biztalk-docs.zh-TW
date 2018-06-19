---
title: 在升級的批次協調流程的執行期間發生例外狀況 |Microsoft 文件
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
ms.openlocfilehash: 9a0789853ba253d7d8e51c34a6c1d1ce64829f8d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006663"
---
# <a name="an-exception-has-occurred-during-the-execution-of-the-upgrade-batch-orchestration"></a>在升級的批次協調流程的執行期間發生例外狀況
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|BizTalk Server EDI|  
|元件|批次處理引擎|  
|符號名稱|ExceptionOccuredDuringUpgrade|  
|訊息文字|升級的批次協調流程執行期間發生例外狀況。 ErrorMessage = {0}|  
  
## <a name="explanation"></a>說明  
 錯誤/警告/資訊事件表示升級批次協調流程無法處理訊息正確因為 ErrorMessage 欄位中指定的錯誤情況。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，判斷錯誤狀況是從 ErrorMessage 欄位，解決錯誤，然後再重新提交訊息。