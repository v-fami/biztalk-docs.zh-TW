---
title: "單一登入： 事件 10740 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e8521e7-32af-4a58-8b1a-66ea1d13f1e1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 928760bebef1119207ee6a3021cd39c22ceacad8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10740"></a>單一登入： 事件 10740
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10740|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_INVALID_WINDOWS_USER|  
|訊息文字|Windows 帳戶無效，無法對應用程式 update.%r<br /><br /> 應用程式名稱: %1 %r<br /><br /> Windows 帳戶: %2 %r<br /><br /> 錯誤碼： %3|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示 Windows 帳戶 （事件訊息中指定） 不是有效的應用程式更新。 發生這個問題變更主控件群組應用程式的 Windows 帳戶。 主機群組應用程式適用於單一登入外部系統的 Windows 系統。 它們可以將外部使用者的一組對應的單一 Windows 帳戶。 應用程式的應用程式使用者欄位中定義它們對應的 Windows 帳戶。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  
  
-   請檢查您的 Windows 帳戶已使用無效。  
  
-   重新建立具有正確的 Windows 帳戶屬性的 Windows 帳戶。  
  
 如需詳細資訊，請參閱下列資源：  
  
-   [密碼同步處理](../core/password-synchronization2.md)