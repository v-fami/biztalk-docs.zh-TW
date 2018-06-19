---
title: 單一登入： 事件 10652 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae7fe452-bcec-4722-8ec6-78d4fe462a0a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62066b2fbbc47d07fa57f047313ed5ed8cda47d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270910"
---
# <a name="single-sign-on-event-10652"></a>單一登入： 事件 10652
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10652|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_PASSWORD_SYNC_START_FAILED|  
|訊息文字|密碼同步處理服務無法 initialize.%r<br /><br /> 錯誤碼： %1|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示密碼同步處理服務無法啟動因為發生例外狀況。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   請檢查 ENTSSO 或其他服務的相關錯誤的應用程式和系統事件記錄檔。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [密碼同步處理](../core/password-synchronization2.md)