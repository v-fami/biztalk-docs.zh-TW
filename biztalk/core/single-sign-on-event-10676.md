---
title: 單一登入： 事件 10676 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec0e86fb-921d-4505-b458-51b565123ea7
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3805e59e5e8984652ec40af9f93db793d5d3b5fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271654"
---
# <a name="single-sign-on-event-10676"></a>單一登入： 事件 10676
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10676|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_REQUIRE_OLD_PASSWORD|  
|訊息文字|外部密碼變更。 變更外部帳戶的密碼時，配接器必須提供舊 password.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 外部帳戶： %3|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示密碼同步配接器已設定為預期來自外部系統中，舊密碼，但未提供舊密碼。 未設定外部系統 （外部密碼同步配接器） 或是如預期般的工作或 「 密碼同步配接器設定不正確。 這項錯誤也可能會傳回錯誤的程式碼的符號名稱 ENTSSO_E_REQUIRE_OLD_PASSWORD。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   使用者可設定屬性設為使用 SSO 管理工具**驗證舊密碼**密碼同步配接器選項內容 索引標籤上。這個屬性也可以設定時建立配接器透過命令列工具，旗標名稱 (ssops.exe)`verifyOldPassword`和也時建立新的密碼同步配接器使用 「 密碼同步配接器精靈 」。  
  
## <a name="more-info"></a>其他資訊
  
-   [密碼同步處理](../core/password-synchronization2.md)  
  
-   **密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]