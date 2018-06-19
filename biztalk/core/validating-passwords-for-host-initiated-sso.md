---
title: 驗證密碼的主控件初始化的 SSO |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- passwords, host initiated [SSO]
- host initiated SSO, passwords
ms.assetid: 3cc1d68a-27ac-46ce-ba1e-21139a9df55e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03a33eb83630831863f231ff9594e3082f0faa98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287854"
---
# <a name="validating-passwords-for-host-initiated-sso"></a>驗證密碼的主控件初始化的 SSO
當主控件初始化的 SSO 之分支機構應用程式建立時，依照預設會啟用非 Windows 使用者的密碼驗證。 這表示當應用程式呼叫 SSO 以取得 Windows 使用者 Token 來存取資源時，它們必須提供非 Windows 使用者帳戶與非 Windows 密碼。 若密碼不符合該非 Windows 使用者在 SSO 資料庫中的密碼，就會拒絕存取。 如有必要，可以停用分支機構應用程式的密碼驗證功能。 密碼驗證功能可套用至主控件初始化的 SSO 之個別與主控件群組類型分支機構應用程式。  
  
 個別類型主控件初始化的 SSO 分支機構應用程式的範例 XML 檔案為：  
  
```  
<sso>  
<application name="SAP">  
<description>The SAP application</description>   
<contact>someone@example.com</contact>   
<appuserAccount>domain\AppUserGroupAccount</appuserAccount>   
<appAdminAccount>domain\AppAdminGroupAccount</appAdminAccount>   
<field ordinal="0" label="User Id" masked="no" />   
<field ordinal="1" label="Password" masked="yes" />   
<flags groupApp="no"  configStoreApp="no" allowTickets="no" validateTickets="yes" allowLocalAccounts="no" timeoutTickets="yes" adminAccountSame="no" enableApp="no" />  
</application>  
</sso>  
  
```  
  
 若是主控件初始化的 SSO 之個別應用程式，則 appUserAccount 是包含 Windows 網域帳戶使用者清單的群組帳戶，這些網域帳戶使用者與其對應的非 Windows 帳戶為一對一對應。  
  
 主控件群組類型主控件初始化的 SSO 分支機構應用程式的範例 XML 檔案為：  
  
```  
<sso>  
<application name="SAP">  
<description>The SAP application</description>   
<contact>someone@example.com</contact>   
<appuserAccount>domain\AppUserAccount</appuserAccount>   
<appAdminAccount>domain\AppAdminGroupAccount</appAdminAccount>   
<field ordinal="0" label="User Id" masked="no" />   
<field ordinal="1" label="Password" masked="yes" />   
<flags  configStoreApp="no" allowTickets="no" validateTickets="yes" allowLocalAccounts="no" timeoutTickets="yes" adminAccountSame="no" enableApp="no" />  
</application>  
</sso>  
  
```  
  
 在主控件初始化的 SSO 之群組應用程式中，appUserAccount 必須是個別使用者帳戶。 此帳戶也就是所有非 Windows 帳戶所對應至的帳戶。  
  
## <a name="see-also"></a>另請參閱  
 [主控件初始化的 SSO](../core/host-initiated-sso.md)