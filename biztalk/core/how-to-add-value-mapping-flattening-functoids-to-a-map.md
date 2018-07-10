---
title: 如何新增值對應 （簡維） 運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00a447c3-58d0-42ab-a5c4-417ee7800a6b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81486bedb71d69dde815f2849e0faf5b3b841f08
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981287"
---
# <a name="how-to-add-value-mapping-flattening-functoids-to-a-map"></a><span data-ttu-id="609a7-102">如何新增值對應 (簡維) 運算質至對應</span><span class="sxs-lookup"><span data-stu-id="609a7-102">How to Add Value Mapping (Flattening) Functoids to a Map</span></span>
<span data-ttu-id="609a7-103">**值對應 （簡維）** 運算質可讓您藉由將多個記錄轉換為單一記錄簡維輸入執行個體訊息部分。</span><span class="sxs-lookup"><span data-stu-id="609a7-103">The **Value Mapping (Flattening)** functoid enables you to flatten a portion of an input instance message by converting multiple records into a single record.</span></span> <span data-ttu-id="609a7-104">這是轉換 Microsoft Commerce Server 目錄中的一般作業。</span><span class="sxs-lookup"><span data-stu-id="609a7-104">This is a common operation in converting Microsoft Commerce Server catalogs.</span></span>  
  
 <span data-ttu-id="609a7-105">如需概念性資訊**值對應 （簡維）** 運算質，請參閱[值對應 （簡維） 運算質](../core/value-mapping-flattening-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="609a7-105">For conceptual information about the **Value Mapping (Flattening)** functoid, see [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md).</span></span>  
  
### <a name="to-add-the-value-mapping-flattening-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="609a7-106">新增值對應 (簡維) 運算質至對應並進行設定</span><span class="sxs-lookup"><span data-stu-id="609a7-106">To add the Value Mapping (Flattening) functoid to a map and configure it</span></span>  
  
1. <span data-ttu-id="609a7-107">具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 [**進階運算質**来選取該運算質類別索引標籤。</span><span class="sxs-lookup"><span data-stu-id="609a7-107">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
    <span data-ttu-id="609a7-108">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="609a7-108">The list of advanced functoids in the chosen category appears.</span></span>  
  
2. <span data-ttu-id="609a7-109">拖曳**值對應 （簡維）** 運算質 (![](../core/media/bts-tls-valmapflat.gif "bts_tls_valmapflat")) 從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="609a7-109">Drag the **Value Mapping (Flattening)** functoid (![](../core/media/bts-tls-valmapflat.gif "bts_tls_valmapflat")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="609a7-110">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="609a7-110">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="609a7-111">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="609a7-111">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="609a7-112">若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="609a7-112">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="609a7-113">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="609a7-113">Functoids are executed from left to right.</span></span> <span data-ttu-id="609a7-114">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="609a7-114">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3. <span data-ttu-id="609a7-115">若要建立的第一個輸入的參數**值對應 （簡維）** 運算質建立輸入的連結，藉由拖曳**值對應 （簡維）** 」 運算質，在來源中的記錄或欄位節點結構描述，或其左邊的另一個運算質具有布林資料類型，而且，將會產生輸入的值"true"或"false"。</span><span class="sxs-lookup"><span data-stu-id="609a7-115">To establish the first input parameter for the **Value Mapping (Flattening)** functoid, create an input link by dragging the **Value Mapping (Flattening)** functoid to a record or field node in the source schema, or to another functoid to its left, that has a Boolean data type and that will produce an input value of "true" or "false."</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="609a7-116">您也可以拖曳朝相反的方向，將布林值的來源拖曳**值對應 （簡維）** 運算質。</span><span class="sxs-lookup"><span data-stu-id="609a7-116">You can also drag in the opposite direction, dragging the source of the Boolean value to the **Value Mapping (Flattening)** functoid.</span></span>  
  
4. <span data-ttu-id="609a7-117">若要建立的第二個輸入的參數**值對應 （簡維）** 運算質建立輸入的連結，藉由拖曳**值對應 （簡維）** 」 運算質，在來源中的記錄或欄位節點結構描述，或藉由在來源結構描述拖曳記錄或欄位節點**值對應 （簡維）** 運算質，或是插入常數。</span><span class="sxs-lookup"><span data-stu-id="609a7-117">To establish the second input parameter for the **Value Mapping (Flattening)** functoid, create an input link by dragging the **Value Mapping (Flattening)** functoid to a record or field node in the source schema, or by dragging a record or field node in the source schema to the **Value Mapping (Flattening)** functoid, or insert a constant.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="609a7-118">第二個輸入參數**值對應 （簡維）** 運算質也可以從另一個運算質的輸出是其左邊。</span><span class="sxs-lookup"><span data-stu-id="609a7-118">The second input parameter to the **Value Mapping (Flattening)** functoid can also be from the output of another functoid to its left.</span></span> <span data-ttu-id="609a7-119">藉由將其中一個相關運算質拖曳至其他相關的運算質，以建立代表此輸入來源的連結。</span><span class="sxs-lookup"><span data-stu-id="609a7-119">Create the links the represent such sources of input by dragging one of the relevant functoids to the other relevant functoid.</span></span>  
  
5. <span data-ttu-id="609a7-120">若要使用的輸出參數**值對應 （簡維）** 運算質，建立輸出連結，藉由拖曳**值對應 （簡維）** 」 運算質的記錄或欄位與目的結構描述中，或是將目的結構描述中的記錄欄位拖曳**值對應 （簡維）** 運算質。</span><span class="sxs-lookup"><span data-stu-id="609a7-120">To use the output parameter from the **Value Mapping (Flattening)** functoid, create an output link by dragging the **Value Mapping (Flattening)** functoid to a record or field in the destination schema, or by dragging a record field in the destination schema to the **Value Mapping (Flattening)** functoid.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="609a7-121">與其他運算質的輸出一樣**值對應 （簡維）** 運算質可用來當做另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="609a7-121">As with other functoids, the output of the **Value Mapping (Flattening)** functoid can be used as input to another functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609a7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="609a7-122">See Also</span></span>  
 [<span data-ttu-id="609a7-123">將進階運算質新增至對應</span><span class="sxs-lookup"><span data-stu-id="609a7-123">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)