---
title: 組態錯誤。 訊息簽章不&#39;t 符合預期的值。 | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f067351-b6b0-479d-b2ff-81e9f45b5924
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dfe2b610724a346ed31fb0951aa90c660f41d82
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975935"
---
# <a name="configuration-error-the-message-signing-doesn39t-match-the-expected-value"></a>組態錯誤。 訊息簽章不&#39;t 符合預期的值。
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                              |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                              |
| 產品版本 |                                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                          |
|    事件識別碼     |                                                                                      -                                                                                       |
|  事件來源   |                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                            |
|    元件    |                                                                                  AS2 引擎                                                                                  |
|  符號名稱  |                                                                   AS2DecoderPartySigningConfigurationError                                                                   |
|  訊息文字   | 組態錯誤。 訊息簽章不符合預期值。 請連絡傳送方夥伴，並確認簽章用法。 AS2-從:"{0}"AS2-到: 「{1}"MessageID:"{2}」 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線的 AS2 解碼器元件無法處理 AS2 訊息因為簽章指定在合作對象設定中，但未簽署 AS2 訊息，或簽章指定為不啟用，但是，訊息簽章。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認內送的 AS2 訊息已簽署，如果簽章的合作對象設定中指定，或如果簽署，未簽署內送 AS2 訊息指未在合作對象設定中啟用。 執行下列其中之一：  
  
1.  如果**覆寫輸入的訊息屬性**的合作對象當做 AS2 訊息傳送者頁面的 [AS2 屬性] 對話方塊中，在 BizTalk Server 管理主控台中，選取屬性**訊息應該簽署的**選取屬性，但不是簽署訊息，請連絡傳送訊息的合作對象並要求他們簽章訊息，並重新傳送它。 或您可以清除**訊息應該簽署**屬性，或有**覆寫輸入的訊息屬性**屬性。  
  
2.  如果**覆寫輸入的訊息屬性**選取屬性，**訊息應該簽署**清除屬性，但訊息已簽署，請連絡傳送訊息的合作對象並不要求他們簽署訊息，並重新傳送它。 或者您可以選取**訊息應該簽署**屬性。