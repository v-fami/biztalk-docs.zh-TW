---
title: "錯誤-無效的根節點類別名稱 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.rootNodeClassNameNotValid
ms.assetid: 48b4f7e4-8c20-4e94-86be-1425ea62f8c5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ff170609ef37b1d7f2b00a4d4ca3952b89eef9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---root-node-class-name-not-valid"></a><span data-ttu-id="37778-102">錯誤-無效的根節點類別名稱</span><span class="sxs-lookup"><span data-stu-id="37778-102">Error - Root Node Class Name Not Valid</span></span>
<span data-ttu-id="37778-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="37778-103">**Error Code**</span></span>  
  
 <span data-ttu-id="37778-104">BEC2012</span><span class="sxs-lookup"><span data-stu-id="37778-104">BEC2012</span></span>  
  
 <span data-ttu-id="37778-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="37778-105">**Explanation**</span></span>  
  
 <span data-ttu-id="37778-106">**RootNode TypeName**根節點，此結構描述中的其中一個屬性是無效的。</span><span class="sxs-lookup"><span data-stu-id="37778-106">The **RootNode TypeName** property of one of the root nodes in this schema is not valid.</span></span> <span data-ttu-id="37778-107">因為值**RootNode TypeName**屬性做為自動產生的 C# 類別名稱的名稱時，它必須是有效的 C# 識別項，且不能是 BizTalk 保留的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="37778-107">Because the value of the **RootNode TypeName** property is used as the name of an automatically generated C# class name, it must be a valid C# identifier and cannot be a reserved BizTalk keyword.</span></span>  
  
 <span data-ttu-id="37778-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="37778-108">**User Action**</span></span>  
  
 <span data-ttu-id="37778-109">選取指定的根節點，然後在 Microsoft®[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性視窗中，變更**RootNode TypeName**屬性的值，是有效的 C# 識別項並不是 BizTalk 保留的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="37778-109">Select the indicated root node, and then in the Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, change the **RootNode TypeName** property to a value that is a valid C# identifier and is not a reserved BizTalk keyword.</span></span>