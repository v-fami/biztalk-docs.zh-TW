---
title: "錯誤-連結選項衝突 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.linkOptionConflict
ms.assetid: dbad5c00-500b-4931-a54c-8b311fbfda53
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31f5829f971e524a5e4d2c0f443174c6511a6314
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---link-option-conflict"></a><span data-ttu-id="4cf30-102">錯誤-連結選項衝突</span><span class="sxs-lookup"><span data-stu-id="4cf30-102">Error - Link Option Conflict</span></span>
<span data-ttu-id="4cf30-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="4cf30-103">**Error Code**</span></span>  
  
 <span data-ttu-id="4cf30-104">btm1022</span><span class="sxs-lookup"><span data-stu-id="4cf30-104">btm1022</span></span>  
  
 <span data-ttu-id="4cf30-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="4cf30-105">**Explanation**</span></span>  
  
 <span data-ttu-id="4cf30-106">目的結構描述中指定節點的編譯器指示詞，與針對其連入連結指定的編譯器指示詞衝突。</span><span class="sxs-lookup"><span data-stu-id="4cf30-106">The indicated nodes in the destination schema have conflicting compiler directives specified for their incoming links.</span></span>  
  
 <span data-ttu-id="4cf30-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="4cf30-107">**User Action**</span></span>  
  
 <span data-ttu-id="4cf30-108">選取一個或兩個連結到目的結構描述中指定節點的連結，然後在 [Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗中，變更其編譯器指示詞使其相容。</span><span class="sxs-lookup"><span data-stu-id="4cf30-108">Select one or both of the links leading to the indicated nodes in the destination schema and then in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, change their compiler directives so that they are compatible.</span></span>