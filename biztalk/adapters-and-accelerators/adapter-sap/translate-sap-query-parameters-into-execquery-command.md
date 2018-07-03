---
title: SAP 查詢參數轉譯為 EXECQUERY 命令 mySAP 配接器在 BizTalk 中 |Microsoft Docs
description: 要轉譯範例 EXECQUERY，SAP 查詢的指導方針
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a545e20-2607-4946-a60d-0a227b86d093
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8ffd480e952e0df7114a93f6cb2a5baf631ad96
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021693"
---
# <a name="translate-sap-query-parameters-into-execquery-command"></a><span data-ttu-id="cbe01-103">SAP 查詢參數轉譯為 EXECQUERY 命令</span><span class="sxs-lookup"><span data-stu-id="cbe01-103">Translate SAP query parameters into EXECQUERY command</span></span>
<span data-ttu-id="cbe01-104">說明如何查詢參數轉譯為 EXECQUERY 命令文字。</span><span class="sxs-lookup"><span data-stu-id="cbe01-104">Explains how the parameters of a query translate into an EXECQUERY command text.</span></span> <span data-ttu-id="cbe01-105">本主題會使用自訂的 SAP 查詢，ZQUERY_TST_NEW 的範例。</span><span class="sxs-lookup"><span data-stu-id="cbe01-105">This topic uses the example of a custom SAP query, ZQUERY_TST_NEW.</span></span>  
  
## <a name="open-the-query-in-sap-gui"></a><span data-ttu-id="cbe01-106">在 SAP GUI 中開啟查詢</span><span class="sxs-lookup"><span data-stu-id="cbe01-106">Open the Query in SAP GUI</span></span>  
 <span data-ttu-id="cbe01-107">執行下列步驟，以在 SAP 中開啟查詢。</span><span class="sxs-lookup"><span data-stu-id="cbe01-107">Perform the following steps to open the query in SAP.</span></span> <span data-ttu-id="cbe01-108">此處提供的步驟適用於 ZQUERY_TST_NEW 查詢，並且專屬於 SAP 版本。</span><span class="sxs-lookup"><span data-stu-id="cbe01-108">The steps provided here are for ZQUERY_TST_NEW query and are specific to SAP versions.</span></span>  
  
1. <span data-ttu-id="cbe01-109">執行交易 SQ01。</span><span class="sxs-lookup"><span data-stu-id="cbe01-109">Run the transaction SQ01.</span></span>  
  
2. <span data-ttu-id="cbe01-110">在 **查詢，從使用者群組**頁面上，按一下**快速檢視器**。</span><span class="sxs-lookup"><span data-stu-id="cbe01-110">In the **Query from User Group** page, click **Quick Viewer**.</span></span>  
  
3. <span data-ttu-id="cbe01-111">在 **快速檢視器**頁面上，於**快速檢視**文字方塊中，輸入`ZQUERY_TST_NEW`，然後按一下**顯示**。</span><span class="sxs-lookup"><span data-stu-id="cbe01-111">In the **Quick Viewer** page, in the **Quick View** text box, type `ZQUERY_TST_NEW`, and then click **Display**.</span></span>  
  
4. <span data-ttu-id="cbe01-112">在 **快速檢視器**頁面上，按一下**選取項目欄位**索引標籤，列出查詢中的所有參數。</span><span class="sxs-lookup"><span data-stu-id="cbe01-112">In the **Quick Viewer** page, click the **Selection fields** tab to list all the parameters in the query.</span></span>  
  
    <span data-ttu-id="cbe01-113">下圖顯示在查詢定義的所有參數。</span><span class="sxs-lookup"><span data-stu-id="cbe01-113">The following figure shows all the parameters in the query definition.</span></span>  
  
    <span data-ttu-id="cbe01-114">![SAP 查詢的參數清單](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-types.gif "sap_query_param_types")</span><span class="sxs-lookup"><span data-stu-id="cbe01-114">![List of parameters for an SAP query](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-types.gif "sap_query_param_types")</span></span>  
  
5. <span data-ttu-id="cbe01-115">按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="cbe01-115">Click **Execute**.</span></span> <span data-ttu-id="cbe01-116">會顯示下列頁面。</span><span class="sxs-lookup"><span data-stu-id="cbe01-116">The following page is displayed.</span></span>  
  
    <span data-ttu-id="cbe01-117">![提供 SAP 查詢的參數值](../../adapters-and-accelerators/adapter-sap/media/sap-query-all-params.gif "sap_query_all_params")</span><span class="sxs-lookup"><span data-stu-id="cbe01-117">![Provide parameter values for an SAP query](../../adapters-and-accelerators/adapter-sap/media/sap-query-all-params.gif "sap_query_all_params")</span></span>  
  
6. <span data-ttu-id="cbe01-118">按一下黃色箭號，以定義每個參數。</span><span class="sxs-lookup"><span data-stu-id="cbe01-118">Click the yellow arrows to define each parameter.</span></span> <span data-ttu-id="cbe01-119">您可以定義特定允許/非-允許的值，或者您可以定義允許/非-容許值的範圍。</span><span class="sxs-lookup"><span data-stu-id="cbe01-119">You can either define specific allowable/non-allowable values or you can define a range of allowable/non-allowable values.</span></span>  <span data-ttu-id="cbe01-120">EXECQUERY 語法必須根據每個參數的 SAP GUI 中設定的值指定。</span><span class="sxs-lookup"><span data-stu-id="cbe01-120">The EXECQUERY syntax must be specified based on the values configured in the SAP GUI for each parameter.</span></span>  
  
   <span data-ttu-id="cbe01-121">下一節提供有關 SAP GUI 中定義之值的方式，以及如何將這些值轉譯為 EXECQUERY 語法說明。</span><span class="sxs-lookup"><span data-stu-id="cbe01-121">The next section provides an explanation about how the values are defined in the SAP GUI and how those values translate to EXECQUERY syntax.</span></span>  
  
## <a name="frame-an-execquery-syntax"></a><span data-ttu-id="cbe01-122">框架 EXECQUERY 語法</span><span class="sxs-lookup"><span data-stu-id="cbe01-122">Frame an EXECQUERY Syntax</span></span>  
 <span data-ttu-id="cbe01-123">讓我們看看起來像 EXECQUERY 語法基礎查詢定義中所定義的參數值。</span><span class="sxs-lookup"><span data-stu-id="cbe01-123">Let’s look at what the EXECQUERY syntax looks like based on the parameter values defined in the query definition.</span></span> <span data-ttu-id="cbe01-124">若要了解這一點，我們將示範的第一個參數，值的設定方式的範例**二位數字**，來轉譯**ZQUERY_TST_NEW**查詢。</span><span class="sxs-lookup"><span data-stu-id="cbe01-124">To understand this, we’ll show examples of how the values configured for the first parameter, **Two digit number**, translate to the  **ZQUERY_TST_NEW** query.</span></span>  
  
 <span data-ttu-id="cbe01-125">首先，讓我們假設中的值**單一 vals** （加上一個綠點） 索引標籤會定義下列的螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="cbe01-125">First, let’s assume the values in the **Single vals** tab (with a green dot) are defined as shown in the following screenshot:</span></span>  
  
 <span data-ttu-id="cbe01-126">![查詢接受的參數值的清單](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-val.gif "sap_query_param_val")</span><span class="sxs-lookup"><span data-stu-id="cbe01-126">![List of parameter values that a query can take](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-val.gif "sap_query_param_val")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbe01-127">在您按一下的黃色箭頭之後，會出現此對話方塊**二位數字**參數。</span><span class="sxs-lookup"><span data-stu-id="cbe01-127">This dialog box appears after you click the yellow arrow against the **Two digit number** parameter.</span></span>  
  
 <span data-ttu-id="cbe01-128">在此情況下，EXECQUERY 語法看起來像：</span><span class="sxs-lookup"><span data-stu-id="cbe01-128">In such a case, the EXECQUERY syntax looks like:</span></span>  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5'  
```  
  
 <span data-ttu-id="cbe01-129">相同查詢中，除了中的值**單一 vals**索引標籤 （具有一個綠點），您可以也在值**單一 vals**  索引標籤 （具有一個紅點） 定義如下所示：</span><span class="sxs-lookup"><span data-stu-id="cbe01-129">For the same query, in addition to the values in the **Single vals** tab (with a green dot), you can also have the values in the **Single vals** tab (with a red dot) defined as following:</span></span>  
  
 <span data-ttu-id="cbe01-130">![查詢不接受的參數值的清單](../../adapters-and-accelerators/adapter-sap/media/2af88a57-4ff6-4bcc-8961-0f25dbfb8166.gif "2af88a57-4ff6-4bcc-8961-0f25dbfb8166")</span><span class="sxs-lookup"><span data-stu-id="cbe01-130">![List of parameter values that a query cannot take](../../adapters-and-accelerators/adapter-sap/media/2af88a57-4ff6-4bcc-8961-0f25dbfb8166.gif "2af88a57-4ff6-4bcc-8961-0f25dbfb8166")</span></span>  
  
 <span data-ttu-id="cbe01-131">在此情況下，EXECQUERY 語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="cbe01-131">In such a case, EXECQUERY syntax looks like:</span></span>  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8'  
```  
  
 <span data-ttu-id="cbe01-132">現在，如果您新增至值**範圍** 索引標籤 （具有一個綠點），如下列螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="cbe01-132">Now, if you add values to the **Ranges** tab (with a green dot), like shown in the following screenshot:</span></span>  
  
 <span data-ttu-id="cbe01-133">![查詢接受的參數值的範圍](../../adapters-and-accelerators/adapter-sap/media/74907c7d-5a7a-4a2d-a614-6a835eca1764.gif "74907c7d-5a7a-4a2d-a614-6a835eca1764")</span><span class="sxs-lookup"><span data-stu-id="cbe01-133">![Range of parameter values that a query can take](../../adapters-and-accelerators/adapter-sap/media/74907c7d-5a7a-4a2d-a614-6a835eca1764.gif "74907c7d-5a7a-4a2d-a614-6a835eca1764")</span></span>  
  
 <span data-ttu-id="cbe01-134">EXECQUERY 語法看起來像：</span><span class="sxs-lookup"><span data-stu-id="cbe01-134">the EXECQUERY syntax looks like:</span></span>  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8', @P1 BETWEEN '2' and '5'  
```  
  
 <span data-ttu-id="cbe01-135">同樣地，如果您新增至值**範圍**索引標籤 （一個紅點），如下列螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="cbe01-135">Similarly, if you add values to the **Ranges** tab (with a red dot), like shown in the following screenshot:</span></span>  
  
 <span data-ttu-id="cbe01-136">![查詢不接受的參數值的範圍](../../adapters-and-accelerators/adapter-sap/media/ccc6a7bb-bc47-4325-8b58-094201f791bf.gif "ccc6a7bb-bc47-4325-8b58-094201f791bf")</span><span class="sxs-lookup"><span data-stu-id="cbe01-136">![Range of parameter values that a query cannot take](../../adapters-and-accelerators/adapter-sap/media/ccc6a7bb-bc47-4325-8b58-094201f791bf.gif "ccc6a7bb-bc47-4325-8b58-094201f791bf")</span></span>  
  
 <span data-ttu-id="cbe01-137">EXECQUERY 語法看起來像：</span><span class="sxs-lookup"><span data-stu-id="cbe01-137">the EXECQUERY syntax looks like:</span></span>  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8', @P1 BETWEEN '2' and '5', NOT @P1 BETWEEN '6' AND '8'  
```  
  
 <span data-ttu-id="cbe01-138">為了簡化和了解，本主題只討論的第一個參數，關於**二位數字**。</span><span class="sxs-lookup"><span data-stu-id="cbe01-138">For simplicity and understanding, this topic only talks about the first parameter, **Two digit number**.</span></span> <span data-ttu-id="cbe01-139">您可以使用類似的方法來判斷如何定義其他參數的值轉譯為 EXECQUERY 語法。</span><span class="sxs-lookup"><span data-stu-id="cbe01-139">You can use similar methods to determine how values defined for other parameters translate into an EXECQUERY syntax.</span></span>  
  
