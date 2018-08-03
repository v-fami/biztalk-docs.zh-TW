---
title: 如何設定 SSO 伺服器使用用戶端公用程式 |Microsoft Docs
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
ms.openlocfilehash: 8f212bb5e6601274a473c6f9854d5e23af9715cd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008863"
---
# <a name="how-to-set-the-sso-server-using-the-client-utility"></a><span data-ttu-id="d1fc6-102">如何設定和使用用戶端公用程式的 SSO 伺服器</span><span class="sxs-lookup"><span data-stu-id="d1fc6-102">How to Set the SSO Server Using the Client Utility</span></span>
<span data-ttu-id="d1fc6-103">每次使用 ssoclient 時，您必須先將使用者指向包含其組態資訊的正確「單一登入」伺服器。</span><span class="sxs-lookup"><span data-stu-id="d1fc6-103">Each time you use ssoclient, you must first point the user to the correct Single Sign-On server that contains their configuration information.</span></span>  
  
### <a name="to-set-the-sso-server-for-a-user-using-the-client-utility"></a><span data-ttu-id="d1fc6-104">使用用戶端公用程式設定使用者的 SSO 伺服器</span><span class="sxs-lookup"><span data-stu-id="d1fc6-104">To set the SSO Server for a user using the client utility</span></span>  
  
1. <span data-ttu-id="d1fc6-105">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="d1fc6-105">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="d1fc6-106">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="d1fc6-106">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="d1fc6-107">預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="d1fc6-107">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="d1fc6-108">型別<strong>ssoclient – 伺服器*\<單一登入伺服器\></strong><em>，其中\<</em>單一登入伺服器\>* 是連接到要單一登入伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="d1fc6-108">Type <strong>ssoclient –server *\<Single Sign-On Server\></strong><em>, where \<</em>Single Sign-On Server\>* is the name of the Single Sign-On server the user wants to connect to.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d1fc6-109">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="d1fc6-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1fc6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1fc6-110">See Also</span></span>  
 <span data-ttu-id="d1fc6-111">[SSO 分支機構應用程式](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="d1fc6-111">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="d1fc6-112">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="d1fc6-112">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)