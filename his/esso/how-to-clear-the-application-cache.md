---
title: 如何清除應用程式快取 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a897791-d32f-46a4-8c5d-2b2161e92bd9
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 24954e8314bc94d4570eb57acbf1d4b03bebb65b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-clear-the-application-cache"></a><span data-ttu-id="570d7-102">如何清除應用程式快取</span><span class="sxs-lookup"><span data-stu-id="570d7-102">How to Clear the Application Cache</span></span>
<span data-ttu-id="570d7-103">使用 MMC 嵌入式管理單元或**purgecache**命令可移除的認證快取 （所有的資訊與分支機構應用程式相關聯） 的所有單一登入 (SSO) 伺服器上指定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="570d7-103">Use the MMC Snap-In or the **purgecache** command to remove the contents of the credential cache (all the information that is associated with the affiliate application) for the specified application on all Single Sign-On (SSO) servers.</span></span>  
  
### <a name="to-clear-the-cache-using-the-mmc-snap-in"></a><span data-ttu-id="570d7-104">使用 MMC 嵌入式管理單元清除快取</span><span class="sxs-lookup"><span data-stu-id="570d7-104">To clear the cache using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="570d7-105">按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="570d7-105">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="570d7-106">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="570d7-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="570d7-107">按一下  **分支機構應用程式**。</span><span class="sxs-lookup"><span data-stu-id="570d7-107">Click **Affiliate Applications**.</span></span>  
  
4.  <span data-ttu-id="570d7-108">在結果窗格中，以滑鼠右鍵按一下分支機構應用程式，然後按一下 **清除**。</span><span class="sxs-lookup"><span data-stu-id="570d7-108">In the results pane, right-click the affiliate application, and click **Clear**.</span></span>  
  
### <a name="to-clear-the-cache-using-the-command-line"></a><span data-ttu-id="570d7-109">使用命令列清除快取</span><span class="sxs-lookup"><span data-stu-id="570d7-109">To clear the cache using the command line</span></span>  
  
1.  <span data-ttu-id="570d7-110">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="570d7-110">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="570d7-111">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="570d7-111">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="570d7-112">預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="570d7-112">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="570d7-113">型別`ssomanage –purgecache <application name>`，其中\<*應用程式名稱*> 是您想要清除的快取的分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="570d7-113">Type `ssomanage –purgecache <application name>`, where \<*application name*> is the name of the affiliate application that you want to purge the cache for.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="570d7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="570d7-114">See Also</span></span>  
 <span data-ttu-id="570d7-115">[SSO 分支機構應用程式](../esso/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="570d7-115">[SSO Affiliate Applications](../esso/sso-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="570d7-116">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="570d7-116">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)