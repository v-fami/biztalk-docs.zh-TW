---
title: 錯誤-無效的類型名稱 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.typeNameNotValid
ms.assetid: 4c9bceeb-b009-4279-ad16-19af09e6b091
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dac6d85d3b16ec691a4cc73b179515b70686791
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241414"
---
# <a name="error---type-name-not-valid"></a><span data-ttu-id="d1cd3-102">錯誤-無效的類型名稱</span><span class="sxs-lookup"><span data-stu-id="d1cd3-102">Error - Type Name Not Valid</span></span>
<span data-ttu-id="d1cd3-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="d1cd3-103">**Error Code**</span></span>  
  
 <span data-ttu-id="d1cd3-104">BEC2011</span><span class="sxs-lookup"><span data-stu-id="d1cd3-104">BEC2011</span></span>  
  
 <span data-ttu-id="d1cd3-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="d1cd3-105">**Explanation**</span></span>  
  
 <span data-ttu-id="d1cd3-106">**型別名稱**此結構描述檔案屬性無效。</span><span class="sxs-lookup"><span data-stu-id="d1cd3-106">The **Type Name** property of this schema file is not valid.</span></span> <span data-ttu-id="d1cd3-107">因為值**型別名稱**屬性做為自動產生的 C# 類別名稱的名稱時，它必須是有效的 C# 識別項，且不能是 BizTalk 保留的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d1cd3-107">Because the value of the **Type Name** property is used as the name of an automatically generated C# class name, it must be a valid C# identifier and cannot be a reserved BizTalk keyword.</span></span>  
  
 <span data-ttu-id="d1cd3-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="d1cd3-108">**User Action**</span></span>  
  
 <span data-ttu-id="d1cd3-109">在 Microsoft® 中選取相關結構描述檔案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，然後在 [屬性] 視窗中變更**型別名稱**屬性的值，是有效的 C# 識別項並不是 BizTalk 保留的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d1cd3-109">Select the relevant schema file in Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, and then in the Properties window, change the **Type Name** property to a value that is a valid C# identifier and is not a reserved BizTalk keyword.</span></span>