---
title: 單一登入： 事件 11031 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ecd24c2-e251-4eb9-b3ca-ec0f095bb23a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f90be8f631bbd9503de3401bc84d27af32aa991a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015079"
---
# <a name="single-sign-on-event-11031"></a>單一登入： 事件 11031
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                企業單一登入                                                                                                                                |
| 產品版本 |                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                |
|    事件識別碼     |                                                                                                                                          11031                                                                                                                                          |
|  事件來源   |                                                                                                                                         ENTSSO                                                                                                                                          |
|    元件    |                                                                                                                                           不適用                                                                                                                                           |
|  符號名稱  |                                                                                                                         SSO_INFO_PS_WIN_CHANGE_INVALID_MAPPING                                                                                                                          |
|  訊息文字   | Windows 密碼變更。 已偵測到此 Windows 帳戶的對應，但忽略，因為它已經 valid.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> Windows 帳戶: %2 %r<br /><br /> 應用程式: %3 %r<br /><br /> 外部帳戶: %4 %r<br /><br /> 用戶端使用者： %5 |
  
## <a name="explanation"></a>說明  
 它可能是 Windows 帳戶存在且有效，但並非應用程式使用者帳戶中。  
  
## <a name="user-action"></a>使用者動作  
 刪除對應，然後再次嘗試重新建立它。