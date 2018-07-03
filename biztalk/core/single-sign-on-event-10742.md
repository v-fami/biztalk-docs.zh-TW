---
title: 單一登入： 事件 10742 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba62f878-ed12-421f-81ea-9285b2624fe9
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43595ad7a6817bd63e200a80ea90e23bd0245ceb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012991"
---
# <a name="single-sign-on-event-10742"></a>單一登入： 事件 10742
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                         企業單一登入                                                                                                                                          |
| 產品版本 |                                                                                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                         |
|    事件識別碼     |                                                                                                                                                   10742                                                                                                                                                    |
|  事件來源   |                                                                                                                                                   ENTSSO                                                                                                                                                   |
|    元件    |                                                                                                                                                    N\A                                                                                                                                                     |
|  符號名稱  |                                                                                                                                         SSO_WARN_NO_UPDATE_ADAPTER                                                                                                                                         |
|  訊息文字   | 用戶端使用者必須是 SSO 系統管理員帳戶或應用程式系統管理員帳戶的成員，才能更新 adapter.%r<br /><br /> 用戶端使用者: %1 %r<br /><br /> SSO 系統管理員: %2 %r<br /><br /> 應用程式系統管理員: %3 %r<br /><br /> 配接器: %4 %r<br /><br /> 錯誤碼： %5 |

## <a name="explanation"></a>說明  
 這個警告事件表示，嘗試更新指定的配接器，但因為使用的使用者帳戶不是 SSO 系統管理員帳戶或應用程式系統管理員帳戶的成員，所以無法完成。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

- 將使用者帳戶新增至 SSO 系統管理員帳戶或應用程式系統管理員帳戶。  

- 重試更新。  

  如需詳細資訊，請參閱下列資源：  

- [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)
