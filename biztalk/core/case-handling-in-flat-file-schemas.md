---
title: 大小寫處理一般檔案結構描述中的 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9f2b56d2-03fa-41e9-ae28-3275b404d4db
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2312f00a6dab18fa92c0fed05c5c9fa182d500f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231134"
---
# <a name="case-handling-in-flat-file-schemas"></a><span data-ttu-id="9b1e4-102">在 一般檔案結構描述中處理的案例</span><span class="sxs-lookup"><span data-stu-id="9b1e4-102">Case Handling in Flat File Schemas</span></span>

## <a name="overview"></a><span data-ttu-id="9b1e4-103">概觀</span><span class="sxs-lookup"><span data-stu-id="9b1e4-103">Overview</span></span>
<span data-ttu-id="9b1e4-104">您可以使用**案例**屬性來從其對等的 XML 格式進行轉譯時執行的一般檔案資料的大小寫轉換。</span><span class="sxs-lookup"><span data-stu-id="9b1e4-104">You can use the **Case** property to perform case conversion of flat file data when being translated from its equivalent XML format.</span></span> <span data-ttu-id="9b1e4-105">當一般檔案組合器將 XML 訊息轉譯成其相等的一般檔案格式，而**案例**屬性會設為**大寫**或**小寫**，所有資料由對應的結構描述將會轉換成大寫或小寫，分別在轉譯過程。</span><span class="sxs-lookup"><span data-stu-id="9b1e4-105">When the flat file assembler translates an XML message into its equivalent flat file format, and the **Case** property is set to either **Uppercase** or **Lowercase**, all data governed by the corresponding schema will be converted to uppercase or lowercase, respectively, during the translation.</span></span>  
  
 <span data-ttu-id="9b1e4-106">當**案例**屬性設定為 **（預設）**，任何大小寫轉換會執行。</span><span class="sxs-lookup"><span data-stu-id="9b1e4-106">When the **Case** property is set to **(Default)**, no case conversion is performed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b1e4-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b1e4-107">See Also</span></span>  
 <span data-ttu-id="9b1e4-108">**考量當建立一般檔案訊息結構描述**和**案例 （一般檔案結構描述中的節點屬性）**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="9b1e4-108">**Considerations When Creating Flat File Message Schemas** and **Case (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>