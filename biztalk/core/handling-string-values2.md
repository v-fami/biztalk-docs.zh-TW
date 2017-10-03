---
title: "處理字串 Values2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- string values, configuring
- formatting strings
- strings, formatting
- left-justified string values
- jdearglist.txt
- strings, left-justified
- right-justified string values
- strings, right-justified
ms.assetid: 23d54731-b2b9-4610-a533-e041237e0bb3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 024663faa56d92361d861a61a0d64a4608839aa6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="handling-string-values"></a><span data-ttu-id="b435b-102">處理字串值</span><span class="sxs-lookup"><span data-stu-id="b435b-102">Handling String Values</span></span>
<span data-ttu-id="b435b-103">此主題說明如何將一些字串引數設定為靠右對齊 (填補左方)。</span><span class="sxs-lookup"><span data-stu-id="b435b-103">This topic describes how to configure certain string arguments as right-justified (and left padded).</span></span>  
  
## <a name="types-of-string-values"></a><span data-ttu-id="b435b-104">字串值的類型</span><span class="sxs-lookup"><span data-stu-id="b435b-104">Types of String Values</span></span>  
 <span data-ttu-id="b435b-105">JD Edwards EnterpriseOne 透過其互通性層來公開兩種字串值：</span><span class="sxs-lookup"><span data-stu-id="b435b-105">JD Edwards EnterpriseOne exposes two kinds of string values through its interoperability layer:</span></span>  
  
-   <span data-ttu-id="b435b-106">Char： 單一字元</span><span class="sxs-lookup"><span data-stu-id="b435b-106">char: a single character</span></span>  
  
-   <span data-ttu-id="b435b-107">最大長度字串</span><span class="sxs-lookup"><span data-stu-id="b435b-107">maximum length string</span></span>  
  
 <span data-ttu-id="b435b-108">JD Edwards EnterpriseOne 會使用匈牙利文標記法來命名商務功能中這些類型的引數。</span><span class="sxs-lookup"><span data-stu-id="b435b-108">JD Edwards EnterpriseOne uses Hungarian notation to name the arguments of these types in the business functions.</span></span> <span data-ttu-id="b435b-109">例如，這些類型的引數會有下列開頭：</span><span class="sxs-lookup"><span data-stu-id="b435b-109">For example, arguments of these types begin with:</span></span>  
  
-   <span data-ttu-id="b435b-110">c</span><span class="sxs-lookup"><span data-stu-id="b435b-110">c</span></span>  
  
-   <span data-ttu-id="b435b-111">sz</span><span class="sxs-lookup"><span data-stu-id="b435b-111">sz</span></span>  
  
### <a name="left-justified-values"></a><span data-ttu-id="b435b-112">靠左對齊的值</span><span class="sxs-lookup"><span data-stu-id="b435b-112">Left-Justified Values</span></span>  
 <span data-ttu-id="b435b-113">對於大多數 sz-type 引數 (最大文字長度或 char 陣列)，JD Edwards EnterpriseOne 需要一個靠左對齊的值。</span><span class="sxs-lookup"><span data-stu-id="b435b-113">For a majority of sz-type arguments, maximum length string or char array, JD Edwards EnterpriseOne expects a left-justified value.</span></span> <span data-ttu-id="b435b-114">例如，最大長度為 40 的街道地址行，JD Edwards EnterpriseOne 所需如下：</span><span class="sxs-lookup"><span data-stu-id="b435b-114">For examples, for a street address line, which is of maximum length 40, JD Edwards EnterpriseOne expects (for example):</span></span>  
  
 <span data-ttu-id="b435b-115">"4567 Main St"。</span><span class="sxs-lookup"><span data-stu-id="b435b-115">"4567 Main St.    "</span></span>  
  
 <span data-ttu-id="b435b-116">利用空白填補至長度 40。</span><span class="sxs-lookup"><span data-stu-id="b435b-116">padded to length 40 with blanks.</span></span> <span data-ttu-id="b435b-117">因為 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 會為您填補，所以您不需要輸入填補的空白。</span><span class="sxs-lookup"><span data-stu-id="b435b-117">It is not necessary for you to enter the padding because Microsoft BizTalk Adapter for JD Edwards EnterpriseOne provides this for you.</span></span> <span data-ttu-id="b435b-118">您只需要在用戶端程式碼中，輸入 "4567 Main St "。</span><span class="sxs-lookup"><span data-stu-id="b435b-118">You only need to enter "4567 Main St ", in your client code.</span></span>  
  
### <a name="right-justified-values"></a><span data-ttu-id="b435b-119">靠右對齊的值</span><span class="sxs-lookup"><span data-stu-id="b435b-119">Right-Justified Values</span></span>  
 <span data-ttu-id="b435b-120">對於此類型的一些子集值，JD Edwards EnterpriseOne 需要填補左方且靠右對齊的值。</span><span class="sxs-lookup"><span data-stu-id="b435b-120">For some subset of values for this type, JD Edwards EnterpriseOne expects values that are right justified with padding on the left.</span></span> <span data-ttu-id="b435b-121">例如，對於 B4200310 來源模組中的商務函式，引數 szBusinessUnit 是長度為 12。</span><span class="sxs-lookup"><span data-stu-id="b435b-121">For example, for business functions in the B4200310 source module, the argument szBusinessUnit is of length 12.</span></span> <span data-ttu-id="b435b-122">這個引數代表一個工廠，例如生產設備。</span><span class="sxs-lookup"><span data-stu-id="b435b-122">This argument represents a plant, such as a production facility.</span></span> <span data-ttu-id="b435b-123">對於編號為 30 的工廠，JD Edwards EnterpriseOne 所需的值如下：</span><span class="sxs-lookup"><span data-stu-id="b435b-123">For a plant number of 30, JD Edwards EnterpriseOne expects a value of:</span></span>  
  
 <span data-ttu-id="b435b-124">"           30"</span><span class="sxs-lookup"><span data-stu-id="b435b-124">"           30"</span></span>  
  
 <span data-ttu-id="b435b-125">若要輸入值，將會靠右對齊，您必須輸入參數呼叫 jdearglist.txt 檔案中。</span><span class="sxs-lookup"><span data-stu-id="b435b-125">To enter a value that will be right-justified, you must enter the parameter in a file called jdearglist.txt.</span></span> <span data-ttu-id="b435b-126">當您產生結構描述時，會讀取 jdearglist.txt。</span><span class="sxs-lookup"><span data-stu-id="b435b-126">The jdearglist.txt is read when you generate the schema.</span></span> <span data-ttu-id="b435b-127">此文字檔案中的任何值都會自動轉換成靠右對齊的值，並利用空白填補左方。</span><span class="sxs-lookup"><span data-stu-id="b435b-127">Any value in this text file is automatically converted to a right-justified value and padded on the left with blanks.</span></span>  
  
 <span data-ttu-id="b435b-128">您必須使用文字編輯器建立 jdearglist.txt，在裡面建立描述這些參數的項目，然後將檔案儲存在下列資料夾中：</span><span class="sxs-lookup"><span data-stu-id="b435b-128">You must create jdearglist.txt using a text editor, with entries describing these parameters, and save it in the following folder:</span></span>  
  
 <span data-ttu-id="b435b-129">C:\Program Files\Microsoft BizTalk Adapters\JDEEnterpriseOne\config</span><span class="sxs-lookup"><span data-stu-id="b435b-129">C:\Program Files\Microsoft BizTalk Adapters\JDEEnterpriseOne\config</span></span>  
  
 <span data-ttu-id="b435b-130">如果此檔案不存在或是空的，第一次開啟配接器時，BizTalk Adapter for JD Edwards EnterpriseOne 記錄檔中就會出現一則通知訊息。</span><span class="sxs-lookup"><span data-stu-id="b435b-130">If this file does not exist or is empty, an informational message appears in BizTalk Adapter for JD Edwards EnterpriseOne log when the adapter first opens.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b435b-131">如果在產生結構描述後變更此檔案，您必須重新產生結構描述才能重新整理其所含的資料。</span><span class="sxs-lookup"><span data-stu-id="b435b-131">If you change this file after generating your schema, you must regenerate the schema to refresh the data it contains.</span></span> <span data-ttu-id="b435b-132">若要確定此檔案中使用最新的資訊，您可以先使用 [工作管理員] 來停止 browsingagent.exe 程序，然後再重新產生結構描述，不過，應該不需要這樣做。</span><span class="sxs-lookup"><span data-stu-id="b435b-132">To verify that you are using the latest information in this file, you can use the Task Manager to stop the browsingagent.exe process before regenerating your schema; however, this should not be necessary.</span></span>  
  
 <span data-ttu-id="b435b-133">以下是 jdearglist.txt 檔案中之項目的格式範例：</span><span class="sxs-lookup"><span data-stu-id="b435b-133">The following is an example of the format for entries in the jdearglist.txt file:</span></span>  
  
```  
<SourceModule>.<BusinessFunction>.<Argument>  
  
```  
  
 <span data-ttu-id="b435b-134">例如：</span><span class="sxs-lookup"><span data-stu-id="b435b-134">For example:</span></span>  
  
```  
B4200310.F4211FSBeginDoc.szBusinessUnit  
```  
  
 <span data-ttu-id="b435b-135">對於屬於相同商務模組的一組商務功能，可以跨部分或全部商務功能來共用命名相似 (類型相同) 的引數。</span><span class="sxs-lookup"><span data-stu-id="b435b-135">For a set of business functions belonging to the same business module, like-named arguments (of the same type) are shared across some or all of the business functions.</span></span> <span data-ttu-id="b435b-136">您可以使用萬用字元 (*)，而不是商務功能名稱。</span><span class="sxs-lookup"><span data-stu-id="b435b-136">You can use the wildcard character (*) instead of the business function name.</span></span> <span data-ttu-id="b435b-137">例如：</span><span class="sxs-lookup"><span data-stu-id="b435b-137">For example:</span></span>  
  
```  
B4200310.*.szBusinessUnit  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="b435b-138">將 JD Edwards EnterpriseOne 商務程序匯入另一部電腦時，您必須手動複製 jdearglist.txt。</span><span class="sxs-lookup"><span data-stu-id="b435b-138">When importing a JD Edwards EnterpriseOne business process to another computer, you must copy jdearglist.txt manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b435b-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b435b-139">See Also</span></span>  
 [<span data-ttu-id="b435b-140">附錄 b： 資料類型</span><span class="sxs-lookup"><span data-stu-id="b435b-140">Appendix B: Data Types</span></span>](../core/appendix-b-data-types.md)