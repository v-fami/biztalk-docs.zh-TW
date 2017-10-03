---
title: "支援前置 0 量欄位驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- amounts, amount fields
- amounts, leading zeros
- validating, amount fields
ms.assetid: 7c202422-019f-43da-9c2a-4b9fdf0b2859
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1de45b5acbc780fad0847ab207d0d5c72ca2a652
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="supporting-leading-zeros-in-amount-field-validations"></a><span data-ttu-id="8a157-102">支援前置 0 量欄位驗證</span><span class="sxs-lookup"><span data-stu-id="8a157-102">Supporting Leading Zeros in Amount Field Validations</span></span>
<span data-ttu-id="8a157-103">某些訊息類型的驗證原則數量欄位上執行驗證。</span><span class="sxs-lookup"><span data-stu-id="8a157-103">The validation policies of some message types perform validations on Amount fields.</span></span> <span data-ttu-id="8a157-104">若要啟用數量 欄位中的前置零，您必須編輯訊息類型的驗證原則。</span><span class="sxs-lookup"><span data-stu-id="8a157-104">To enable leading zeros in Amount fields, you must edit the validation policy for the message type.</span></span> <span data-ttu-id="8a157-105">您可以建立新版本的預設的驗證原則，並編輯 [商務規則編輯器] 中的引數，或在部署原則之前，您可以編輯預設原則，以手動方式在文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="8a157-105">You can create a new version of the default validation policy, and edit the argument in the Business Rule Composer, or you can edit the default policy manually in a text editor before the policy is deployed.</span></span>  
  
 <span data-ttu-id="8a157-106">下表列出啟用或停用前置零的方法。</span><span class="sxs-lookup"><span data-stu-id="8a157-106">The following table lists the methods that enable or disable leading zeros.</span></span> <span data-ttu-id="8a157-107">此資料表也會指出您需要設定的方法中引數的序數。</span><span class="sxs-lookup"><span data-stu-id="8a157-107">The table also indicates the ordinal number of the argument that you need to set in the method.</span></span> <span data-ttu-id="8a157-108">將它設定為 true 以啟用前置零，或設為 False 可停用它們。</span><span class="sxs-lookup"><span data-stu-id="8a157-108">Set it to True to enable leading zeros, or to False to disable them.</span></span>  
  
|<span data-ttu-id="8a157-109">方法</span><span class="sxs-lookup"><span data-stu-id="8a157-109">Method</span></span>|<span data-ttu-id="8a157-110">引數數目</span><span class="sxs-lookup"><span data-stu-id="8a157-110">Argument number</span></span>|  
|------------|---------------------|  
|<span data-ttu-id="8a157-111">**CheckValidAmount**</span><span class="sxs-lookup"><span data-stu-id="8a157-111">**CheckValidAmount**</span></span>|<span data-ttu-id="8a157-112">6</span><span class="sxs-lookup"><span data-stu-id="8a157-112">6</span></span>|  
|<span data-ttu-id="8a157-113">**CheckCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="8a157-113">**CheckCurrencyAmount**</span></span>|<span data-ttu-id="8a157-114">4</span><span class="sxs-lookup"><span data-stu-id="8a157-114">4</span></span>|  
|<span data-ttu-id="8a157-115">**CheckValidSignCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="8a157-115">**CheckValidSignCurrencyAmount**</span></span>|<span data-ttu-id="8a157-116">3</span><span class="sxs-lookup"><span data-stu-id="8a157-116">3</span></span>|  
|<span data-ttu-id="8a157-117">**CheckValidSignDateCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="8a157-117">**CheckValidSignDateCurrencyAmount**</span></span>|<span data-ttu-id="8a157-118">4</span><span class="sxs-lookup"><span data-stu-id="8a157-118">4</span></span>|  
|<span data-ttu-id="8a157-119">**IsValidTransactionDetailsCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="8a157-119">**IsValidTransactionDetailsCurrencyAmount**</span></span>|<span data-ttu-id="8a157-120">4</span><span class="sxs-lookup"><span data-stu-id="8a157-120">4</span></span>|  
  
 <span data-ttu-id="8a157-121">上表中的每個方法都包含在一個或多個訊息驗證原則。</span><span class="sxs-lookup"><span data-stu-id="8a157-121">Each method in the preceding table is contained in one or more message validation policies.</span></span> <span data-ttu-id="8a157-122">若要在原則中設定引數，您必須搜尋上以確認原則是否包含它的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="8a157-122">To set the argument in a policy, you must search on the method name to verify whether the policy contains it.</span></span> <span data-ttu-id="8a157-123">一種方法可能會多次出現在訊息的原則。</span><span class="sxs-lookup"><span data-stu-id="8a157-123">A method may appear multiple times in a message's policy.</span></span>  
  
### <a name="to-enable-or-disable-leading-zeros"></a><span data-ttu-id="8a157-124">若要啟用或停用前置的零</span><span class="sxs-lookup"><span data-stu-id="8a157-124">To enable or disable leading zeros</span></span>  
  
1.  <span data-ttu-id="8a157-125">開啟文字編輯器，例如 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="8a157-125">Open a text editor, such as Notepad.</span></span>  
  
2.  <span data-ttu-id="8a157-126">在編輯器中，瀏覽至您要啟用或停用前置零的訊息驗證原則的位置。</span><span class="sxs-lookup"><span data-stu-id="8a157-126">In the editor, browse to the location of the message validation policy in which you want to enable or disable leading zeros.</span></span> <span data-ttu-id="8a157-127">例如，您可以找到訊息驗證原則 MT103 訊息類型，MT103_Validation_Policy.xml，在*\<磁碟機 >*: / 程式檔案/Microsoft BizTalk Accelerator for SWIFT/SWIFT 訊息/類別 1/ MT103。</span><span class="sxs-lookup"><span data-stu-id="8a157-127">For example, you can find the message validation policy for the MT103 message type, MT103_Validation_Policy.xml, in *\<drive>*:/Program Files/Microsoft BizTalk Accelerator for SWIFT/SWIFT Messages/Category 1/MT103.</span></span> <span data-ttu-id="8a157-128">開啟 驗證原則。</span><span class="sxs-lookup"><span data-stu-id="8a157-128">Open the validation policy.</span></span>  
  
3.  <span data-ttu-id="8a157-129">在原則中，搜尋上**CheckValidAmount**方法。</span><span class="sxs-lookup"><span data-stu-id="8a157-129">In the policy, search on the **CheckValidAmount** method.</span></span>  
  
4.  <span data-ttu-id="8a157-130">如果您發現此方法，倒數計時適當的引數。</span><span class="sxs-lookup"><span data-stu-id="8a157-130">If you find the method, count down to the appropriate argument.</span></span> <span data-ttu-id="8a157-131">例如，對於**CheckValidAmount**方法，向第六個引數的計數。</span><span class="sxs-lookup"><span data-stu-id="8a157-131">For example, for the **CheckValidAmount** method, count down to the sixth argument.</span></span> <span data-ttu-id="8a157-132">將引數設**True**啟用前置的零或為 False，則停用它們。</span><span class="sxs-lookup"><span data-stu-id="8a157-132">Set the argument to **True** to enable leading zeros or False to disable them.</span></span>  
  
5.  <span data-ttu-id="8a157-133">重複步驟 3 和 4 上表中每個方法。</span><span class="sxs-lookup"><span data-stu-id="8a157-133">Repeat steps 3 and 4 for each method in the preceding table.</span></span>  
  
6.  <span data-ttu-id="8a157-134">儲存檔案，然後關閉編輯器。</span><span class="sxs-lookup"><span data-stu-id="8a157-134">Save the file, and then close the editor.</span></span>