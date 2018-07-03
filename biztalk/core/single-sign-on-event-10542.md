---
title: 單一登入： 事件 10542 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8e12444-b47c-4919-85b6-85c8e33b8342
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be63569d76bf7c0cfb14cb10bda27b6da52a3efc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979375"
---
# <a name="single-sign-on-event-10542"></a>單一登入： 事件 10542
## <a name="details"></a>詳細資料  

|                 |                                                                                                             |
|-----------------|-------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                          企業單一登入                                          |
| 產品版本 |                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                          |
|    事件識別碼     |                                                    10542                                                    |
|  事件來源   |                                                   ENTSSO                                                    |
|    元件    |                                                     CO                                                      |
|  符號名稱  |                                       SSO_WARN_APP_TICKETS_VALIDATED                                        |
|  訊息文字   | 無法為此應用程式贖回票證，而不需要 validated.%r<br /><br /> 應用程式名稱： %1 |

## <a name="explanation"></a>說明  
 這個警告事件表示，應用程式就無法贖回票證而不需經過。 當兌換的票證應用程式是它們可以 validated 或 not validated。 驗證會提高安全性，藉由比較的 BizTalk 訊息中的使用者名稱所發行的使用者名稱。 如果名稱不相同驗證失敗。 BizTalk 訊息流程透過不受信任的主控件，BizTalk 訊息中的使用者名稱會變成不受信任的主機。 驗證可確保 BizTalk 訊息的信任主機僅流經。 系統層級的應用程式 （因為 SSO 系統 選項設定），驗證是必要的但沒有驗證資訊由呼叫端提供，則此訊息表示特別。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

- 如果您使用 BizTalk Server，請確定您的訊息會流經只能透過受信任的主機。 這會減少訊息中的資料遭竄改的風險。  

- 如果您的案例允許，請關閉此應用程式的驗證。 驗證是可以在系統或只是此特定應用程式關閉的管理選項。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [SSO 票證](../core/sso-tickets.md)  

- [如何列出分支機構應用程式屬性](../core/how-to-list-the-properties-of-an-affiliate-application.md)  

- [如何更新分支機構應用程式屬性](../core/how-to-update-the-properties-of-an-affiliate-application.md)
