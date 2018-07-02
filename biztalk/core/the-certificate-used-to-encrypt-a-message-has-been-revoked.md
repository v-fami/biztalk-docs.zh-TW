---
title: 用來加密訊息的憑證已被撤銷 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76c90690-002a-43bc-85f2-8aa5e7511ffa
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4476249160f71e20012ff92f749042775132d5e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971431"
---
# <a name="the-certificate-used-to-encrypt-a-message-has-been-revoked"></a>用來加密訊息的憑證已遭到撤銷
## <a name="details"></a>詳細資料  
  
|                 |                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]    |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                |
|    事件識別碼     |                                            -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI  |
|    元件    |                                       AS2 引擎                                        |
|  符號名稱  |                        EncryptionCertificateHasBeenRevokedError                         |
|  訊息文字   | 用於加密訊息的憑證已遭到撤銷。 憑證指紋： {0} |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄訊息因為識別做為加密憑證的憑證已遭到撤銷。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
-   有訊息的接收者，建立新的憑證，並將公開金鑰傳送給您。 將憑證新增至本機電腦 \ 其他人憑證存放區，並再做為加密憑證的 [傳送埠屬性] 對話方塊中的 [憑證] 頁面中識別的憑證。  
  
-   停用憑證的撤銷清單檢查，藉由開啟 BizTalk Server 管理主控台，開啟為外寄訊息解析合作對象的 AS2 屬性] 對話方塊中，按一下 [一般] 節點，然後清除 [檢查憑證撤銷清單屬性。