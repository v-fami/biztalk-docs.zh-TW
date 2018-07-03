---
title: 單一登入： 事件 10685 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 810b37b5-51c4-4201-8d88-0bf7d9e16dae
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b276432363f6073627aaa9033c2b78b730ccda1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992516"
---
# <a name="single-sign-on-event-10685"></a>單一登入： 事件 10685
## <a name="details"></a>詳細資料  

|                 |                                                                                                      |
|-----------------|------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                      企業單一登入                                       |
| 產品版本 |                      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                      |
|    事件識別碼     |                                                10685                                                 |
|  事件來源   |                                                ENTSSO                                                |
|    元件    |                                                 N\A                                                  |
|  符號名稱  |                                     SSO_WARN_REPLAY_CANNOT_OPEN                                      |
|  訊息文字   | 無法開啟重新執行或進度 file.%r<br /><br /> 檔案名稱: %1 %r<br /><br /> 錯誤碼： %2 |

## <a name="explanation"></a>說明  
 這個警告事件表示 SSO 已重新建立連絡人與 SSO 資料庫中，但無法開啟重新執行或進度檔案。 如果 SSO 無法開啟重新執行檔案，它將繼續進行下一步 重新執行檔案。  

 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示遠透過 SSO 已能夠讀取與 SSO 資料庫重新執行檔案中案例的連絡人會中斷一次中途播放背面重新執行檔案。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告事件，執行下列作業：  

- 您應該檢查相關聯的事件，以判斷為什麼 SSO 無法連絡 SSO 資料庫的系統和應用程式事件記錄檔。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
