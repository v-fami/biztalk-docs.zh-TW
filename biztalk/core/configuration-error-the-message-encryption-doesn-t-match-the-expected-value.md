---
title: "組態錯誤。 訊息加密不 &#39; 符合預期的值 t |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99c37c7d-6654-4004-8345-9d7bfc3659b6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b17460c4dcd6f9d2a8c18e5e7284cd36940d6820
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-error-the-message-encryption-doesn39t-match-the-expected-value"></a>組態錯誤。 訊息加密不 &#39; t 符合預期值
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|AS2DecoderPartyEncryptionConfigurationError|  
|訊息文字|組態錯誤。 訊息加密不符合預期值。 請連絡傳送方夥伴，並確認加密用法。 AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於已在合作對象設定中指定加密，但 AS2 訊息未經過加密，亦或是加密已指定為不啟用，但訊息已經過加密，因此接收管線的 AS2 解碼器元件無法處理 AS2 訊息。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認是否合作對象設定中指定加密或未加密內送 AS2 訊息如果指定加密則為未在設定中啟用合作對象，確定已加密內送 AS2 訊息。 執行下列其中之一：  
  
1.  如果**覆寫輸入的訊息屬性 屬性選取**的合作對象當做 AS2 訊息傳送者 頁面中的 [AS2 屬性] 對話方塊[!INCLUDE[prague](../includes/prague-md.md)]管理主控台中，**訊息應該加密**選取屬性，但是訊息並未加密，請連絡傳送訊息的合作對象並要求他們將訊息加密，，重新傳送它。 您可以清除或**訊息應該加密**屬性，或**覆寫輸入的訊息屬性**屬性。  
  
2.  如果**覆寫輸入的訊息屬性**選取屬性，**訊息應該加密**清除屬性，但訊息經過加密，請連絡傳送訊息的合作對象，要求他們未以加密訊息，並重新傳送它。 您可以選取或**訊息應該加密**屬性。