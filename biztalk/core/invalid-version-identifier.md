---
title: 無效的版本識別碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 504b0b16-7d23-45ef-ae2a-ce1962b83f34
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de725a51ba89312c7cb394e249c1ef40353f256b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022852"
---
# <a name="invalid-version-identifier"></a>無效的版本識別碼
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                       X12Ta1InvalidVersionIdentifierDescription                        |
|  訊息文字   |                               無效的版本識別碼                               |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中的版本識別項 (GS08 欄位中的 X12 交換 或 EDIFACT 交換中的 UNG7 欄位) 不提供支援符合的資料類型和服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立的數字數目。 如果是 X12_AN 資料型別，而且介於 1 到 12 個數字之間，必須是 GS08 欄位。 UNG7.1 中的版本必須是 EDIFACT_AN 資料型別，而且介於 1 到 3 個數字之間。 發行的 UNG7.2 必須 EDIFACT_AN 資料型別，而且介於 1 到 3 個數字之間。 關聯指定代碼在 UNG7.3 必須 EDIFACT_AN 資料型別，而且 1 到 6 位數字之間。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定在 GS08 或 UNG7 版本符合的資料類型和服務結構描述所指定的數字的數目，然後重新傳送交換。