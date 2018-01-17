---
title: "如何判斷 Web 訊息部分類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web messages, message types
- Web services, Web messages
- Web messages, parts
ms.assetid: bdd1f604-ec35-41e3-b5a8-1e0ad0193eff
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6102e39eb38e919c68405ae18bebde0b46c0b053
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-determine-a-web-message-part-type"></a><span data-ttu-id="b5d29-102">如何判斷 Web 訊息部分類型</span><span class="sxs-lookup"><span data-stu-id="b5d29-102">How to Determine a Web Message Part Type</span></span>
<span data-ttu-id="b5d29-103">您可以使用指定之 Web 訊息類型的 [屬性] 視窗，判斷 Web 訊息部分類型是基本 .NET 類型還是結構描述類型。</span><span class="sxs-lookup"><span data-stu-id="b5d29-103">You can determine if a Web message part type is a primitive .NET type or a schema type by using the Properties window for a given Web message type.</span></span>  
  
### <a name="to-determine-a-web-message-part-type"></a><span data-ttu-id="b5d29-104">若要判斷 Web 訊息部分類型</span><span class="sxs-lookup"><span data-stu-id="b5d29-104">To determine a Web message part type</span></span>  
  
1.  <span data-ttu-id="b5d29-105">與協調流程開啟時，在 **檢視**  功能表上，按一下  **其他視窗**,，然後按一下  **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="b5d29-105">With an orchestration open, on the **View** menu, click **Other Windows**,and then click **Orchestration View**.</span></span>  
  
2.  <span data-ttu-id="b5d29-106">展開 **多部分訊息類型** 節點，然後展開 Web 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="b5d29-106">Expand the **Multi-part Message Types** node, and then expand a Web message type.</span></span>  
  
3.  <span data-ttu-id="b5d29-107">選取訊息部分。</span><span class="sxs-lookup"><span data-stu-id="b5d29-107">Select a message part.</span></span>  
  
     <span data-ttu-id="b5d29-108">開頭為 Web 訊息部分簽章 **\<*專案預設命名空間*\>。\<*Web 參考名稱*\>。參考。\<*結構描述根*\>** 是結構描述型別。</span><span class="sxs-lookup"><span data-stu-id="b5d29-108">A Web message part signature that begins as **\<*project default namespace*\>.\<*Web reference name*\>.Reference.\<*schema root*\>** is a schema type.</span></span> <span data-ttu-id="b5d29-109"> **\<*結構描述根*\>** 類型的一部分是建構 Web 訊息部分的 Web 參考結構描述的根項目。</span><span class="sxs-lookup"><span data-stu-id="b5d29-109">The **\<*schema root*\>** part of the type is the root element of the Web reference schema that constructs the Web message part.</span></span> <span data-ttu-id="b5d29-110">否則，訊息部分簽章是基本.NET 類型例如**System.String**或**System.Int32**。</span><span class="sxs-lookup"><span data-stu-id="b5d29-110">Otherwise, the message part signature is a primitive .NET type such as **System.String** or **System.Int32**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d29-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5d29-111">See Also</span></span>  
 [<span data-ttu-id="b5d29-112">建構 Web 訊息</span><span class="sxs-lookup"><span data-stu-id="b5d29-112">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)