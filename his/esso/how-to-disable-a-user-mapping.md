---
title: 如何停用使用者對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51c745dd-4d39-46e5-88bf-b803ae2e0a1b
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 93694ed8a3238be51b255bcad79122169461d885
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250970"
---
# <a name="how-to-disable-a-user-mapping"></a><span data-ttu-id="5c393-102">如何停用使用者對應</span><span class="sxs-lookup"><span data-stu-id="5c393-102">How to Disable a User Mapping</span></span>
<span data-ttu-id="5c393-103">當您要關閉與特定對應關聯的所有作業時，可以停用使用者對應。</span><span class="sxs-lookup"><span data-stu-id="5c393-103">You can disable a user mapping when you want to turn off all operations associated with a given mapping.</span></span> <span data-ttu-id="5c393-104">您必須先停用使用者對應，才能進行移除。</span><span class="sxs-lookup"><span data-stu-id="5c393-104">You must disable a user mapping before you can remove it.</span></span>  
  
 <span data-ttu-id="5c393-105">當您停用使用者對應時，將會顯示為 (D) *\<網域 >\\< 使用者名稱\>* 時列出使用者對應。</span><span class="sxs-lookup"><span data-stu-id="5c393-105">When you disable a user mapping, it will appear as (D) *\<domain>\\<username\>* when you list the user mappings.</span></span>  
  
### <a name="to-disable-a-user-mapping-using-the-administration-utility"></a><span data-ttu-id="5c393-106">使用管理公用程式停用使用者對應</span><span class="sxs-lookup"><span data-stu-id="5c393-106">To disable a user mapping using the administration utility</span></span>  
  
1.  <span data-ttu-id="5c393-107">按一下**啟動**，按一下 **執行**，型別`cmd`，然後按下**ENTER**。</span><span class="sxs-lookup"><span data-stu-id="5c393-107">Click **Start**, click **Run**, type `cmd`, and then press **ENTER**.</span></span>  
  
2.  <span data-ttu-id="5c393-108">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="5c393-108">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="5c393-109">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="5c393-109">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="5c393-110">型別`ssomanage –disablemapping <domain>\<username><application name>`，其中*\<網域 >* 是 Windows 網域使用者帳戶， *\<使用者名稱 >* 是您想要停用的 Windows 使用者名稱認證，和*\<應用程式名稱 >* 是您要移除使用者對應的分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c393-110">Type `ssomanage –disablemapping <domain>\<username><application name>`, where *\<domain>* is the Windows domain for the user account, *\<username>* is the Windows user name for which you want to disable the credentials, and *\<application name>* is the name of the affiliate application for which you want to remove the user mapping.</span></span>  
  
### <a name="to-disable-a-user-mapping-using-the-client-utility"></a><span data-ttu-id="5c393-111">使用用戶端公用程式停用使用者對應</span><span class="sxs-lookup"><span data-stu-id="5c393-111">To disable a user mapping using the client utility</span></span>  
  
1.  <span data-ttu-id="5c393-112">按一下**啟動**，按一下 **執行**，型別`cmd`，然後按下**ENTER**。</span><span class="sxs-lookup"><span data-stu-id="5c393-112">Click **Start**, click **Run**, type `cmd`, and then press **ENTER**.</span></span>  
  
2.  <span data-ttu-id="5c393-113">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="5c393-113">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="5c393-114">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="5c393-114">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="5c393-115">型別`ssoclient –disablemapping <application name>`，其中*\<應用程式名稱 >* 是您要移除使用者對應的分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c393-115">Type `ssoclient –disablemapping <application name>`, where *\<application name>* is the name of the affiliate application for which you want to remove the user mapping.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c393-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c393-116">See Also</span></span>  
 <span data-ttu-id="5c393-117">[SSO 對應](../esso/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="5c393-117">[SSO Mappings](../esso/sso-mappings.md) </span></span>  
 <span data-ttu-id="5c393-118">[管理分支機構應用程式](../esso/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="5c393-118">[Managing Affiliate Applications](../esso/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="5c393-119">管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="5c393-119">Managing User Mappings</span></span>](../esso/managing-user-mappings.md)