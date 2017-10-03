---
title: "單一登入： 事件 10526 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f72d466-8b63-453c-b608-f9d64f635f65
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69a78b337cfdf90ea35367bd8fb20569e56717b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10526"></a>單一登入： 事件 10526
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10526|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_GENERATE_SECRET_FAILED|  
|訊息文字|無法產生新的主要密碼。%r<br /><br /> 用戶端使用者: %1 %r<br /><br /> 用戶端電腦：%2%r<br /><br /> 追蹤識別碼: %3 %r<br /><br /> 錯誤碼： %4|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示，產生新的主要密碼的使用者嘗試已經失敗。 這可能是因為權限 （您必須是 SSO 系統管理員，以產生主要密碼） 的問題，或可能有問題的主要密碼寫入備份檔案。 在這些情況下應該會有相關的郵件應用程式事件記錄檔中。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  
  
-   請檢查應用程式事件記錄檔，取得相關聯的事件或錯誤訊息。  
  
-   檢查您有適當的 SSO 系統管理員權限。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [如何產生主要密碼](../core/how-to-generate-the-master-secret.md)  
  
-   [管理主要密碼](../core/managing-the-master-secret.md)