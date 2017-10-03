---
title: "處理字串 Values1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jdearglist.txt, configuring strings
- strings, left-justified
- strings, configuring
- strings, right-justified
ms.assetid: a180b818-1009-45f5-a503-d10ed7dd27fc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f32b29b9a8688fe8402730c1db8f12e42a67bab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="handling-string-values"></a><span data-ttu-id="2e91a-102">處理字串值</span><span class="sxs-lookup"><span data-stu-id="2e91a-102">Handling String Values</span></span>
<span data-ttu-id="2e91a-103">此主題說明如何將一些字串引數設定為靠右對齊 (填補左方)。</span><span class="sxs-lookup"><span data-stu-id="2e91a-103">This topic describes how to configure certain string arguments as right-justified (and left padded).</span></span>  
  
## <a name="types-of-string-values"></a><span data-ttu-id="2e91a-104">字串值的類型</span><span class="sxs-lookup"><span data-stu-id="2e91a-104">Types of String Values</span></span>  
 <span data-ttu-id="2e91a-105">JD Edwards OneWorld 會透過其互通性層公開兩種字串值：</span><span class="sxs-lookup"><span data-stu-id="2e91a-105">JD Edwards OneWorld exposes two kinds of string values through its interoperability layer:</span></span>  
  
-   <span data-ttu-id="2e91a-106">Char： 單一字元</span><span class="sxs-lookup"><span data-stu-id="2e91a-106">Char: a single character</span></span>  
  
-   <span data-ttu-id="2e91a-107">最大長度字串</span><span class="sxs-lookup"><span data-stu-id="2e91a-107">maximum length string</span></span>  
  
 <span data-ttu-id="2e91a-108">JD Edwards OneWorld 會使用匈牙利文標記法來命名商務功能中這些類型的引數。</span><span class="sxs-lookup"><span data-stu-id="2e91a-108">JD Edwards OneWorld uses Hungarian notation to name the arguments of these types in the business functions.</span></span> <span data-ttu-id="2e91a-109">例如，這些類型的引數會有下列開頭：</span><span class="sxs-lookup"><span data-stu-id="2e91a-109">For example, arguments of these types begin with:</span></span>  
  
-   <span data-ttu-id="2e91a-110">c</span><span class="sxs-lookup"><span data-stu-id="2e91a-110">c</span></span>  
  
-   <span data-ttu-id="2e91a-111">sz</span><span class="sxs-lookup"><span data-stu-id="2e91a-111">sz</span></span>  
  
### <a name="left-justified-values"></a><span data-ttu-id="2e91a-112">靠左對齊的值</span><span class="sxs-lookup"><span data-stu-id="2e91a-112">Left-Justified Values</span></span>  
 <span data-ttu-id="2e91a-113">對於大多數的 sz 型別引數、最大長度字串或 char 陣列，JD Edwards OneWorld 會預期靠左對齊的值。</span><span class="sxs-lookup"><span data-stu-id="2e91a-113">For a majority of sz-type arguments, maximum length string or char array, JD Edwards OneWorld expects a left-justified value.</span></span> <span data-ttu-id="2e91a-114">若為最大長度 40 的街道地址行，JD Edwards OneWorld 則會預期 (例如)：</span><span class="sxs-lookup"><span data-stu-id="2e91a-114">For a street address line, which is of maximum length 40, JD Edwards OneWorld expects (for example):</span></span>  
  
 <span data-ttu-id="2e91a-115">"4567 Main St.       "</span><span class="sxs-lookup"><span data-stu-id="2e91a-115">"4567 Main St.       "</span></span>  
  
 <span data-ttu-id="2e91a-116">利用空白填補至長度 40。</span><span class="sxs-lookup"><span data-stu-id="2e91a-116">padded to length 40 with blanks.</span></span> <span data-ttu-id="2e91a-117">您不需要輸入填補字元，因為 Microsoft BizTalk Adapter for JD Edwards OneWorld 會自動為您填入。</span><span class="sxs-lookup"><span data-stu-id="2e91a-117">It is not necessary for you to enter the padding because Microsoft BizTalk Adapter for JD Edwards OneWorld provides this for you.</span></span> <span data-ttu-id="2e91a-118">您只需要在用戶端程式碼中輸入 "4567 Main St." 即可。</span><span class="sxs-lookup"><span data-stu-id="2e91a-118">You only need to enter "4567 Main St.", in your client code.</span></span>  
  
### <a name="right-justified-values"></a><span data-ttu-id="2e91a-119">靠右對齊的值</span><span class="sxs-lookup"><span data-stu-id="2e91a-119">Right-Justified Values</span></span>  
 <span data-ttu-id="2e91a-120">對於此型別的某些值，JD Edwards OneWorld 會預期靠右對齊且向左填補的值。</span><span class="sxs-lookup"><span data-stu-id="2e91a-120">For some subset of values for this type, JD Edwards OneWorld expects values that are right justified with padding on the left.</span></span> <span data-ttu-id="2e91a-121">例如，對於 B4200310 來源模組中的商務函式，引數 szBusinessUnit 是長度為 12。</span><span class="sxs-lookup"><span data-stu-id="2e91a-121">For example, for business functions in the B4200310 source module, the argument szBusinessUnit is of length 12.</span></span> <span data-ttu-id="2e91a-122">這個引數代表一個工廠，例如生產設備。</span><span class="sxs-lookup"><span data-stu-id="2e91a-122">This argument represents a plant, such as a production facility.</span></span> <span data-ttu-id="2e91a-123">如果工廠編號為 30，J.D.</span><span class="sxs-lookup"><span data-stu-id="2e91a-123">For a plant number of 30, J.D.</span></span> <span data-ttu-id="2e91a-124">Edwards OneWorld XE 預期的值：</span><span class="sxs-lookup"><span data-stu-id="2e91a-124">Edwards OneWorld XE expects a value of:</span></span>  
  
 <span data-ttu-id="2e91a-125">"          30"</span><span class="sxs-lookup"><span data-stu-id="2e91a-125">"          30"</span></span>  
  
 <span data-ttu-id="2e91a-126">若要輸入值，將會靠右對齊，您必須輸入參數呼叫 jdearglist.txt 檔案中。</span><span class="sxs-lookup"><span data-stu-id="2e91a-126">To enter a value that will be right-justified, you must enter the parameter in a file called jdearglist.txt.</span></span> <span data-ttu-id="2e91a-127">當您產生結構描述時，會讀取 jdearglist.txt。</span><span class="sxs-lookup"><span data-stu-id="2e91a-127">The jdearglist.txt is read when you generate the schema.</span></span> <span data-ttu-id="2e91a-128">此文字檔中所列的值都會自動轉換為靠右對齊、並在左邊填滿空格的值。</span><span class="sxs-lookup"><span data-stu-id="2e91a-128">Any value that is listed in this text file is automatically converted to a right-justified value and padded on the left with blanks.</span></span>  
  
 <span data-ttu-id="2e91a-129">您必須建立 jdearglist.txt 使用文字編輯器 中，項目會描述這些參數，並將它儲存在下列資料夾： %BizTalk_Install_Adapter%\config\JDE\\</span><span class="sxs-lookup"><span data-stu-id="2e91a-129">You must create jdearglist.txt using a text editor, with entries describing these parameters, and save it in the following folder: %BizTalk_Install_Adapter%\config\JDE\\</span></span>  
  
 <span data-ttu-id="2e91a-130">其中**%biztalk_install_adapter**是您安裝 BizTalk Adapter for JD Edwards OneWorld 的目錄。</span><span class="sxs-lookup"><span data-stu-id="2e91a-130">Where **%BizTalk_Install_Adapter%** is the directory in which you installed BizTalk Adapter for JD Edwards OneWorld.</span></span>  
  
 <span data-ttu-id="2e91a-131">如果這個檔案不存在或內容空白，則 BizTalk Adapter for JD Edwards OneWorld 記錄檔中就會在配接器第一次開啟時出現一則資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="2e91a-131">If this file does not exist or is empty, an informational message appears in the BizTalk Adapter for JD Edwards OneWorld log when the adapter first opens.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e91a-132">如果在產生結構描述後變更此檔案，您必須重新產生結構描述才能重新整理其所含的資料。</span><span class="sxs-lookup"><span data-stu-id="2e91a-132">If you change this file after generating your schema, you must regenerate the schema to refresh the data it contains.</span></span>  
  
 <span data-ttu-id="2e91a-133">若要確定此檔案中使用最新的資訊，您可以先使用 [工作管理員] 來停止 browsingagent.exe 程序，然後再重新產生結構描述，不過，應該不需要這樣做。</span><span class="sxs-lookup"><span data-stu-id="2e91a-133">To verify that you are using the latest information in this file, you can use the Task Manager to stop the browsingagent.exe process before regenerating your schema; however, this should not be necessary.</span></span>  
  
 <span data-ttu-id="2e91a-134">以下是 jdearglist.txt 檔案中之項目的格式範例：</span><span class="sxs-lookup"><span data-stu-id="2e91a-134">The following is an example of the format for entries in the jdearglist.txt file:</span></span>  
  
```  
<SourceModule>.<BusinessFunction>.<Argument>  
```  
  
 <span data-ttu-id="2e91a-135">例如：</span><span class="sxs-lookup"><span data-stu-id="2e91a-135">For example:</span></span>  
  
```  
B4200310.F4211FSBeginDoc.szBusinessUnit  
```  
  
 <span data-ttu-id="2e91a-136">對於屬於相同商務模組的一組商務功能，可以跨部分或全部商務功能來共用命名相似 (類型相同) 的引數。</span><span class="sxs-lookup"><span data-stu-id="2e91a-136">For a set of business functions belonging to the same business module, like-named arguments (of the same type) are shared across some or all of the business functions.</span></span> <span data-ttu-id="2e91a-137">您可以使用萬用字元 (*)，而不是商務功能名稱。</span><span class="sxs-lookup"><span data-stu-id="2e91a-137">You can use the wildcard character (*) instead of the business function name.</span></span> <span data-ttu-id="2e91a-138">例如：</span><span class="sxs-lookup"><span data-stu-id="2e91a-138">For example:</span></span>  
  
```  
B4200310.*.szBusinessUnit  
```  
  
> [!NOTE]
>  <span data-ttu-id="2e91a-139">將 JD Edwards OneWorld 商務程序匯入其他電腦時，您必須手動複製 jdearglist.txt。</span><span class="sxs-lookup"><span data-stu-id="2e91a-139">When importing a JD Edwards OneWorld business process to another computer, you must copy jdearglist.txt manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e91a-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e91a-140">See Also</span></span>  
 <span data-ttu-id="2e91a-141">[在 Jdearglist 中設定字串左右對齊](../core/setting-string-justification-in-jdearglist.md) </span><span class="sxs-lookup"><span data-stu-id="2e91a-141">[Setting String Justification in Jdearglist](../core/setting-string-justification-in-jdearglist.md) </span></span>  
 [<span data-ttu-id="2e91a-142">附錄 a： 資料類型</span><span class="sxs-lookup"><span data-stu-id="2e91a-142">Appendix A: Data Types</span></span>](../core/appendix-a-data-types.md)