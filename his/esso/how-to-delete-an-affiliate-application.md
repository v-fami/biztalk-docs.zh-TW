---
title: 如何刪除分支機構應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec290d38-0220-4bf2-b596-2d6453e51c8d
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: d0632f7e4217cb9bbccd2ee604688f22eb6de348
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250978"
---
# <a name="how-to-delete-an-affiliate-application"></a><span data-ttu-id="b947f-102">如何刪除分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="b947f-102">How to Delete an Affiliate Application</span></span>
<span data-ttu-id="b947f-103">使用 MMC 嵌入式管理單元或**deleteapps**認證資料庫中刪除指定的分支機構應用程式的命令。</span><span class="sxs-lookup"><span data-stu-id="b947f-103">Use the MMC Snap-In or the **deleteapps** command to delete the specified affiliate application from the Credential database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b947f-104">當您刪除分支機構應用程式時，SSO 系統會自動刪除所有與其關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="b947f-104">When you delete an affiliate application, the SSO system automatically deletes all mappings associated with it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b947f-105">您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="b947f-105">You must be an SSO administrator or SSO affiliate administrator to perform this task.</span></span>  
  
### <a name="to-delete-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="b947f-106">若要使用 MMC 嵌入式管理單元刪除分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="b947f-106">To delete an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="b947f-107">按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="b947f-107">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="b947f-108">在 範圍 窗格的 MMC 嵌入式管理單元，依序展開 **企業單一登入** 節點。</span><span class="sxs-lookup"><span data-stu-id="b947f-108">In the scope pane of the MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="b947f-109">以滑鼠右鍵按一下分支機構應用程式，然後按一下 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="b947f-109">Right-click the affiliate application, and then click **Delete**.</span></span>  
  
### <a name="to-delete-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="b947f-110">使用命令列刪除分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="b947f-110">To delete an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="b947f-111">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="b947f-111">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="b947f-112">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="b947f-112">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="b947f-113">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="b947f-113">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="b947f-114">型別`ssomanage –deleteapp <application name>`，其中*\<應用程式名稱 >* 是您想要移除認證資料庫中的分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="b947f-114">Type `ssomanage –deleteapp <application name>`, where *\<application name>* is the name of the affiliate application you want to remove from the Credential database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b947f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b947f-115">See Also</span></span>  
 <span data-ttu-id="b947f-116">[SSO 分支機構應用程式](../esso/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="b947f-116">[SSO Affiliate Applications](../esso/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="b947f-117">[如何啟用分支機構應用程式](../esso/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="b947f-117">[How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="b947f-118">[管理使用者對應](../esso/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="b947f-118">[Managing User Mappings](../esso/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="b947f-119">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="b947f-119">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)