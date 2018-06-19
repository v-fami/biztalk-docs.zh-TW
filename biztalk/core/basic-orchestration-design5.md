---
title: 基本協調流程 Design5 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, design
- exception handling, orchestration design
ms.assetid: 0941d617-e30c-4ca7-852f-193e16781ca7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 224b8e507fc9319a2a4b66006914b3ebc27a8421
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230846"
---
# <a name="basic-orchestration-design"></a>基本協調流程設計
當您在 BizTalk 配接器中為 PeopleSoft Enterprise 建立基本協調流程時，會在協調流程的接收埠收到 XML。 接著該 XML 會傳送到後端系統進行處理。 在後端系統中可能會發生例外狀況，進而停止協調流程並產生錯誤。 產生的錯誤會提供有關協調流程無法完成的資訊。 這項資訊在偵錯錯誤成因時不是很有幫助。  
  
 ![](../core/media/siebeladapter-15-exceptionhandling-start.gif "SiebelAdapter_15_ExceptionHandling_Start")  
例外狀況處理  
  
 發生錯誤時擱置呼叫。 在稽核記錄中，該呼叫會設定為 FAILED (失敗)。 當您在稽核記錄中以滑鼠右鍵按一下 [失敗] 時，失敗的呼叫會開啟快顯訊息。 按一下報告選取內容，您就會看到該錯誤以及來自後端系統的失敗原因。  
  
 若要防止協調流程進入擱置狀態並要重新導向該錯誤，您可以建立 CatchExpression。 為了截獲後端所產生的例外狀況並協助找出錯誤成因，您可以在協調流程中使用「範圍」圖形。  
  
 ![](../core/media/siebeladapter-16-exceptionhandling-total.gif "SiebelAdapter_16_ExceptionHandling_Total")  
例外狀況處理總覽  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling2.md)