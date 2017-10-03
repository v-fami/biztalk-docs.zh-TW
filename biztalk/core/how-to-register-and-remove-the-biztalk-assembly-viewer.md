---
title: "如何註冊和移除 BizTalk 組件檢視器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f80b906-0a9e-4bcd-984d-db4550f2e51f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: deae453be1a89049f223e2da9813e449d68eeb07
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-register-and-remove-the-biztalk-assembly-viewer"></a><span data-ttu-id="2b8a1-102">如何註冊和移除 BizTalk 組件檢視工具</span><span class="sxs-lookup"><span data-stu-id="2b8a1-102">How to Register and Remove the BizTalk Assembly Viewer</span></span>
<span data-ttu-id="2b8a1-103">在 BizTalk Server 安裝期間，不會自動註冊 BizTalk「組件檢視工具」。</span><span class="sxs-lookup"><span data-stu-id="2b8a1-103">The BizTalk Assembly Viewer is not registered automatically during BizTalk Server setup.</span></span> <span data-ttu-id="2b8a1-104">若要註冊或移除 BizTalk「組件檢視工具」，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="2b8a1-104">To register or remove the BizTalk Assembly Viewer, follow these steps.</span></span>  
  
### <a name="to-add-assembly-viewer-to-the-windows-registry"></a><span data-ttu-id="2b8a1-105">若要將組件檢視工具加入至 Windows 登錄</span><span class="sxs-lookup"><span data-stu-id="2b8a1-105">To add Assembly Viewer to the Windows registry</span></span>  
  
1.  <span data-ttu-id="2b8a1-106">從**啟動**功能表上，按一下 **執行**。</span><span class="sxs-lookup"><span data-stu-id="2b8a1-106">From the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="2b8a1-107">在 [執行] 對話方塊中，輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="2b8a1-107">In the Run dialog box, type **cmd**.</span></span>  
  
3.  <span data-ttu-id="2b8a1-108">從命令列中，瀏覽至\< *BizTalk Server 安裝資料夾*> \Developer Tools\ 目錄所在的位置。</span><span class="sxs-lookup"><span data-stu-id="2b8a1-108">From the command line, navigate to \<*BizTalk Server Installation Folder*>\Developer Tools\ where BTSAsmExt.dll resides.</span></span>  
  
4.  <span data-ttu-id="2b8a1-109">在命令列輸入：</span><span class="sxs-lookup"><span data-stu-id="2b8a1-109">At the command line, type:</span></span>  
  
     <span data-ttu-id="2b8a1-110">regsvr32 BTSAsmExt.dll</span><span class="sxs-lookup"><span data-stu-id="2b8a1-110">regsvr32 BTSAsmExt.dll</span></span>  
  
5.  <span data-ttu-id="2b8a1-111">若要開始使用「組件檢視工具」，請登出然後再登入電腦。</span><span class="sxs-lookup"><span data-stu-id="2b8a1-111">To begin using Assembly View, log off and then log back onto the computer.</span></span>  
  
### <a name="to-remove-assembly-viewer-from-the-windows-registry"></a><span data-ttu-id="2b8a1-112">若要從 Windows 登錄中移除組件檢視工具</span><span class="sxs-lookup"><span data-stu-id="2b8a1-112">To remove Assembly Viewer from the Windows registry</span></span>  
  
1.  <span data-ttu-id="2b8a1-113">從**啟動**功能表上，按一下 **執行**。</span><span class="sxs-lookup"><span data-stu-id="2b8a1-113">From the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="2b8a1-114">在**執行** 對話方塊中，輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="2b8a1-114">In the **Run** dialog box, type **cmd**.</span></span>  
  
3.  <span data-ttu-id="2b8a1-115">從命令列中，瀏覽至\< *BizTalk Server 安裝資料夾*> \Developer Tools\ 目錄所在的位置。</span><span class="sxs-lookup"><span data-stu-id="2b8a1-115">From the command line, navigate to \<*BizTalk Server Installation Folder*>\Developer Tools\ where BTSAsmExt.dll resides.</span></span>  
  
4.  <span data-ttu-id="2b8a1-116">在命令列輸入：</span><span class="sxs-lookup"><span data-stu-id="2b8a1-116">At the command line, type:</span></span>  
  
     <span data-ttu-id="2b8a1-117">regsvr32/u BTSAsmExt.dll</span><span class="sxs-lookup"><span data-stu-id="2b8a1-117">regsvr32/u BTSAsmExt.dll</span></span>  
  
5.  <span data-ttu-id="2b8a1-118">若要完成移除，請登出然後再登入電腦。</span><span class="sxs-lookup"><span data-stu-id="2b8a1-118">To complete the removal, log off and then log back onto the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b8a1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b8a1-119">See Also</span></span>  
 [<span data-ttu-id="2b8a1-120">檢視 BizTalk 組件檢視器的組件</span><span class="sxs-lookup"><span data-stu-id="2b8a1-120">Viewing Assemblies with the BizTalk Assembly Viewer</span></span>](../core/viewing-assemblies-with-the-biztalk-assembly-viewer.md)