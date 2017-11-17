---
title: "錯誤-第二個輸入表格抽選程式運算質未正確 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.secondInputForTableExtractorNotValid
ms.assetid: 099f7374-8625-40af-a74b-24c4de941a7b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5970c0bfa23cc7da33b2c041cc326987ec278e09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---second-input-for-table-extractor-functoid-not-valid"></a><span data-ttu-id="fc938-102">錯誤-第二個輸入表格抽選程式運算質不正確</span><span class="sxs-lookup"><span data-stu-id="fc938-102">Error - Second Input for Table Extractor Functoid Not Valid</span></span>
<span data-ttu-id="fc938-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="fc938-103">**Error Code**</span></span>  
  
 <span data-ttu-id="fc938-104">btm1073</span><span class="sxs-lookup"><span data-stu-id="fc938-104">btm1073</span></span>  
  
 <span data-ttu-id="fc938-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="fc938-105">**Explanation**</span></span>  
  
 <span data-ttu-id="fc938-106">第二個輸入參數相關**表格抽選程式**運算質不正確。</span><span class="sxs-lookup"><span data-stu-id="fc938-106">The second input parameter to the relevant **Table Extractor** functoid is not valid.</span></span> <span data-ttu-id="fc938-107">這個參數必須是正整數常數，指出有效的資料行中的表格迴圈格線設定**表格迴圈**運算質的第一個輸入參數所指示。</span><span class="sxs-lookup"><span data-stu-id="fc938-107">This parameter must be a positive integer constant that indicates a valid column in the table looping grid configured for the **Table Looping** functoid that is indicated by the first input parameter.</span></span>  
  
 <span data-ttu-id="fc938-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="fc938-108">**User Action**</span></span>  
  
 <span data-ttu-id="fc938-109">請確認相關的輸入的參數**表格抽選程式**運算質，透過其**輸入參數**屬性和**設定\<運算質 >運算質**對話方塊中，您可以在下表所示。</span><span class="sxs-lookup"><span data-stu-id="fc938-109">Ensure that the input parameters to the relevant **Table Extractor** functoid, as accessed through its **Input Parameters** property and the **Configure \<Functoid> Functoid** dialog box, are as shown in the following table.</span></span>  
  
|<span data-ttu-id="fc938-110">表格擷取程式運算質輸入參數編號</span><span class="sxs-lookup"><span data-stu-id="fc938-110">Table Extractor functoid input parameter number</span></span>|<span data-ttu-id="fc938-111">Description</span><span class="sxs-lookup"><span data-stu-id="fc938-111">Description</span></span>|  
|-----------------------------------------------------|-----------------|  
|<span data-ttu-id="fc938-112">1</span><span class="sxs-lookup"><span data-stu-id="fc938-112">1</span></span>|<span data-ttu-id="fc938-113">從連結**表格迴圈**從這個運算質**表格抽選程式**依其第二個參數指定運算質會提取資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="fc938-113">Link from the **Table Looping** functoid from which this **Table Extractor** functoid will pull column data as indicated by its second parameter.</span></span>|  
|<span data-ttu-id="fc938-114">2</span><span class="sxs-lookup"><span data-stu-id="fc938-114">2</span></span>|<span data-ttu-id="fc938-115">透過設定資料表中的有效資料行數目**表格迴圈格線**屬性**表格迴圈**第一個輸入參數所指定的運算質。</span><span class="sxs-lookup"><span data-stu-id="fc938-115">The number of a valid column in the data table configured through the **Table Looping Grid** property of the **Table Looping** functoid specified by the first input parameter.</span></span>|