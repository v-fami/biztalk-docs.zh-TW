---
title: 組態錯誤。 訊息簽章不&#39;t 符合此合作對象設定簽章 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cea0016-12e8-4ee8-ac44-11024b5e74ef
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 729fff283d8fa63ce9e933a0dc69a4a8f2200874
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980455"
---
# <a name="configuration-error-the-message-signature-doesn39t-match-the-signature-configured-for-this-party"></a>組態錯誤。 訊息簽章不&#39;t 符合此合作對象設定簽章
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                             |
| 產品版本 |                                                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                         |
|    事件識別碼     |                                                                                                     -                                                                                                      |
|  事件來源   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                           |
|    元件    |                                                                                                 AS2 引擎                                                                                                 |
|  符號名稱  |                                                                                                     -                                                                                                      |
|  訊息文字   | 組態錯誤。 訊息簽章不符合此合作對象的設定簽章。 請連絡傳送方夥伴，並確認所用的憑證。 AS2-從:"{0}"AS2-到: 「{1}"MessageID:"{2}」 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，AS2 接收管線無法驗證簽章，執行 MIME 處理時。 這會導致從使用不同的憑證來處理收到的訊息，比用來簽署訊息的寄件者。 如果 BizTalk Server 會使用錯誤的合作對象設定來驗證內送 AS2 訊息的簽章，也可能會發生。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  
  
-   請確定正確的合作對象由內送 AS2 訊息的合作對象解析程序。 這樣做的驗證會解析正確的合作對象，當 BizTalk Server 會嘗試比對 AS2-From 標頭中的內送訊息和合作對象屬性 對話方塊的 一般 頁面中的 別名 清單中的 EDIINT-AS2 From 值。 如果這麼做無法解決合作對象，請確認正確的合作對象已解決，當 BizTalk Server 會嘗試比對 AS2-From 內容屬性設定為內送訊息和合作對象的名稱。  
  
-   請確定憑證中 [憑證] 頁面的 [合作對象屬性] 對話方塊中，定義並儲存在本機電腦 \ 其他人 」 存放區，對應至用來簽署訊息的憑證。