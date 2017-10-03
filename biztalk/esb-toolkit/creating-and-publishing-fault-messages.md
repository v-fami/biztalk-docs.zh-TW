---
title: "建立和發佈錯誤訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc7ba1d9-b647-4cba-a3dc-4400505ff51f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57833cefedcf53b7355c17cf97d429d2eb988819
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-publishing-fault-messages"></a>建立並發佈錯誤訊息
為了協助您了解如何使用來管理例外狀況的例外狀況管理架構的功能，本節會說明常見的案例，根據訊息提交至 ESB 應用程式。  
  
 情節是由使用者提交到系統發票所組成。 處理協調流程中的發票的過程中，「 BizTalk 商務規則引擎擲回應用程式例外狀況，因為資料的某些部分不正確。 商務程序應該攔截例外狀況，將有問題的訊息傳送至另一個人或系統，可以修正該訊息，然後再重新提交訊息以進行處理。  
  
 使用 ESB 無法協調流程的例外狀況路由的功能時，程序步驟如下所示：  
  
1.  例外狀況處理常式中的程式碼偵測到錯誤，並藉由呼叫建立的錯誤訊息**CreateFaultMessage**方法，如下列程式碼範例所示。  
  
    ```csharp  
    // Create fault exception message.  
    faultMsg = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.CreateFaultMessage();  
    ```  
  
2.  ESB 例外狀況機制會自動插入錯誤描述的錯誤訊息內容 （例如，「 商務規則引擎時擲回除以零的錯誤處理 LoanProcessing 原則。"）。  
  
3.  ESB 例外狀況機制自動將特定失敗的屬性和應用程式特有的屬性升級為錯誤訊息內容，並從目前的環境中設定的值。 這些屬性如下所示：  
  
    -   **應用程式**（自動填入）  
  
    -   **DateTime** （自動擴展以 UTC 值）  
  
    -   **描述**(自動填入，例外狀況訊息)  
  
    -   **ErrorType** (自動填入，例外狀況型別)  
  
    -   **MachineName** (自動填入內容，目前的伺服器名稱)  
  
    -   **範圍**(自動填入內容-「 範圍 」 圖形，其中包含目前的例外狀況處理常式)  
  
    -   **ServiceName** (自動填入，協調流程的名稱)  
  
    -   **ServiceInstanceID**(自動填入，協調流程執行個體識別碼，做為 GUID)  
  
4.  例外狀況處理常式中的程式碼，視需要設定其他錯誤訊息的屬性，如下列程式碼範例所示。  
  
    ```csharp  
    // Set fault message properties.  
    faultMsg.Body.FailureCategory = "MessageBuild";  
    faultMsg.Body.FaultCode = 1000;  
    faultMsg.Body.FaultDescription = "Some error occurred";  
    faultMsg.Body.FaultSeverity =  
       Microsoft.Practices.ESB.ExceptionHandling.FaultSeverity.Severe;  
    ```  
  
5.  ESB 例外狀況機制會自動將序列化目前**例外狀況**成為錯誤訊息物件。  
  
6.  例外狀況處理常式中的程式碼可以選擇性地將目前的協調流程訊息 ESB 錯誤訊息使用**AddMessage （faultMsg、 messageToAdd）**方法。 這個方法會序列化，並保存訊息，包括所有的內容屬性，如下列程式碼範例所示。  
  
    ```csharp  
    // Add other current orchestration messages to the fault message.  
    Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.AddMessage(  
                                faultMsg, approvedRequestMsg);  
    Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.AddMessage(  
                                faultMsg, DeniedRequestMsg, @"c:\temp");  
    ```  
  
7.  例外狀況處理常式中的程式碼將 ESB 錯誤訊息發佈至 Messagebox 資料庫，使用直接繫結連接埠。  
  
8.  如果發行成功，就會發生下列事件：  
  
    -   協調流程或傳送埠訂閱可以處理 ESB 錯誤訊息，並擷取任何加入的訊息、 完成，但其內容屬性值。  
  
    -   全域例外狀況處理常式 （傳送埠） 會自動發佈至 ESB 管理入口網站的 ESB 錯誤訊息。