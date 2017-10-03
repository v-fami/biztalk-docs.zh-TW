---
title: "如何建立不含對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 520ec44f-5aca-4271-8835-b8e784214061
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81be2591c1d8f20f5b8dd01cf01c03e8daed9c9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-map-without-maps"></a><span data-ttu-id="bbdee-102">如何建立不含對應的對應</span><span class="sxs-lookup"><span data-stu-id="bbdee-102">How to Create a Map without Maps</span></span>
<span data-ttu-id="bbdee-103">若您擁有已經用來轉換執行個體訊息的 XSLT 程式碼，則可直接使用該程式碼而不需建立對應。</span><span class="sxs-lookup"><span data-stu-id="bbdee-103">If you have XSLT code you have been using to convert instance messages, you can use that code directly instead of creating a map.</span></span>  
  
 <span data-ttu-id="bbdee-104">使用您的 XSLT 程式碼包含建立空的對應，並設定其**自訂 XSLT 路徑**格線屬性。</span><span class="sxs-lookup"><span data-stu-id="bbdee-104">Using your XSLT code involves creating an empty map and setting its **Custom XSLT Path** grid property.</span></span> <span data-ttu-id="bbdee-105">如果您的 XSLT 程式碼使用外部.NET 組件，您也需要建立自訂延伸模組 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="bbdee-105">If your XSLT code uses external .NET assemblies, you also need to create a custom extension XML file.</span></span> <span data-ttu-id="bbdee-106">自訂延伸模組 XML 檔案結構的相關資訊，請參閱**自訂延伸模組 XML （格線屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdee-106">For information about the structure of a custom extension XML file, see the **Custom Extension XML (Grid Property)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="use-custom-xslt-code-in-place-of-a-map"></a><span data-ttu-id="bbdee-107">使用自訂 XSLT 程式碼取代對應</span><span class="sxs-lookup"><span data-stu-id="bbdee-107">Use custom XSLT code in place of a map</span></span>  
  
1.  <span data-ttu-id="bbdee-108">在專案中建立空白 BizTalk 對應，並設定來源與目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="bbdee-108">Create an empty BizTalk map in your project and set the source and destination schemas.</span></span>  
  
     <span data-ttu-id="bbdee-109">如需建立對應及設定結構描述資訊，請參閱[建立對應](../core/creating-maps.md)。</span><span class="sxs-lookup"><span data-stu-id="bbdee-109">For information about creating the map and setting the schemas, see [Creating Maps](../core/creating-maps.md).</span></span>  
  
2.  <span data-ttu-id="bbdee-110">在 [格線] 檢視中，按一下對應工具格線。</span><span class="sxs-lookup"><span data-stu-id="bbdee-110">In the Grid view, click the mapper grid.</span></span>  
  
     <span data-ttu-id="bbdee-111">[屬性] 視窗會顯示**方格**屬性。</span><span class="sxs-lookup"><span data-stu-id="bbdee-111">The Properties window shows the **Grid** properties.</span></span>  
  
3.  <span data-ttu-id="bbdee-112">在 [屬性] 視窗中，選取**自訂 XSLT 路徑**按一下省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bbdee-112">In the Properties window, select **Custom XSLT Path** and click the ellipsis (**…**) button.</span></span>  
  
4.  <span data-ttu-id="bbdee-113">在**開啟**對話方塊，瀏覽至檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="bbdee-113">In the **Open** dialog box, navigate to the file and click **Open**.</span></span>  
  
     <span data-ttu-id="bbdee-114">**自訂 XSLT 路徑**屬性設定。</span><span class="sxs-lookup"><span data-stu-id="bbdee-114">The **Custom XSLT Path** property is set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbdee-115">[BizTalk 對應工具] 僅支援 XSLT 1.0。</span><span class="sxs-lookup"><span data-stu-id="bbdee-115">BizTalk Mapper supports XSLT 1.0 only.</span></span> <span data-ttu-id="bbdee-116">在 [BizTalk 對應工具] 中不支援使用 XSLT 2.0。</span><span class="sxs-lookup"><span data-stu-id="bbdee-116">Using XSLT 2.0 in BizTalk Mapper is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbdee-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbdee-117">See Also</span></span>  
 <span data-ttu-id="bbdee-118">[關於對應](../core/about-maps.md) </span><span class="sxs-lookup"><span data-stu-id="bbdee-118">[About Maps](../core/about-maps.md) </span></span>  
 <span data-ttu-id="bbdee-119">[使用內嵌 XSLT 與 XSLT 呼叫範本指令碼](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span><span class="sxs-lookup"><span data-stu-id="bbdee-119">[Scripting Using Inline XSLT and XSLT Call Templates](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span></span>  
 [<span data-ttu-id="bbdee-120">自訂 XSLT</span><span class="sxs-lookup"><span data-stu-id="bbdee-120">Custom XSLT</span></span>](../core/custom-xslt.md)   