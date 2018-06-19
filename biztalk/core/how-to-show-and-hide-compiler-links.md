---
title: 如何顯示和隱藏編譯器連結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66bfd9de-c4d2-46ee-854f-cf7c7cd07368
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66d9b9ee8901ea2d93a73fd227a0ac1623e25669
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255542"
---
# <a name="how-to-show-and-hide-compiler-links"></a><span data-ttu-id="0e290-102">如何顯示和隱藏編譯器連結</span><span class="sxs-lookup"><span data-stu-id="0e290-102">How to Show and Hide Compiler Links</span></span>
<span data-ttu-id="0e290-103">當您編譯對應時，BizTalk 對應工具會建立其他連結，稱為編譯器連結，以說明對應中所需的所有連結。</span><span class="sxs-lookup"><span data-stu-id="0e290-103">When you compile a map, BizTalk Mapper creates additional links, known as compiler links to account for all linking needed in the map.</span></span> <span data-ttu-id="0e290-104">部分連結僅由您所建立的連結暗示。</span><span class="sxs-lookup"><span data-stu-id="0e290-104">Some of these links are only implied by the links you created.</span></span> <span data-ttu-id="0e290-105">當您編譯或測試對應時，Visual Studio 輸出視窗中的最後一行可讓您在主視窗中顯示或隱藏這些額外的編譯器連結。</span><span class="sxs-lookup"><span data-stu-id="0e290-105">When you compile, or test, a map, the final line in the Visual Studio Output window allows you to show or hide these additional compiler links in the main window.</span></span> <span data-ttu-id="0e290-106">依照預設，編譯器連結會以紅色虛線出現。</span><span class="sxs-lookup"><span data-stu-id="0e290-106">By default, the compiler links appear as red dashed lines.</span></span>  
  
### <a name="to-show-or-hide-compiler-links"></a><span data-ttu-id="0e290-107">顯示或隱藏編譯器連結</span><span class="sxs-lookup"><span data-stu-id="0e290-107">To show or hide compiler links</span></span>  
  
1.  <span data-ttu-id="0e290-108">在 [方案總管] 中，以滑鼠右鍵按一下您想要檢視，然後再按一下的編譯器連結的對應**測試對應**。</span><span class="sxs-lookup"><span data-stu-id="0e290-108">In Solution Explorer, right-click the map whose complier links you want to view, and then click **Test Map**.</span></span>  
  
2.  <span data-ttu-id="0e290-109">在 Visual Studio 錯誤清單視窗中，捲動到結尾，並指出的該行上按兩下**此處按兩下以顯示/隱藏編譯器連結**。</span><span class="sxs-lookup"><span data-stu-id="0e290-109">In the Visual Studio Error List window, scroll to the end and double-click the line that says **Double-click here to show/Hide compiler links**.</span></span>  
  
     <span data-ttu-id="0e290-110">若要將編譯器連結的顯示狀態從顯示變更為隱藏或從隱藏變更為顯示，只要再按兩下該行即可。</span><span class="sxs-lookup"><span data-stu-id="0e290-110">To change the display state of compiler links from shown to hidden, or from hidden to shown, just double-click that line again.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0e290-111">當您建置/重建 BizTalk 專案或方案，其中包含一個或多個對應，訊息**此處按兩下以顯示/隱藏編譯器連結**會顯示在**錯誤清單**Visual Studio for 視窗專案或方案中的所有對應。</span><span class="sxs-lookup"><span data-stu-id="0e290-111">When you build/rebuild a BizTalk project or solution containing one or more maps, the message **Double-click here to show/Hide compiler links** is displayed in the **Error List** window of Visual Studio for all the maps in the project or solution.</span></span>  
  
 <span data-ttu-id="0e290-112">若要測試對應，您必須為輸入和輸出執行個體設定屬性。</span><span class="sxs-lookup"><span data-stu-id="0e290-112">To test a map, you must configure the properties for the input and output instances.</span></span> <span data-ttu-id="0e290-113">如需如何設定這些屬性的詳細資訊，請參閱[如何設定對應驗證和測試參數](../core/how-to-configure-map-validation-and-test-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0e290-113">For more information about how to configure these properties, see [How to Configure Map Validation and Test Parameters](../core/how-to-configure-map-validation-and-test-parameters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e290-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e290-114">See Also</span></span>  
 [<span data-ttu-id="0e290-115">使用連結指定記錄和欄位對應</span><span class="sxs-lookup"><span data-stu-id="0e290-115">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)