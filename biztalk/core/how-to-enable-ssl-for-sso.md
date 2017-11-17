---
title: "如何為 SSO 啟用 SSL |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, SSL
- managing [SSO], enabling SSL
- SSL
ms.assetid: 0d75962a-a0b0-4e69-8001-54e7df617006
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ae2f3840cd2620f9c03a5b207b32d8bbd4feee9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-ssl-for-sso"></a><span data-ttu-id="58017-102">如何為 SSO 啟用 SSL</span><span class="sxs-lookup"><span data-stu-id="58017-102">How to Enable SSL for SSO</span></span>
<span data-ttu-id="58017-103">使用此命令以啟用所有「企業單一登入」(SSO) 伺服器與 SSO 資料庫之間的「安全通訊端層」(SSL)。</span><span class="sxs-lookup"><span data-stu-id="58017-103">Use this command to enable Secure Sockets Layer (SSL) between all the Enterprise Single Sign-On (SSO) servers and the SSO database.</span></span>  
  
### <a name="to-enable-ssl-for-enterprise-single-sign-on"></a><span data-ttu-id="58017-104">若要啟用企業單一登入的 SSL</span><span class="sxs-lookup"><span data-stu-id="58017-104">To enable SSL for Enterprise Single Sign-On</span></span>  
  
1.  <span data-ttu-id="58017-105">依序按一下 **[開始]**及 **[執行]**，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="58017-105">Click **Start**, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="58017-106">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="58017-106">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="58017-107">預設安裝目錄是**\<磁碟機 >**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="58017-107">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="58017-108">型別**ssoconfig – setSSL\<是/否 >**，其中\<**是/否**> 表示您是否要啟用 SSO 系統中的 SSL。</span><span class="sxs-lookup"><span data-stu-id="58017-108">Type **ssoconfig –setSSL \<yes/no>**, where \<**yes/no**> indicates whether you want to enable SSL in the SSO system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="58017-109">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="58017-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58017-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58017-110">See Also</span></span>  
 [<span data-ttu-id="58017-111">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="58017-111">Using SSO</span></span>](../core/using-sso.md)