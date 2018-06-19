---
title: 判斷提示運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e91dac06-f909-4fb2-8c87-828a3dfe2c27
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03237c27e0e35642be197b549c8b0102d9350702
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230310"
---
# <a name="assert-functoid"></a><span data-ttu-id="605ad-102">判斷提示運算質</span><span class="sxs-lookup"><span data-stu-id="605ad-102">Assert Functoid</span></span>

## <a name="overview"></a><span data-ttu-id="605ad-103">概觀</span><span class="sxs-lookup"><span data-stu-id="605ad-103">Overview</span></span>
<span data-ttu-id="605ad-104">**Assert**運算質輸出的字串值或擲回例外狀況的布林值為基礎。</span><span class="sxs-lookup"><span data-stu-id="605ad-104">The **Assert** functoid either outputs a string value or throws an exception based on a Boolean value.</span></span> <span data-ttu-id="605ad-105">如果您將此運算質結合的一或多個**邏輯**運算質，您可以有效地測試對應中條件的相關假設。</span><span class="sxs-lookup"><span data-stu-id="605ad-105">If you combine this functoid with one or more of the **Logical** functoids, you can effectively test assumptions about conditions in your map.</span></span> <span data-ttu-id="605ad-106">例如，如果您有對應預期訂單訂單金額絕對不會超過特定閾值時，您可以測試訂單值使用**Greater Than**運算質，然後連接到**Assert**運算質。</span><span class="sxs-lookup"><span data-stu-id="605ad-106">For example, if you have a map that expects purchase order amounts never to exceed a certain threshold, you can test the purchase order value by using the **Greater Than** functoid and then connect it to the **Assert** functoid.</span></span> <span data-ttu-id="605ad-107">如果 「 邏輯 」 運算質傳回**True**、 **Assert**運算質將會擲回例外狀況，使用您提供的字串。</span><span class="sxs-lookup"><span data-stu-id="605ad-107">If the logical functoid returns **True**, the **Assert** functoid will throw an exception using a string you provide.</span></span>  
  
 <span data-ttu-id="605ad-108">![判斷提示運算質](../core/media/assertfunctoid.gif "AssertFunctoid")</span><span class="sxs-lookup"><span data-stu-id="605ad-108">![Assert Functoid](../core/media/assertfunctoid.gif "AssertFunctoid")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="605ad-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="605ad-109">See Also</span></span>  
 <span data-ttu-id="605ad-110">**判斷提示運算質參考**和**邏輯運算質參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="605ad-110">**Assert Functoid Reference** and **Logical Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>