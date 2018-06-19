---
title: 主控件初始化的 SSO |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- host initiated SSO
- SSO, SSO database
- SSO, host initiated
- managing [SSO], host intitiated
ms.assetid: 492f730d-08ec-47d6-a88b-0d373bd8912b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 136ed2555410187a98960d6671c0c960aeebdd04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246358"
---
# <a name="host-initiated-sso"></a><span data-ttu-id="625b1-102">主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="625b1-102">Host Initiated SSO</span></span>
<span data-ttu-id="625b1-103">主控件初始化的單一登入，可讓來自主控件系統的要求存取 Windows 系統上的資源。</span><span class="sxs-lookup"><span data-stu-id="625b1-103">Host initiated Single Sign-On enables a request from the host system to access a resource on a Windows system.</span></span> <span data-ttu-id="625b1-104">主控件系統 (例如 RACF 帳戶) 存在於非 Windows 環境，且位於非 Windows 使用者的內容底下。</span><span class="sxs-lookup"><span data-stu-id="625b1-104">The host system (for example, a RACF account) exists in a non-Windows environment and under the context of a non-Windows user.</span></span> <span data-ttu-id="625b1-105">「單一登入認證存放區」會對應主控件帳戶到 Windows 帳戶，以啟用此存取。</span><span class="sxs-lookup"><span data-stu-id="625b1-105">The Single Sign-On Credential Store maps host accounts to Windows accounts, enabling this access.</span></span>  
  
 <span data-ttu-id="625b1-106">下列主題描述主控件初始化的 SSO 特定組態。</span><span class="sxs-lookup"><span data-stu-id="625b1-106">The following topics describe configuration specific to Host initiated SSO.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="625b1-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="625b1-107">In This Section</span></span>  
  
-   [<span data-ttu-id="625b1-108">如何設定主機的需求初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="625b1-108">How to Configure Requirements for Host Initiated SSO</span></span>](../core/how-to-configure-requirements-for-host-initiated-sso.md)  
  
-   [<span data-ttu-id="625b1-109">如何啟用和停用主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="625b1-109">How to Enable and Disable Host Initiated SSO</span></span>](../core/how-to-enable-and-disable-host-initiated-sso.md)  
  
-   [<span data-ttu-id="625b1-110">如何建立分支機構應用程式主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="625b1-110">How to Create Affiliate Applications for Host Initiated SSO</span></span>](../core/how-to-create-affiliate-applications-for-host-initiated-sso.md)  
  
-   [<span data-ttu-id="625b1-111">驗證密碼的主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="625b1-111">Validating Passwords for Host Initiated SSO</span></span>](../core/validating-passwords-for-host-initiated-sso.md)  
  
-   [<span data-ttu-id="625b1-112">如何管理使用者對應的主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="625b1-112">How to Manage User Mappings for Host Initiated SSO</span></span>](../core/how-to-manage-user-mappings-for-host-initiated-sso.md)  
  
-   [<span data-ttu-id="625b1-113">如何使用追蹤公用程式中主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="625b1-113">How to Use the Trace Utility in Host Initiated SSO</span></span>](../core/how-to-use-the-trace-utility-in-host-initiated-sso.md)