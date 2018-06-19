---
title: 錯誤-結構描述檔案不在組建 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.schemaFileNotInBuild
ms.assetid: 9190868d-a1ae-48bf-ac85-510086805887
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3b5d6d11bec6b9f263e2f204f004a9a162de471
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241598"
---
# <a name="error---schema-file-not-in-build"></a><span data-ttu-id="7991d-102">錯誤-結構描述檔案不在組建中</span><span class="sxs-lookup"><span data-stu-id="7991d-102">Error - Schema File Not In Build</span></span>
<span data-ttu-id="7991d-103">**說明**</span><span class="sxs-lookup"><span data-stu-id="7991d-103">**Explanation**</span></span>  
  
 <span data-ttu-id="7991d-104">命令 (**驗證執行個體**，**產生執行個體**，或**驗證結構描述**) 無法執行，因為**建置動作**結構描述檔案的屬性設定為**無**，這些命令時，防止此結構描述。</span><span class="sxs-lookup"><span data-stu-id="7991d-104">The command (**Validate Instance**, **Generate Instance**, or **Validate Schema**) could not be performed because the **Build Action** property of the schema file is set to **None**, preventing this schema from participating in these commands.</span></span>  
  
 <span data-ttu-id="7991d-105">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="7991d-105">**User Action**</span></span>  
  
 <span data-ttu-id="7991d-106">在 Microsoft 中選取相關結構描述檔案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，然後在 [屬性] 視窗中變更**建置動作**屬性**編譯**。</span><span class="sxs-lookup"><span data-stu-id="7991d-106">Select the relevant schema file in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, and then in the Properties window, change the **Build Action** property to a **Compile**.</span></span> <span data-ttu-id="7991d-107">然後嘗試**驗證執行個體**，**產生執行個體**，或**驗證結構描述**命令一次。</span><span class="sxs-lookup"><span data-stu-id="7991d-107">Then attempt the **Validate Instance**, **Generate Instance**, or **Validate Schema** command again.</span></span>