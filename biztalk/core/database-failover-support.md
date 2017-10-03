---
title: "資料庫容錯移轉支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09347fdd-2929-4ed9-b0d8-698508663ecd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3bbc795191eb2c13ca35d55846719cebc20d61a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="database-failover-support"></a>對資料庫容錯移轉的支援
您可以將傳遞的執行個體**PolicyFetchErrorHandler**委派做為參數的多載建構函式**原則**類別。 從資料庫提取原則詳細資訊而發生錯誤時，便會叫用委派執行個體。 您也可以使用 try-catch 區塊來捕捉**RuleStoreConnectionException**和**RuleStoreCompatibilityException**規則引擎無法連線至規則引擎時引發的例外狀況資料庫。  
  
 如果您不傳遞的執行個體**PolicyFetchErrorHandler**委派的參數為**原則**建構函式，或如果您使用**CallRules**圖形中協調流程，然後，如果錯誤發生時從資料庫提取原則詳細資料發生下列事件：  
  
1.  規則引擎會使用值**PolicyFetchErrorHandlerAssembly**和**PolicyFetchErrorHandlerClass**下的登錄項目**HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**。 預設值**PolicyFetchErrorHandlerAssembly**和**PolicyFetchErrorHandlerClass**登錄項目是**Microsoft.BizTalk.RuleEngineExtensions**和**Microsoft.BizTalk.RuleEngineExtension.ExceptionHelper**分別。  
  
2.  **ExceptionHelper**類別會實作**IPolicyFetchErrorMaker**介面。  
  
3.  規則引擎會叫用**ipolicyfetcherrormaker**方法**IPolicyFetchErrorMaker**介面來取得錯誤處理方法的指標，並叫用它。  
  
4.  預設錯誤處理方法會叫用**SetDBFailure**方法，定義於 BTSDBAccessor.dll 中。  
  
5.  **SetDBFailure**方法會導致 BizTalk 服務關閉。 如果資料庫仍然無法使用，BizTalk 服務會在一分鐘內重新啟動並關閉。 此循環會不斷重複，直到資料庫可以使用為止。