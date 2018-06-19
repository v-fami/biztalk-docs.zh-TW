---
title: 如何停用分支機構應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7df6e78-6d18-443d-82dc-4351c20a8c4e
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 6bae89d2a05ec34095e0fa2ac3feafc7b88b894e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250922"
---
# <a name="how-to-disable-an-affiliate-application"></a><span data-ttu-id="a7b3a-102">如何停用分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="a7b3a-102">How to Disable an Affiliate Application</span></span>
<span data-ttu-id="a7b3a-103">使用 MMC 嵌入式管理單元或**disableapp**停用指定的分支機構應用程式的命令。</span><span class="sxs-lookup"><span data-stu-id="a7b3a-103">Use the MMC Snap-In or the **disableapp** command to disable the specified affiliate application.</span></span>  
  
### <a name="to-disable-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="a7b3a-104">若要使用 MMC 嵌入式管理單元停用分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="a7b3a-104">To disable an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="a7b3a-105">按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="a7b3a-105">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="a7b3a-106">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="a7b3a-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="a7b3a-107">以滑鼠右鍵按一下分支機構應用程式，然後按一下 **停用**。</span><span class="sxs-lookup"><span data-stu-id="a7b3a-107">Right-click the affiliate application, and then click **Disable**.</span></span>  
  
### <a name="to-disable-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="a7b3a-108">使用命令列停用分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="a7b3a-108">To disable an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="a7b3a-109">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="a7b3a-109">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="a7b3a-110">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="a7b3a-110">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="a7b3a-111">預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="a7b3a-111">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="a7b3a-112">型別`ssomanage –disableapp <application name>`，其中\<*應用程式名稱*> 是您想要停用分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="a7b3a-112">Type `ssomanage –disableapp <application name>`, where \<*application name*> is the name of the affiliate application you want to disable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b3a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7b3a-113">See Also</span></span>  
 <span data-ttu-id="a7b3a-114">[SSO 分支機構應用程式](../esso/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="a7b3a-114">[SSO Affiliate Applications](../esso/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="a7b3a-115">[如何啟用分支機構應用程式](../esso/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="a7b3a-115">[How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="a7b3a-116">[管理使用者對應](../esso/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="a7b3a-116">[Managing User Mappings](../esso/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="a7b3a-117">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="a7b3a-117">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)