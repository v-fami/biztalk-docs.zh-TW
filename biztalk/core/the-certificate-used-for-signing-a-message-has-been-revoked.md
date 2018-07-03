---
title: 已撤銷用於簽署訊息的憑證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f822235a-8ad8-4b63-94de-9b7f9361a071
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2e05acaa5a1bca68952072f90364ac3890be9af
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022716"
---
# <a name="the-certificate-used-for-signing-a-message-has-been-revoked"></a>用於簽章訊息的憑證已遭到撤銷
## <a name="details"></a>詳細資料  
  
|                 |                                                                                          |
|-----------------|------------------------------------------------------------------------------------------|
|  產品名稱   |    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]    |
| 產品版本 |                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                |
|    事件識別碼     |                                            -                                             |
|  事件來源   |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI  |
|    元件    |                                        AS2 引擎                                        |
|  符號名稱  |                          SigningCertificateHasBeenRevokedError                           |
|  訊息文字   | 用於簽章訊息的憑證已遭到撤銷。 憑證指紋： {0} |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄訊息因為識別做為簽署憑證的憑證已遭到撤銷。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
-   建立新的憑證，以取代已撤銷的憑證。 將憑證新增至目前的使用者憑證存放區，它識別為在 [憑證] 頁面的 [群組屬性] 對話方塊中，簽章的憑證，然後將憑證的公開金鑰傳送給收件者的 AS2 訊息。  
  
-   停用憑證的撤銷清單檢查，藉由開啟 BizTalk Server 管理主控台，開啟為外寄訊息解析合作對象的 AS2 屬性] 對話方塊中，按一下 [一般] 節點，然後清除 [檢查憑證撤銷清單屬性。