---
title: ESB 例外狀況 API 成員 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a095549-7e5d-4a7c-96d2-8fc6ca3efd63
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e267f8533948fc46c4604ebfffb6d22367a321e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295582"
---
# <a name="the-esb-exception-api-members"></a>ESB 例外狀況應用程式開發介面成員
**ESB。ExceptionHandling**組件會公開建立錯誤訊息，並且將管理，然後進行處理時，擷取的公用方法下, 表中所述。  
  
|成員，並使用案例|Description|  
|-------------------------|-----------------|  
|**CreateFaultMessage** [例外狀況處理常式範圍]|**公用靜態 XLANGMessage CreateFaultMessage()** 不採用任何參數。 傳回做為 ESB 錯誤訊息的執行個體**XLANGMessage**填入目前協調流程的名稱，協調流程執行個體識別碼 (GUID) 的執行個體**System.Exception**執行個體，和其他環境屬性。 **注意：** 此應用程式發展介面 (API) 需要被呼叫只會從例外狀況區塊 XLANG 內。|  
|**AddMessage** [例外狀況處理常式範圍]|**公用靜態的 void AddMessage （faultMessage、 existingMessage）** 接受做為參數的兩個**XLANGMessage**執行個體; 第一個是新建的 ESB 錯誤訊息，而且第二個是任何現有的訊息執行個體中協調流程。 方法的錯誤訊息保存現有的訊息執行個體和其訊息內容屬性，並讓其可供擷取使用**GetMessage**方法。 無傳回值。|  
|**SetException** [例外狀況處理常式範圍]|**公用靜態的 void SetException （faultMessage、 例外狀況）** ESB 錯誤訊息，做為接受做為參數**XLANGMessage**執行個體和**例外狀況**為**物件**執行個體。 方法到現有的錯誤訊息的例外狀況持續發生，並讓其可供擷取使用**GetException**方法。 無傳回值。|  
|**GetMessage** [訂閱者/處理器]|**公用靜態 XLANGMessage GetMessage(faultMessage, messageName)** 花費的時間參數 ESB 錯誤訊息從訂用帳戶收到**XLANGMessage**執行個體和 (**字串**) 的先前已加入至錯誤訊息 （在原始的協調流程圖形的例外狀況處理常式） 的訊息名稱。 傳回**XLANGMessage**符合訊息名稱，並包含所有的原始內容屬性，包括任何自訂的升級的屬性的執行個體。|  
|**GetMessages** [訂閱者/處理器]|**公用靜態 MessageCollection GetMessages(faultMessage)** 接受做為在 ESB 錯誤收到的訊息從訂用帳戶的單一參數**XLANGMessage**執行個體。 傳回**MessageCollection**填入所有執行個體**XLANGMessage**先前加入至錯誤訊息 （在原始的協調流程圖形的例外狀況處理常式） 的執行個體。 每個**XLANGMessage**執行個體會包含所有的原始內容屬性，包括任何自訂的升級的屬性。|  
|**GetException** [訂閱者/處理器]|**公用靜態 System.Exception GetException(faultMessage)** 接受做為從訂用帳戶收到錯誤訊息的單一參數**XLANGMessage**執行個體。 傳回**System.Exception**先前加入至錯誤訊息 （在原始的協調流程圖形的例外狀況處理常式） 的物件。|  
|**FaultSeverity** [例外狀況處理常式範圍和訂閱者/處理器]|ESB 錯誤訊息的公用讀取/寫入屬性**XLANGMessage**類別公開的錯誤訊息的嚴重性。 中的值**FaultCodes**列舉型別：**資訊**(0)，**警告**(1)、**錯誤**(2)、**嚴重**(3)，或**重大**(4)。|  
|**MessageCollection** [訂閱者/處理器]|所傳回的訊息集合**GetMessages**方法。 此類別衍生自**ArrayList**實作以允許使用反覆項目列舉值和**MoveNext**方法。|