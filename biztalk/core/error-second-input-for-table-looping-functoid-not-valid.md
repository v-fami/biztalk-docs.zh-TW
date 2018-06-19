---
title: 錯誤-表格迴圈運算質不是有效第二個輸入 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.secondInputForTableLoopingNotValid
ms.assetid: 22771f36-5969-40b1-a957-3ca67e19c3fd
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abb321a26300a514357225713db1b197fb828851
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970260"
---
# <a name="error---second-input-for-table-looping-functoid-not-valid"></a><span data-ttu-id="05344-102">錯誤-表格迴圈運算質不是有效第二個輸入</span><span class="sxs-lookup"><span data-stu-id="05344-102">Error - Second Input for Table Looping Functoid Not Valid</span></span>
<span data-ttu-id="05344-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="05344-103">**Error Code**</span></span>  
  
 <span data-ttu-id="05344-104">btm1072</span><span class="sxs-lookup"><span data-stu-id="05344-104">btm1072</span></span>  
  
 <span data-ttu-id="05344-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="05344-105">**Explanation**</span></span>  
  
 <span data-ttu-id="05344-106">第二個輸入參數相關**表格迴圈**運算質不正確。</span><span class="sxs-lookup"><span data-stu-id="05344-106">The second input parameter to the relevant **Table Looping** functoid is not valid.</span></span> <span data-ttu-id="05344-107">此參數必須是正整數，它指示關聯表格迴圈格線中的欄數。</span><span class="sxs-lookup"><span data-stu-id="05344-107">This parameter must be a positive integer that indicates the number of columns in the associated table looping grid.</span></span>  
  
 <span data-ttu-id="05344-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="05344-108">**User Action**</span></span>  
  
 <span data-ttu-id="05344-109">請確定輸入的參數**表格迴圈**運算質，透過 **輸入參數**屬性和**設定\<運算質\>運算質**對話方塊中，您可以在下表所示。</span><span class="sxs-lookup"><span data-stu-id="05344-109">Ensure that the input parameters to the **Table Looping** functoid, as accessed through the **Input Parameters** property and the **Configure \<Functoid\> Functoid** dialog box, are as shown in the following table.</span></span>  
  
|<span data-ttu-id="05344-110">「表格迴圈」運算質輸入參數編號</span><span class="sxs-lookup"><span data-stu-id="05344-110">Table Looping functoid input parameter number</span></span>|<span data-ttu-id="05344-111">Description</span><span class="sxs-lookup"><span data-stu-id="05344-111">Description</span></span>|  
|---------------------------------------------------|-----------------|  
|<span data-ttu-id="05344-112">1</span><span class="sxs-lookup"><span data-stu-id="05344-112">1</span></span>|<span data-ttu-id="05344-113">輸入執行個體訊息從一筆記錄的連結或來源結構描述中的欄位，其中發生次數控制的一組相關聯的次數**表格抽選程式**運算質會執行。</span><span class="sxs-lookup"><span data-stu-id="05344-113">Link from a record or field in the source schema, the number of occurrences of which an input instance message controls the number of times the set of associated **Table Extractor** functoids are run.</span></span>|  
|<span data-ttu-id="05344-114">2</span><span class="sxs-lookup"><span data-stu-id="05344-114">2</span></span>|<span data-ttu-id="05344-115">透過設定資料表中的資料行數目**表格迴圈格線**屬性之相關**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="05344-115">The number of columns in the data table configured through the **Table Looping Grid** property of the relevant **Table Looping** functoid.</span></span>|  
|<span data-ttu-id="05344-116">3 – 100</span><span class="sxs-lookup"><span data-stu-id="05344-116">3 – 100</span></span>|<span data-ttu-id="05344-117">常數與連結 (來自來源結構描述或其他運算質的輸出)，它們將會成為表格迴圈格線的可能資料來源。</span><span class="sxs-lookup"><span data-stu-id="05344-117">Constants and links (from the source schema or output from other functoids) that will become possible sources of data with the table looping grid.</span></span>|