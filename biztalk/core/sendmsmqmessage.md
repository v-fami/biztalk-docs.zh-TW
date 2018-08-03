---
title: SendMSMQMessage |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, examples
- examples, MSMQ adapters
ms.assetid: 398bc396-0c66-4d55-886a-0d9bdab6476f
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27c6a0f6b9e35b68fccd38d62fe7e1ae86f4f6ad
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024492"
---
# <a name="sendmsmqmessage"></a>SendMSMQMessage
SendMSMQMessage 範例將示範如何從 .NET 架構的應用程式將訊息傳送至 MSMQ 連接埠。 此外還提供如何設定 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用 MSMQ 接收位置的指示。  

 您應該要注意的訊息佇列中的許多作業是非同步的。 也就是說，許多 MSMQ API 呼叫 (例如**System.Messaging.MessageQueue.Send**) 傳回給呼叫者完全完成要求的作業之前。 MSMQ 提供一項機制，會在作業全部完成之後將回應傳遞至應用程式。 這個機制需要用到「管理佇列」。 MSMQ 管理佇列中訊息的形式傳回的意見反應。 當進行原始 MSMQ API 呼叫時，便會指定 MSMQ 要將回應傳送所至的管理佇列。 因此，例如，當傳送訊息，使用**System.Messaging.MessageQueue.Send** API，應用程式可以使用指定名稱的管理佇列**PROPID_M_ADMIN_QUEUE**訊息屬性呼叫中傳遞的訊息**System.Messaging.MessageQueue.Send**。 即使應用程式可能會收到成功的傳回碼， **System.Messaging.MessageQueue.Send**呼叫時，如果後續訊息傳送作業失敗，MSMQ 訊息寫入來指出指定的管理佇列。 如果應用程式未指定管理佇列，傳送失敗會導致訊息遺失而無法擷取診斷，訊息實際上會毫無跡象消失。 有了數種情況下，可能會造成這種情形，例如，進行非交易式 MSMQ 中的傳送至異動式佇列的錯誤。  

 在此範例的內容，是很重要的程式碼呼叫中指定交易類型**System.Messaging.MessageQueue.Send**這是與的佇列訊息是所指定的交易支援一致傳送。 如果沒有做到這點，而且如果沒有指定管理佇列是 （在此情況下在此範例中），MSMQ 捨棄而且不會指出，它確實已傳送的訊息 （也就是沒有錯誤碼傳回應用程式，無法診斷資訊寫入事件記錄檔依此類推)。  

## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<範例路徑\>\AdaptersUsage\SendMSMQMessage\  

 下表顯示此範例中的檔案，並描述其用途。  


|                                 檔案                                 |                                                                      描述                                                                       |
|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| App.ico、AssemblyInfo.cs、SendMSMQMessage.csproj、SendMSMQMessage.sln |                           提供專案、 解決方案和相關的檔案，此範例的簡易圖形應用程式。                           |
|                         Form1.cs、Form1.resx                          | 提供 Microsoft[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]針對此範例的簡單圖形化應用程式的.NET 來源和格式檔案。 |

## <a name="how-to-use-this-sample"></a>如何使用此範例  
 您可以在此範例包含為了舉例說明如何將訊息傳送至 MSMQ 接收位置內的簡易圖形應用程式中使用程式碼[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]從。NET 功能的應用程式例如 Microsoft Office，從 ASP.NET 頁面中，依此類推。  

## <a name="building-and-initializing-the-sample"></a>建置和初始化範例  

#### <a name="to-build-the-sample-executable"></a>建置範例可執行檔  

1. 使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 SendMSMQMessage.sln。  

2. 按一下 [ **建置** ] 功能表上的 [ **建置方案**]。  

## <a name="configuring-biztalk-server-and-creating-the-msmq-queue"></a>設定 BizTalk Server，並建立 MSMQ 佇列  
 使用下列程序來設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]並建立執行範例的 MSMQ 佇列。  

#### <a name="to-create-the-msmq-queue-in-windows-server-2008-r2-or-windows-server-2008-sp2"></a>在 Windows Server 2008 R2 或 Windows Server 2008 SP2 中建立 MSMQ 佇列  

1.  按一下 **開始**，以滑鼠右鍵按一下**電腦**，然後按一下**管理**。  

2.  依序展開**功能**節點。  如果**Message Queuing**是未安裝，以滑鼠右鍵按一下**功能**，然後選取**新增功能**。  檢查**Message Queuing**，按一下**下一步**，然後按一下**安裝**該系統上安裝 MSMQ。  

3.  依序展開**訊息佇列**節點。  

4.  以滑鼠右鍵按一下**私用佇列**節點中，按一下**新增**，然後按一下**私用佇列**。  

5.  底下**佇列名稱**，輸入`test`。 請確認**Transactional**選取核取方塊。  

6.  按一下 [確定] 。  

#### <a name="to-create-the-msmq-queue-in-windows-7-or-windows-vista-sp2"></a>在 Windows 7 或 Windows Vista SP2 中建立 MSMQ 佇列  

1.  按一下 **開始**，以滑鼠右鍵按一下**電腦**，然後按一下**管理**。  

2.  依序展開**服務和應用程式**，然後展開**Message Queuing**節點。  

    > [!NOTE]
    >  如果**Message Queuing**未安裝在電腦中，移至**控制台 > 程式 > 程式和功能**，然後選取**開啟或關閉開啟的 Windows 功能**。 核取下所有的功能**Microsoft Message Queue (MSMQ) 伺服器**，然後按一下**確定**。  

3.  以滑鼠右鍵按一下**私用佇列**節點中，按一下**新增**，然後按一下**私用佇列**。  

4.  底下**佇列名稱**，輸入**測試**。 請確認**Transactional**選取核取方塊。  

5.  按一下 [確定] 。  

#### <a name="to-configure-biztalk-server"></a>設定 BizTalk Server  

1. 選取要接收訊息的資料夾。 下列步驟假設您已選取 C:\Demo\Report，不過您可以視需要調整步驟以使用其他資料夾。  

2. 開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

3. 建立新的應用程式，名為**MSMQSample**。  

4. 以滑鼠右鍵按一下**接收連接埠**，按一下**新增**，然後按一下**單向接收埠**。  

5. 中**接收埠屬性**對話方塊中，於**名稱**方塊中輸入**MyReceivePort**，然後按一下 **確定**。  

6. 以滑鼠右鍵按一下**接收位置**，按一下**新增**，然後按一下**單向接收位置**。 在 [**選取接收埠**] 對話方塊中，選取您剛才的接收埠建立，然後按一下**確定**。  

7. 在 **接收位置屬性**對話方塊中，於**名稱**方塊中，輸入接收埠名稱，例如**MSMQReceiveLocation**。  

8. 在 **接收位置屬性**對話方塊的 傳輸類型，選取**MSMQ** 。  

9. 按一下 [**設定**來開啟**MSMQ 傳輸屬性**] 對話方塊。 設定**佇列**來`localhost\private$\test`，將**交易式**來`True`，然後按一下 **確定**。  

10. 展開 應用程式中，選取**傳送埠**，選取**新增**，選取**靜態單向傳送埠**。  

11. 在 **傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入傳送埠名稱，例如**MySendPort**。  

12. 設定**傳輸類型**屬性設**檔案**。  

13. 按一下 [**設定**來開啟**File 傳輸屬性**] 對話方塊。  

14. 在  **FILE 傳輸屬性** 對話方塊中，將**目的地資料夾**屬性設**C:\Demo\Report**，保留其他屬性，預設值，然後按一下 **確定**。  

15. 選取 **篩選條件**，然後藉由設定新增新的資料列**屬性**到**BTS。ReceivePortName**。 離開**運算子**資料行設定為**==**，將**值**資料行**MyReceivePort**，然後按一下 **[確定]**。  

16. 以滑鼠右鍵按一下您的新傳送埠，然後按一下**登錄**。  

17. 以滑鼠右鍵按一下您的新傳送埠，同樣地，然後按一下**啟動**。  

18. 以滑鼠右鍵按一下您的新接收位置，然後按一下**啟用**。  

    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 現在就可使用此範例。  

## <a name="running-the-sample"></a>執行範例  
 使用下列程序執行 SendMSMQMessage 範例。  

#### <a name="to-run-the-sample"></a>執行範例  

1. 在命令視窗中，瀏覽至下列資料夾：  

    \<範例路徑\>\AdaptersUsage\SendMSMQMessage\bin\Debug  

2. 執行 SendMSMQMessage.exe，它會啟動此範例中提供的使用者介面的圖形應用程式的檔案。  

3. 在圖形化的應用程式，在**BizTalk 電腦名稱**方塊中，輸入本機電腦的名稱。  

4. 請嘗試**傳送包裝**選項：  

   1. 選擇性地變更中的文字**訊息主體** 方塊中。  

   2. 按一下 **傳送包裝**。  

      如果作業成功，您會看到下列項目：  

   - 單字**成功**會出現在按鈕正上方的方塊中的紅色字型。  

   - 在您的目的地資料夾，C:\Demo\Reports 中會出現一個檔案。 此檔案包含的文字**訊息主體**包裝簡單的 XML 標記，由.NET 訊息佇列的程式庫中的方塊。  

     如果作業失敗，您將在按鈕正上方的方塊中看見錯誤訊息。  

5. 請嘗試**傳送精確**選項：  

   1. 選擇性地變更中的文字**訊息主體** 方塊中。  

   2. 按一下 **傳送精確**。  

      如果作業成功，您會看到下列項目：  

   - 單字**成功**會出現在按鈕正上方的方塊中的紅色字型。  

   - 在您的目的地資料夾，C:\Demo\Reports 中會出現一個檔案。 此檔案包含的文字**訊息主體**方塊出現在文字方塊中的相同。  

     如果作業失敗，您將在按鈕正上方的方塊中看見錯誤訊息。  

## <a name="see-also"></a>另請參閱  
 [配接器範例 - 用法](../core/adapter-samples-usage.md)