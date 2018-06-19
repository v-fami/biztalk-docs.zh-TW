---
title: 錯誤-表格迴圈資料無效 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.tableLoopingDataNotValid
ms.assetid: 19c38e79-bab0-4899-ae24-e1485327e891
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9478026980ecaf3e2049773737250c56d18262c8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968526"
---
# <a name="error---table-looping-data-not-valid"></a><span data-ttu-id="ffb5f-102">錯誤-表格迴圈資料無效</span><span class="sxs-lookup"><span data-stu-id="ffb5f-102">Error - Table Looping Data Not Valid</span></span>
<span data-ttu-id="ffb5f-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="ffb5f-103">**Error Code**</span></span>  
  
 <span data-ttu-id="ffb5f-104">btm1065</span><span class="sxs-lookup"><span data-stu-id="ffb5f-104">btm1065</span></span>  
  
 <span data-ttu-id="ffb5f-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="ffb5f-105">**Explanation**</span></span>  
  
 <span data-ttu-id="ffb5f-106">關聯的相關資料的資料表**表格迴圈**運算質不是有效的可能是因為運算質，或設定不正確的表格迴圈格線設定不正確第二個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="ffb5f-106">The table of data associated with the relevant **Table Looping** functoid is not valid, probably due to an incorrectly configured second input parameter to the functoid, or an incorrectly configured table looping grid.</span></span>  
  
 <span data-ttu-id="ffb5f-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="ffb5f-107">**User Action**</span></span>  
  
 <span data-ttu-id="ffb5f-108">請確定輸入的參數**表格迴圈**運算質，透過 **輸入參數**屬性和**設定\<運算質\>運算質**對話方塊中，您可以在下表所示。</span><span class="sxs-lookup"><span data-stu-id="ffb5f-108">Ensure that the input parameters to the **Table Looping** functoid, as accessed through the **Input Parameters** property and the **Configure \<Functoid\> Functoid** dialog box, are as shown in the following table.</span></span>  
  
|<span data-ttu-id="ffb5f-109">「表格迴圈」運算質輸入參數編號</span><span class="sxs-lookup"><span data-stu-id="ffb5f-109">Table Looping functoid input parameter number</span></span>|<span data-ttu-id="ffb5f-110">Description</span><span class="sxs-lookup"><span data-stu-id="ffb5f-110">Description</span></span>|  
|---------------------------------------------------|-----------------|  
|<span data-ttu-id="ffb5f-111">1</span><span class="sxs-lookup"><span data-stu-id="ffb5f-111">1</span></span>|<span data-ttu-id="ffb5f-112">輸入執行個體訊息從一筆記錄的連結或來源結構描述中的欄位，其中發生次數控制的一組相關聯的次數**表格抽選程式**運算質會執行。</span><span class="sxs-lookup"><span data-stu-id="ffb5f-112">Link from a record or field in the source schema, the number of occurrences of which an input instance message controls the number of times the set of associated **Table Extractor** functoids are run.</span></span>|  
|<span data-ttu-id="ffb5f-113">2</span><span class="sxs-lookup"><span data-stu-id="ffb5f-113">2</span></span>|<span data-ttu-id="ffb5f-114">透過設定資料表中的資料行數目**表格迴圈格線**屬性之相關**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="ffb5f-114">The number of columns in the data table configured through the **Table Looping Grid** property of the relevant **Table Looping** functoid.</span></span>|  
|<span data-ttu-id="ffb5f-115">3 – 100</span><span class="sxs-lookup"><span data-stu-id="ffb5f-115">3 – 100</span></span>|<span data-ttu-id="ffb5f-116">常數與連結 (來自來源結構描述或其他運算質的輸出)，它們將會成為表格迴圈格線的可能資料來源。</span><span class="sxs-lookup"><span data-stu-id="ffb5f-116">Constants and links (from the source schema or output from other functoids) that will become possible sources of data with the table looping grid.</span></span>|  
  
 <span data-ttu-id="ffb5f-117">此外，請確定您正確設定表格迴圈格線中，透過 [**表格迴圈格線**屬性和**表格迴圈組態**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ffb5f-117">Also, ensure that you properly configure the table looping grid, as accessed through the **Table Looping Grid** property and the **Table Looping Configuration** dialog box.</span></span> <span data-ttu-id="ffb5f-118">常數或連結的值必須選擇將用來存取每一個儲存格相關聯的**表格抽選程式**運算質。</span><span class="sxs-lookup"><span data-stu-id="ffb5f-118">A constant or link value must be chosen for every cell that will be accessed by an associated **Table Extractor** functoid.</span></span>