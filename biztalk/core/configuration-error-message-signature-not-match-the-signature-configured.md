---
title: 組態錯誤。 訊息簽章不 &#39; 與此合作對象設定簽章相符的 t |Microsoft 文件
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
ms.openlocfilehash: 23214832300fe6125318ce67083f6bee0a364158
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232486"
---
# <a name="configuration-error-the-message-signature-doesn39t-match-the-signature-configured-for-this-party"></a>組態錯誤。 訊息簽章不 &#39; t 符合此合作對象設定簽章
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|-|  
|訊息文字|組態錯誤。 訊息簽章不符合此合作對象的設定簽章。 請連絡傳送方夥伴，並確認所用的憑證。 AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，AS2 接收管線無法驗證簽章，執行 MIME 處理時。 這可能造成無法處理接收的訊息比用來簽署訊息的寄件者使用不同的憑證。 如果 BizTalk Server 使用之錯誤的合作對象設定來驗證內送 AS2 訊息的簽章，也可能會發生。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  
  
-   請確定正確的合作對象由內送 AS2 訊息的合作對象解析程序。 這樣做會驗證正確的合作對象已解決時 BizTalk Server 會嘗試尋找相符項目之間的 AS2-從內送訊息和合作對象屬性 對話方塊的 一般 頁面中的 別名 清單中的 ediint-as2 From 值中的標頭。 如果不解決合作對象，請確認正確的合作對象已解決時 BizTalk Server 會嘗試尋找相符項目之間的 AS2-從內容屬性設定為內送訊息和合作對象的名稱。  
  
-   請確定憑證的合作對象屬性 對話方塊的 憑證 頁面中定義，並且儲存在本機電腦 \ 其他人 」 存放區，對應至用來簽署訊息的憑證。