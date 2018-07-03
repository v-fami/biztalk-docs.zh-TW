---
title: 編譯器指示詞和連結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- compilier directives
- maps, compiling
- BizTalk Mapper, compiler directives
- links [maps], compiling
ms.assetid: 1655e10c-af98-4100-849d-b8214f93cfe9
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38e00b7d20e6fd0aff4f6af72377e301a812b8fd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991999"
---
# <a name="compiler-directives-and-links"></a><span data-ttu-id="fcbe4-102">編譯器指示詞和連結</span><span class="sxs-lookup"><span data-stu-id="fcbe4-102">Compiler Directives and Links</span></span>
<span data-ttu-id="fcbe4-103">您可以設定以下兩個以逐一連結為基礎的編譯器指示詞：</span><span class="sxs-lookup"><span data-stu-id="fcbe4-103">You can configure the following two compiler directives on a link-by-link basis:</span></span>  
  
- <span data-ttu-id="fcbe4-104">從輸入執行個體訊息中擷取何種資料，並複製為輸出執行個體訊息中相關的項目或屬性值。</span><span class="sxs-lookup"><span data-stu-id="fcbe4-104">What data from the input instance message is retrieved and copied as the relevant element or attribute value in the output instance message.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="fcbe4-105">此處的資料包含複製項目名稱或屬性本身的選項，而不是任何與項目或屬性相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="fcbe4-105">Data here includes the option to copy the name of the element or attribute itself, rather than any value associated with the element or attribute.</span></span> <span data-ttu-id="fcbe4-106">項目和屬性名稱一般不會被視為 XML 執行個體訊息中附帶資料的一部分。</span><span class="sxs-lookup"><span data-stu-id="fcbe4-106">Element and attribute names are not normally thought of as part of the data carried in an XML instance message.</span></span>  
  
- <span data-ttu-id="fcbe4-107">如何執行來源與目的結構描述之間的節點比對。</span><span class="sxs-lookup"><span data-stu-id="fcbe4-107">How node-matching is performed between the source and destination schemas.</span></span>  
  
  <span data-ttu-id="fcbe4-108">本節提供這些指示詞可用選項的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="fcbe4-108">This section provides a detailed explanation of these options available for these directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fcbe4-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="fcbe4-109">In This Section</span></span>  
  
-   [<span data-ttu-id="fcbe4-110">資料轉換設定</span><span class="sxs-lookup"><span data-stu-id="fcbe4-110">Data Transformation Configuration</span></span>](../core/data-transformation-configuration.md)  
  
-   [<span data-ttu-id="fcbe4-111">節點階層層級比對</span><span class="sxs-lookup"><span data-stu-id="fcbe4-111">Node-Hierarchy Level Matching</span></span>](../core/node-hierarchy-level-matching.md)