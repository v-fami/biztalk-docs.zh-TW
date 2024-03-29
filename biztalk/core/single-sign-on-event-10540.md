---
title: 單一登入： 事件 10540 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce91ff30-3d68-4c5f-a955-5c426e94d917
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1bcd7cc64a79634aa7868791d7e74e92cd1c4a3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990943"
---
# <a name="single-sign-on-event-10540"></a>單一登入： 事件 10540
## <a name="details"></a>詳細資料  

|                 |                                                                                  |
|-----------------|----------------------------------------------------------------------------------|
|  產品名稱   |                            企業單一登入                             |
| 產品版本 |            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]            |
|    事件識別碼     |                                      10540                                       |
|  事件來源   |                                      ENTSSO                                      |
|    元件    |                                        CO                                        |
|  符號名稱  |                         SSO_WARN_APP_TICKETS_NOT_ALLOWED                         |
|  訊息文字   | 未啟用此 application.%r 的票證<br /><br /> 應用程式名稱： %1 |

## <a name="explanation"></a>說明  
 這個警告事件指出 「 票證 」 功能，尚未啟用此應用程式。 使用 SSO 票證是每個 SSO 應用程式的選擇性功能。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

- 請連絡您的應用程式系統管理員啟用此 SSO 應用程式的票證。 這可以使用 SSO 管理工具 （GUI 或命令列）。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [SSO 票證](../core/sso-tickets.md)  

- [如何列出分支機構應用程式屬性](../core/how-to-list-the-properties-of-an-affiliate-application.md)  

- [如何更新分支機構應用程式屬性](../core/how-to-update-the-properties-of-an-affiliate-application.md)
