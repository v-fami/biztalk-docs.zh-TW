---
title: 錯誤-重複的屬性欄位升級 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.dupPropFieldPromo
ms.assetid: 59ac55c3-7613-493c-85a3-3965c250a3bb
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87d9f6ee346f5aae98ea69c2ce4e00c4fa1d6dbf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241342"
---
# <a name="error---duplicate-property-field-promotion"></a><span data-ttu-id="9c62f-102">錯誤-重複的屬性欄位升級</span><span class="sxs-lookup"><span data-stu-id="9c62f-102">Error - Duplicate Property Field Promotion</span></span>
<span data-ttu-id="9c62f-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="9c62f-103">**Error Code**</span></span>  
  
 <span data-ttu-id="9c62f-104">BEC2016</span><span class="sxs-lookup"><span data-stu-id="9c62f-104">BEC2016</span></span>  
  
 <span data-ttu-id="9c62f-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="9c62f-105">**Explanation**</span></span>  
  
 <span data-ttu-id="9c62f-106">此結構描述中的多個節點會做為屬性欄位升級為相同**欄位項目**相同的屬性結構描述中的節點。</span><span class="sxs-lookup"><span data-stu-id="9c62f-106">Multiple nodes in this schema are being promoted as Property Fields to the same **Field Element** node in the same property schema.</span></span>  
  
 <span data-ttu-id="9c62f-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="9c62f-107">**User Action**</span></span>  
  
 <span data-ttu-id="9c62f-108">使用**屬性欄位** 索引標籤**升級屬性**對話方塊中，透過存取**升級屬性**屬性**結構描述**節點，以刪除所有只保留一個具有相同相關聯的屬性欄位升級**欄位項目**屬性結構描述中的節點。</span><span class="sxs-lookup"><span data-stu-id="9c62f-108">Use the **Property Fields** tab of the **Promote Properties** dialog box, accessed through the **Promote Properties** property of the **Schema** node, to delete all but one of the Property Field promotions that are associated with the same **Field Element** node in the property schema.</span></span> <span data-ttu-id="9c62f-109">您可能想要加入新**欄位項目**屬性結構描述的節點，讓已刪除的升級可以重新升級為它們自己**欄位項目**節點。</span><span class="sxs-lookup"><span data-stu-id="9c62f-109">You may want to add new **Field Element** nodes to the property schema so that the deleted promotions can be re-promoted to their own **Field Element** nodes.</span></span>