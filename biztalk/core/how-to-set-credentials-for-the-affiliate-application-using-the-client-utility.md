---
title: "如何使用用戶端公用程式之分支機構應用程式設定認證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], configuring credentials
- SSOClient [SSO], configuring credentials
- applications [SSO], credentials
ms.assetid: 454b6257-3538-40be-840c-00172a2c1dce
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31ba167bc35d01907166bb6610720e03be654c4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-credentials-for-the-affiliate-application-using-the-client-utility"></a><span data-ttu-id="2294d-102">如何使用用戶端公用程式之分支機構應用程式設定認證</span><span class="sxs-lookup"><span data-stu-id="2294d-102">How to Set Credentials for the Affiliate Application Using the Client Utility</span></span>
<span data-ttu-id="2294d-103">使用此命令設定使用者的認證，讓使用者能夠存取特定應用程式。</span><span class="sxs-lookup"><span data-stu-id="2294d-103">Use this command to set the credentials for a user so that the user is able to access a specific application.</span></span> <span data-ttu-id="2294d-104">此命令也會自動啟用對應。</span><span class="sxs-lookup"><span data-stu-id="2294d-104">This command also automatically enables the mapping.</span></span>  
  
 <span data-ttu-id="2294d-105">當您輸入此命令時，不會顯示密碼。</span><span class="sxs-lookup"><span data-stu-id="2294d-105">This command does not display the password as you type it.</span></span>  
  
 <span data-ttu-id="2294d-106">若使用者對應已經存在，此命令會為現有對應設定認證。</span><span class="sxs-lookup"><span data-stu-id="2294d-106">If the user mapping already exists, this command will set the credentials for that existing mapping.</span></span> <span data-ttu-id="2294d-107">若您未建立使用者對應，SSO 系統會提示您輸入應用程式的使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="2294d-107">If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.</span></span>  
  
### <a name="to-set-credentials-for-the-affiliate-application-using-the-client-utility"></a><span data-ttu-id="2294d-108">使用用戶端公用程式設定分支機構應用程式的認證</span><span class="sxs-lookup"><span data-stu-id="2294d-108">To set credentials for the affiliate application using the client utility</span></span>  
  
1.  <span data-ttu-id="2294d-109">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="2294d-109">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="2294d-110">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="2294d-110">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="2294d-111">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="2294d-111">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="2294d-112">型別**ssoclient – setcredentials\<應用程式名稱 >**，其中**\<應用程式名稱 >**是特定的應用程式，您想要設定的認證。</span><span class="sxs-lookup"><span data-stu-id="2294d-112">Type **ssoclient –setcredentials \<application name>**, where **\<application name>** is the specific application for which you want to set the credentials for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2294d-113">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="2294d-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="2294d-114">提示輸入使用者認證時，請輸入此應用程式的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="2294d-114">When prompted for the user credentials, enter the user password for this application.</span></span>  
  
5.  <span data-ttu-id="2294d-115">若您未建立使用者對應，SSO 系統會提示您輸入應用程式的使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="2294d-115">If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2294d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2294d-116">See Also</span></span>  
 <span data-ttu-id="2294d-117">[SSO 分支機構應用程式](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="2294d-117">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="2294d-118">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="2294d-118">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)