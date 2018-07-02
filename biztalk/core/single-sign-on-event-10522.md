---
title: 單一登入： 事件 10522 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd634a57-01dc-44bd-bcf9-668689db7b77
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f8bb97c8c537cca8b2f9c6e9176409d7da4dd3e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972127"
---
# <a name="single-sign-on-event-10522"></a>單一登入： 事件 10522
## <a name="details"></a>詳細資料  

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
|  產品名稱   |                                   企業單一登入                                   |
| 產品版本 |                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                   |
|    事件識別碼     |                                             10522                                             |
|  事件來源   |                                            ENTSSO                                             |
|    元件    |                                              N\A                                              |
|  符號名稱  |                                      SSO_ERROR_REENCRYPT                                      |
|  訊息文字   | SSO 資料庫重新加密失敗。 將再試一次在 %1 minutes.%r<br /><br /> 錯誤碼： %2 |

## <a name="explanation"></a>說明  
 這個錯誤事件表示 SSO 資料庫重新加密失敗。 當主要密碼伺服器上，啟動 SSO 服務時，第一件事就是檢查是否有任何項目仍然使用先前的主要密碼加密的 SSO 資料庫中。 如果找到任何項目，它會解密該資訊 （使用先前的密碼），並重新使用目前的主要祕密加密。 如果因為任何原因此程序失敗，則會發出此事件訊息。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  

- 請檢查以判斷錯誤的根本原因可能是錯誤碼。 這可能是資料庫或網路問題。 如果它是有間歇性、 的則需要採取任何動作不，因為會在短暫延遲之後，再次嘗試重新加密。 如果此問題不是間歇性發生，請停止 SSO 服務，並嘗試解決此問題。 一旦解決問題，然後重新啟動 SSO 服務重新啟動 SSO 服務將自動執行重新加密。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)  

- [主要密碼伺服器](../core/master-secret-server.md)
