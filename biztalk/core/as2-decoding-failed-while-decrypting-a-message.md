---
title: 解碼訊息時發生 AS2 解碼失敗 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab6f7ecd-23cf-4f6f-8f63-acc6618dc544
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82a9be7ca6cea6f5ef42795c77b8c73b859b0f17
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001903"
---
# <a name="as2-decoding-failed-while-decrypting-a-message"></a>解碼訊息時發生 AS2 解碼失敗
## <a name="details"></a>詳細資料  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |                    解密訊息時發生 AS2 解碼失敗。                     |

## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線的 AS2 解碼器元件無法解密 AS2 訊息。 如果解密程序中使用的憑證無效，不會儲存在適當的位置，或不符合加密程序中使用的憑證，也可能會發生。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  

- 確認 AS2 訊息中的加密包裝函式有效。 如果沒有的話，判斷為何訊息已編碼的編碼器的不正確。  

- 確認加密程序中使用的公用金鑰和解密程序中使用的私用金鑰相符合。  

- 請確認用來加密和解密憑證的金鑰使用方法屬性設為 資料編密 」。  

- 請確認沒有中斷的鏈結的中繼憑證授權單位。 如果沒有，刪除舊的憑證，以及建立並使用新的憑證。  

- 請確認該憑證尚未逾時藉由檢查到期日的憑證存放區 （使用 MMC 憑證嵌入式管理單元）.  

- 請確認憑證藉由檢查憑證撤銷清單中未被撤銷。 (您可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中勾選 [一般 AS2] 屬性的 [檢查憑證撤銷清單] 屬性，讓 BizTalk Server 自動檢查此項目)。  

- 確認用來解密憑證會儲存在目前使用者 \ 個人存放區，每個 BizTalk 伺服器裝載 MIME/SMIME 解碼器管線的每個主控件執行個體服務帳戶。
