---
title: "Siebel 配接器使用 WCF 服務模型以叫用商務服務方法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, invoking business service methods
- business service methods, invoking by using the WCF service model
ms.assetid: b41cf944-efdc-453f-824b-70581e7143e7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27eafcbfadc353e8aed9430e2d1bed3ef9e16017
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-business-service-methods-with-the-siebel-adapter-using-the-wcf-service-model"></a>Siebel 配接器使用 WCF 服務模型以叫用商務服務方法
您可以建立 WCF 用戶端目標方法的 Siebel 商務服務。 您接著可以使用 WCF 用戶端叫用 Siebel 系統上的這些方法。 Siebel 商務服務便會顯示在 [商務服務] 節點下[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 對應至該服務的節點下便會顯示每個商務服務所公開的方法。 您可以遵循的步驟中[Siebel 配接器之 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-siebel/overview-of-the-wcf-service-model-with-the-siebel-adapter.md)來產生 WCF 用戶端為商務服務，並使用它來叫用服務的方法。  
  
 下列程式碼使用 WCF 用戶端來叫用**Execute**時間戳記商務服務的方法。 時間戳記，傳回的 Siebel 伺服器的當地時間，然後寫入主控台。 在這個範例 WCF 用戶端會從產生的組態檔初始化[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需產生的組態檔的範例，請參閱[設定 WCF 用戶端在 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using microsoft.lobservices.siebel._2007._03.BusinessServices.TimeStamp;  
  
namespace Business_Service  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BusinessServices_TimeStamp_OperationClient client = null;  
  
            try  
            {  
                client =  
                     new BusinessServices_TimeStamp_OperationClient("SiebelBinding_BusinessServices_TimeStamp_Operation");  
  
                client.ClientCredentials.UserName.UserName = "YourUserName";  
                client.ClientCredentials.UserName.Password = "YourPassword";  
                client.Open();  
  
                ExecuteResponseRecord er = client.Execute();  
                Console.WriteLine(er.Time);  
  
                Console.WriteLine("\nHit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine(e.Message);  
            }  
            finally  
            {  
                // Close the client.  
                if (client != null)  
                {  
                    if (client.State == CommunicationState.Opened)  
                        client.Close();  
                    else  
                        client.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [開發 Siebel 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)