---
title: 自訂 XSLT |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- functoid types, Scripting
- maps, customizing
- functoid types, Looping
- maps, extending
- XSLT, maps
- Scripting functoids
- maps, XSLT
- customizing, maps
- maps, replacing
ms.assetid: e254d16d-4d16-4c23-a3ed-cc98eea9939a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4adf2abe438b3972419184b1297eaff5578c5bde
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238342"
---
# <a name="custom-xslt"></a><span data-ttu-id="e4cb1-102">自訂 XSLT</span><span class="sxs-lookup"><span data-stu-id="e4cb1-102">Custom XSLT</span></span>
<span data-ttu-id="e4cb1-103">若您熟悉「可延伸樣式表語言轉換」(XSLT) 程式碼，可以用它來自訂、延伸或取代 BizTalk 對應。</span><span class="sxs-lookup"><span data-stu-id="e4cb1-103">If you are familiar with Extensible Stylesheet Language Transformations (XSLT) code, you can use it to customize, extend, or replace BizTalk maps.</span></span> <span data-ttu-id="e4cb1-104">若要使用 XSLT 最簡單的方法是使用**指令碼處理**運算質。</span><span class="sxs-lookup"><span data-stu-id="e4cb1-104">The simplest way to use XSLT is with the **Scripting** functoid.</span></span> <span data-ttu-id="e4cb1-105">**指令碼處理**運算質接受的許多指令碼。啟用.NET 的語言，包括 XSLT。</span><span class="sxs-lookup"><span data-stu-id="e4cb1-105">The **Scripting** functoid accepts scripts in many .NET-enabled languages, including XSLT.</span></span> <span data-ttu-id="e4cb1-106">如需有關使用 XSLT 與**指令碼處理**運算質，請參閱[指令碼使用的內嵌 XSLT 與 XSLT 呼叫範本](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="e4cb1-106">For more information about using XSLT with the **Scripting** functoid, see [Scripting Using Inline XSLT and XSLT Call Templates](../core/scripting-using-inline-xslt-and-xslt-call-templates.md).</span></span>  
  
 <span data-ttu-id="e4cb1-107">若您擁有已用來將某個執行個體訊息轉換成另一個執行個體訊息的 XSLT 程式碼，則可以直接使用該程式碼取代 BizTalk 對應。</span><span class="sxs-lookup"><span data-stu-id="e4cb1-107">If you have XSLT code that you have been using to convert one instance message into another, you can use that code directly in place of a BizTalk map.</span></span> <span data-ttu-id="e4cb1-108">如需資訊取代 BizTalk 對應以您的 XSLT 程式碼，請參閱[如何建立不含對應](../core/how-to-create-a-map-without-maps.md)。</span><span class="sxs-lookup"><span data-stu-id="e4cb1-108">For information about replacing BizTalk maps with your XSLT code, see [How to Create a Map without Maps](../core/how-to-create-a-map-without-maps.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4cb1-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4cb1-109">See Also</span></span>  
 <span data-ttu-id="e4cb1-110">[對應](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="e4cb1-110">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="e4cb1-111">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="e4cb1-111">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)