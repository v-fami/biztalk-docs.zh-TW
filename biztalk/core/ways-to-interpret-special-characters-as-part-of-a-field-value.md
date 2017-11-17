---
title: "將特殊字元解譯為欄位值的一部分的方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e19a202-4e4d-42e0-ba1e-fddc52792b21
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b96a3c7502a47541e8e58ec3df3eccf6098e3abc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ways-to-interpret-special-characters-as-part-of-a-field-value"></a><span data-ttu-id="389e4-102">如何將特殊字元解譯為欄位值的一部分</span><span class="sxs-lookup"><span data-stu-id="389e4-102">Ways to Interpret Special Characters as Part of a Field Value</span></span>
<span data-ttu-id="389e4-103">位置及分隔記錄中的欄位可以包含不同類型的特殊字元，例如填補、換行及逸出字元。</span><span class="sxs-lookup"><span data-stu-id="389e4-103">Fields in both positional and delimited records can contain special characters of different types, such as pad, wrap, and escape characters.</span></span> <span data-ttu-id="389e4-104">分隔記錄還能包含一或多個不同的分隔符號字元，用來區隔記錄中的欄位或用來區隔不同的記錄。</span><span class="sxs-lookup"><span data-stu-id="389e4-104">Delimited records can also contain one or more different delimiter characters that are used to separate the fields within a record and one record from another record.</span></span> <span data-ttu-id="389e4-105">有時候這些字元本身就是資料的一部分，而不應解譯為上述狀況的特殊字元。</span><span class="sxs-lookup"><span data-stu-id="389e4-105">Sometimes these special characters are part of the data itself, and are not meant to be interpreted as special in those cases.</span></span>  
  
 <span data-ttu-id="389e4-106">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所使用的一般檔案結構描述支援兩種不同的技術，可將這種用法的特殊字元標幟為僅是欄位所含資料的一部分。</span><span class="sxs-lookup"><span data-stu-id="389e4-106">The flat file schemas used by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] support two different techniques for flagging occurrences of otherwise special characters as simply part of the data contained by a field.</span></span> <span data-ttu-id="389e4-107">這兩種技術分別採用逸出字元和換行字元。</span><span class="sxs-lookup"><span data-stu-id="389e4-107">These two techniques employ escape characters and wrap characters, respectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="389e4-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="389e4-108">In This Section</span></span>  
  
-   [<span data-ttu-id="389e4-109">逸出字元</span><span class="sxs-lookup"><span data-stu-id="389e4-109">Escape Characters</span></span>](../core/escape-characters.md)  
  
-   [<span data-ttu-id="389e4-110">換行字元</span><span class="sxs-lookup"><span data-stu-id="389e4-110">Wrap Characters</span></span>](../core/wrap-characters.md)