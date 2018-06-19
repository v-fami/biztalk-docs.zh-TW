---
title: 如何新增現有的對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fbeaea05-016e-488c-90f3-af8c6b9a3d84
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a61fb0faf5f4eed614257361b00cea781db2d94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247454"
---
# <a name="how-to-add-existing-maps"></a><span data-ttu-id="d7450-102">如何新增現有的對應</span><span class="sxs-lookup"><span data-stu-id="d7450-102">How to Add Existing Maps</span></span>
<span data-ttu-id="d7450-103">您可能時常要新增現有的對應到 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="d7450-103">There may be times when you want to add an existing map to a BizTalk project.</span></span> <span data-ttu-id="d7450-104">在進行之前，您必須確定對應的來源與目的結構描述都包含在您要新增對應的 BizTalk 專案中；或者，由對應的 .NET 組件所參考。</span><span class="sxs-lookup"><span data-stu-id="d7450-104">Before doing so, you must ensure that the source and destination schemas of the map are included in the BizTalk project to which you are adding the map; or, referenced by the corresponding .NET assembly.</span></span>  
  
### <a name="to-add-an-existing-map-to-a-biztalk-project"></a><span data-ttu-id="d7450-105">新增現有的對應到 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="d7450-105">To add an existing map to a BizTalk project</span></span>  
  
1.  <span data-ttu-id="d7450-106">以滑鼠右鍵按一下方案總管] 中的 BizTalk 專案，指向**新增**，然後按一下 [**現有項目**。</span><span class="sxs-lookup"><span data-stu-id="d7450-106">Right-click a BizTalk project in Solution Explorer, point to **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="d7450-107">在**加入現有項目**對話方塊中，瀏覽至包含以加入、 選取它，然後按一下對應的資料夾**新增**。</span><span class="sxs-lookup"><span data-stu-id="d7450-107">In the **Add Existing Item** dialog box, browse to the folder containing the map to be added, select it, and then click **Add**.</span></span>  
  
     <span data-ttu-id="d7450-108">對應就會在 BizTalk 對應工具中開啟。</span><span class="sxs-lookup"><span data-stu-id="d7450-108">The map opens in BizTalk Mapper.</span></span> <span data-ttu-id="d7450-109">新增的對應也會顯示為 [方案總管] 中目前 BizTalk 專案的子項目。</span><span class="sxs-lookup"><span data-stu-id="d7450-109">The newly added map also appears as a child of the current BizTalk project in Solution Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7450-110">若您瀏覽至 BizTalk 專案資料夾以外的資料夾，則會在專案資料夾中建立您所新增對應的複本，而加入專案中的對應就是此複本。</span><span class="sxs-lookup"><span data-stu-id="d7450-110">If you browsed to a folder other than the BizTalk project folder, a copy of the map you added was created in the project folder, and it was this copy of the map that was added to the project.</span></span> <span data-ttu-id="d7450-111">後續的對應變更會在此複本進行，而不是其他資料夾中的原始對應。</span><span class="sxs-lookup"><span data-stu-id="d7450-111">Subsequent changes to the map are made to this copy, not to the original map in the other folder.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d7450-112">BizTalk 對應只能開啟 BizTalk 對應工具，裝載於 Microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]殼層。</span><span class="sxs-lookup"><span data-stu-id="d7450-112">BizTalk maps can only be opened by BizTalk Mapper, which is hosted within the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell.</span></span> <span data-ttu-id="d7450-113">若按兩下 Windows 檔案總管中的對應，將會開啟新的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 執行個體，只要相對應的結構描述正確載入，[BizTalk 對應工具] 就會開啟對應。</span><span class="sxs-lookup"><span data-stu-id="d7450-113">If you double-click a map in Windows Explorer, a new instance of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] will be opened, and then the map will be opened by BizTalk Mapper, provided the corresponding schemas are loaded properly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7450-114">如果現有的對應包含自訂運算質，則相對應的 DLL 必須複製到資料夾 “%BTSINSTALLPATH%\Developer Tools\Mapper Extensions”。</span><span class="sxs-lookup"><span data-stu-id="d7450-114">If the existing map contains custom functoids, then the corresponding DLLs must be copied to the folder “%BTSINSTALLPATH%\Developer Tools\Mapper Extensions”.</span></span> <span data-ttu-id="d7450-115">否則，非但不會載入對應，還會擲回錯誤，因為無法載入自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="d7450-115">Else, the map will not load and throws an error because of failure to load custom functoids.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7450-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7450-116">See Also</span></span>  
 <span data-ttu-id="d7450-117">[管理專案中的對應](../core/managing-maps-within-projects.md) </span><span class="sxs-lookup"><span data-stu-id="d7450-117">[Managing Maps Within Projects](../core/managing-maps-within-projects.md) </span></span>  
 [<span data-ttu-id="d7450-118">開發自訂運算質</span><span class="sxs-lookup"><span data-stu-id="d7450-118">Developing Custom Functoids</span></span>](../core/developing-custom-functoids.md)