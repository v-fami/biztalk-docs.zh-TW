---
title: "單一登入： 事件 10705 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81456bdd-dfd8-4483-aa76-5ec72350cc70
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41db0b3aeba4e3c71da3193af807f881bb4ae586
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10705"></a>單一登入： 事件 10705
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10705|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_PS_NOT_ADAPTER|  
|訊息文字|指定的配接器不是配接器應用程式。 檢查應用程式 type.%r<br /><br /> 配接器： %1|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示指定的配接器不是配接器應用程式。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  
  
-   使用 SSO 管理 MMC 嵌入式管理單元，以滑鼠右鍵按一下指定的配接器，然後按一下 內容來判斷應用程式類型，或使用命令列工具 ssops-清單和 ssops-顯示畫面來判斷應用程式類型。  
  
-   您可以使用 SSO 管理 MMC 嵌入式管理單元或 ssops-addapp，設定配接器應用程式。  
  
 如需詳細資訊，請參閱下列資源：  
  
-   [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)