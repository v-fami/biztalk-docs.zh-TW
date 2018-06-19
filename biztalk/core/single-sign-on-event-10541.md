---
title: 單一登入： 事件 10541 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e206158-5652-453c-91ac-9a75ab02809a
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 201a43682898f312687f3d5d453f3b050bc75d48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270102"
---
# <a name="single-sign-on-event-10541"></a>單一登入： 事件 10541
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10541|  
|事件來源|ENTSSO|  
|元件|CO|  
|符號名稱|SSO_WARN_SSO_TICKETS_VALIDATED|  
|訊息文字|不驗證就無法贖回票證。|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示無法在不驗證就贖回 SSO 票證。 就會贖回 SSO 票證時也可以驗證或未驗證。 驗證會提高安全性，藉由比較發出票證的 BizTalk 訊息中的使用者名稱的使用者名稱。 如果名稱不是相同驗證失敗。 BizTalk 訊息流程透過未受信任的主機，則會將 BizTalk 訊息中的使用者名稱變更為未受信任的主機。 驗證可確保 BizTalk 訊息的受信任的主機只行經。 這則訊息特別表示在 SSO 系統層級 （因為 SSO 系統 選項設定），需要驗證，但沒有驗證資訊由呼叫端提供的。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  
  
-   如果您使用 BizTalk Server，請確定您的訊息流動只能透過受信任的主機。 這會降低訊息中的資料遭到竄改的風險。  
  
-   如果您的情況允許，關閉此應用程式的驗證。 驗證是可以在系統或只針對此特定應用程式關閉的管理選項。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [SSO 票證](../core/sso-tickets.md)  
  
-   [如何列出分支機構應用程式的屬性](../core/how-to-list-the-properties-of-an-affiliate-application.md)  
  
-   [如何更新分支機構應用程式的內容](../core/how-to-update-the-properties-of-an-affiliate-application.md)