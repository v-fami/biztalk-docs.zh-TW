---
title: 單一登入： 事件 10543 |Microsoft 文件
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
ms.openlocfilehash: e9bf30640bf61f9c88de3fedbb5727be7a715aa8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269998"
---
# <a name="single-sign-on-event-10543"></a>單一登入： 事件 10543
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10543|  
|事件來源|ENTSSO|  
|元件|CO|  
|符號名稱|SSO_WARN_ORIGINAL_TICKET_VALIDATED|  
|訊息文字|票證已發出並在需要驗證。 它無法贖回此應用程式 validated.%r<br /><br /> 應用程式名稱： %1|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示應用程式票證已發出在需要驗證。 不驗證就無法贖回票證。 驗證票證會在每個分支機構應用程式為基礎。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  
  
-   如果您使用企業單一登入，請確定您的訊息流動只能透過受信任的主機。 這會降低訊息中的資料遭到竄改的風險。  
  
-   如果您的情況允許，關閉此應用程式的驗證。 驗證是可以在系統或只針對此特定應用程式關閉的管理選項。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [SSO 票證](../core/sso-tickets.md)  
  
-   [如何列出分支機構應用程式的屬性](../core/how-to-list-the-properties-of-an-affiliate-application.md)  
  
-   [如何更新分支機構應用程式的內容](../core/how-to-update-the-properties-of-an-affiliate-application.md)