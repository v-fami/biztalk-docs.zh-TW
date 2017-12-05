---
title: "如何停用 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disabling, SSO
- SSO, disabling
- managing [SSO], disabling
ms.assetid: 0fe4f87a-d7c2-4af6-afee-1065bc4a5285
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7096a9c77dda72bbf0aea3ec76423c759fa90df
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-disable-sso"></a><span data-ttu-id="e18c0-102">如何停用 SSO</span><span class="sxs-lookup"><span data-stu-id="e18c0-102">How to Disable SSO</span></span>
<span data-ttu-id="e18c0-103">您可以使用 MMC 嵌入式管理單元或是命令列，以停用整個「單一登入」系統。</span><span class="sxs-lookup"><span data-stu-id="e18c0-103">You can disable the entire Single Sign-On system by using either the MMC Snap-In or the command line.</span></span>  
  
 <span data-ttu-id="e18c0-104">停用所有「單一登入伺服器」時將會有短暫的延遲，因為它們會輪詢 SSO 資料庫是否有最新的全域資訊。</span><span class="sxs-lookup"><span data-stu-id="e18c0-104">There will be a short delay for all Single Sign-On Servers to be disabled, as they poll the SSO database for the latest global information.</span></span>  
  
### <a name="to-disable-enterprise-single-sign-on-using-the-mmc-snap-in"></a><span data-ttu-id="e18c0-105">使用 MMC 嵌入式管理單元停用企業單一登入</span><span class="sxs-lookup"><span data-stu-id="e18c0-105">To disable Enterprise Single Sign-On using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="e18c0-106">在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="e18c0-106">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="e18c0-107">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="e18c0-107">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="e18c0-108">以滑鼠右鍵按一下**系統**，然後按一下 **停用**。</span><span class="sxs-lookup"><span data-stu-id="e18c0-108">Right-click **System**, and then click **Disable**.</span></span>  
  
### <a name="to-disable-enterprise-single-sign-on-using-the-command-line"></a><span data-ttu-id="e18c0-109">使用命令列停用企業單一登入</span><span class="sxs-lookup"><span data-stu-id="e18c0-109">To disable Enterprise Single Sign-On using the command line</span></span>  
  
1.  <span data-ttu-id="e18c0-110">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="e18c0-110">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="e18c0-111">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e18c0-111">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e18c0-112">預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e18c0-112">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="e18c0-113">型別**ssomanage – disablesso**。</span><span class="sxs-lookup"><span data-stu-id="e18c0-113">Type **ssomanage –disablesso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e18c0-114">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="e18c0-114">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e18c0-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="e18c0-115">See Also</span></span>  
 <span data-ttu-id="e18c0-116">[如何啟用 SSO](../core/how-to-enable-sso.md) </span><span class="sxs-lookup"><span data-stu-id="e18c0-116">[How to Enable SSO](../core/how-to-enable-sso.md) </span></span>  
 [<span data-ttu-id="e18c0-117">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="e18c0-117">Using SSO</span></span>](../core/using-sso.md)