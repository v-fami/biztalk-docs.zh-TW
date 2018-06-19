---
title: 如何註冊和移除 BizTalk 組件檢視器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f80b906-0a9e-4bcd-984d-db4550f2e51f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ad3628f61fec11f135bf2235f5e0d25f52992d3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970028"
---
# <a name="how-to-register-and-remove-the-biztalk-assembly-viewer"></a><span data-ttu-id="40a95-102">如何註冊和移除 BizTalk 組件檢視工具</span><span class="sxs-lookup"><span data-stu-id="40a95-102">How to Register and Remove the BizTalk Assembly Viewer</span></span>
<span data-ttu-id="40a95-103">在 BizTalk Server 安裝期間，不會自動註冊 BizTalk「組件檢視工具」。</span><span class="sxs-lookup"><span data-stu-id="40a95-103">The BizTalk Assembly Viewer is not registered automatically during BizTalk Server setup.</span></span> <span data-ttu-id="40a95-104">若要註冊或移除 BizTalk「組件檢視工具」，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="40a95-104">To register or remove the BizTalk Assembly Viewer, follow these steps.</span></span>  
  
### <a name="to-add-assembly-viewer-to-the-windows-registry"></a><span data-ttu-id="40a95-105">若要將組件檢視工具加入至 Windows 登錄</span><span class="sxs-lookup"><span data-stu-id="40a95-105">To add Assembly Viewer to the Windows registry</span></span>  
  
1.  <span data-ttu-id="40a95-106">從**啟動**功能表上，按一下 **執行**。</span><span class="sxs-lookup"><span data-stu-id="40a95-106">From the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="40a95-107">在 [執行] 對話方塊中，輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="40a95-107">In the Run dialog box, type **cmd**.</span></span>  
  
3.  <span data-ttu-id="40a95-108">從命令列中，瀏覽至\< *BizTalk Server 安裝資料夾*\>\Developer Tools\ 目錄所在的位置。</span><span class="sxs-lookup"><span data-stu-id="40a95-108">From the command line, navigate to \<*BizTalk Server Installation Folder*\>\Developer Tools\ where BTSAsmExt.dll resides.</span></span>  
  
4.  <span data-ttu-id="40a95-109">在命令列輸入：</span><span class="sxs-lookup"><span data-stu-id="40a95-109">At the command line, type:</span></span>  
  
     <span data-ttu-id="40a95-110">regsvr32 BTSAsmExt.dll</span><span class="sxs-lookup"><span data-stu-id="40a95-110">regsvr32 BTSAsmExt.dll</span></span>  
  
5.  <span data-ttu-id="40a95-111">若要開始使用「組件檢視工具」，請登出然後再登入電腦。</span><span class="sxs-lookup"><span data-stu-id="40a95-111">To begin using Assembly View, log off and then log back onto the computer.</span></span>  
  
### <a name="to-remove-assembly-viewer-from-the-windows-registry"></a><span data-ttu-id="40a95-112">若要從 Windows 登錄中移除組件檢視工具</span><span class="sxs-lookup"><span data-stu-id="40a95-112">To remove Assembly Viewer from the Windows registry</span></span>  
  
1.  <span data-ttu-id="40a95-113">從**啟動**功能表上，按一下 **執行**。</span><span class="sxs-lookup"><span data-stu-id="40a95-113">From the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="40a95-114">在**執行** 對話方塊中，輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="40a95-114">In the **Run** dialog box, type **cmd**.</span></span>  
  
3.  <span data-ttu-id="40a95-115">從命令列中，瀏覽至\< *BizTalk Server 安裝資料夾*\>\Developer Tools\ 目錄所在的位置。</span><span class="sxs-lookup"><span data-stu-id="40a95-115">From the command line, navigate to \<*BizTalk Server Installation Folder*\>\Developer Tools\ where BTSAsmExt.dll resides.</span></span>  
  
4.  <span data-ttu-id="40a95-116">在命令列輸入：</span><span class="sxs-lookup"><span data-stu-id="40a95-116">At the command line, type:</span></span>  
  
     <span data-ttu-id="40a95-117">regsvr32/u BTSAsmExt.dll</span><span class="sxs-lookup"><span data-stu-id="40a95-117">regsvr32/u BTSAsmExt.dll</span></span>  
  
5.  <span data-ttu-id="40a95-118">若要完成移除，請登出然後再登入電腦。</span><span class="sxs-lookup"><span data-stu-id="40a95-118">To complete the removal, log off and then log back onto the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a95-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="40a95-119">See Also</span></span>  
 [<span data-ttu-id="40a95-120">使用 BizTalk 組件檢視工具檢視組件</span><span class="sxs-lookup"><span data-stu-id="40a95-120">Viewing Assemblies with the BizTalk Assembly Viewer</span></span>](../core/viewing-assemblies-with-the-biztalk-assembly-viewer.md)