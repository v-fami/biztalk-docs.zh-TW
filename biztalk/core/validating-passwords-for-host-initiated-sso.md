---
title: "驗證密碼的主控件初始化的 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passwords, host initiated [SSO]
- host initiated SSO, passwords
ms.assetid: 3cc1d68a-27ac-46ce-ba1e-21139a9df55e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03a33eb83630831863f231ff9594e3082f0faa98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="validating-passwords-for-host-initiated-sso"></a><span data-ttu-id="75bc5-102">驗證密碼的主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="75bc5-102">Validating Passwords for Host Initiated SSO</span></span>
<span data-ttu-id="75bc5-103">當主控件初始化的 SSO 之分支機構應用程式建立時，依照預設會啟用非 Windows 使用者的密碼驗證。</span><span class="sxs-lookup"><span data-stu-id="75bc5-103">When an affiliate application for host initiated SSO is created, password validation for the non-Windows user is enabled by default.</span></span> <span data-ttu-id="75bc5-104">這表示當應用程式呼叫 SSO 以取得 Windows 使用者 Token 來存取資源時，它們必須提供非 Windows 使用者帳戶與非 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="75bc5-104">This means when applications call SSO to obtain the Windows user token to access resources, they must provide the non-Windows user account and the non-Windows password.</span></span> <span data-ttu-id="75bc5-105">若密碼不符合該非 Windows 使用者在 SSO 資料庫中的密碼，就會拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="75bc5-105">If the password does not match the password in the SSO database for that non-Windows user, access is denied.</span></span> <span data-ttu-id="75bc5-106">如有必要，可以停用分支機構應用程式的密碼驗證功能。</span><span class="sxs-lookup"><span data-stu-id="75bc5-106">If necessary, the password validation feature can be disabled for the affiliate application.</span></span> <span data-ttu-id="75bc5-107">密碼驗證功能可套用至主控件初始化的 SSO 之個別與主控件群組類型分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="75bc5-107">The password validation feature applies to both individual and host group type affiliate applications for host initiated SSO.</span></span>  
  
 <span data-ttu-id="75bc5-108">個別類型主控件初始化的 SSO 分支機構應用程式的範例 XML 檔案為：</span><span class="sxs-lookup"><span data-stu-id="75bc5-108">An example XML file for Individual type host initiated SSO affiliate application is:</span></span>  
  
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
  
 <span data-ttu-id="75bc5-109">若是主控件初始化的 SSO 之個別應用程式，則 appUserAccount 是包含 Windows 網域帳戶使用者清單的群組帳戶，這些網域帳戶使用者與其對應的非 Windows 帳戶為一對一對應。</span><span class="sxs-lookup"><span data-stu-id="75bc5-109">In the case of individual applications for host initiated SSO, the appUserAccount is a group account that contains the list of Windows domain account users that have a 1 to 1 mapping with their corresponding non-Windows accounts.</span></span>  
  
 <span data-ttu-id="75bc5-110">主控件群組類型主控件初始化的 SSO 分支機構應用程式的範例 XML 檔案為：</span><span class="sxs-lookup"><span data-stu-id="75bc5-110">An example XML file for host group type host initiated SSO affiliate application is:</span></span>  
  
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
  
 <span data-ttu-id="75bc5-111">在主控件初始化的 SSO 之群組應用程式中，appUserAccount 必須是個別使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="75bc5-111">In group applications for host initiated SSO, the appUserAccount must be an individual user account.</span></span> <span data-ttu-id="75bc5-112">此帳戶也就是所有非 Windows 帳戶所對應至的帳戶。</span><span class="sxs-lookup"><span data-stu-id="75bc5-112">It is this account that all non-Windows accounts are mapped to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75bc5-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75bc5-113">See Also</span></span>  
 [<span data-ttu-id="75bc5-114">主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="75bc5-114">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)