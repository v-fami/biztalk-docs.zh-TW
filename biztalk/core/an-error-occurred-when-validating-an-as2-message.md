---
title: 驗證 AS2 訊息時發生錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0cf97c63-2bff-4474-9cd8-f68634493dcc
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ac51c94b1a414a7cef5d7777eb4dcd08845e5d2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996343"
---
# <a name="an-error-occurred-when-validating-an-as2-message"></a>驗證 AS2 訊息時發生錯誤
## <a name="details"></a>詳細資料  

|                 |                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                   |
| 產品版本 |                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                               |
|    事件識別碼     |                                                           -                                                           |
|  事件來源   |                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                 |
|    元件    |                                                      AS2 引擎                                                       |
|  符號名稱  |                                                           -                                                           |
|  訊息文字   | 驗證 AS2 訊息時發生錯誤。 請確定所用的憑證尚未逾時或遭到撤銷。 |

## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，AS2 接收管線或 AS2 傳送管線無法驗證 AS2 訊息。 當用於簽章驗證程序的憑證無效、未存放在適當的位置，或和用於簽署程序的憑證不符時，此錯誤便可能會發生。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  

- 確認 AS2 訊息中的簽章包裝函式是有效的。 如果是無效的，請判定編碼器無法正確簽署訊息的原因。  

- 確認用於簽署程序的私密金鑰和用於簽章驗證程序的公開金鑰是相符的。  

- 確認用於簽署和簽章驗證之憑證的 [金鑰使用方式] 屬性已設為 [資料編密]。  

- 請確認沒有中斷的鏈結的中繼憑證授權單位。 如果沒有，刪除舊的憑證，以及建立並使用新的憑證。  

- 請確認該憑證尚未逾時藉由檢查到期日的憑證存放區 （使用 MMC 憑證嵌入式管理單元）.  

- 請確認憑證藉由檢查憑證撤銷清單中未被撤銷。 (您可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中勾選 [一般 AS2] 屬性的 [檢查憑證撤銷清單] 屬性，讓 BizTalk Server 自動檢查此項目)。  

- 確認用於簽章驗證的憑證儲存在本機電腦/其他人存放區，每個 BizTalk 伺服器裝載 MIME/SMIME 解碼器管線的每個主控件執行個體服務帳戶。
