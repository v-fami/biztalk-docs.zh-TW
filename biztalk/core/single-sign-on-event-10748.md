---
title: "單一登入： 事件 10748 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b4b18ea-6565-4c0b-89f8-30a8c67601ba
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d83f0bfec0137e0788b55ca6aa5857f3dcfcc50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10748"></a>單一登入： 事件 10748
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10748|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_PS_ADAPTER_NOT_RUNNING|  
|訊息文字|無法連絡目的地配接器。<br /><br /> 它可能無法執行或 initialized.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> SSO 伺服器名稱: %3 %r<br /><br /> 錯誤碼： %4|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示密碼同步處理無法連絡指定的密碼同步配接器。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  
  
-   請檢查外部介面卡。  
  
-   您可以使用 MMC 嵌入式管理單元或命令列工具來啟用配接器。  
  
-   請檢查系統和應用程式事件日誌中的相關錯誤。  
  
 如需詳細資訊，請參閱下列資源：  
  
-   [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)