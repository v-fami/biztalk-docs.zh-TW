---
title: 單一登入： 事件 10539 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a67f5719-da7c-4ae0-a6fe-ff7b653a184d
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7934b3011af2656f413270b4d249ca4f7f96bae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006271"
---
# <a name="single-sign-on-event-10539"></a>單一登入： 事件 10539
## <a name="details"></a>詳細資料  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  產品名稱   |                 企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    事件識別碼     |                           10539                            |
|  事件來源   |                           ENTSSO                           |
|    元件    |                             CO                             |
|  符號名稱  |              SSO_WARN_SSO_TICKETS_NOT_ALLOWED              |
|  訊息文字   |        未啟用 SSO 系統的票證。         |

## <a name="explanation"></a>說明  
 這個警告事件表示未啟用 使用 SSO 票證。 允許使用 SSO 票證是 SSO 系統的選用功能。 SSO 系統上尚未啟用此功能。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  

- 請連絡您的 SSO 系統管理員，才能啟用票證，SSO 系統。 這可以使用 SSO 管理工具 （GUI 或命令列）。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [如何設定 SSO 票證](../core/how-to-configure-the-sso-tickets.md)  

- [使用 SSO](../core/using-sso.md)
