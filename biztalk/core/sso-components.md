---
title: "SSO 元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passwords, synchronizing [SSO]
- SSO, components
- SSO, password synchronization
- SSO, sub-services
ms.assetid: e29e68df-f770-4220-a9f8-cb9323403017
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1111f1a0dfac47412ae28b58f93ddc51e1f562b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sso-components"></a>SSO 元件
企業單一登入 (SSO) 服務的子服務如下：  
  
-   **對應。** 此元件將 Windows 系統中的使用者帳戶對應至後端系統中的使用者帳戶。  
  
-   **查閱。** 此元件會尋查後端系統中 SSO 資料庫的使用者認證。 這是 SSO 執行階段元件。  
  
-   **系統管理。** 此元件管理分支機構應用程式與每個分支機構應用程式的對應。  
  
-   **密碼。** 此元件會產生主要密碼，然後將它分派至系統中的其他 SSO 伺服器。 它只在扮演主要密碼伺服器的單一登入伺服器上才有作用。  
  
-   **密碼同步處理。** 此元件簡化 SSO 資料庫的管理，維持跨使用者目錄的密碼同步。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 伺服器](../core/sso-server.md)   
 [安裝 SSO](../core/installing-sso.md)