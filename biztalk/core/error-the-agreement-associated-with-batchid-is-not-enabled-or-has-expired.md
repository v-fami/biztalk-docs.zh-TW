---
title: 與 BatchId 相關的協議尚未啟用，或已過期。 批次處理無法繼續。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d92cb07-7646-42b3-90a8-18acbcd145cd
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ace947d1c05774882b1e8f78f7b093f0795ba919
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018286"
---
# <a name="the-agreement-associated-with-batchid-is-not-enabled-or-has-expired-batching-cannot-continue"></a>與 BatchId 相關的協議尚未啟用，或已過期。 批次處理無法繼續。
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
|  產品名稱   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]         |
| 產品版本 |                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                     |
|    事件識別碼     |                                                 -                                                  |
|  事件來源   |       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI       |
|    元件    |                                             將 EDI 引擎                                             |
|  符號名稱  |                                    ErrorBatchAgreementDisabled                                     |
|  訊息文字   | 與 BatchId 相關的協議{0}未啟用或已過期。 批次處理無法繼續。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法啟動，批次或程序的批次訊息因為取得過期的合約。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定具有指定識別碼的批次存在內含協議的協議屬性中，且其開始和結束日期落在協議的開始和結束日期。 也請確定已啟用合約。