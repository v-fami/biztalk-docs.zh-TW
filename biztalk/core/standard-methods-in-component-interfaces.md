---
title: 元件介面中的標準方法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- component interfaces, standard methods
- methods, viewing
- methods, component interfaces
- methods, changing
ms.assetid: 2273d946-3fc8-4b2d-a6a1-9e4f0da74d5b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f44b3977a3921d92b1f3f83dd3e744f14b5709fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278046"
---
# <a name="standard-methods-in-component-interfaces"></a><span data-ttu-id="85641-102">元件介面中的標準方法</span><span class="sxs-lookup"><span data-stu-id="85641-102">Standard Methods in Component Interfaces</span></span>
<span data-ttu-id="85641-103">元件介面的標準方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="85641-103">The standard methods for the component interface are as follows:</span></span>  
  
-   `Create`  
  
-   `Find`  
  
-   `Get`  
  
-   `Save`  
  
 <span data-ttu-id="85641-104">只有基礎元件中的那些方法才能夠使用。</span><span class="sxs-lookup"><span data-stu-id="85641-104">Only those methods in the underlying component are available.</span></span> <span data-ttu-id="85641-105">例如，假設基礎元件不包含 `Add` 功能，就無法使用 `Create`。</span><span class="sxs-lookup"><span data-stu-id="85641-105">For example, if the underlying component does not contain `Add` capabilities, `Create` is unavailable.</span></span>  
  
## <a name="viewing-or-changing-available-methods"></a><span data-ttu-id="85641-106">檢視或變更可用方法</span><span class="sxs-lookup"><span data-stu-id="85641-106">Viewing or Changing Available Methods</span></span>  
  
#### <a name="to-view-or-change-available-methods"></a><span data-ttu-id="85641-107">檢視或變更可用方法</span><span class="sxs-lookup"><span data-stu-id="85641-107">To view or change available methods</span></span>  
  
1.  <span data-ttu-id="85641-108">開啟元件介面**屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="85641-108">Open the component interface **Properties** dialog box.</span></span>  
  
     ![](../core/media/psadapter-46-ps-properties.gif "PSAdapter_46_PS_Properties")  
  
2.  <span data-ttu-id="85641-109">按一下**標準方法** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="85641-109">Click the **Standard Methods** tab.</span></span>  
  
3.  <span data-ttu-id="85641-110">選取需要的方法，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="85641-110">Select the desired methods, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85641-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85641-111">See Also</span></span>  
 <span data-ttu-id="85641-112">[如何建立元件介面](../core/how-to-create-component-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="85641-112">[How to Create Component Interfaces](../core/how-to-create-component-interfaces.md) </span></span>  
 [<span data-ttu-id="85641-113">附錄 c： 使用元件介面</span><span class="sxs-lookup"><span data-stu-id="85641-113">Appendix C: Using Component Interfaces</span></span>](../core/appendix-c-using-component-interfaces.md)