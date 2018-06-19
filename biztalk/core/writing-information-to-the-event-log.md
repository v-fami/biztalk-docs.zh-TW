---
title: 將資訊寫入至事件記錄檔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d7398dc-29d8-4a7a-bab4-c8f128b47dca
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f848cafd6ee9247511db3b9a6dad7dc5da91236b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289574"
---
# <a name="writing-information-to-the-event-log"></a>將資訊寫入事件日誌
您可能會想要將資訊寫入預設的應用程式日誌或自訂的事件日誌，以便監視 BizTalk 應用程式中不同商務程序的進度。 寫入事件日誌，在下列實例中可能會很有用：  
  
-   您想要使用 Windows 提供的工具，以標準的方式存取應用程式訊息。  
  
-   您想要將資訊與來自伺服器環境的其他訊息一起封存，做成更完整的歷程記錄。  
  
-   您希望能夠使用可與事件日誌互動的工具來監視應用程式。  
  
> [!NOTE]
>  System.Diagnostics.EventLog.WriteEntry 方法對訊息字串有大小限制。 如果訊息字串超過 32766 個位元組，就會收到例外狀況。  
  
## <a name="writing-to-the-application-log"></a>寫入應用程式日誌  
 您可以撰寫應用程式記錄檔或任何其他記錄檔從您的程式碼使用**System.Diagnostics.EventLog**下列所示：  
  
```  
System.Diagnostics.EventLog.WriteEntry("Orchestration Debug", System.String.Format("The Value = {0}", iResult));  
```  
  
 您還可以這麼做：  
  
```  
EventLog appLog = new EventLog();   
appLog.Source = "This Application's Name";  
appLog.WriteEntry("An entry to the Application event log.");  
```  
  
 如果您使用自訂的記錄檔，您應該使用**SourceExists**方法，以確保它存在之前您寫入。  
  
## <a name="writing-to-a-custom-log"></a>寫入自訂日誌  
 寫入自訂日誌的方式與寫入應用程式日誌相同，但是有一點除外，就是您必須先建立自訂日誌。 建立自訂日誌的程式碼十分簡單：  
  
```  
// Create the source, if it does not already exist. if(!EventLog.SourceExists("MySource"))   
{   
  //An event log source should not be created and immediately used.  
  //There is a latency time to enable the source, it should be created  
  //prior to executing the application that uses the source.  
  EventLog.CreateEventSource("MySource", "MyNewLog");  
}  
```  
  
 但是，您不應該假設您的程式碼會在具有安全性權限的帳戶下執行，而建立新的事件日誌。 建立事件日誌需要系統管理員權限，而且應該在個別的公用程式中進行，或者最好是成為 .msi 安裝的一部分。 如需使用自訂指令碼包含匯出的.msi 安裝的詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。