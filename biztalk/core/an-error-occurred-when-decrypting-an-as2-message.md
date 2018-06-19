---
title: 解密 AS2 訊息時，發生錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bfb1d2a-c79d-4541-8a6d-bab0986f456b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 183933ae48468569cdd89f1d051f4bf961c71e05
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22230182"
---
# <a name="an-error-occurred-when-decrypting-an-as2-message"></a>解密 AS2 訊息時發生錯誤
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|제품 이름|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|제품 버전|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|이벤트 ID|-|  
|이벤트 원본|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|元件|AS2 引擎|  
|符號名稱|-|  
|訊息文字|解密 AS2 訊息時發生錯誤。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線的 AS2 解碼器元件無法解密 AS2 訊息。 如果解密程序中使用的憑證無效，不會儲存在適當的位置，或不符合加密程序中使用的憑證，也可能會發生。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  
  
-   確認 AS2 訊息中的加密包裝函式有效。 如果沒有，判斷為什麼訊息編碼不正確編碼器。  
  
-   確認加密程序中使用的公開金鑰和私密金鑰解密程序中使用相符。  
  
-   確認用來加密和解密憑證的金鑰使用方法屬性設為 「 資料加密 」。  
  
-   請確認沒有中斷的鏈結的中繼憑證授權單位。 如果沒有，請刪除舊的憑證，以及建立並使用新的憑證。  
  
-   請確認該憑證尚未逾時藉由檢查到期日的憑證存放區 （使用 MMC 憑證嵌入式管理單元）.  
  
-   確認憑證藉由檢查憑證撤銷清單中未被撤銷。 (您可以藉由檢查憑證撤銷清單中的屬性中的一般 AS2 屬性自動檢查此 BizTalk Server[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。)  
  
-   確認用來解密憑證會儲存在目前使用者 \ 個人存放區的每個 BizTalk 伺服器裝載 MIME/SMIME 解碼器管線的每個主控件執行個體服務帳戶。