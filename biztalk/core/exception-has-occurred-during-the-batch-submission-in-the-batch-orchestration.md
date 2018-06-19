---
title: 在批次處理協調流程中的批次提交期間發生例外狀況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c58b2fa9-d036-4e09-a0f8-77a2f983881a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a3e61cc7375acf5d9faf0d72ab36127532c66ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245830"
---
# <a name="an-exception-has-occurred-during-the-batch-submission-in-the-batching-orchestration"></a>在批次處理協調流程中的批次提交期間發生例外狀況
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|ExceptionOccured|  
|訊息文字|在批次處理協調流程中的批次提交期間發生例外狀況。 批次識別碼 = {0}，ErrorMessage {1}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，批次處理協調流程無法加入批次項目至批次因為 ErrorMessage 欄位中指定的錯誤情況。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，判斷錯誤狀況是從 ErrorMessage 欄位，解決錯誤，然後再重新提交訊息。