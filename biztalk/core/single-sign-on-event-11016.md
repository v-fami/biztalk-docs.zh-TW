---
title: 單一登入： 事件 11016 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3963b706-168d-438d-a068-637f8a6b7b0c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96f39cba26da1b3e03c7259643c3dcf2704bbdf3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974511"
---
# <a name="single-sign-on-event-11016"></a>單一登入： 事件 11016
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                                                   企業單一登入                                                                                                                                                                    |
| 產品版本 |                                                                                                                                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                   |
|    事件識別碼     |                                                                                                                                                                             11016                                                                                                                                                                              |
|  事件來源   |                                                                                                                                                                             ENTSSO                                                                                                                                                                             |
|    元件    |                                                                                                                                                                              不適用                                                                                                                                                                               |
|  符號名稱  |                                                                                                                                                                RPC 擴充錯誤資訊 %r                                                                                                                                                                |
|  訊息文字   | %1 %r<br /><br /> 錯誤碼： %2<br /><br /> AuthzInitializeContextFromSid 函式失敗，ERROR_ACCESS_DENIED。 這表示執行 SSO server 的服務帳戶沒有足夠的權限，可檢查 Active Directory 中的群組成員資格。 請檢查您的文件，如需有關如何修正此 problem.%r |
  
## <a name="explanation"></a>說明  
 執行 SSO server 的服務帳戶沒有足夠的權限，可檢查 Active Directory 中的群組成員資格。  
  
## <a name="user-action"></a>使用者動作  
 請參閱[SSO 伺服器](../core/sso-server.md)SSO 文件中。