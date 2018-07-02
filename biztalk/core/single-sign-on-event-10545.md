---
title: 單一登入： 事件 10545 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 268cb7be-b191-4335-a4cc-7c15d879507c
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a21543359b9a0d59aba3071874b6b01210118a5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969127"
---
# <a name="single-sign-on-event-10545"></a>單一登入： 事件 10545
## <a name="details"></a>詳細資料  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  產品名稱   |                 企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    事件識別碼     |                           10545                            |
|  事件來源   |                           ENTSSO                           |
|    元件    |                             CO                             |
|  符號名稱  |             SSO_WARN_ISSUE_TICKETS_NOT_ALLOWED             |
|  訊息文字   |        未啟用 SSO 系統的票證。         |

## <a name="explanation"></a>說明  
 這個警告事件表示 SSO 系統不會啟用票證。 如果在系統層級停用票證，票證目前無法使用的分支機構應用程式層級是。 可以在系統層級中啟用票證，然後在分支機構應用程式層級中將它停用。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

- 啟用 SSO 系統層級的票證。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [SSO 票證](../core/sso-tickets.md)  

- [如何設定 SSO 票證](../core/how-to-configure-the-sso-tickets.md)
