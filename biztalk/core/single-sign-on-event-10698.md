---
title: 單一登入： 事件 10698 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f467934d-fef5-4962-a341-18f272d84108
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aacd272480ddb58de38960ae8dc1a744815ced64
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966471"
---
# <a name="single-sign-on-event-10698"></a>單一登入： 事件 10698
## <a name="details"></a>詳細資料  

|                 |                                                                      |
|-----------------|----------------------------------------------------------------------|
|  產品名稱   |                      企業單一登入                       |
| 產品版本 |      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]      |
|    事件識別碼     |                                10698                                 |
|  事件來源   |                                ENTSSO                                |
|    元件    |                                 N\A                                  |
|  符號名稱  |                     SSO_INFO_REPLAY_FILE_DELETED                     |
|  訊息文字   | 重新執行或進度檔案已刪除。%r<br /><br /> 檔案名稱： %1 |

## <a name="explanation"></a>說明  
 這個資訊事件表示 SSO 已刪除重新執行和/或進度檔案。  

 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示遠透過 SSO 無法閱讀與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。  

## <a name="user-action"></a>使用者動作  

- 使用者不必採取任何動作。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何設定密碼同步處理](../core/how-to-configure-password-synchronization.md)  

- [密碼同步](../core/password-synchronization2.md)
