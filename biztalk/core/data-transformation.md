---
title: 資料轉換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps, data translation
- data translation, about data translation
- data transformation, about data transformation
- maps, data transformation
- data transformation, maps
- data translation, maps
ms.assetid: a6aa5e9a-8d9c-478d-8f69-f9b16ed1a18c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4366e37d206902ec3aff5e016c02c4bd721da5b6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015952"
---
# <a name="data-transformation"></a><span data-ttu-id="1cb8e-102">資料轉換</span><span class="sxs-lookup"><span data-stu-id="1cb8e-102">Data Transformation</span></span>
<span data-ttu-id="1cb8e-103">對應資料會依賴資料轉換。</span><span class="sxs-lookup"><span data-stu-id="1cb8e-103">Mapping data relies on data transformation.</span></span>  
  
 <span data-ttu-id="1cb8e-104">資料轉換為目的結構描述中建立記錄和欄位的來源結構描述 （通常不同） 的記錄與欄位之間的對應關係的程序。</span><span class="sxs-lookup"><span data-stu-id="1cb8e-104">Data transformation is the process of creating a correspondence between records and fields of a source schema to (often different) records and fields in a destination schema.</span></span> <span data-ttu-id="1cb8e-105">對應訂單和發票上的送貨地址和帳單地址資訊，即是資料轉換的例子。</span><span class="sxs-lookup"><span data-stu-id="1cb8e-105">An example of data transformation is to map shipping and billing address information from a purchase order to an invoice.</span></span> <span data-ttu-id="1cb8e-106">這是最基本的對應類型。</span><span class="sxs-lookup"><span data-stu-id="1cb8e-106">This is the most basic type of mapping.</span></span> <span data-ttu-id="1cb8e-107">資料轉換也可應用於下列作業：</span><span class="sxs-lookup"><span data-stu-id="1cb8e-107">Data transformation can also apply to operations such as:</span></span>  
  
- <span data-ttu-id="1cb8e-108">計算迴圈記錄中資料的平均值，然後將結果傳送至目的結構描述的單一欄位。</span><span class="sxs-lookup"><span data-stu-id="1cb8e-108">Averaging data from a looping record and sending the output to a single field in the destination schema.</span></span>  
  
- <span data-ttu-id="1cb8e-109">將字元資料轉換為它的 ASCII 格式。</span><span class="sxs-lookup"><span data-stu-id="1cb8e-109">Converting character data to its ASCII format.</span></span>  
  
- <span data-ttu-id="1cb8e-110">在一或多項紀錄中新增或刪減資料，然後將結果放到目的結構描述中的單一欄位。</span><span class="sxs-lookup"><span data-stu-id="1cb8e-110">Adding or subtracting data from one or more records and putting the result in a single field in the destination schema.</span></span>  
  
  <span data-ttu-id="1cb8e-111">如果您要將資料從某種格式轉譯成另一種格式，您要使用管線。</span><span class="sxs-lookup"><span data-stu-id="1cb8e-111">If you want to translate data from one format to another, you would use a pipeline.</span></span> <span data-ttu-id="1cb8e-112">這對於解決企業應用程式整合的問題相當有幫助，採用的作法是將特定類型的訊息轉譯為現有系統所要求的其他格式，但是這無法使用對應來完成。</span><span class="sxs-lookup"><span data-stu-id="1cb8e-112">This can be helpful in solving enterprise application integration problems by translating a given type of message into alternative formats required by existing systems but cannot be done using a map.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cb8e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cb8e-113">See Also</span></span>  
 <span data-ttu-id="1cb8e-114">[對應](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="1cb8e-114">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="1cb8e-115">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="1cb8e-115">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)