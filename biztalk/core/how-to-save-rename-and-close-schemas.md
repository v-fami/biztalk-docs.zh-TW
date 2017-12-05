---
title: "如何儲存、 重新命名，並關閉結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65e15d9e-40ae-4850-9c13-88033cb3b3bb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a295bacf263e3ecad9a9aa081fb0d5d3be2f635
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-save-rename-and-close-schemas"></a><span data-ttu-id="a7df7-102">如何儲存、重新命名及關閉結構描述</span><span class="sxs-lookup"><span data-stu-id="a7df7-102">How to Save, Rename, and Close Schemas</span></span>
<span data-ttu-id="a7df7-103">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，結構描述為 XML 結構描述定義 (XSD) 語言檔案，以 .xsd 副檔名存在檔案系統上。</span><span class="sxs-lookup"><span data-stu-id="a7df7-103">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], schemas are XML Schema definition (XSD) language files and reside on the file system with .xsd extensions.</span></span> <span data-ttu-id="a7df7-104">當您使用「BizTalk 編輯器」開發結構描述時，需要定期儲存和關閉結構描述檔案，偶爾可能需要重新命名這些檔案。</span><span class="sxs-lookup"><span data-stu-id="a7df7-104">When you use BizTalk Editor to develop schemas, you will routinely need to save and close schema files, and occasionally you may need to rename them.</span></span> <span data-ttu-id="a7df7-105">本主題描述執行這些基本作業所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="a7df7-105">This topic describes the steps required to perform these basic operations.</span></span>  
  
### <a name="to-save-a-schema"></a><span data-ttu-id="a7df7-106">儲存結構描述</span><span class="sxs-lookup"><span data-stu-id="a7df7-106">To save a schema</span></span>  
  
1.  <span data-ttu-id="a7df7-107">若有必要，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中主要編輯視窗的頂端按一下適當的索引標籤，為您要儲存的結構描述啟動「BizTalk 編輯器」。</span><span class="sxs-lookup"><span data-stu-id="a7df7-107">If necessary, activate BizTalk Editor for the schema to be saved by clicking the appropriate tab at the top of the main editing window in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="a7df7-108">在**檔案**功能表上，按一下 **儲存*\<名稱的結構描述\>***。</span><span class="sxs-lookup"><span data-stu-id="a7df7-108">On the **File** menu, click **Save *\<Name of Schema\>***.</span></span>  
  
     <span data-ttu-id="a7df7-109">若結構描述之前有未儲存的變更，則其顯示在主要編輯視窗頂端索引標籤中的名稱結尾將不再有星號 (*) 以指示未儲存的變更。</span><span class="sxs-lookup"><span data-stu-id="a7df7-109">If the schema had unsaved changes, its name as displayed on the tab at the top of the main editing window will no longer end with an asterisk (*), which is used to indicate unsaved changes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7df7-110">您可以按一下以儲存新的名稱下的結構描述**儲存*\<名稱的結構描述\>*為**上**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="a7df7-110">You can save the schema under a new name by clicking **Save *\<Name of Schema\>* As** on the **File** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7df7-111">您可以將結構描述儲存為部分儲存在專案中的所有已變更的項目，依序按一下**全部儲存**上**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="a7df7-111">You can save the schema as part of saving all changed items in the project by clicking **Save All** on the **File** menu.</span></span>  
  
#### <a name="to-rename-a-schema"></a><span data-ttu-id="a7df7-112">重新命名結構描述</span><span class="sxs-lookup"><span data-stu-id="a7df7-112">To rename a schema</span></span>  
  
1.  <span data-ttu-id="a7df7-113">在 方案總管 中，以滑鼠右鍵按一下您想要重新命名，然後按一下 結構描述**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="a7df7-113">In Solution Explorer, right-click the schema that you want to rename, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="a7df7-114">在 [方案總管] 中結構描述所在位置出現的 [編輯] 方塊中，輸入結構描述的新名稱，或改變它的現有名稱，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="a7df7-114">In the editing box that appears in the location of the schema in Solution Explorer, type the new name for the schema, or alter its existing name, and then press ENTER.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7df7-115">您也可能想要變更**型別名稱**當您重新命名的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a7df7-115">You may also want to change the **Type Name** of the schema when you rename.</span></span> <span data-ttu-id="a7df7-116">您變更**型別名稱**選取**結構描述**在 方案總管 並輸入新的名稱在**型別名稱**屬性 視窗中。</span><span class="sxs-lookup"><span data-stu-id="a7df7-116">You change the **Type Name** by selecting the **schema** in the solution explorer and entering the new name in the **Type Name** in the Properties window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a7df7-117">您不能重新命名任何一個已經用於其他結構描述的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a7df7-117">You should not rename any schema that is being used by another schema.</span></span> <span data-ttu-id="a7df7-118">這包括已經被其他結構描述包含、匯入或重新定義的結構描述，以及已經為其建立升級的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="a7df7-118">This includes schemas that have been included, imported, or redefined by other schemas, as well as property schemas for which promotions have already been established.</span></span> <span data-ttu-id="a7df7-119">若這麼做，所使用的結構描述將找不到重新命名的結構描述，因為它所包含的名稱已經不正確。</span><span class="sxs-lookup"><span data-stu-id="a7df7-119">If you do so, the schema that is being used will not be able to find the renamed schema because the name it contains will no longer be accurate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7df7-120">專案成員檔案 (如結構描述檔案) 的特定名稱選擇可能由於與 C# 保留字以及 .NET Framework 類型和命名空間名稱 (如 "System") 發生衝突，之後會導致編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="a7df7-120">Certain name choices for project member files, such as schema files, can cause compilation errors later on due to conflicts with C# reserved words and.NET Framework type and namespace names (such as "System").</span></span> <span data-ttu-id="a7df7-121">結構描述的範例包括 schema.xsd、XmlContent 及 RootNodes。</span><span class="sxs-lookup"><span data-stu-id="a7df7-121">Examples for schemas include schema.xsd, XmlContent, and RootNodes.</span></span> <span data-ttu-id="a7df7-122">這是因為**型別名稱**屬性預設為基底 （不含副檔名） 部分**Filename**屬性。</span><span class="sxs-lookup"><span data-stu-id="a7df7-122">This is because the **Type Name** property defaults to the base (non-extension) portion of the **Filename** property.</span></span> <span data-ttu-id="a7df7-123">您可以藉由明確地變更的值解決這種類型的編譯錯誤**型別名稱**為不衝突的屬性。</span><span class="sxs-lookup"><span data-stu-id="a7df7-123">You can work around this type of compilation error by explicitly changing the value of the **Type Name** property to something that does not conflict.</span></span>  
  
#### <a name="to-close-a-schema"></a><span data-ttu-id="a7df7-124">關閉結構描述</span><span class="sxs-lookup"><span data-stu-id="a7df7-124">To close a schema</span></span>  
  
1.  <span data-ttu-id="a7df7-125">若有必要，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中主要編輯視窗的頂端按一下適當的索引標籤，為您要關閉的結構描述啟動「BizTalk 編輯器」。</span><span class="sxs-lookup"><span data-stu-id="a7df7-125">If necessary, activate BizTalk Editor for the schema to be closed by clicking the appropriate tab at the top of the main editing window in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="a7df7-126">在 **[檔案]** 功能表上按一下 **[關閉]**。</span><span class="sxs-lookup"><span data-stu-id="a7df7-126">On the **File** menu, click **Close**.</span></span>  
  
     <span data-ttu-id="a7df7-127">會關閉已經關閉的結構描述之「BizTalk 編輯器」。</span><span class="sxs-lookup"><span data-stu-id="a7df7-127">BizTalk Editor closes for the schema that has been closed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7df7-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="a7df7-128">See Also</span></span>  
 [<span data-ttu-id="a7df7-129">管理專案中的結構描述</span><span class="sxs-lookup"><span data-stu-id="a7df7-129">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)