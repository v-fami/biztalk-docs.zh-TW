---
title: "佇列管理支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d60d06ba-8cf3-46d6-af59-626f12fc572a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faeb3f141e114cf1f86157084f50d0a0d490833a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-queue-management"></a>佇列管理支援
有了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries 配接器，現在您可以使用 MQSeries 佇列管理員，在遠端建立與刪除佇列。 這是因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用遠端 MQSAgent COM+ 物件直接與 MQSeries 佇列管理員通訊所致。 通常此 MQSAgent 是在執行階段用來讀取與寫入遠端 MQSeries Server 佇列的訊息。 此遠端服務同時可支援一個以上的 BizTalk Server 作為其用戶端。 此外，佇列的建立與刪除功能都是由此 MQSAgent 提供，可以從協調流程或配接器中直接呼叫。 這樣一來，協調流程或配接器可以建立臨時佇列，然後用它來傳送訊息、接收另一個佇列的回應，並最終刪除臨時佇列，形成一個高度動態的實例。  
  
## <a name="createqueue-and-deletequeue-apis"></a>CreateQueue 與 DeleteQueue 等 API  
 CreateQueue 與 DeleteQueue 等 API 的定義如下所示：  
  
### <a name="structure-definition"></a>結構定義  
  
```  
typedef enum QueueUsage {  
      Normal       = 0,  
      Transmission = 1  
} QueueUsage;  
  
typedef enum ResultCode {  
      QueueAlreadyExists                     = 0, //  no bits set  
      QueueCreated                           = 1, //  QueueCreated  
      QueueCreatedAndRemoteDefinitionUpdated = 5, //  QueueCreated | RemoteDefinitionUpdated  
      QueueAndRemoteDefinitionCreated        = 7, //  QueueCreated | RemoteDefinitionCreated | RemoteDefinitionUpdated  
      QueueDoesNotExist                      = 8, //  QueueDoesNotExist  
      QueueDeleted                           = 16 //  QueueDeleted  
} ResultCode;  
```  
  
### <a name="interface-definition"></a>介面定義  
  
```  
[  
            object,  
            uuid(E90AC1A6-657B-4680-AF6A-89F11113FB8B),  
            dual,  
            nonextensible,  
            helpstring("IMQSAdmin Interface"),  
            pointer_default(unique)  
]  
interface IMQSAdmin2 : IDispatch{  
  
HRESULT CreateQueue (  
[in]BSTR queueManager,  
[in]BSTR newQueueName,  
[in]QueueUsage usage,  
[in]BSTR remoteDefinition,  
[in]BSTR remoteQName,  
[in]BSTR remoteQMgrName,  
[in]BOOL updateExistingRemoteDefinition,  
[out, retval]ResultCode* resultCode);  
  
HRESULT DeleteQueue (  
[in]BSTR queueManager,  
[in]BSTR newQueueName,  
[out, retval]ResultCode* resultCode);  
};  
  
      [  
            uuid(412AF00D-7CA8-4d2a-AFF6-F61CE2E29A0D),  
            helpstring("MQSAdmin Class")  
      ]  
      coclass MQSAdmin  
      {  
            [default] interface IMQSAdmin2;  
      };  
  
```  
  
## <a name="examples"></a>範例  
 完成範例 1 的步驟，建立可用來建立或刪除 MQSeries Server 佇列的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] C# 主控台應用程式。  
  
### <a name="example-1"></a>範例 1  
  
##### <a name="create-a-c-console-application-to-manage-mqseries-server-queues"></a>建立 C# 主控台應用程式以管理 MQSeries Server 佇列  
  
1.  建立新 Visual C# 主控台應用程式中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]名稱**MQSeriesQueues**。  
  
2.  以下列程式碼取代所產生 Program.cs 檔案中的任何現有程式碼：  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using MQSAgentLib;  
  
    namespace MQSeriesQueues  
    {  
        class ManageQueues  
        {  
            public static void Main(string[] args)  
            {  
                // The first argument should be "c" (without quotes)  
                // to create a queue, anything else to delete a queue.  
                // The 2nd and 3rd arguments should be the name of   
                // the MQSeries Queue Manager and the name of   
                // the queue to be created or deleted for example  
                // the following usage will create the local   
                // queue testq for the Queue Manager QM_Test  
                // MQSeriesQueues c QM_Test testq  
                createordeleteQs(args[0], args[1], args[2]);  
            }  
  
            static void createordeleteQs(string Qswitch, string QMgr, string QName)  
            {   
            if ((Qswitch =="c" & (QMgr != null & QName != null)))  
                {  
                    CreateQueue(QMgr, QName);  
                }  
                else if(QMgr != null & QName != null)  
                {  
                    DeleteQueue(QMgr, QName);  
                }  
             }  
  
            static void CreateQueue(string Qmgr, string Qname)  
            {  
                MQSAdmin admin = new MQSAdmin();    
  
                ResultCode resultCode = admin.CreateQueue(Qmgr, Qname, 0, "", "", "", 0);  
  
                if ((resultCode & ResultCode.QueueCreated) == ResultCode.QueueCreated)  
                {  
                    Console.WriteLine("Queue Created.");  
                }  
                else if ((resultCode & ResultCode.QueueAlreadyExists) == ResultCode.QueueAlreadyExists)  
                {  
                    Console.WriteLine("Queue Already Exists.");  
                }  
            }  
  
            static void DeleteQueue(string Qmgr, string Qname)  
            {  
                MQSAdmin admin = new MQSAdmin();  
  
                ResultCode resultCode = admin.DeleteQueue(Qmgr, Qname);  
  
                if ((resultCode & ResultCode.QueueDeleted) == ResultCode.QueueDeleted)  
                {  
                    Console.WriteLine("Queue successfully deleted.");  
                }  
                if ((resultCode & ResultCode.QueueDoesNotExist) == ResultCode.QueueDoesNotExist)  
                {  
                    Console.WriteLine("Queue did not exist anyway!");  
                }  
            }  
  
        }  
    }  
    ```  
  
3.  將參考加入至這個專案**MQSAgent 1.0 型別程式庫**。 **MQSAgent 1.0 型別程式庫**位於**COM**  索引標籤**將參考加入** 對話方塊。  
  
    > [!NOTE]
    >  其中正在執行此主控台應用程式的電腦，必須安裝 MQSAgent COM+ 元件。 如需安裝 MQSAgent COM + 元件的詳細資訊，請參閱[使用 MQSAgent COM + 組態精靈](../core/using-the-mqsagent-com-configuration-wizard.md)。  
  
4.  建置主控台應用程式。  
  
5.  開啟命令提示字元，移至已編譯主控台應用程式的相同目錄。  
  
6.  輸入已編譯主控台應用程式的名稱加上適當的參數，然後按 ENTER。 例如，若要刪除佇列**qm_test**佇列管理員**testq**在命令提示字元中輸入下列文字，然後按 ENTER 鍵：  
  
    ```  
    MQSeriesQueues d QM_Test testq  
    ```  
  
7.  若要建立佇列**qm_test**佇列管理員**testq**在命令提示字元中輸入下列文字，然後按 ENTER 鍵：  
  
    ```  
    MQSeriesQueues c QM_Test testq  
    ```