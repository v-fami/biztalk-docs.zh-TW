---
title: 資料庫容錯移轉支援 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 09347fdd-2929-4ed9-b0d8-698508663ecd
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3bbc795191eb2c13ca35d55846719cebc20d61a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238630"
---
# <a name="database-failover-support"></a><span data-ttu-id="acdc3-102">對資料庫容錯移轉的支援</span><span class="sxs-lookup"><span data-stu-id="acdc3-102">Database Failover Support</span></span>
<span data-ttu-id="acdc3-103">您可以將傳遞的執行個體**PolicyFetchErrorHandler**委派做為參數的多載建構函式**原則**類別。</span><span class="sxs-lookup"><span data-stu-id="acdc3-103">You can pass an instance of the **PolicyFetchErrorHandler** delegate as a parameter to overloaded constructors of the **Policy** class.</span></span> <span data-ttu-id="acdc3-104">從資料庫提取原則詳細資訊而發生錯誤時，便會叫用委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="acdc3-104">When an error occurs while fetching the policy details from the database, the delegate instance is invoked.</span></span> <span data-ttu-id="acdc3-105">您也可以使用 try-catch 區塊來捕捉**RuleStoreConnectionException**和**RuleStoreCompatibilityException**規則引擎無法連線至規則引擎時引發的例外狀況資料庫。</span><span class="sxs-lookup"><span data-stu-id="acdc3-105">You can also use a try-catch block to trap **RuleStoreConnectionException** and **RuleStoreCompatibilityException** exceptions that are raised when the rule engine fails to connect to the Rule Engine database.</span></span>  
  
 <span data-ttu-id="acdc3-106">如果您不傳遞的執行個體**PolicyFetchErrorHandler**委派的參數為**原則**建構函式，或如果您使用**CallRules**圖形中協調流程，然後，如果錯誤發生時從資料庫提取原則詳細資料發生下列事件：</span><span class="sxs-lookup"><span data-stu-id="acdc3-106">If you do not pass an instance of the **PolicyFetchErrorHandler** delegate as a parameter to the **Policy** constructor, or if you use the **CallRules** shape in an orchestration, then if an error occurs while fetching the policy details from the database, the following events happen:</span></span>  
  
1.  <span data-ttu-id="acdc3-107">規則引擎會使用值**PolicyFetchErrorHandlerAssembly**和**PolicyFetchErrorHandlerClass**下的登錄項目**HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**。</span><span class="sxs-lookup"><span data-stu-id="acdc3-107">The rule engine uses the values of the **PolicyFetchErrorHandlerAssembly** and **PolicyFetchErrorHandlerClass** registry entries under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**.</span></span> <span data-ttu-id="acdc3-108">預設值**PolicyFetchErrorHandlerAssembly**和**PolicyFetchErrorHandlerClass**登錄項目是**Microsoft.BizTalk.RuleEngineExtensions**和**Microsoft.BizTalk.RuleEngineExtension.ExceptionHelper**分別。</span><span class="sxs-lookup"><span data-stu-id="acdc3-108">The default values for the **PolicyFetchErrorHandlerAssembly** and **PolicyFetchErrorHandlerClass** registry entries are **Microsoft.BizTalk.RuleEngineExtensions** and **Microsoft.BizTalk.RuleEngineExtension.ExceptionHelper** respectively.</span></span>  
  
2.  <span data-ttu-id="acdc3-109">**ExceptionHelper**類別會實作**IPolicyFetchErrorMaker**介面。</span><span class="sxs-lookup"><span data-stu-id="acdc3-109">The **ExceptionHelper** class implements the **IPolicyFetchErrorMaker** interface.</span></span>  
  
3.  <span data-ttu-id="acdc3-110">規則引擎會叫用**ipolicyfetcherrormaker**方法**IPolicyFetchErrorMaker**介面來取得錯誤處理方法的指標，並叫用它。</span><span class="sxs-lookup"><span data-stu-id="acdc3-110">The rule engine invokes the **get_ErrorHandler** method on the **IPolicyFetchErrorMaker** interface to get a pointer to the error-handling method and invokes it.</span></span>  
  
4.  <span data-ttu-id="acdc3-111">預設錯誤處理方法會叫用**SetDBFailure**方法，定義於 BTSDBAccessor.dll 中。</span><span class="sxs-lookup"><span data-stu-id="acdc3-111">The default error-handling method invokes the **SetDBFailure** method, which is defined in BTSDBAccessor.dll.</span></span>  
  
5.  <span data-ttu-id="acdc3-112">**SetDBFailure**方法會導致 BizTalk 服務關閉。</span><span class="sxs-lookup"><span data-stu-id="acdc3-112">The **SetDBFailure** method causes the BizTalk service to shut down.</span></span> <span data-ttu-id="acdc3-113">如果資料庫仍然無法使用，BizTalk 服務會在一分鐘內重新啟動並關閉。</span><span class="sxs-lookup"><span data-stu-id="acdc3-113">The BizTalk service restarts in one minute and shuts down if the databases are still not available.</span></span> <span data-ttu-id="acdc3-114">此循環會不斷重複，直到資料庫可以使用為止。</span><span class="sxs-lookup"><span data-stu-id="acdc3-114">This cycle repeats until the databases are available.</span></span>