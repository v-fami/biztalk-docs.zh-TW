---
title: 錯誤-運算質有任何輸入 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.functiodHasNoInput
ms.assetid: ea59b902-953d-4a5f-aa28-dbaa0a017dca
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fd2626d0b3332ddbf2def47502e7b323a0ae0e7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000775"
---
# <a name="error---functoid-has-no-input"></a><span data-ttu-id="c0563-102">錯誤-運算質有沒有輸入</span><span class="sxs-lookup"><span data-stu-id="c0563-102">Error - Functoid Has No Input</span></span>
<span data-ttu-id="c0563-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="c0563-103">**Error Code**</span></span>  

 <span data-ttu-id="c0563-104">btm1012</span><span class="sxs-lookup"><span data-stu-id="c0563-104">btm1012</span></span>  

 <span data-ttu-id="c0563-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="c0563-105">**Explanation**</span></span>  

 <span data-ttu-id="c0563-106">指定的運算質至少需要一個輸入參數，卻沒有指定輸入參數。</span><span class="sxs-lookup"><span data-stu-id="c0563-106">The indicated functoid requires at least one input parameter, but no input parameters have been specified.</span></span>  

 <span data-ttu-id="c0563-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="c0563-107">**User Action**</span></span>  

 <span data-ttu-id="c0563-108">使用下列一或兩種方式，針對指定的運算質提供適當數目的輸入參數，應特別注意輸入參數的順序：</span><span class="sxs-lookup"><span data-stu-id="c0563-108">Use one or both of the following methods to provide the appropriate number of input parameters to the indicated functoid, paying particular attention to the expected order of input parameters:</span></span>  

- <span data-ttu-id="c0563-109">使用拖曳方式在指定的運算質與來源結構描述中之節點或其他運算質之輸出間建立連結，這些節點位於指定運算質左邊的地圖格線頁中。</span><span class="sxs-lookup"><span data-stu-id="c0563-109">Drag to create links between the indicated functoid and either nodes in the source schema or the output of other functoids that are located to the left of the indicated functoid in a map grid page.</span></span>  

- <span data-ttu-id="c0563-110">選取指定的運算質，然後按一下省略符號 (**...**) 按鈕相關聯**輸入參數**屬性，在 Microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後設定並重新安排輸入參數順序**設定\<運算質\>運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0563-110">Select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then configure and rearrange the order of the input parameters in the **Configure \<Functoid\> Functoid** dialog box.</span></span> <span data-ttu-id="c0563-111">您可以在此對話方塊中建立常數輸入參數、賦予這些參數值，並使用相對於其他輸入參數的順序排列這些參數。</span><span class="sxs-lookup"><span data-stu-id="c0563-111">Constant input parameters can be created, given values, and put in the proper order relative to the other input parameters in this dialog box.</span></span>
