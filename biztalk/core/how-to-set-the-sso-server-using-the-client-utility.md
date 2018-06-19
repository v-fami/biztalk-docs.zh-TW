---
title: 如何設定使用用戶端公用程式的 SSO 伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], selecting servers
- managing [SSO applications], selecting servers
- SSOClient [SSO], selecting servers
ms.assetid: a0f1038c-60c9-4e9d-a730-1ecfa036743b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49b2145320bd8e22b01d312d62246fa282fb534e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25971148"
---
# <a name="how-to-set-the-sso-server-using-the-client-utility"></a><span data-ttu-id="6be35-102">如何設定 SSO 伺服器使用用戶端公用程式</span><span class="sxs-lookup"><span data-stu-id="6be35-102">How to Set the SSO Server Using the Client Utility</span></span>
<span data-ttu-id="6be35-103">每次使用 ssoclient 時，您必須先將使用者指向包含其組態資訊的正確「單一登入」伺服器。</span><span class="sxs-lookup"><span data-stu-id="6be35-103">Each time you use ssoclient, you must first point the user to the correct Single Sign-On server that contains their configuration information.</span></span>  
  
### <a name="to-set-the-sso-server-for-a-user-using-the-client-utility"></a><span data-ttu-id="6be35-104">使用用戶端公用程式設定使用者的 SSO 伺服器</span><span class="sxs-lookup"><span data-stu-id="6be35-104">To set the SSO Server for a user using the client utility</span></span>  
  
1.  <span data-ttu-id="6be35-105">在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="6be35-105">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="6be35-106">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="6be35-106">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6be35-107">預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="6be35-107">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="6be35-108">型別 **ssoclient – 伺服器*\<單一登入伺服器\>* * *，其中\<* 單一登入伺服器\>* 是單一登入伺服器的名稱使用者想要連接到。</span><span class="sxs-lookup"><span data-stu-id="6be35-108">Type **ssoclient –server *\<Single Sign-On Server\>***, where \<* Single Sign-On Server\>* is the name of the Single Sign-On server the user wants to connect to.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6be35-109">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="6be35-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be35-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6be35-110">See Also</span></span>  
 <span data-ttu-id="6be35-111">[SSO 分支機構應用程式](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="6be35-111">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="6be35-112">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="6be35-112">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)