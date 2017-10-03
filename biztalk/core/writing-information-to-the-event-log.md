---
title: "將資訊寫入至事件記錄檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d7398dc-29d8-4a7a-bab4-c8f128b47dca
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f848cafd6ee9247511db3b9a6dad7dc5da91236b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="writing-information-to-the-event-log"></a><span data-ttu-id="55dd3-102">將資訊寫入事件日誌</span><span class="sxs-lookup"><span data-stu-id="55dd3-102">Writing Information to the Event Log</span></span>
<span data-ttu-id="55dd3-103">您可能會想要將資訊寫入預設的應用程式日誌或自訂的事件日誌，以便監視 BizTalk 應用程式中不同商務程序的進度。</span><span class="sxs-lookup"><span data-stu-id="55dd3-103">You may want to monitor the progress of the different business processes within your BizTalk application by writing information to the default Application log or to a custom event log.</span></span> <span data-ttu-id="55dd3-104">寫入事件日誌，在下列實例中可能會很有用：</span><span class="sxs-lookup"><span data-stu-id="55dd3-104">Writing to the event log can be useful in the following scenarios:</span></span>  
  
-   <span data-ttu-id="55dd3-105">您想要使用 Windows 提供的工具，以標準的方式存取應用程式訊息。</span><span class="sxs-lookup"><span data-stu-id="55dd3-105">You want to access application messages in a standard way using tools supplied by Windows.</span></span>  
  
-   <span data-ttu-id="55dd3-106">您想要將資訊與來自伺服器環境的其他訊息一起封存，做成更完整的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="55dd3-106">You want to archive information with other messages from the server environment for a more complete history.</span></span>  
  
-   <span data-ttu-id="55dd3-107">您希望能夠使用可與事件日誌互動的工具來監視應用程式。</span><span class="sxs-lookup"><span data-stu-id="55dd3-107">You want the ability to monitor your application using tools that interact with the event log.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55dd3-108">System.Diagnostics.EventLog.WriteEntry 方法對訊息字串有大小限制。</span><span class="sxs-lookup"><span data-stu-id="55dd3-108">The System.Diagnostics.EventLog.WriteEntry method has a size limitation on the message string.</span></span> <span data-ttu-id="55dd3-109">如果訊息字串超過 32766 個位元組，就會收到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="55dd3-109">You will receive exception if the message string exceeds 32766 bytes.</span></span>  
  
## <a name="writing-to-the-application-log"></a><span data-ttu-id="55dd3-110">寫入應用程式日誌</span><span class="sxs-lookup"><span data-stu-id="55dd3-110">Writing to the Application Log</span></span>  
 <span data-ttu-id="55dd3-111">您可以撰寫應用程式記錄檔或任何其他記錄檔從您的程式碼使用**System.Diagnostics.EventLog**下列所示：</span><span class="sxs-lookup"><span data-stu-id="55dd3-111">You can write to the Application log or any other log from your code by using **System.Diagnostics.EventLog** as shown in the following:</span></span>  
  
```  
System.Diagnostics.EventLog.WriteEntry("Orchestration Debug", System.String.Format("The Value = {0}", iResult));  
```  
  
 <span data-ttu-id="55dd3-112">您還可以這麼做：</span><span class="sxs-lookup"><span data-stu-id="55dd3-112">Similar, you can also do,</span></span>  
  
```  
EventLog appLog = new EventLog();   
appLog.Source = "This Application's Name";  
appLog.WriteEntry("An entry to the Application event log.");  
```  
  
 <span data-ttu-id="55dd3-113">如果您使用自訂的記錄檔，您應該使用**SourceExists**方法，以確保它存在之前您寫入。</span><span class="sxs-lookup"><span data-stu-id="55dd3-113">If you are using a custom log, you should use the **SourceExists** method to ensure it exists before you write to it.</span></span>  
  
## <a name="writing-to-a-custom-log"></a><span data-ttu-id="55dd3-114">寫入自訂日誌</span><span class="sxs-lookup"><span data-stu-id="55dd3-114">Writing to a Custom Log</span></span>  
 <span data-ttu-id="55dd3-115">寫入自訂日誌的方式與寫入應用程式日誌相同，但是有一點除外，就是您必須先建立自訂日誌。</span><span class="sxs-lookup"><span data-stu-id="55dd3-115">Writing to a custom log is similar to writing to the Application log with the exception that you must first create the custom log.</span></span> <span data-ttu-id="55dd3-116">建立自訂日誌的程式碼十分簡單：</span><span class="sxs-lookup"><span data-stu-id="55dd3-116">The code to create a custom log is straightforward:</span></span>  
  
```  
// Create the source, if it does not already exist. if(!EventLog.SourceExists("MySource"))   
{   
  //An event log source should not be created and immediately used.  
  //There is a latency time to enable the source, it should be created  
  //prior to executing the application that uses the source.  
  EventLog.CreateEventSource("MySource", "MyNewLog");  
}  
```  
  
 <span data-ttu-id="55dd3-117">但是，您不應該假設您的程式碼會在具有安全性權限的帳戶下執行，而建立新的事件日誌。</span><span class="sxs-lookup"><span data-stu-id="55dd3-117">However, you should not assume that your code will be run under an account that has the security privileges to create a new event log.</span></span> <span data-ttu-id="55dd3-118">建立事件日誌需要系統管理員權限，而且應該在個別的公用程式中進行，或者最好是成為 .msi 安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="55dd3-118">Creating an event log takes administrator privileges and should be done in a separate utility program or, ideally, as part of an .msi installation.</span></span> <span data-ttu-id="55dd3-119">如需使用自訂指令碼包含匯出的.msi 安裝的詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="55dd3-119">For more information about using custom script with an exported .msi installation, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span></span>