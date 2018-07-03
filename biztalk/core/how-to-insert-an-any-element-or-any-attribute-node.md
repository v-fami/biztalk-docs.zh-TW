---
title: 如何插入 Any 項目或 Any 屬性節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4cbfdc04-6c83-4639-82de-169b6f009a2e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bce55126fe800841aef325f22de0afe62e03cec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021073"
---
# <a name="how-to-insert-an-any-element-or-any-attribute-node"></a><span data-ttu-id="47035-102">如何插入 Any 項目或 Any 屬性節點</span><span class="sxs-lookup"><span data-stu-id="47035-102">How to Insert an Any Element or Any Attribute Node</span></span>
<span data-ttu-id="47035-103">BizTalk 編輯器支援兩種 any 節點： **Any 項目**並**Any 屬性**。</span><span class="sxs-lookup"><span data-stu-id="47035-103">BizTalk Editor supports two types of any nodes: **Any Element** and **Any Attribute**.</span></span> <span data-ttu-id="47035-104">這些節點可讓您建立您的結構描述對應至您不知道什麼項目或屬性會出現在對應的執行個體訊息中位置的位置。</span><span class="sxs-lookup"><span data-stu-id="47035-104">These nodes allow you to create locations within your schema that correspond to locations within the corresponding instance messages where you do not know what elements or attributes will appear.</span></span> <span data-ttu-id="47035-105">如需有關處理執行個體訊息時如何解譯這些節點的詳細資訊，請直接參考網站上 XML 結構描述定義 (XSD) 語言的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="47035-105">For detailed information about how these nodes are interpreted when processing instance messages, refer directly to information about the XML Schema definition (XSD) language on the Web.</span></span> <span data-ttu-id="47035-106">如需這項資訊的連結，請參閱[網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。</span><span class="sxs-lookup"><span data-stu-id="47035-106">For links to this information, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  

## <a name="insert-an-any-element-node-or-an-any-attribute-node"></a><span data-ttu-id="47035-107">插入 Any 項目或 Any 屬性節點</span><span class="sxs-lookup"><span data-stu-id="47035-107">Insert an Any Element node or an Any Attribute node</span></span>  

1.  <span data-ttu-id="47035-108">在結構描述樹狀結構檢視中，選取**記錄**想要插入的節點**Any 項目**節點或**Any 屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="47035-108">In the schema tree view, select the **Record** node into which you want to insert the **Any Element** node or the **Any Attribute** node.</span></span>  

2.  <span data-ttu-id="47035-109">上**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下**Any 項目**或是**Any 屬性**視需要。</span><span class="sxs-lookup"><span data-stu-id="47035-109">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Any Element** or **Any Attribute**, as appropriate.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="47035-110">設定**Process Contents**屬性設**Lax** for **Any 項目**或是**Any 屬性**節點可能無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="47035-110">Setting the **Process Contents** property to **Lax** for **Any Element** or **Any Attribute** nodes may not work correctly.</span></span> <span data-ttu-id="47035-111">通過驗證**Any 項目**或是**Any 屬性**節點，將屬性設定為**略過**。</span><span class="sxs-lookup"><span data-stu-id="47035-111">To pass validation on **Any Element** or **Any Attribute** nodes, set the property to **Skip**.</span></span>  <span data-ttu-id="47035-112">這個屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="47035-112">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
> 
>  <span data-ttu-id="47035-113">若要建立包含地圖**Any 項目**或**Any 屬性**節點，您必須使用[大量複製](mass-copy-functoid.md)運算質或[指令碼處理](scripting-functoid.md)運算質 （與內嵌 XSLT 或內嵌 XSLT 呼叫範本） 來執行這類節點中，對應，或直接不對應這些節點。</span><span class="sxs-lookup"><span data-stu-id="47035-113">To create a map that contains **Any Element** or **Any Attribute** nodes, you must use either the [Mass Copy](mass-copy-functoid.md) functoid or the [Scripting](scripting-functoid.md) functoid (with Inline XSLT or Inline XSLT Call Template) to perform the mapping for such nodes, or simply not map those nodes.</span></span>  

## <a name="see-also"></a><span data-ttu-id="47035-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47035-114">See Also</span></span>  
- [<span data-ttu-id="47035-115">將節點插入至結構描述</span><span class="sxs-lookup"><span data-stu-id="47035-115">Inserting Nodes into a Schema</span></span>](../core/inserting-nodes-into-a-schema.md)
- <span data-ttu-id="47035-116">**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="47035-116">**Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
