---
title: 單一登入： 事件 11035 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d551083c-a897-4a76-a40c-2254d3a3e52e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 194d3069f0b74022e6b16a28de1c7f81ae3030f1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001719"
---
# <a name="single-sign-on-event-11035"></a>單一登入： 事件 11035
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                               企業單一登入                                                                                                                                                |
| 產品版本 |                                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                               |
|    事件識別碼     |                                                                                                                                                         11035                                                                                                                                                          |
|  事件來源   |                                                                                                                                                         ENTSSO                                                                                                                                                         |
|    元件    |                                                                                                                                                          不適用                                                                                                                                                           |
|  符號名稱  |                                                                                                                                           SSO_INFO_PS_WIN_CHANGE_NO_ADAPTER                                                                                                                                            |
|  訊息文字   | Windows 密碼變更。 已偵測到此 Windows 帳戶的對應，但忽略，因為此 application.%r 未設定密碼同步處理<br /><br /> 追蹤識別碼: %1 %r<br /><br /> Windows 帳戶: %2 %r<br /><br /> 應用程式: %3 %r<br /><br /> 外部帳戶: %4 %r<br /><br /> 用戶端使用者： %5 |
  
## <a name="explanation"></a>說明  
 已偵測到此 Windows 帳戶的對應，但忽略，因為未針對此應用程式設定密碼同步處理。  
  
## <a name="user-action"></a>使用者動作  
 如需設定密碼同步處理資訊，請參閱[密碼同步化](../core/password-synchronization2.md)。