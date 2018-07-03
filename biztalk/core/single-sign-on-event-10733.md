---
title: 單一登入： 事件 10733 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01520ae4-f692-4697-82ce-53a8a63b5bd9
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd392f2a00d3010039501b99f731f1d9c350cdda
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023484"
---
# <a name="single-sign-on-event-10733"></a>單一登入： 事件 10733
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                             |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                  企業單一登入                                                                  |
| 產品版本 |                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                  |
|    事件識別碼     |                                                                            10733                                                                            |
|  事件來源   |                                                                           ENTSSO                                                                            |
|    元件    |                                                                             N\A                                                                             |
|  符號名稱  |                                                              SSO_WARN_PS_SET_WINDOWS_PASSWORD                                                               |
|  訊息文字   | 無法更新 SSO 資料庫中的 Windows 密碼。%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> Windows 帳戶： %2\\%3 %r<br /><br /> 錯誤碼： %4 |

## <a name="explanation"></a>說明  
 這個警告事件表示「密碼同步」無法更新 SSO 資料庫中指定的 Windows 帳戶密碼。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

- 請檢查系統和應用程式事件日誌中的相關錯誤。  

- 請確認指定帳戶的密碼是有效的 Windows 密碼。  

  如需詳細資訊，請參閱下列資源：  

- [密碼同步](../core/password-synchronization2.md)
