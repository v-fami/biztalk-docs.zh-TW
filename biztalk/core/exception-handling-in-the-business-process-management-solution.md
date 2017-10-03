---
title: "在商務程序管理解決方案中處理的例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, tutorials
- process management solution tutorial, errors
ms.assetid: ac9fcb33-7dac-448e-88b8-04d4d439ea6a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cd3134b8ed4e2fc6fd4a50d9b64397692ea32b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="exception-handling-in-the-business-process-management-solution"></a>在商務程序管理解決方案中處理的例外狀況
商務程序管理解決方案會使用一個特殊的例外狀況處理協調流程，以及標準的 BizTalk Server 例外狀況處理，來處理配接器、管線、對應及路由失敗，這是一個新的錯誤報告功能。 這個自訂的系統建基於**ExceptionHandler**協調流程。 解決方案會使用**ExceptionHandler**重試作業或重試在暫時問題過後可能會成功呼叫的協調流程。  
  
> [!NOTE]
>  您可以重新使用程式碼從協調流程，例如**Activate**，使用**ExceptionHandler**協調流程。 所有這些協調流程包含標題為範圍**CallingCode**附加**例外狀況**區塊。 中的程式碼取代**CallingCode**範圍與您的程式碼。 **例外狀況**區塊會定義所有變數需要呼叫**ExceptionHandler**協調流程。 編輯指派給變數的值。  
  
 解決方案會使用自訂的例外狀況及數個預先定義的 BizTalk 例外狀況，以在無法復原的錯誤時使用，例如遇到格式錯誤的訂單訊息時。  
  
> [!NOTE]
>  解決方案會使用自訂的配接器來處理某些連接埠上的失敗。 如需配接器的詳細資訊，請參閱[Ops 配接器](../core/the-ops-adapter.md)。  
  
 本章節描述**ExceptionHandler**協調流程和自訂的例外狀況。 本節也會簡短討論解決方案如何利用錯誤報告產品的功能。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [ExceptionHandler 協調流程](../core/the-exceptionhandler-orchestration.md)  
  
-   [自訂例外狀況](../core/custom-exceptions.md)