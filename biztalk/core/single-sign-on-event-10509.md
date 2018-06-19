---
title: 單一登入： 事件 10509 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f906823f-db3f-45fc-bf61-cbe6a9566bd7
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4d61cbb7af195aa88c36b64149366334c835b80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270350"
---
# <a name="single-sign-on-event-10509"></a>單一登入： 事件 10509
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10509|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_INFO_SERVICE_REMOVE_FAILED|  
|訊息文字|無法移除 SSO service.%r<br /><br /> 錯誤碼： %1|  
  
## <a name="explanation"></a>說明  
 此事件表示 ENTSSO 服務無法解除安裝。 只可以在手動解除安裝的企業單一登入期間會發生此事件。  
  
## <a name="user-action"></a>使用者動作  
 若要解決此事件，執行下列作業：  
  
-   請檢查 ENTSSO 或其他服務的相關錯誤的應用程式和系統事件記錄檔。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [安裝 SSO](../core/installing-sso.md)  
  
-   [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)