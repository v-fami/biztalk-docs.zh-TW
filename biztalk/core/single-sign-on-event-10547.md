---
title: 單一登入： 事件 10547 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be25cdc9-d6c1-488d-9ead-877a2454c3d1
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1af15d6a6259142d243738ab83cabe3e0c63e9c6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010943"
---
# <a name="single-sign-on-event-10547"></a>單一登入： 事件 10547
## <a name="details"></a>詳細資料  

|                 |                                                                           |
|-----------------|---------------------------------------------------------------------------|
|  產品名稱   |                         企業單一登入                         |
| 產品版本 |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]         |
|    事件識別碼     |                                   10547                                   |
|  事件來源   |                                  ENTSSO                                   |
|    元件    |                                    CO                                     |
|  符號名稱  |                          SSO_WARN_UPDATE_FAILED                           |
|  訊息文字   | 無法重新加密期間，更新 SSO 資料庫中的認證 |

## <a name="explanation"></a>說明  
 這個警告事件表示，仍無法使用新的加密結果更新的認證。 變更主要密碼時，藉由產生新的祕密或還原舊的密碼，來解密使用舊的密碼加密的所有密碼和重新加密以新的密碼在 SSO 資料庫上執行重新加密。 如果認證已刪除，正在重新加密的過程中所顯示的一樣，會發生此事件。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

- 等候另一個在短暫的延遲; 之後所發生的重新加密如果，不會自動發生，請重新啟動 SSO 服務，其會觸發新的重新加密，如果有必要。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [了解 SSO](../core/understanding-sso.md)
