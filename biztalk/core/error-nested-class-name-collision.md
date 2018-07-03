---
title: 錯誤-巢狀的類別名稱衝突 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.nestedClassNameCollision
ms.assetid: dd636d25-d0c1-41be-a2ba-b38ea97b973d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 856841093c37848924dc6e9b6d160186e03ad304
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003327"
---
# <a name="error---nested-class-name-collision"></a><span data-ttu-id="a4dcc-102">錯誤-巢狀的類別名稱衝突</span><span class="sxs-lookup"><span data-stu-id="a4dcc-102">Error - Nested Class Name Collision</span></span>
<span data-ttu-id="a4dcc-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="a4dcc-103">**Error Code**</span></span>  

 <span data-ttu-id="a4dcc-104">BEC2017</span><span class="sxs-lookup"><span data-stu-id="a4dcc-104">BEC2017</span></span>  

 <span data-ttu-id="a4dcc-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="a4dcc-105">**Explanation**</span></span>  

 <span data-ttu-id="a4dcc-106">**型別名稱**此結構描述的屬性找不到要與相同**RootNode TypeName**的其中一個結構描述中根節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="a4dcc-106">The **Type Name** property of this schema was found to be the same as the **RootNode TypeName** property of one of the root nodes in the schema.</span></span> <span data-ttu-id="a4dcc-107">C# 不允許具有相同名稱的巢狀類別；因此，此情況會引起錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4dcc-107">C# disallows nested classes with the same names; therefore this condition causes an error.</span></span>  

 <span data-ttu-id="a4dcc-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="a4dcc-108">**User Action**</span></span>  

 <span data-ttu-id="a4dcc-109">您必須變更一個或兩個相關的屬性值，以避免名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="a4dcc-109">You must change one or both of the relevant property values so that you avoid the name collision.</span></span> <span data-ttu-id="a4dcc-110">您可以執行下列動作之一：</span><span class="sxs-lookup"><span data-stu-id="a4dcc-110">Either:</span></span>  

- <span data-ttu-id="a4dcc-111">在 Microsoft 中選取相關結構描述檔案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，然後在 [屬性] 視窗中變更**型別名稱**屬性唯一有效的值。</span><span class="sxs-lookup"><span data-stu-id="a4dcc-111">Select the relevant schema file in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, and then in the Properties window, change the **Type Name** property to a unique valid value.</span></span>  

   <span data-ttu-id="a4dcc-112">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="a4dcc-112">\- or -</span></span>  

- <span data-ttu-id="a4dcc-113">選取指定的根節點，然後在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性視窗中，變更**RootNode TypeName**屬性唯一有效的值。</span><span class="sxs-lookup"><span data-stu-id="a4dcc-113">Select the indicated root node, and then in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, change the **RootNode TypeName** property to a unique valid value.</span></span>
