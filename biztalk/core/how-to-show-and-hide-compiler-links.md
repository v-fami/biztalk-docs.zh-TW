---
title: 如何顯示和隱藏編譯器連結 |Microsoft Docs
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
ms.openlocfilehash: f3c006f5de761837ec1ed0d6f983d380a76a50a5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010047"
---
# <a name="how-to-show-and-hide-compiler-links"></a><span data-ttu-id="a00c1-102">如何顯示和隱藏編譯器連結</span><span class="sxs-lookup"><span data-stu-id="a00c1-102">How to Show and Hide Compiler Links</span></span>
<span data-ttu-id="a00c1-103">當您編譯對應時，BizTalk 對應工具會建立其他連結，稱為編譯器連結，以說明對應中所需的所有連結。</span><span class="sxs-lookup"><span data-stu-id="a00c1-103">When you compile a map, BizTalk Mapper creates additional links, known as compiler links to account for all linking needed in the map.</span></span> <span data-ttu-id="a00c1-104">部分連結僅由您所建立的連結暗示。</span><span class="sxs-lookup"><span data-stu-id="a00c1-104">Some of these links are only implied by the links you created.</span></span> <span data-ttu-id="a00c1-105">當您編譯或測試對應時，Visual Studio 輸出視窗中的最後一行可讓您在主視窗中顯示或隱藏這些額外的編譯器連結。</span><span class="sxs-lookup"><span data-stu-id="a00c1-105">When you compile, or test, a map, the final line in the Visual Studio Output window allows you to show or hide these additional compiler links in the main window.</span></span> <span data-ttu-id="a00c1-106">依照預設，編譯器連結會以紅色虛線出現。</span><span class="sxs-lookup"><span data-stu-id="a00c1-106">By default, the compiler links appear as red dashed lines.</span></span>  
  
### <a name="to-show-or-hide-compiler-links"></a><span data-ttu-id="a00c1-107">顯示或隱藏編譯器連結</span><span class="sxs-lookup"><span data-stu-id="a00c1-107">To show or hide compiler links</span></span>  
  
1. <span data-ttu-id="a00c1-108">在 [方案總管] 中，以滑鼠右鍵按一下您想要檢視，然後再按一下的編譯器連結的對應**測試對應**。</span><span class="sxs-lookup"><span data-stu-id="a00c1-108">In Solution Explorer, right-click the map whose complier links you want to view, and then click **Test Map**.</span></span>  
  
2. <span data-ttu-id="a00c1-109">在 Visual Studio 錯誤清單 視窗中，捲動到結尾，然後按兩下行前**按此處兩下顯示/隱藏編譯器連結**。</span><span class="sxs-lookup"><span data-stu-id="a00c1-109">In the Visual Studio Error List window, scroll to the end and double-click the line that says **Double-click here to show/Hide compiler links**.</span></span>  
  
    <span data-ttu-id="a00c1-110">若要將編譯器連結的顯示狀態從顯示變更為隱藏或從隱藏變更為顯示，只要再按兩下該行即可。</span><span class="sxs-lookup"><span data-stu-id="a00c1-110">To change the display state of compiler links from shown to hidden, or from hidden to shown, just double-click that line again.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="a00c1-111">當您建置/重建 BizTalk 專案或方案，其中包含一或多個對應，訊息**按此處兩下顯示/隱藏編譯器連結**會顯示在**錯誤清單**適用於 Visual Studio 視窗專案或方案中的所有對應。</span><span class="sxs-lookup"><span data-stu-id="a00c1-111">When you build/rebuild a BizTalk project or solution containing one or more maps, the message **Double-click here to show/Hide compiler links** is displayed in the **Error List** window of Visual Studio for all the maps in the project or solution.</span></span>  
  
   <span data-ttu-id="a00c1-112">若要測試對應，您必須為輸入和輸出執行個體設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a00c1-112">To test a map, you must configure the properties for the input and output instances.</span></span> <span data-ttu-id="a00c1-113">如需如何設定這些屬性的詳細資訊，請參閱[如何設定對應驗證和測試參數](../core/how-to-configure-map-validation-and-test-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="a00c1-113">For more information about how to configure these properties, see [How to Configure Map Validation and Test Parameters](../core/how-to-configure-map-validation-and-test-parameters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00c1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a00c1-114">See Also</span></span>  
 [<span data-ttu-id="a00c1-115">使用連結指定記錄和欄位對應</span><span class="sxs-lookup"><span data-stu-id="a00c1-115">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)