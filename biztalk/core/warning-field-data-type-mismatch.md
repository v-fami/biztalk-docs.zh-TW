---
title: 警告-欄位資料型別不符 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.fieldDataTypeMismatch
ms.assetid: 0c15d926-1d05-404b-bb16-a5fe8bc3575d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af42f5c921333e34c9ee219020cdb0fba97a7b5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288166"
---
# <a name="warning---field-data-type-mismatch"></a><span data-ttu-id="a270e-102">警告-欄位資料型別不符</span><span class="sxs-lookup"><span data-stu-id="a270e-102">Warning - Field Data Type Mismatch</span></span>
<span data-ttu-id="a270e-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="a270e-103">**Error Code**</span></span>  
  
 <span data-ttu-id="a270e-104">BEC1002</span><span class="sxs-lookup"><span data-stu-id="a270e-104">BEC1002</span></span>  
  
 <span data-ttu-id="a270e-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="a270e-105">**Explanation**</span></span>  
  
 <span data-ttu-id="a270e-106">**資料型別**不同找不到指定的節點屬性**資料型別**屬性**欄位項目**，正在升級中的節點對應屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="a270e-106">The **Data Type** property of the indicated node was found to be different than the **Data Type** property of the **Field Element** node to which it is being promoted in the corresponding property schema.</span></span> <span data-ttu-id="a270e-107">結構描述中節點的資料類型應該符合資料類型指派給**欄位項目**節點用於其屬性欄位升級，或至少將指派的資料類型應該對應至相同的 common language runtime (CLR) 類型。</span><span class="sxs-lookup"><span data-stu-id="a270e-107">The data type of a node in a schema should match the data type assigned to the **Field Element** node used for its Property Field promotion, or at least, the assigned data types should map to the same common language runtime (CLR) type.</span></span>  
  
 <span data-ttu-id="a270e-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="a270e-108">**User Action**</span></span>  
  
 <span data-ttu-id="a270e-109">變更**資料型別**指定節點的屬性和**欄位項目**節點，正在升級至相同的資料輸入的值，或至少資料型別值對應至相同的 CLR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="a270e-109">Change the **Data Type** properties of the indicated node and the **Field Element** node to which it is being promoted to the same data type value, or at least to data type values that map to the same CLR data type.</span></span>