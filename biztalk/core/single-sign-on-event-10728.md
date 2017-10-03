---
title: "單一登入： 事件 10728 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f579189c-c9a5-4d2c-a3d5-f0ba03c5a3ef
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5052d03713808754abf04e8c2ba1590800e6cf9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10728"></a>單一登入： 事件 10728
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10728|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_VERSION|  
|訊息文字|這個版本的 SSO 伺服器與不相容的 SSO 資料庫。 請升級您的主要密碼 server.%r<br /><br /> SQL Server 名稱: %1 %r<br /><br /> SSO 資料庫名稱: %2 %r<br /><br /> SSO 資料庫版本: %3 %r<br /><br /> 必要版本： %4|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示 SSO 伺服器版本會比 （原先建立版） 還新的 SSO 資料庫。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   升級 SSO 主要密碼伺服器以符合此 SSO 伺服器目前的版本。 這將會升級 SSO 資料庫目前的版本。  
  
 如需詳細資訊，請參閱下列資源：  
  
-   [管理主要密碼](../core/managing-the-master-secret.md)