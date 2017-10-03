---
title: "單一登入介面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2e3c2d3-a7e9-4a45-965d-bfe4bf200c34
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee479a29a424228b31bc3fcd5752f8da7cc3ce28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-interface"></a>單一登入介面

## <a name="interfaces"></a>介面
下表描述組成單一登入介面的 COM 和.NET Framework 介面。  
  
|.NET|COM|Description|  
|----------|---------|-----------------|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOAdmin|ISSOAdmin 介面 (COM)|建立、更新和刪除 SSO 應用程式。 也會執行其他的管理功能。|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOConfigStore|ISSOConfigStore 介面 (COM)|取得和設定 SSO 組態存放區中的資訊。|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup1|ISSOLookup1 介面 (COM)|可讓您查詢目前使用者在指定應用程式上的外部認證。|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup2|ISSOLookup2 介面 (COM)|如上所示，還可讓您查詢指定的外部使用者的 Windows 認證。|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapper|ISSOMapper 介面 (COM)|可讓您設定目前使用者在指定應用程式上的外部認證。|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapping|ISSOMapping 介面 (COM)|建立和維護使用者與附屬應用程式之間的對應。|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOTicket|ISSOTicket 介面 (COM)|建立包含適當的安全性資訊的票證。 然後會傳送此票證與來自應用程式的適當訊息。|  


## <a name="password-sync-helper"></a>密碼同步協助程式  
 此外，Host Integration Server 還支援「密碼同步協助程式」(PS 協助程式) 元件。 在設計密碼同步元件時可以使用「PS 協助程式」。 下表描述「PS 協助程式」所公開的 COM 和 .NET Framework 介面。  
  
|.NET|COM|Description|  
|----------|---------|-----------------|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOPSWrapper|ISSONotification 介面 (COM)|處理非 Windows 作業系統的密碼變更。|  
||SExternalAccount 結構 (COM)|描述外部帳戶。|  
||SPasswordChange 結構 (COM)|描述密碼變更。|  
||SPasswordChangeComplete 結構 (COM)|描述密碼變更完成。|  
||SStatus 結構 (COM)|描述錯誤或事件。|  
||SAdapterInGroup 結構 (COM)|描述指定群組中的配接器。|  
||SAdapter 結構 (COM)|描述特定的配接器。|

## <a name="see-also"></a>另請參閱
請參閱 SSO COM 物件[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 