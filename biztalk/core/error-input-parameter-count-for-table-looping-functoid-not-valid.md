---
title: "錯誤-表格迴圈運算質不是有效的輸入參數計數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.badParamCountForTableLooping
ms.assetid: 616e54aa-f6e3-4a49-afe2-278a0724e226
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 137ee97363adce49bfce6e74c3e154832e70471e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---input-parameter-count-for-table-looping-functoid-not-valid"></a><span data-ttu-id="24834-102">錯誤-表格迴圈運算質不是有效的輸入參數計數</span><span class="sxs-lookup"><span data-stu-id="24834-102">Error - Input Parameter Count for Table Looping Functoid Not Valid</span></span>
<span data-ttu-id="24834-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="24834-103">**Error Code**</span></span>  
  
 <span data-ttu-id="24834-104">btm1070</span><span class="sxs-lookup"><span data-stu-id="24834-104">btm1070</span></span>  
  
 <span data-ttu-id="24834-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="24834-105">**Explanation**</span></span>  
  
 <span data-ttu-id="24834-106">指定相關的輸入參數數目**表格迴圈**運算質不正確。</span><span class="sxs-lookup"><span data-stu-id="24834-106">The number of input parameters specified for the relevant **Table Looping** functoid is not valid.</span></span>  
  
 <span data-ttu-id="24834-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="24834-107">**User Action**</span></span>  
  
 <span data-ttu-id="24834-108">請確定輸入的參數**表格迴圈**運算質，透過 **輸入參數**屬性和**設定\<運算質 > 運算質**對話方塊中，您可以在下表所示。</span><span class="sxs-lookup"><span data-stu-id="24834-108">Ensure that the input parameters to the **Table Looping** functoid, as accessed through the **Input Parameters** property and the **Configure \<Functoid> Functoid** dialog box, are as shown in the following table.</span></span>  
  
|<span data-ttu-id="24834-109">「表格迴圈」運算質輸入參數編號</span><span class="sxs-lookup"><span data-stu-id="24834-109">Table Looping functoid input parameter number</span></span>|<span data-ttu-id="24834-110">Description</span><span class="sxs-lookup"><span data-stu-id="24834-110">Description</span></span>|  
|---------------------------------------------------|-----------------|  
|<span data-ttu-id="24834-111">1</span><span class="sxs-lookup"><span data-stu-id="24834-111">1</span></span>|<span data-ttu-id="24834-112">輸入執行個體訊息從一筆記錄的連結或來源結構描述中的欄位，其中發生次數控制的一組相關聯的次數**表格抽選程式**運算質會執行。</span><span class="sxs-lookup"><span data-stu-id="24834-112">Link from a record or field in the source schema, the number of occurrences of which an input instance message controls the number of times the set of associated **Table Extractor** functoids are run.</span></span>|  
|<span data-ttu-id="24834-113">2</span><span class="sxs-lookup"><span data-stu-id="24834-113">2</span></span>|<span data-ttu-id="24834-114">透過設定資料表中的資料行數目**表格迴圈格線**屬性之相關**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="24834-114">The number of columns in the data table configured through the **Table Looping Grid** property of the relevant **Table Looping** functoid.</span></span>|  
|<span data-ttu-id="24834-115">3 – 100</span><span class="sxs-lookup"><span data-stu-id="24834-115">3 – 100</span></span>|<span data-ttu-id="24834-116">常數與連結 (來自來源結構描述或其他運算質的輸出)，它們將會成為表格迴圈格線的可能資料來源。</span><span class="sxs-lookup"><span data-stu-id="24834-116">Constants and links (from the source schema or output from other functoids) that will become possible sources of data with the table looping grid.</span></span>|