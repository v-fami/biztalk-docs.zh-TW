---
title: "建立 Web 服務與 Web 方法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, publishing
- Web services, schemas
- orchestrations, naming conventions
- Web services, naming conventions
- schemas, Web services
ms.assetid: a7c47000-501c-47b1-bafa-82370585c1db
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74065489e427ae0612897f1f333e3c8e154a535f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-web-services-and-web-methods"></a><span data-ttu-id="44927-102">建立 Web 服務與 Web 方法</span><span class="sxs-lookup"><span data-stu-id="44927-102">Creating Web Services and Web Methods</span></span>
<span data-ttu-id="44927-103">將結構描述發佈為 Web 服務時，您會在 [BizTalk Web 服務發佈精靈] 中控制 Web 服務與 Web 方法的建立。</span><span class="sxs-lookup"><span data-stu-id="44927-103">When you publish schemas as a Web service, you control the creation of Web services and Web methods in the BizTalk Web Services Publishing Wizard.</span></span> <span data-ttu-id="44927-104">您可以在 Web 服務頁面上可用的樹狀結構中，將 Web 服務描述、Web 服務和 Web 方法重新命名。</span><span class="sxs-lookup"><span data-stu-id="44927-104">You can rename the Web service description, Web service and Web method inside the tree available on the Web Services page.</span></span> <span data-ttu-id="44927-105">您可以新增和移除 Web 服務與 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="44927-105">You can add and remove Web services and Web methods.</span></span> <span data-ttu-id="44927-106">精靈會使用所選要求結構描述的根項目名稱，當作輸入參數名稱。</span><span class="sxs-lookup"><span data-stu-id="44927-106">The wizard uses the root element names of the selected request schemas as the input parameter name.</span></span> <span data-ttu-id="44927-107">Web 方法的傳回值會傳回回應結構描述。</span><span class="sxs-lookup"><span data-stu-id="44927-107">The Web method return value returns the response schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44927-108">ASP.NET Web 用戶端可能會合併相同型別的 in 和 out 參數，以變更 Web 方法簽章。</span><span class="sxs-lookup"><span data-stu-id="44927-108">ASP.NET Web clients may change the Web method signature by combining the in and out parameters of the same type.</span></span> <span data-ttu-id="44927-109">例如，ASP.NET Web 用戶端可能會變更 BizTalk Web 方法，從**string myService （字串一部分）**至**void myService （ref 字串的一部分）**。</span><span class="sxs-lookup"><span data-stu-id="44927-109">For example, an ASP.NET Web client may change a BizTalk Web method from **string myService(string part)** to **void myService(ref string part)**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44927-110">如果您收到定義為單向連接埠、 Web 方法回應型別是**void**和 Web 用戶端傳回任何資訊。</span><span class="sxs-lookup"><span data-stu-id="44927-110">If your receive port is defined as one-way, the Web method response type is **void** and no information is returned to the Web client.</span></span> <span data-ttu-id="44927-111">SOAP 配接器和協調流程，不會將所擲回的例外狀況傳回 Web 用戶端。</span><span class="sxs-lookup"><span data-stu-id="44927-111">The SOAP adapter and orchestration do not return thrown exceptions to the Web client.</span></span>  
  
## <a name="web-services-naming-conventions-for-published-orchestrations"></a><span data-ttu-id="44927-112">已發佈協調流程的 Web 服務命名慣例</span><span class="sxs-lookup"><span data-stu-id="44927-112">Web services naming conventions for published orchestrations</span></span>  
 <span data-ttu-id="44927-113">[BizTalk Web 服務發佈精靈] 會根據您在 [Web 服務] 頁面中所定義的 Web 服務描述，產生 Web 服務 (.asmx) 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="44927-113">The BizTalk Web Services Publishing Wizard generates Web service (.asmx) file names based on the Web services description that you define in the Web Service page.</span></span> <span data-ttu-id="44927-114">下列資料表會顯示 Web 服務檔案名稱的預設值。</span><span class="sxs-lookup"><span data-stu-id="44927-114">The following table shows the default values for the Web service file names.</span></span>  
  
|<span data-ttu-id="44927-115">產生的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="44927-115">Generated Web service</span></span>|<span data-ttu-id="44927-116">檔案名稱</span><span class="sxs-lookup"><span data-stu-id="44927-116">File name</span></span>|  
|---------------------------|---------------|  
|<span data-ttu-id="44927-117">BizTalkWebService</span><span class="sxs-lookup"><span data-stu-id="44927-117">BizTalkWebService</span></span>|<span data-ttu-id="44927-118">Visual Studio Web 服務專案名稱</span><span class="sxs-lookup"><span data-stu-id="44927-118">Visual Studio Web Service project name</span></span>|  
|<span data-ttu-id="44927-119">WebService1</span><span class="sxs-lookup"><span data-stu-id="44927-119">WebService1</span></span>|<span data-ttu-id="44927-120">Web 服務 (.asmx) 檔案名稱</span><span class="sxs-lookup"><span data-stu-id="44927-120">Web service (.asmx) file name</span></span>|  
|<span data-ttu-id="44927-121">WebMethod1</span><span class="sxs-lookup"><span data-stu-id="44927-121">WebMethod1</span></span>|<span data-ttu-id="44927-122">Web 方法名稱</span><span class="sxs-lookup"><span data-stu-id="44927-122">Web method name</span></span>|  
  
 <span data-ttu-id="44927-123">所產生的 Web 服務不會反映剩餘節點的名稱。</span><span class="sxs-lookup"><span data-stu-id="44927-123">The generated Web service does not reflect the names of the remaining nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44927-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44927-124">See Also</span></span>  
 <span data-ttu-id="44927-125">[結構描述發佈為 Web 服務](../core/publishing-schemas-as-a-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="44927-125">[Publishing Schemas as a Web Service](../core/publishing-schemas-as-a-web-service.md) </span></span>  
 [<span data-ttu-id="44927-126">如何使用 BizTalk Web 服務發佈精靈將結構描述發佈為 Web 服務</span><span class="sxs-lookup"><span data-stu-id="44927-126">How to Use the BizTalk Web Services Publishing Wizard to Publish Schemas as a Web Service</span></span>](../core/publish-schemas-as-web-services-with-biztalk-web-services-publishing-wizard.md)