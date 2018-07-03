---
title: 單一登入： 事件 10669 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e88a583d-7385-42dd-841e-aa2d2215dd69
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3006b8c861ac56effa504480f2645f22f9deae8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019259"
---
# <a name="single-sign-on-event-10669"></a>單一登入： 事件 10669
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                   企業單一登入                                                                   |
| 產品版本 |                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                   |
|    事件識別碼     |                                                                             10669                                                                             |
|  事件來源   |                                                                            ENTSSO                                                                             |
|    元件    |                                                                              N\A                                                                              |
|  符號名稱  |                                                            SSO_WARN_CHANGE_WINDOWS_PASSWORD_FAILED                                                            |
|  訊息文字   | 無法變更 Windows password.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> Windows 帳戶: %3 %r<br /><br /> 錯誤碼： %4 |

## <a name="explanation"></a>說明  
 這個警告事件表示 SSO 失敗，若要變更 Windows 密碼。 SSO 會呼叫 Win32 函式 NetUserChangePassword 函式來變更與對應相關聯的 Windows 密碼。 如果此函式會失敗這則錯誤訊息會發出。 錯誤的程式碼會傳回從 NetUserChangePassword。 請參閱 MSDN 中進一步了解此函式的文件。 最有可能失敗的原因是舊的密碼不正確，或新的密碼不符合所需的 Windows 密碼原則。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

- 驗證舊密碼。 如果舊的密碼不正確的則可以設定以手動方式在 SSO 資料庫中，使用命令列工具或管理 MMC。  

- 確認新的密碼符合所需的 Windows 密碼原則。 如果密碼不符合 Windows 密碼原則便會再考慮使用密碼篩選。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [密碼同步](../core/password-synchronization2.md)
