---
title: 如何建立元件介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating component interfaces
- component interfaces, creating
ms.assetid: 9def053a-cbf6-4b34-b2e8-b2d03bffc5fe
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86ee68edba66b05d3c2541dd9c41cc074bd790b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249294"
---
# <a name="how-to-create-component-interfaces"></a><span data-ttu-id="f324b-102">如何建立元件介面</span><span class="sxs-lookup"><span data-stu-id="f324b-102">How to Create Component Interfaces</span></span>
<span data-ttu-id="f324b-103">您可以使用 PeopleSoft 應用程式設計工具建立元件介面。</span><span class="sxs-lookup"><span data-stu-id="f324b-103">You create component interfaces using the PeopleSoft Application Designer.</span></span> <span data-ttu-id="f324b-104">(如需應用程式設計工具的詳細資訊，請參閱 PeopleSoft Enterprise 文件。)</span><span class="sxs-lookup"><span data-stu-id="f324b-104">(For more information about Application Designer, see the PeopleSoft Enterprise documentation.)</span></span>  
  
 <span data-ttu-id="f324b-105">您可以在元件檢視中新增記錄內的屬性。</span><span class="sxs-lookup"><span data-stu-id="f324b-105">You can add properties from the records in the component view.</span></span> <span data-ttu-id="f324b-106">在元件介面中，您可以刪除不想公開的屬性。</span><span class="sxs-lookup"><span data-stu-id="f324b-106">In the component interface, you can delete a property that you do not want to expose.</span></span> <span data-ttu-id="f324b-107">按一下屬性，然後再按一下，直到您可以輸入新的名稱，便能重新命名屬性。</span><span class="sxs-lookup"><span data-stu-id="f324b-107">You can rename properties by clicking the property and then clicking again until you can type a new name.</span></span> <span data-ttu-id="f324b-108">如果您重新命名屬性，在元件介面內就只能用新名稱參考它，不能使用基礎元件名稱。</span><span class="sxs-lookup"><span data-stu-id="f324b-108">If you rename a property, you can reference it in the component interface only by the new name, not by the underlying component name.</span></span>  
  
 <span data-ttu-id="f324b-109">屬性相鄰的圖示可能各不相同。</span><span class="sxs-lookup"><span data-stu-id="f324b-109">Properties may have various icons adjacent to them.</span></span> <span data-ttu-id="f324b-110">例如，EMPLID 的圖示會指出它是基礎記錄內的索引鍵欄位。</span><span class="sxs-lookup"><span data-stu-id="f324b-110">For example, EMPLID has an icon that indicates that it is a key field from the underlying record.</span></span> <span data-ttu-id="f324b-111">NAME 的圖示會指出它是基礎記錄內的其他索引鍵欄位</span><span class="sxs-lookup"><span data-stu-id="f324b-111">NAME has an icon that indicates that it is an alternate key field from the underlying record.</span></span> <span data-ttu-id="f324b-112">(如需屬性圖示的完整清單，請參閱 PeopleBooks 文件)。</span><span class="sxs-lookup"><span data-stu-id="f324b-112">(For a complete list of property icons, see the PeopleBooks documentation.)</span></span>  
  
### <a name="creating-a-new-component-interface"></a><span data-ttu-id="f324b-113">建立新元件介面</span><span class="sxs-lookup"><span data-stu-id="f324b-113">Creating a new component interface</span></span>  
  
1.  <span data-ttu-id="f324b-114">開啟 PeopleSoft 應用程式設計工具。</span><span class="sxs-lookup"><span data-stu-id="f324b-114">Open the PeopleSoft Application Designer.</span></span>  
  
2.  <span data-ttu-id="f324b-115">在 [檔案]  功能表上，按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="f324b-115">On the **File** menu, click **New**.</span></span>  
  
     ![](../core/media/psadapter-42-ps-new-compinterface.gif "PSAdapter_42_PS_New_CompInterface")  
  
3.  <span data-ttu-id="f324b-116">在**新增**對話方塊中，選取**元件介面**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f324b-116">In the **New** dialog box, select **Component Interface**, and then click **OK**.</span></span>  
  
     ![](../core/media/psadapter-43-ps-selectsourcecomp.gif "PSAdapter_43_PS_SelectSourceComp")  
  
4.  <span data-ttu-id="f324b-117">在**選取元件介面的來源元件**視窗中，選取要做基礎 」 的元件介面，然後按一下 元件**選取**。</span><span class="sxs-lookup"><span data-stu-id="f324b-117">In the **Select Source Component for Component Interface** window, select the component to use as a basis for the component interface, and then click **Select**.</span></span>  
  
     ![](../core/media/psadapter-44-ps-appdesigner1.gif "PSAdapter_44_PS_AppDesigner1")  
  
    > [!NOTE]
    >  <span data-ttu-id="f324b-118">若為大型元件介面，請手動公開元件屬性。</span><span class="sxs-lookup"><span data-stu-id="f324b-118">If the component interface is large, expose the component properties manually.</span></span>  
  
5.  <span data-ttu-id="f324b-119">在**應用程式設計工具**對話方塊方塊中，選擇下列選項：</span><span class="sxs-lookup"><span data-stu-id="f324b-119">In the **Application Designer** dialog box, choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="f324b-120">按一下**否**建立元件介面，而不會顯示屬性，並手動公開元件屬性。</span><span class="sxs-lookup"><span data-stu-id="f324b-120">Click **No** to create the component interface without displaying properties and to expose component properties manually.</span></span>  
  
         <span data-ttu-id="f324b-121">a.</span><span class="sxs-lookup"><span data-stu-id="f324b-121">a.</span></span> <span data-ttu-id="f324b-122">從左窗格的相關欄位拖曳至右窗格中。</span><span class="sxs-lookup"><span data-stu-id="f324b-122">Drag the relevant fields from the left pane to the right pane.</span></span>  
  
         <span data-ttu-id="f324b-123">b.</span><span class="sxs-lookup"><span data-stu-id="f324b-123">b.</span></span> <span data-ttu-id="f324b-124">若要選取不同的函式來執行，以滑鼠右鍵按一下 靠右或向左窗格中，取決於哪一個窗格為作用中。</span><span class="sxs-lookup"><span data-stu-id="f324b-124">To select various functions to perform, right-click either the right or left pane, depending on which pane is active.</span></span>  
  
         <span data-ttu-id="f324b-125">如需功能的完整清單，請參閱 PeopleBooks 文件。</span><span class="sxs-lookup"><span data-stu-id="f324b-125">For a complete list of functions, see the PeopleBooks documentation.</span></span>  
  
    -   <span data-ttu-id="f324b-126">按一下**是**建立元件介面，並顯示基礎元件介面的屬性。</span><span class="sxs-lookup"><span data-stu-id="f324b-126">Click **Yes** to create the component interface and display the properties of the underlying component interface.</span></span>  
  
         ![](../core/media/psadapter-45-ps-appdesigner2.gif "PSAdapter_45_PS_AppDesigner2")  
  
## <a name="see-also"></a><span data-ttu-id="f324b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f324b-127">See Also</span></span>  
 <span data-ttu-id="f324b-128">[元件介面中的標準方法](../core/standard-methods-in-component-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="f324b-128">[Standard Methods in Component Interfaces](../core/standard-methods-in-component-interfaces.md) </span></span>  
 <span data-ttu-id="f324b-129">[附錄 c： 使用元件介面](../core/appendix-c-using-component-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="f324b-129">[Appendix C: Using Component Interfaces](../core/appendix-c-using-component-interfaces.md) </span></span>  
 [<span data-ttu-id="f324b-130">附錄 a： 元件介面方法</span><span class="sxs-lookup"><span data-stu-id="f324b-130">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)