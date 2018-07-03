---
title: 單一登入： 事件 10543 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46b1ffda-a6c1-408c-acb4-074183d697bc
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf5c026384bf463f6ee0a33045dd1e7b1fca4188
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998441"
---
# <a name="single-sign-on-event-10543"></a>單一登入： 事件 10543
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                               企業單一登入                                                                |
| 產品版本 |                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                               |
|    事件識別碼     |                                                                         10543                                                                          |
|  事件來源   |                                                                         ENTSSO                                                                         |
|    元件    |                                                                           CO                                                                           |
|  符號名稱  |                                                           SSO_WARN_ORIGINAL_TICKET_VALIDATED                                                           |
|  訊息文字   | 核發此票證時需要驗證。 即無法兌換此應用程式不含 validated.%r<br /><br /> 應用程式名稱： %1 |

## <a name="explanation"></a>說明  
 這個警告事件表示應用程式票證核發需要驗證。 不驗證就無法贖回票證。 驗證票證位於每個分支機構應用程式為基礎。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

- 如果您使用企業單一登入，請確定您的訊息會流經只能透過受信任的主機。 這會減少訊息中的資料遭竄改的風險。  

- 如果您的案例允許，請關閉此應用程式的驗證。 驗證是可以在系統或只是此特定應用程式關閉的管理選項。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [SSO 票證](../core/sso-tickets.md)  

- [如何列出分支機構應用程式屬性](../core/how-to-list-the-properties-of-an-affiliate-application.md)  

- [如何更新分支機構應用程式屬性](../core/how-to-update-the-properties-of-an-affiliate-application.md)
