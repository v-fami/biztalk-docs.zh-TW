---
title: 用來解密訊息的憑證已被撤銷 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01767cb2-b16e-4b4b-ac4d-cd79b6c8860a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cd9404f13f737b4cb82317193344e006979d333
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277910"
---
# <a name="the-certificate-used-to-decrypt-a-message-has-been-revoked"></a>用來解密訊息的憑證已被撤銷。
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|DecryptionCertificateHasBeenRevokedError|  
|訊息文字|用於解密訊息的憑證已遭到撤銷。 憑證指紋: {0}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送訊息因為用來將訊息解密憑證已遭到撤銷。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
-   建立新的憑證來取代已撤銷的憑證。 將憑證新增至目前的使用者/個人憑證存放區，然後將憑證的公開金鑰傳送給傳送 AS2 訊息。  
  
-   停用的撤銷清單檢查藉由開啟 BizTalk Server 管理主控台，開啟 AS2 屬性 對話方塊的合作對象解析外寄訊息，按一下 一般 節點，然後清除 檢查憑證撤銷清單屬性。