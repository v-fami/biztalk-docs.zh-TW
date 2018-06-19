---
title: 單一登入： 事件 10527 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 40995ad8-9f74-4e96-863d-427e23025ba1
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf1785361ad343b3da4c7dc07b6a73a362fa14d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270198"
---
# <a name="single-sign-on-event-10527"></a>單一登入： 事件 10527
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10527|  
|事件來源|ENTSSO|  
|元件|0|  
|符號名稱|SSO_ERROR_GET_SECRET_FAILED|  
|訊息文字|要求取得主要密碼 failed.%r<br /><br /> 密碼數目: %1 %r<br /><br /> 用戶端使用者: %2 %r<br /><br /> 用戶端電腦: %3 %r<br /><br /> 追蹤識別碼: %4 %r<br /><br /> 錯誤碼： %5|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示取得主要密碼的要求已失敗。 在這些情況下應該會有相關的郵件應用程式事件記錄檔中。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   請檢查應用程式事件記錄檔，取得相關聯的事件或錯誤訊息。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [如何產生主要密碼](../core/how-to-generate-the-master-secret.md)  
  
-   [管理主要密碼](../core/managing-the-master-secret.md)