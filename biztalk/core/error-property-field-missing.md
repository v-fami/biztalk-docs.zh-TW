---
title: 錯誤-屬性欄位遺失 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.propFieldMissing
ms.assetid: 8d07e72b-f876-4a37-8c95-ec7aa0033983
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d77311e4c8585cfb7f6108364e6a5085619595a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240958"
---
# <a name="error---property-field-missing"></a><span data-ttu-id="01859-102">錯誤-屬性欄位遺失</span><span class="sxs-lookup"><span data-stu-id="01859-102">Error - Property Field Missing</span></span>
<span data-ttu-id="01859-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="01859-103">**Error Code**</span></span>  
  
 <span data-ttu-id="01859-104">BEC2008</span><span class="sxs-lookup"><span data-stu-id="01859-104">BEC2008</span></span>  
  
 <span data-ttu-id="01859-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="01859-105">**Explanation**</span></span>  
  
 <span data-ttu-id="01859-106">此結構描述中的指定的節點正在升級至**欄位項目**對應不存在的屬性結構描述中節點。</span><span class="sxs-lookup"><span data-stu-id="01859-106">The indicated node in this schema is being promoted to a **Field Element** node in the corresponding property schema that does not exist.</span></span> <span data-ttu-id="01859-107">會發生此狀況時**欄位項目**節點已移除或已使用做為目標的屬性升級之後，重新命名屬性結構描述中。</span><span class="sxs-lookup"><span data-stu-id="01859-107">This condition can occur when a **Field Element** node is removed from, or renamed in, a property schema after it has been used as the target of a property promotion.</span></span>  
  
 <span data-ttu-id="01859-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="01859-108">**User Action**</span></span>  
  
 <span data-ttu-id="01859-109">請修改屬性結構描述，使其包含遺漏**欄位項目**節點或使用**升級屬性**對話方塊來刪除或修改相關的屬性升級。</span><span class="sxs-lookup"><span data-stu-id="01859-109">Either modify the property schema so that it contains the missing **Field Element** node, or use the **Promote Properties** dialog box to delete or otherwise modify the relevant property promotion.</span></span>