---
title: 如何列出分支機構應用程式的屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fac15775-39d0-470e-b9d2-21b2d02e1de7
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: e35f1f068f63d4db9738733bcada55047e81a19a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250954"
---
# <a name="how-to-list-the-properties-of-an-affiliate-application"></a><span data-ttu-id="82566-102">如何列出分支機構應用程式的屬性</span><span class="sxs-lookup"><span data-stu-id="82566-102">How to List the Properties of an Affiliate Application</span></span>
<span data-ttu-id="82566-103">**Displayapp**命令顯示分支機構應用程式的下列資訊。</span><span class="sxs-lookup"><span data-stu-id="82566-103">The **displayapp** command shows the following information about the affiliate application.</span></span> <span data-ttu-id="82566-104">如需分支機構應用程式屬性的詳細資訊，請參閱[SSO 分支機構應用程式](../esso/sso-affiliate-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="82566-104">For more information about the properties for an affiliate application, see [SSO Affiliate Applications](../esso/sso-affiliate-applications.md).</span></span>  
  
 <span data-ttu-id="82566-105">單一登入 (SSO) 系統會從您用來更新分支機構應用程式的 XML 檔案中取得這項資訊。</span><span class="sxs-lookup"><span data-stu-id="82566-105">The Single Sign-On (SSO) system obtains this information from the XML file that you used to update the affiliate application.</span></span> <span data-ttu-id="82566-106">如需詳細資訊，請參閱[如何更新分支機構應用程式的內容](../esso/how-to-update-the-properties-of-an-affiliate-application.md)。</span><span class="sxs-lookup"><span data-stu-id="82566-106">For more information, see [How to Update the Properties of an Affiliate Application](../esso/how-to-update-the-properties-of-an-affiliate-application.md).</span></span>  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-administration-utility"></a><span data-ttu-id="82566-107">使用管理公用程式顯示分支機構應用程式的屬性</span><span class="sxs-lookup"><span data-stu-id="82566-107">To display the properties of an affiliate application using the administration utility</span></span>  
  
1.  <span data-ttu-id="82566-108">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="82566-108">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="82566-109">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="82566-109">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="82566-110">預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="82566-110">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="82566-111">型別`ssomanage –displayapp <application name>`，其中*\<應用程式名稱 >* 是您想要顯示的屬性的分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="82566-111">Type `ssomanage –displayapp <application name>`, where *\<application name>* is the name of the affiliate application that you want to display the properties for.</span></span>  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-client-utility"></a><span data-ttu-id="82566-112">使用用戶端公用程式顯示分支機構應用程式的屬性</span><span class="sxs-lookup"><span data-stu-id="82566-112">To display the properties of an affiliate application using the client utility</span></span>  
  
1.  <span data-ttu-id="82566-113">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="82566-113">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="82566-114">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="82566-114">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="82566-115">預設安裝目錄是\<*安裝磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="82566-115">The default installation directory is \<*install drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="82566-116">型別`ssoclient –displayapp <application name>`，其中*\<應用程式名稱 >* 是您想要顯示的屬性的分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="82566-116">Type `ssoclient –displayapp <application name>`, where *\<application name>* is the name of the affiliate application that you want to display the properties for.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82566-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82566-117">See Also</span></span>  
 <span data-ttu-id="82566-118">[管理使用者對應](../esso/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="82566-118">[Managing User Mappings](../esso/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="82566-119">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="82566-119">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)