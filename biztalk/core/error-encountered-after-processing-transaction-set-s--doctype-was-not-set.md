---
title: 處理交易集因為未設定 DocType 後所發生的錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a323658c-77d8-4059-aa15-d88c08e5450d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df010d497f61a14644c46f8b7f5cdfa183340615
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003375"
---
# <a name="error-encountered-after-processing-transaction-sets-because-doctype-was-not-set"></a>處理交易集因為未設定 DocType 後發生錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                     DocTypeNotSet                                      |
|  訊息文字   |     在處理之後所發生的錯誤{0}交易集。 未設定 DocType     |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送交易集，因為 ST01 (x12 交換) 或 UNH2.1 （適用於 EDIFACT 交換） 未設定為交易集。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認的交易集發生錯誤的 ST01 或 UNH1 區段，會設定為有效的文件類型。