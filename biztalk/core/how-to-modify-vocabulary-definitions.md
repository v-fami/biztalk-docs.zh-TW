---
title: 如何修改詞彙定義 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vocabularies, facts
- modifying, vocabularies
- vocabularies, definitions
- vocabularies, modifying
ms.assetid: 866bb9b9-34e1-4a05-a84e-540c7f7fae3b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6aa62ebf0adda5798824003fa25cf1ed07b62932
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254166"
---
# <a name="how-to-modify-vocabulary-definitions"></a><span data-ttu-id="2ed9a-102">如何修改詞彙定義</span><span class="sxs-lookup"><span data-stu-id="2ed9a-102">How to Modify Vocabulary Definitions</span></span>
<span data-ttu-id="2ed9a-103">您可以使用「詞彙定義精靈」變更顯示名稱或變更與顯示名稱關聯的繫結，以修改未發佈的詞彙版本中的詞彙定義。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-103">You can modify a vocabulary definition in an unpublished version of a vocabulary by using the Vocabulary Definition Wizard to change the display name or to change the binding associated with the display name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ed9a-104">並非所有項目均可修改。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-104">Not all elements can be modified.</span></span>  
  
 <span data-ttu-id="2ed9a-105">本主題包含下列工作的程序：</span><span class="sxs-lookup"><span data-stu-id="2ed9a-105">This topic contains procedures for the following tasks:</span></span>  
  
-   <span data-ttu-id="2ed9a-106">修改詞彙定義</span><span class="sxs-lookup"><span data-stu-id="2ed9a-106">To modify a vocabulary definition</span></span>  
  
-   <span data-ttu-id="2ed9a-107">新增事實到詞彙或詞彙定義</span><span class="sxs-lookup"><span data-stu-id="2ed9a-107">To add a fact to a vocabulary or vocabulary definition</span></span>  
  
### <a name="to-modify-a-vocabulary-definition"></a><span data-ttu-id="2ed9a-108">修改詞彙定義</span><span class="sxs-lookup"><span data-stu-id="2ed9a-108">To modify a vocabulary definition</span></span>  
  
1.  <span data-ttu-id="2ed9a-109">詞彙定義，以滑鼠右鍵按一下，然後按一下 **修改**。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-109">Right-click the vocabulary definition, and then click **Modify**.</span></span>  
  
2.  <span data-ttu-id="2ed9a-110">使用「詞彙定義精靈」以建立所需的新詞彙定義。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-110">Use the Vocabulary Definition Wizard as you would to create a new vocabulary definition.</span></span>  
  
### <a name="to-add-a-fact-to-a-vocabulary-or-vocabulary-definition"></a><span data-ttu-id="2ed9a-111">新增事實到詞彙或詞彙定義</span><span class="sxs-lookup"><span data-stu-id="2ed9a-111">To add a fact to a vocabulary or vocabulary definition</span></span>  
  
1.  <span data-ttu-id="2ed9a-112">在 [事實總管] 視窗中，按一下**詞彙**索引標籤，然後選取您想要更新的未發佈的詞彙版本。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-112">In the Facts Explorer window, click the **Vocabularies** tab, and select the unpublished vocabulary version that you want to update.</span></span>  
  
2.  <span data-ttu-id="2ed9a-113">按一下**資料庫**， **XML 結構描述**，或 **.NET 類別**。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-113">Click **Databases**, **XML Schemas**, or **.NET Classes**.</span></span>  
  
3.  <span data-ttu-id="2ed9a-114">巡覽資料來源階層到您需要的事實。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-114">Navigate through the data source hierarchy to the fact you want.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ed9a-115">事實可以是資料庫資料表或資料庫資料表資料行、XML 文件項目或屬性，或 .NET 類別或類別成員。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-115">The fact can be a database table or database table column, an XML document element or attribute, or a .NET class or class member.</span></span>  
  
4.  <span data-ttu-id="2ed9a-116">按一下事實並按住滑鼠鍵。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-116">Click the fact and hold down the mouse button.</span></span>  
  
5.  <span data-ttu-id="2ed9a-117">拖曳事實**詞彙** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-117">Drag the fact over the **Vocabularies** tab.</span></span>  
  
     <span data-ttu-id="2ed9a-118">**詞彙**索引標籤隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-118">The **Vocabularies** tab opens.</span></span>  
  
6.  <span data-ttu-id="2ed9a-119">拖曳事實到您要修改的詞彙版本。</span><span class="sxs-lookup"><span data-stu-id="2ed9a-119">Drag the fact to the vocabulary version you want to modify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed9a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ed9a-120">See Also</span></span>  
 [<span data-ttu-id="2ed9a-121">如何建立詞彙定義</span><span class="sxs-lookup"><span data-stu-id="2ed9a-121">How to Create Vocabulary Definitions</span></span>](../core/how-to-create-vocabulary-definitions.md)