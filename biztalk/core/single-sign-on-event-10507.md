---
title: 單一登入： 事件 10507 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b02d8dfa-7655-471e-84af-e58d08c3cefd
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6df0c2d898fd715cbbdebf6fe5d11b780f0fa037
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974831"
---
# <a name="single-sign-on-event-10507"></a>單一登入： 事件 10507
## <a name="details"></a>詳細資料  

|                 |                                                                 |
|-----------------|-----------------------------------------------------------------|
|  產品名稱   |                    企業單一登入                    |
| 產品版本 |   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]    |
|    事件識別碼     |                              10504                              |
|  事件來源   |                             ENTSSO                              |
|    元件    |                               N\A                               |
|  符號名稱  |                 SSO_INFO_SERVICE_INSTALL_FAILED                 |
|  訊息文字   | 無法安裝 SSO service.%r<br /><br /> 錯誤碼： %1 |

## <a name="explanation"></a>說明  
 這個事件表示 ENTSSO 服務無法安裝。 手動安裝的企業單一登入期間，只可以發生此事件。  

## <a name="user-action"></a>使用者動作  
 若要解決此事件，執行下列作業：  

- 請檢查 ENTSSO 或其他服務的相關錯誤的應用程式和系統事件記錄檔。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [安裝 SSO](../core/installing-sso.md)  

- [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)
