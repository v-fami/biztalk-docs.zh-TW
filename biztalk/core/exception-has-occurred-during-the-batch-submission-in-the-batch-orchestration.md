---
title: 批次處理協調流程中提交批次期間發生例外狀況 |Microsoft Docs
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
ms.openlocfilehash: 838e9aff43dd260fd4af8e46ca88782c2389dfc7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971527"
---
# <a name="an-exception-has-occurred-during-the-batch-submission-in-the-batching-orchestration"></a>批次處理協調流程中提交批次期間發生例外狀況
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                  |
| 產品版本 |                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                              |
|    事件識別碼     |                                                          -                                                          |
|  事件來源   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                |
|    元件    |                                                   批次引擎                                                   |
|  符號名稱  |                                                  ExceptionOccured                                                   |
|  訊息文字   | 在批次處理協調流程中提交批次期間發生例外狀況。 批次識別碼 = {0}，ErrorMessage {1} |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，批次處理協調流程無法將批次項目加入批次因為 ErrorMessage 欄位中指定的錯誤情況。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，判斷錯誤狀況是從 [訊息] 欄位、 解決錯誤，然後重新提交訊息。