---
title: "單一登入： 事件 10560 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8677a807-2973-4753-8816-c93c45697d92
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d630dccdd21aaade843d4aa8fd7026d05fd71da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10560"></a>單一登入： 事件 10560
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10560|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_ERROR_BACKUP_SECRET_FAILED|  
|訊息文字|無法備份主要 secrets.%r<br /><br /> 檔案名稱: %1 %r<br /><br /> 目前的 MSID: %2 %r<br /><br /> 之前的 MSID: %3 %r<br /><br /> 用戶端使用者: %4 %r<br /><br /> 錯誤碼： %5|  
  
## <a name="explanation"></a>說明  
 嘗試備份主要密碼失敗。 使用者嘗試此備份可能已經不正確的權限、 路徑或目錄。  
  
## <a name="user-action"></a>使用者動作  
 如需備份主要密碼資訊，請參閱[管理主要密碼](../core/managing-the-master-secret.md)。