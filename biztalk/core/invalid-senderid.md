---
title: 無效的 SenderId |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be8055ab-8aba-49ac-ad33-fb33d4ff3e8b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7517adcd214f789c8af37d4abce2478e6da20507
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976535"
---
# <a name="invalid-senderid"></a>無效的 SenderId
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                            X12Ta1InvalidSenderIdDescription                            |
|  訊息文字   |                                    無效的 SenderId                                    |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 ISA06 欄位中的寄件者識別碼或 [UNB2.1] 欄位中的傳送者識別不符合的資料型別和數字的數目建立服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema)。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定 ISA06 欄位是 X12_AN 資料類型，而且是 15 個字元長度 （不論有無結尾的空格） 或 [UNB2.1] 欄位是 EDIFACT_AN 資料類型，並介於 1 到 35 個字元。 重新傳送交換。