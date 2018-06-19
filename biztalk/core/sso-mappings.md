---
title: SSO 對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps [SSO]
- maps [SSO], creating
- SSO, maps
ms.assetid: b44f7a0c-595c-49dc-9d75-2e76f29dca88
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98b44a1a9e8be3b275a4dd328c70323d79eb8a54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277238"
---
# <a name="sso-mappings"></a>SSO 對應
當「企業單一登入」(SSO) 系統管理員或 SSO 分支機構系統管理員定義分支機構應用程式時，系統管理員可以將它定義為具有個別對應的應用程式，或具有群組對應的應用程式。  
  
## <a name="individual-mappings"></a>個別對應  
 SSO 個別對應可以讓系統管理員和使用者在 Windows 使用者與其對應的非 Windows 認證之間建立一對一的對應。 使用個別對應時，使用者可以管理自己的對應。 SSO 系統為使用者的 Windows 帳戶與使用者的非 Windows 帳戶維護一對一的關係。  
  
 Windows 一般使用者可以為個別類型應用程式建立與管理他們自己的對應。 相同的分支機構應用程式可以當做 Windows 初始化的 SSO 與主控件初始化的 SSO 類型應用程式。  
  
> [!IMPORTANT]
>  只能為 Windows 網域帳戶建立對應。 無法對應本機帳戶。  
  
> [!NOTE]
>  只有個別使用者可以在使用個別對應時取得其個別帳戶的認證。  
  
## <a name="group-mapping"></a>群組對應  
 SSO 群組對應是由 Windows 群組 (包含多個 Windows 使用者) 對應到分支機構應用程式中的單一帳戶所組成。  
  
 您也可以為「SSO 應用程式使用者」角色指定多個帳戶。 您指定的每個帳戶都可以與一個外部帳戶關聯。 例如，您可以將網域群組對應到 EXTERNALUSER1，並將個別網域帳戶對應到 EXTERNALUSER2。 若相同使用者有多個對應，會使用「SSO 應用程式使用者」順序中的第一個對應。  
  
 只有應用程式系統管理員、SSO 分支機構系統管理員或 SSO 系統管理員可以建立或管理群組對應。  
  
 您無法為 Windows 初始化的 SSO 與主控件初始化的 SSO 指定相同的群組應用程式。  
  
> [!IMPORTANT]
>  只能為 Windows 網域帳戶建立對應。 無法對應本機帳戶。  
  
> [!IMPORTANT]
>  當您使用群組對應時，群組的成員可以取得群組對應的認證資訊。  
  
## <a name="see-also"></a>另請參閱  
 [管理使用者對應](../core/managing-user-mappings.md)   
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)