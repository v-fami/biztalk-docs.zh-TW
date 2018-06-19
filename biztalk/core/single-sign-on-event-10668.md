---
title: 單一登入： 事件 10668 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0eb3dd4d-04b5-4713-93c1-76af012d6920
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 006855842ea2d789290200d5c5a9692b6e046e8a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271438"
---
# <a name="single-sign-on-event-10668"></a>單一登入： 事件 10668
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10668|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_NO_OLD_WINDOWS_PASSWORD|  
|訊息文字|無法變更 Windows 密碼，因為此帳戶的舊 Windows 密碼無法使用 SSO database.%r 中<br /><br /> 若要設定此 Windows account.%r 的外部認證使用 SSO 管理工具<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> Windows 帳戶： %3|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示密碼同步無法變更 Windows 密碼，因為在 SSO 資料庫中沒有此帳戶的舊 Windows 密碼。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  
  
-   判斷哪些應用程式已指派給此配接器 （在事件記錄檔訊息中的名稱），然後使用 SSO 管理工具來設定此 Windows 帳戶的外部認證。 您必須在所有這些應用程式設定 （適用於指定的 Windows 帳戶） 的外部密碼。  
  
## <a name="more-info"></a>其他資訊
  
-   [密碼同步處理](../core/password-synchronization2.md)  
  
-   **密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]