---
title: 驗證對應 (EDI) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: caf58ecf-ed10-4c13-8d7d-e007b9158b0e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6cfe1394d82f4fedb57aacb40bad27c95de2a46
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993335"
---
# <a name="validating-a-map-edi"></a><span data-ttu-id="f9738-102">驗證對應 (EDI)</span><span class="sxs-lookup"><span data-stu-id="f9738-102">Validating a Map (EDI)</span></span>
<span data-ttu-id="f9738-103">您可以在設計階段驗證對應。</span><span class="sxs-lookup"><span data-stu-id="f9738-103">You can validate a map at design time.</span></span> <span data-ttu-id="f9738-104">若要這樣做，您可以使用的 XML 工具延伸模組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="f9738-104">To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="f9738-105">這項作業會產生兩個檔案：一個檔案包含對應的基礎 XSLT，一個檔案包含延伸模組物件。</span><span class="sxs-lookup"><span data-stu-id="f9738-105">This operation generates a file containing the underlying XSLT of the map and a file containing extension objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f9738-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="f9738-106">Prerequisites</span></span>  
 <span data-ttu-id="f9738-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="f9738-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-validate-a-map"></a><span data-ttu-id="f9738-108">若要驗證對應</span><span class="sxs-lookup"><span data-stu-id="f9738-108">To validate a map</span></span>  
  
1. <span data-ttu-id="f9738-109">在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟專案。</span><span class="sxs-lookup"><span data-stu-id="f9738-109">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project.</span></span> <span data-ttu-id="f9738-110">在 [方案總管] 中，將您要驗證的對應及其輸入和輸出訊息結構描述加入至該專案。</span><span class="sxs-lookup"><span data-stu-id="f9738-110">To the project in Solution Explorer, add the map that you want to validate and its input and output message schemas.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="f9738-111">訊息結構描述位於底下的適當子資料夾[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f9738-111">The message schemas are located in the appropriate subfolder under the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder.</span></span> <span data-ttu-id="f9738-112">如需有關安裝的結構描述檔案的詳細資訊，請參閱 <<c0> [ 如何安裝 EDI 結構描述檔案](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550)。</span><span class="sxs-lookup"><span data-stu-id="f9738-112">For more information on installing the schema files, see [How to Install EDI Schema Files](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550).</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="f9738-113">您不必建置專案來驗證對應。</span><span class="sxs-lookup"><span data-stu-id="f9738-113">You do not have to build the project to validate a map.</span></span>  
  
2. <span data-ttu-id="f9738-114">以滑鼠右鍵按一下方案總管 中的對應，然後按一下**驗證對應**。</span><span class="sxs-lookup"><span data-stu-id="f9738-114">Right-click the map in Solution Explorer, and then click **Validate Map**.</span></span>  
  
3. <span data-ttu-id="f9738-115">確認 [輸出] 視窗中有指出作業成功的訊息。</span><span class="sxs-lookup"><span data-stu-id="f9738-115">Verify that there is a message in the Output window indicating that the operation succeeded.</span></span>  
  
4. <span data-ttu-id="f9738-116">請注意任何警告，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中已張貼**輸出**視窗。</span><span class="sxs-lookup"><span data-stu-id="f9738-116">Note any warnings that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has posted in the **Output** window.</span></span>  
  
5. <span data-ttu-id="f9738-117">在 [**輸出**] 視窗中，請注意輸出 XSLT 的路徑與名稱。</span><span class="sxs-lookup"><span data-stu-id="f9738-117">In the **Output** window, note the name and path of the output XSLT.</span></span> <span data-ttu-id="f9738-118">這個 XSL 檔案將和對應檔案同名，但是它會另外加上副檔名 XSL。</span><span class="sxs-lookup"><span data-stu-id="f9738-118">This XSL file will be given the same name as the map file, but with an XSL extension.</span></span> <span data-ttu-id="f9738-119">您可以按 CTRL，然後按一下連結，在 BizTalk 編輯器中顯示該 XSL 檔案。</span><span class="sxs-lookup"><span data-stu-id="f9738-119">You can press CTRL and click the link to display the XSL file in the BizTalk Editor.</span></span>  
  
6. <span data-ttu-id="f9738-120">在 [**輸出**] 視窗中，記下名稱和路徑的延伸模組物件 XML。</span><span class="sxs-lookup"><span data-stu-id="f9738-120">In the **Output** window, note the name and path of the extension object XML.</span></span> <span data-ttu-id="f9738-121">您可以按 CTRL，然後按一下連結，在 BizTalk 編輯器中顯示該 XSL 檔案。</span><span class="sxs-lookup"><span data-stu-id="f9738-121">You can press CTRL and click the link to display the XSL file in the BizTalk Editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9738-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9738-122">See Also</span></span>  
 [<span data-ttu-id="f9738-123">使用設計階段 XML 工具</span><span class="sxs-lookup"><span data-stu-id="f9738-123">Using Design-Time XML Tools</span></span>](../core/using-design-time-xml-tools.md)