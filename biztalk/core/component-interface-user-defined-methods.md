---
title: 元件介面使用者定義方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- component interfaces, user-defined methods
- user-defined methods, component interface
- custom component interfaces, limitations
- collection limitations
- custom methods, samples
- samples, custom methods
- component interfaces, limitations for custom CI
ms.assetid: e4b15889-35ff-44aa-819d-eade9690bdd6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68149876dc51d90b4dbc07772fd9b9b5c60fb7db
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022564"
---
# <a name="component-interface-user-defined-methods"></a><span data-ttu-id="d07f6-102">元件介面使用者定義方法</span><span class="sxs-lookup"><span data-stu-id="d07f6-102">Component Interface User-Defined Methods</span></span>
<span data-ttu-id="d07f6-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise 支援在元件介面中使用使用者定義的方法。</span><span class="sxs-lookup"><span data-stu-id="d07f6-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise supports user-defined methods in component interfaces.</span></span> <span data-ttu-id="d07f6-104">簽章的格式如下：</span><span class="sxs-lookup"><span data-stu-id="d07f6-104">The signatures are of the form:</span></span>  
  
```  
myRet=myCI.myMethod(parameter1, parameter2, ...)  
```  
  
 <span data-ttu-id="d07f6-105">其中：</span><span class="sxs-lookup"><span data-stu-id="d07f6-105">where:</span></span>  
  
- <span data-ttu-id="d07f6-106">`parameter1` 和 `parameter2` 為輸入參數。</span><span class="sxs-lookup"><span data-stu-id="d07f6-106">`parameter1`, `parameter2` are input parameters.</span></span>  
  
- <span data-ttu-id="d07f6-107">`myRet` 是傳回的值。</span><span class="sxs-lookup"><span data-stu-id="d07f6-107">`myRet` is the return value.</span></span>  
  
  <span data-ttu-id="d07f6-108">這些參數只能是方法的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="d07f6-108">The parameters can only be input parameters to the method.</span></span> <span data-ttu-id="d07f6-109">只有一個值可以從方法傳回當做傳回參數。</span><span class="sxs-lookup"><span data-stu-id="d07f6-109">Only one value can be returned from the method as the return parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d07f6-110">包含使用者定義方法的元件介面應只啟用 PeopleSoft `Get` 函數。</span><span class="sxs-lookup"><span data-stu-id="d07f6-110">The component interface that contains user-defined methods should only have the PeopleSoft `Get` function enabled.</span></span> <span data-ttu-id="d07f6-111">如果元件介面有索引鍵，自訂方法就無法運作。</span><span class="sxs-lookup"><span data-stu-id="d07f6-111">If the component interface has keys, then custom methods will not work.</span></span>  
  
## <a name="custom-ci-limitation"></a><span data-ttu-id="d07f6-112">自訂 CI 限制</span><span class="sxs-lookup"><span data-stu-id="d07f6-112">Custom CI Limitation</span></span>  
 <span data-ttu-id="d07f6-113">BizTalk Adapter for PeopleSoft Enterprise 可以處理所提供的自訂 PeopleSoft 方法，但元件介面不能有索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d07f6-113">BizTalk Adapter for PeopleSoft Enterprise can handle custom PeopleSoft methods provided that the component interface does not have keys.</span></span> <span data-ttu-id="d07f6-114">如果元件介面有索引鍵，自訂方法就無法運作。</span><span class="sxs-lookup"><span data-stu-id="d07f6-114">If the component interface has keys, custom methods will not work.</span></span>  
  
### <a name="workaround"></a><span data-ttu-id="d07f6-115">解決方式</span><span class="sxs-lookup"><span data-stu-id="d07f6-115">Workaround</span></span>  
 <span data-ttu-id="d07f6-116">建立一個沒有索引鍵的新元件介面，然後寫入將索引鍵併為呼叫參數一部分的新自訂方法。</span><span class="sxs-lookup"><span data-stu-id="d07f6-116">Create a new component interface that does not have keys, and write a new custom method that incorporates the keys as part of the calling parameters.</span></span> <span data-ttu-id="d07f6-117">例如，您可以在 USER_PROFILE 元件介面中使用 SetPassword 自訂方法；但 USER_PROFILE 有索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d07f6-117">For example, you could use the SetPassword custom method in the USER_PROFILE component interface; however USER_PROFILE has keys.</span></span> <span data-ttu-id="d07f6-118">您可以建立一個沒有索引鍵的新元件介面，然後在新元件介面中建立自訂的方法。</span><span class="sxs-lookup"><span data-stu-id="d07f6-118">You can create a new component interface that has no keys, and then create a custom method in your new component interface.</span></span> <span data-ttu-id="d07f6-119">這個方法會接受兩個參數、使用者識別碼和密碼。</span><span class="sxs-lookup"><span data-stu-id="d07f6-119">This method would accept two parameters, user ID and password.</span></span> <span data-ttu-id="d07f6-120">自訂的方法接著就可以使用 `Get` 叫用 USER_PROFILE，然後再叫用 `SetPassword`。</span><span class="sxs-lookup"><span data-stu-id="d07f6-120">The custom method could then invoke USER_PROFILE with a `Get` and then invoke `SetPassword`.</span></span> <span data-ttu-id="d07f6-121">如需詳細資訊，請參閱 PeopleSoft 文件。</span><span class="sxs-lookup"><span data-stu-id="d07f6-121">Consult the PeopleSoft documentation for more details.</span></span>  
  
 <span data-ttu-id="d07f6-122">因為 PeopleSoft 中的限制，使用者定義的方法中出現的 `Date`、`DateTime` 和 `Time` 類型在用戶端程式碼中會對應為字串。</span><span class="sxs-lookup"><span data-stu-id="d07f6-122">Due to a limitation in PeopleSoft, `Date`, `DateTime`, and `Time` types appearing in user-defined methods are mapped as strings in the client code.</span></span>  
  
## <a name="collection-limitation"></a><span data-ttu-id="d07f6-123">集合限制</span><span class="sxs-lookup"><span data-stu-id="d07f6-123">Collection Limitation</span></span>  
 <span data-ttu-id="d07f6-124">使用者定義的方法無法傳回集合，甚至是任何 API 物件。</span><span class="sxs-lookup"><span data-stu-id="d07f6-124">User-defined methods cannot return a collection, or more generally, any API object.</span></span> <span data-ttu-id="d07f6-125">這表示 您只能傳回簡單類型，例如字串和數字。</span><span class="sxs-lookup"><span data-stu-id="d07f6-125">This means that you can only return simple types, for example, strings and numbers.</span></span> <span data-ttu-id="d07f6-126">避開這個限制的一個方法是，以 XML 字串形式傳送集合，並將用戶端寫成剖析這個字串以用正確格式來擷取項目。</span><span class="sxs-lookup"><span data-stu-id="d07f6-126">You can get around this limitation by sending a collection as an XML string and programming the client to parse the strings to extract the items into the correct format.</span></span> <span data-ttu-id="d07f6-127">您可以檢視 GET_CI_INFO 自訂元件介面，以查看這個解決方法的範例。</span><span class="sxs-lookup"><span data-stu-id="d07f6-127">You can examine the GET_CI_INFO custom component interface to see an example of this workaround.</span></span>  
  
## <a name="sample-custom-method"></a><span data-ttu-id="d07f6-128">自訂方法範例</span><span class="sxs-lookup"><span data-stu-id="d07f6-128">Sample Custom Method</span></span>  
 <span data-ttu-id="d07f6-129">您可以使用下列的基本自訂方法 SayHello，測試您的元件介面使用自訂方法的功能。</span><span class="sxs-lookup"><span data-stu-id="d07f6-129">You can use the following basic custom method, SayHello, to test the functionality of your component interface using custom methods.</span></span>  
  
 <span data-ttu-id="d07f6-130">下列 PeopleCode 函式是 ACB_EMPLOYEE 這個 PeopleSoft 元件介面的使用者定義方法。</span><span class="sxs-lookup"><span data-stu-id="d07f6-130">The following PeopleCode function is a user-defined method of a PeopleSoft component interface named ACB_EMPLOYEE.</span></span> <span data-ttu-id="d07f6-131">範例會傳回字串，其中傳回的值是**Hello**後面輸入參數的值。</span><span class="sxs-lookup"><span data-stu-id="d07f6-131">The sample returns a string where the return value is **Hello** followed by the value of the input parameter.</span></span>  
  
```  
Function SayHello(&sName As string) Returns string  
      &EOL = Char(10);  
      &sResult = "Hello " | &sName | &EOL;  
      Return &sResult;  
End-Function;  
```  
  
> [!NOTE]
>  <span data-ttu-id="d07f6-132">若要同時 (使用一個命令) 修改多個表格，您可以建立另一個元件介面，或是建立一個元件介面使用者定義方法。</span><span class="sxs-lookup"><span data-stu-id="d07f6-132">To modify multiple tables at the same time (using one command) you can either create another component interface or create a component interface user-defined method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d07f6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d07f6-133">See Also</span></span>  
 [<span data-ttu-id="d07f6-134">附錄 A：元件介面方法</span><span class="sxs-lookup"><span data-stu-id="d07f6-134">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)