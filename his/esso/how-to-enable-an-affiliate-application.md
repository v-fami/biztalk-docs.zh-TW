---
title: 如何啟用分支機構應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 051bc35f-55e6-4811-9559-b1bb66a570ce
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 53dcd9886bc808f84b112146971a6f9519c404e2
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250930"
---
# <a name="how-to-enable-an-affiliate-application"></a><span data-ttu-id="2c3ff-102">如何啟用分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="2c3ff-102">How to Enable an Affiliate Application</span></span>
<span data-ttu-id="2c3ff-103">您可以使用 MMC 嵌入式管理單元或**enableapp**命令以啟用指定的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="2c3ff-103">You can use the MMC Snap-In or the **enableapp** command to enable the specified affiliate application.</span></span>  
  
### <a name="to-enable-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="2c3ff-104">若要使用 MMC 嵌入式管理單元啟用分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="2c3ff-104">To enable an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="2c3ff-105">按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="2c3ff-105">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="2c3ff-106">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="2c3ff-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="2c3ff-107">以滑鼠右鍵按一下分支機構應用程式，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="2c3ff-107">Right-click the affililate application, and then click **Enable**.</span></span>  
  
### <a name="to-enable-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="2c3ff-108">若要啟用分支機構應用程式使用命令列</span><span class="sxs-lookup"><span data-stu-id="2c3ff-108">To enable an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="2c3ff-109">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="2c3ff-109">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="2c3ff-110">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="2c3ff-110">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="2c3ff-111">預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="2c3ff-111">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="2c3ff-112">型別`ssomanage –enableapp <application name>`，其中\<*應用程式名稱*> 是您想要啟用分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="2c3ff-112">Type `ssomanage –enableapp <application name>`, where \<*application name*> is the name of the affiliate application you want to enable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3ff-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c3ff-113">See Also</span></span>  
 <span data-ttu-id="2c3ff-114">[SSO 分支機構應用程式](../esso/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="2c3ff-114">[SSO Affiliate Applications](../esso/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="2c3ff-115">[如何建立分支機構應用程式](../esso/how-to-create-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="2c3ff-115">[How to Create an Affiliate Application](../esso/how-to-create-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="2c3ff-116">[管理使用者對應](../esso/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="2c3ff-116">[Managing User Mappings](../esso/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="2c3ff-117">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="2c3ff-117">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)