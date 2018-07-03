---
title: 單一登入： 事件 11026 |Microsoft Docs
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
ms.openlocfilehash: 452ccc24174a1e32a133c0ccc6c7a0b5f09c530f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013487"
---
# <a name="single-sign-on-event-11026"></a>單一登入： 事件 11026
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                企業單一登入                                                                                                                                |
| 產品版本 |                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                |
|    事件識別碼     |                                                                                                                                          11026                                                                                                                                          |
|  事件來源   |                                                                                                                                         ENTSSO                                                                                                                                          |
|    元件    |                                                                                                                                           不適用                                                                                                                                           |
|  符號名稱  |                                                                                                                             SSO_WARN_EXISTING_GROUP_MAPPING                                                                                                                             |
|  訊息文字   | 無法建立新的群組對應，因為有衝突，以使用現有的對應。 請刪除現有的對應，然後重試 again.%r<br /><br /> 現有的對應: %1 %r<br /><br /> 新的對應: %2 %r<br /><br /> 外部帳戶: %3 %r<br /><br /> 應用程式名稱： %4 |
  
## <a name="explanation"></a>說明  
 最可能的原因是您的系統使用企業單一登入，和舊的群組應用程式的舊版本。  
  
## <a name="user-action"></a>使用者動作  
 刪除並重建為建議警告中的對應。 如果失敗，您可能需要升級至較新版本的企業單一登入。