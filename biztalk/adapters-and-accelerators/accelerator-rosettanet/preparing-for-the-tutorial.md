---
title: BizTalk Server 的 RosettaNet 回送教學課程的必要條件 |Microsoft 文件
description: 若要逐步執行 RosettaNet 加速器 (BTARN)，以在 BizTalk Server 中的回送教學課程的必要條件
caps.latest.revision: 9
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e26696c-86c5-448b-9cd6-bfd4a279151a
ms.author: mandia
ms.openlocfilehash: 9767f7823e80d4de67345ba0fbf59c1435adb8e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206958"
---
# <a name="prepare-for-the-tutorial"></a><span data-ttu-id="909e3-103">準備進行教學課程</span><span class="sxs-lookup"><span data-stu-id="909e3-103">Prepare for the tutorial</span></span>

## <a name="prerequisites"></a><span data-ttu-id="909e3-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="909e3-104">Prerequisites</span></span>
<span data-ttu-id="909e3-105">再開始回送教學課程：</span><span class="sxs-lookup"><span data-stu-id="909e3-105">Before starting the Loopback tutorial:</span></span>
  
-   <span data-ttu-id="909e3-106">[安裝和設定](install-configure-biztalk-accelerator-for-rosettanet.md)快速鍵。</span><span class="sxs-lookup"><span data-stu-id="909e3-106">[Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md) the accelerator.</span></span> <span data-ttu-id="909e3-107">您可能要將 btarnhttpreceive 虛擬目錄加入至 Windows SharePoint 受管理的路徑排除清單，在 SharePoint 管理中心內。</span><span class="sxs-lookup"><span data-stu-id="909e3-107">You may have to add the btarnhttpreceive virtual directory to the Windows SharePoint managed path exclusion list in SharePoint Central Administration.</span></span>  
  
-   <span data-ttu-id="909e3-108">確定 BizTalkServerIsolatedHost 和 biztalkserverapplication 主控件有**信任的驗證**啟用選項。</span><span class="sxs-lookup"><span data-stu-id="909e3-108">Be sure the BizTalkServerIsolatedHost and BizTalkServerApplication hosts have the **Authentication trusted** option enabled.</span></span> <span data-ttu-id="909e3-109">若要確認，開啟 BizTalk Server 管理主控台，並展開**主機**。</span><span class="sxs-lookup"><span data-stu-id="909e3-109">To verify, open the BizTalk Server Administration console, and expand **Hosts**.</span></span> <span data-ttu-id="909e3-110">以滑鼠右鍵按一下主應用程式中，選取**屬性**，並檢查**信任的驗證**如果未啟用。</span><span class="sxs-lookup"><span data-stu-id="909e3-110">Right-click the host, select **Properties**, and check **Authentication Trusted** if it's not enabled.</span></span>  

    <span data-ttu-id="909e3-111">如果您有一個以上的主控件執行個體，然後刪除所有主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="909e3-111">If you have more than one host instance, then delete all but one host instance.</span></span> <span data-ttu-id="909e3-112">例如，刪除 BizTalk Server 外掛式主控的件執行個體，並保留 BizTalkServerApplication 主控件執行個體）。</span><span class="sxs-lookup"><span data-stu-id="909e3-112">For example, delete the BizTalk Server Isolated Host instance, and keep the BizTalkServerApplication host instance).</span></span> <span data-ttu-id="909e3-113">這可讓您選取**信任的驗證**主機相關聯的執行個體，然後再重新建立其他主控件執行個體上。</span><span class="sxs-lookup"><span data-stu-id="909e3-113">This lets you select **Authentication Trusted** on the host associated with that instance, and then re-create the additional host instances.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="909e3-114">下一步</span><span class="sxs-lookup"><span data-stu-id="909e3-114">Next step</span></span>
 [<span data-ttu-id="909e3-115">步驟 1： 建立主要組織</span><span class="sxs-lookup"><span data-stu-id="909e3-115">Step 1: Create the Home Organization</span></span>](step-1-create-the-home-organization.md)