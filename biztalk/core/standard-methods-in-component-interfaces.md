---
title: 元件介面中的標準方法 |Microsoft Docs
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
ms.openlocfilehash: eecb56f262a56e6567b44b146c631542cb1ceda6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994823"
---
# <a name="standard-methods-in-component-interfaces"></a><span data-ttu-id="06ac6-102">元件介面中的標準方法</span><span class="sxs-lookup"><span data-stu-id="06ac6-102">Standard Methods in Component Interfaces</span></span>
<span data-ttu-id="06ac6-103">元件介面的標準方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="06ac6-103">The standard methods for the component interface are as follows:</span></span>  
  
- `Create`  
  
- `Find`  
  
- `Get`  
  
- `Save`  
  
  <span data-ttu-id="06ac6-104">只有基礎元件中的那些方法才能夠使用。</span><span class="sxs-lookup"><span data-stu-id="06ac6-104">Only those methods in the underlying component are available.</span></span> <span data-ttu-id="06ac6-105">例如，假設基礎元件不包含 `Add` 功能，就無法使用 `Create`。</span><span class="sxs-lookup"><span data-stu-id="06ac6-105">For example, if the underlying component does not contain `Add` capabilities, `Create` is unavailable.</span></span>  
  
## <a name="viewing-or-changing-available-methods"></a><span data-ttu-id="06ac6-106">檢視或變更可用方法</span><span class="sxs-lookup"><span data-stu-id="06ac6-106">Viewing or Changing Available Methods</span></span>  
  
#### <a name="to-view-or-change-available-methods"></a><span data-ttu-id="06ac6-107">檢視或變更可用方法</span><span class="sxs-lookup"><span data-stu-id="06ac6-107">To view or change available methods</span></span>  
  
1.  <span data-ttu-id="06ac6-108">開啟元件介面**屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="06ac6-108">Open the component interface **Properties** dialog box.</span></span>  
  
     <span data-ttu-id="06ac6-109">![](../core/media/psadapter-46-ps-properties.gif "PSAdapter_46_PS_Properties")</span><span class="sxs-lookup"><span data-stu-id="06ac6-109">![](../core/media/psadapter-46-ps-properties.gif "PSAdapter_46_PS_Properties")</span></span>  
  
2.  <span data-ttu-id="06ac6-110">按一下 [**標準方法**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="06ac6-110">Click the **Standard Methods** tab.</span></span>  
  
3.  <span data-ttu-id="06ac6-111">選取需要的方法，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="06ac6-111">Select the desired methods, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ac6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06ac6-112">See Also</span></span>  
 <span data-ttu-id="06ac6-113">[如何建立元件介面](../core/how-to-create-component-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="06ac6-113">[How to Create Component Interfaces](../core/how-to-create-component-interfaces.md) </span></span>  
 [<span data-ttu-id="06ac6-114">附錄 C：使用元件介面</span><span class="sxs-lookup"><span data-stu-id="06ac6-114">Appendix C: Using Component Interfaces</span></span>](../core/appendix-c-using-component-interfaces.md)