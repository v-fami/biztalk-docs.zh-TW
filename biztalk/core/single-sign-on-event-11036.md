---
title: 單一登入： 事件 11036 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2dad0427-83dd-42ac-b0bc-d113abdc8e89
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f19a3ff1d35d3c2de04ec9c3846de94d7a2657a7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013911"
---
# <a name="single-sign-on-event-11036"></a>單一登入： 事件 11036
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                                                企業單一登入                                                                                                                                                                |
| 產品版本 |                                                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                |
|    事件識別碼     |                                                                                                                                                                          11036                                                                                                                                                                          |
|  事件來源   |                                                                                                                                                                         ENTSSO                                                                                                                                                                          |
|    元件    |                                                                                                                                                                           不適用                                                                                                                                                                           |
|  符號名稱  |                                                                                                                                                         SSO_INFO_PS_WIN_CHANGE_ADAPTER_NO_SYNC                                                                                                                                                          |
|  訊息文字   | Windows 密碼變更。 已偵測到此 Windows 帳戶的對應，但忽略，因為此應用程式設定的配接器不支援對外部 systems.%r 的密碼同步處理<br /><br /> 追蹤識別碼: %1 %r<br /><br /> Windows 帳戶: %2 %r<br /><br /> 應用程式: %3 %r<br /><br /> 配接器: %4 %r<br /><br /> 用戶端使用者： %5 |
  
## <a name="explanation"></a>說明  
 已偵測到此 Windows 帳戶的對應，但忽略，因為此應用程式設定的配接器不支援密碼同步處理到外部系統。  
  
## <a name="user-action"></a>使用者動作  
 請檢查您的配接器組態。  
  
 如需有關密碼同步處理，請參閱[密碼同步化](../core/password-synchronization2.md)。