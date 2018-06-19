---
title: 是否有 BizTalk Server 的版本？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb651202-f682-4e5f-8a79-221877af20a7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce5508a3b7c78e52fe5fcbef40e351dce58f2816
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288846"
---
# <a name="what-version-of-biztalk-server-do-i-have"></a><span data-ttu-id="23656-103">是否有 BizTalk Server 的版本？</span><span class="sxs-lookup"><span data-stu-id="23656-103">What Version of BizTalk Server Do I Have?</span></span>
<span data-ttu-id="23656-104">您可能執行不同版本與不同版本的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="23656-104">You may be running different versions and different editions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="23656-105">本主題會示範如何判斷[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝資訊，包括版本號碼、 版本與安裝路徑。</span><span class="sxs-lookup"><span data-stu-id="23656-105">This topic shows you how to determine [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation information, including the version number, edition, and installation path.</span></span>  
  
## <a name="use-the-registry"></a><span data-ttu-id="23656-106">使用登錄</span><span class="sxs-lookup"><span data-stu-id="23656-106">Use the registry</span></span>
  
1.  <span data-ttu-id="23656-107">選取**啟動**，型別`regedt32`，然後再開啟它。</span><span class="sxs-lookup"><span data-stu-id="23656-107">Select **Start**, type `regedt32`, and then open it.</span></span>  
  
2.  <span data-ttu-id="23656-108">展開**HKEY_LOCAL_MACHINE**，依序展開**軟體**，依序展開**Microsoft**，依序展開**BizTalk Server**，然後選取  **3.0**。</span><span class="sxs-lookup"><span data-stu-id="23656-108">Expand **HKEY_LOCAL_MACHINE**, expand **SOFTWARE**, expand **Microsoft**, expand **BizTalk Server**, and then select **3.0**.</span></span>  
  
3.  <span data-ttu-id="23656-109">在右窗格會顯示安裝資訊，包括：</span><span class="sxs-lookup"><span data-stu-id="23656-109">The right pane displays installation information, including:</span></span>  
  
    |<span data-ttu-id="23656-110">子機碼</span><span class="sxs-lookup"><span data-stu-id="23656-110">Sub-key</span></span>|<span data-ttu-id="23656-111">Description</span><span class="sxs-lookup"><span data-stu-id="23656-111">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="23656-112">**InstallPath**</span><span class="sxs-lookup"><span data-stu-id="23656-112">**InstallPath**</span></span>|<span data-ttu-id="23656-113">列出您安裝的安裝路徑[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="23656-113">Lists the installation path where you installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>|  
    |<span data-ttu-id="23656-114">**ProductEdition**</span><span class="sxs-lookup"><span data-stu-id="23656-114">**ProductEdition**</span></span>|<span data-ttu-id="23656-115">列出版本，包括：</span><span class="sxs-lookup"><span data-stu-id="23656-115">Lists the edition, including:</span></span><br /><br /> <span data-ttu-id="23656-116">開發人員</span><span class="sxs-lookup"><span data-stu-id="23656-116">-   Developer</span></span><br /><span data-ttu-id="23656-117">分支機構</span><span class="sxs-lookup"><span data-stu-id="23656-117">-   Branch</span></span><br /><span data-ttu-id="23656-118">標準</span><span class="sxs-lookup"><span data-stu-id="23656-118">-   Standard</span></span><br /><span data-ttu-id="23656-119">企業</span><span class="sxs-lookup"><span data-stu-id="23656-119">-   Enterprise</span></span>|  
    |<span data-ttu-id="23656-120">**ProductVersion**</span><span class="sxs-lookup"><span data-stu-id="23656-120">**ProductVersion**</span></span>|<span data-ttu-id="23656-121">列出的基底的產品版本。</span><span class="sxs-lookup"><span data-stu-id="23656-121">Lists the base product version.</span></span> <span data-ttu-id="23656-122">如需特定產品版本，包括 service pack 和累計更新，請參閱[BizTalk 版本](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx)。</span><span class="sxs-lookup"><span data-stu-id="23656-122">For specific product version, including service packs and cumulative updates, see [BizTalk Versions](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx).</span></span>|  

## <a name="use-the-control-panel"></a><span data-ttu-id="23656-123">使用控制台</span><span class="sxs-lookup"><span data-stu-id="23656-123">Use the control panel</span></span>

1.  <span data-ttu-id="23656-124">選取**啟動**，型別`Programs and Features`，然後再開啟它。</span><span class="sxs-lookup"><span data-stu-id="23656-124">Select **Start**, type `Programs and Features`, and then open it.</span></span>  

2. <span data-ttu-id="23656-125">在清單中，選取**Microsoft BizTalk Server**。</span><span class="sxs-lookup"><span data-stu-id="23656-125">In the list, select **Microsoft BizTalk Server**.</span></span> <span data-ttu-id="23656-126">列出的版本與版本。</span><span class="sxs-lookup"><span data-stu-id="23656-126">The version and edition are listed.</span></span>

<span data-ttu-id="23656-127">請參閱[BizTalk 版本](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx)。</span><span class="sxs-lookup"><span data-stu-id="23656-127">See [BizTalk Versions](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="23656-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23656-128">See Also</span></span>  
 [<span data-ttu-id="23656-129">開始使用</span><span class="sxs-lookup"><span data-stu-id="23656-129">Get started</span></span>](../core/getting-started-with-biztalk-server.md)