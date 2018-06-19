---
title: 單一登入： 事件 11026 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e39b252d-2ed0-4006-aac2-4dce6504afb2
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecee6d3c3e6dcf01b8489c4041f4aab717eba585
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278278"
---
# <a name="single-sign-on-event-11026"></a>單一登入： 事件 11026
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11026|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_EXISTING_GROUP_MAPPING|  
|訊息文字|無法建立新群組對應，因為與現有的對應相衝突。 請刪除現有的對應，然後再試一次 again.%r<br /><br /> 現有的對應: %1 %r<br /><br /> 新的對應: %2 %r<br /><br /> 外部帳戶: %3 %r<br /><br /> 應用程式名稱： %4|  
  
## <a name="explanation"></a>說明  
 最可能的原因是您的系統使用較舊版本的企業單一登入，與舊群組應用程式。  
  
## <a name="user-action"></a>使用者動作  
 刪除並重新建立警告中建議的對應。 如果這個作業失敗，您可能需要升級至較新版本的企業單一登入。