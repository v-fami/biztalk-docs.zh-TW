---
title: 單一登入： 事件 10678 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af92ce1-fdac-432f-be6b-cf8958aee776
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: daa6639e361abf364e012ec9a4f19f049bbcd08f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270046"
---
# <a name="single-sign-on-event-10678"></a>單一登入： 事件 10678
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10678|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_PASSWORD_MISMATCH|  
|訊息文字|外部密碼變更。 配接器所提供的舊密碼不符合現有的密碼和外部 account.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 外部帳戶： %4|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示配接器所提供的舊密碼不符合現有外部帳戶的密碼。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列：  
  
-   判斷哪些應用程式已指派給此配接器 （在事件記錄檔訊息中的名稱），然後使用 SSO 管理工具來設定這個外部帳戶的外部認證。 您必須在所有這些應用程式設定 （適用於指定的帳戶） 的外部密碼。  
  
## <a name="more-info"></a>其他資訊
  
-   [密碼同步處理](../core/password-synchronization2.md)  
  
-   **密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]