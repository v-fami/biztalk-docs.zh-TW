---
title: ExceptionHandler 協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors, systems
- errors, applications
- applications, errors
- orchestrations, errors [process management solutions]
- process management solution tutorial, errors
ms.assetid: ac154e76-9dfe-433a-948b-e098df705fe5
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1b79a1c6d9e6fada206ba0298913fe8f369783c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22280022"
---
# <a name="the-exceptionhandler-orchestration"></a>ExceptionHandler 協調流程
商務程序管理解決方案會使用兩種類型的例外狀況： 系統例外狀況和應用程式例外狀況。 系統例外狀況像是資源錯誤—例如網路連線失敗。 在一段時間後，這些問題有可能會自己解決，所以解決方案會重試造成系統例外狀況的所有作業。 應用程式例外狀況產生的問題較不易自行解決，如邏輯錯誤或某種形式的不一致。 解決方案會使用**ExceptionHandlerOrch**協調流程來處理系統和應用程式錯誤。  
  
 訂單處理階段 (**CableOrder1**， **CableOrder2**) 和其附屬協調流程 (**Activate**，**分析**， **取消**，**變更**，**完成**，**驗證**) 所有使用**ExceptionHandlerOrch**。  
  
> [!NOTE]
>  您可能想要閱讀本節**ExceptionHandlerOrch**協調流程開啟 microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
## <a name="application-errors"></a>應用程式錯誤  
 第一次呼叫來記錄錯誤的例外狀況處理常式**Utilities**方法**ErrorHandler**物件存放至**公用程式**組件。 然後，例外狀況處理常式測試錯誤為系統錯誤或應用程式錯誤。 下列擷取畫面顯示處理應用程式例外狀況的協調流程分支：  
  
 ![ExceptionHandler 協調流程的應用程式分支](../core/media/applicationerrorbranchofexceptionhandler.gif "ApplicationErrorBranchofExceptionHandler")  
  
 表示應用程式錯誤，協調流程會建構字串，描述錯誤並呼叫**ErrorHandlerOrch**協調流程。 此協調流程將錯誤傳送給作業，其中運算子決定要修復錯誤或終止作業。 若運算子修復錯誤，修復的訊息會從 ErrorHandlerOrch 協調流程傳回，並重試作業。 例外狀況處理常式會藉由呼叫**Invoke**方法**Recaller**物件存放至**公用程式**組件。 **Recaller**物件使用反映以呼叫造成錯誤的程式碼。  
  
 如果呼叫**Invoke**成功，例外狀況處理常式會結束。 否則，它回執行迴圈，並嘗試呼叫**Invoke**一次。 如需有關**Recaller**物件，請參閱[Recaller 物件](../core/the-recaller-object.md)。  
  
## <a name="system-errors"></a>系統錯誤  
 下圖顯示的系統錯誤分支**ExceptionHandler**協調流程：  
  
 ![ExceptionHandler 協調流程的系統錯誤](../core/media/systemerrorbranchofexceptionhandler.gif "SystemErrorBranchofExceptionHandler")  
  
 針對系統錯誤，例外狀況處理常式會先呼叫**CheckInterrupt**協調流程，然後等候一分鐘。 等候的時間可先清除暫時短暫的錯誤 (如網路連線問題)，再進行重試。 在進行遠端呼叫時，常有可能會發生網路問題。  
  
> [!NOTE]
>  在可中斷的設計中，一般的規則是在任何等待時間期間或之後立即測試是否有中斷的情形發生。  
  
 等候之後, 處理常式使用**Invoke**方法**Recaller**執行原始的程式碼的物件。 若呼叫成功，就會結束處理常式。 否則，處理常式會再試著執行兩次原始程式碼。 如果所有的三次嘗試失敗，處理常式會建構錯誤字串，並呼叫**ErrorHandlerOrch**協調流程。  
  
 如果處理系統例外狀況時造成例外狀況，例外狀況區塊將會取得此例外狀況：  
  
 ![系統錯誤分支的例外狀況處理常式](../core/media/exceptionhandlerofsystemerrorbranch.gif "ExceptionHandlerofSystemErrorBranch")  
  
 例外狀況處理常式會測試例外狀況的類型；如果是系統例外狀況，就遞減重試計數器；否則，設定旗標以表示其為應用程式例外狀況。  
  
## <a name="the-errorhandlerorch-orchestration"></a>ErrorHandlerOrch 協調流程  
 下圖顯示的第一個部分**ErrorHandlerOrch**協調流程：  
  
 ![錯誤處理常式協調流程中，第一個部分](../core/media/errorhandlerfirstpart.gif "ErrorHandlerFirstPart")  
  
 **ErrorHandlerOrch**協調流程會先測試**IsBadOrder**參數，以查看錯誤是錯誤的訂單 (**IsBadOrder**為 true) 或其他一些錯誤。 若錯誤是錯誤的訂單，協調流程會從原始的訂單傳回位址以指定訊息的目的地，然後將訊息傳回到客戶服務系統。 若錯誤不是錯誤的訂單，協調流程會建立訂單錯誤訊息，並將它傳送到作業系統。  
  
 發生上述其中一種錯誤後，協調流程會接聽回應訊息或中斷訊息：  
  
 ![錯誤處理常式的第二個部分](../core/media/errorhandlersecondpart.gif "ErrorHandlerSecondPart")  
  
 若協調流程收到回應，會將回應傳回呼叫者。 如果協調流程收到中斷訊息，將訊息傳遞到中斷連接埠，並擲出自**InterruptException**。  
  
 如需解決方案如何使用和處理中斷的詳細資訊，請參閱[中斷商務程序管理解決方案中處理](../core/interrupt-handling-in-the-business-process-management-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在商務程序管理解決方案中處理的例外狀況](../core/exception-handling-in-the-business-process-management-solution.md)   
 [自訂例外狀況](../core/custom-exceptions.md)   
 [中斷商務程序管理解決方案中的處理](../core/interrupt-handling-in-the-business-process-management-solution.md)   
 [Recaller 物件](../core/the-recaller-object.md)