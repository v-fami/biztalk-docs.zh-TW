---
title: 使用 Siebel 配接器使用 WCF 服務模型執行商務元件上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, performing operations on business components
- how to, perform operations using the proxy
- business components, performing operations by using the WCF service model
- performing operations, using the proxy
ms.assetid: 7a5fdc95-6159-4f43-aac5-4e2f84e9138b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99ac40efda9ed8c27fb5ac5fedfbe782b9a4f645
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222222"
---
# <a name="run-operations-on-business-components-with-the-siebel-adapter-using-the-wcf-service-model"></a>使用 Siebel 配接器使用 WCF 服務模型執行商務元件上的作業
您可以建立 WCF 用戶端為目標的 Siebel 商務元件。 您接著可以使用 WCF 用戶端 Siebel 系統上執行插入、 更新、 查詢、 刪除、 關聯、 中斷和商務元件上的子記錄的查詢作業。 Siebel 商務物件便會顯示在 [商務物件] 節點下[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 商業元件構成每個商務物件便會顯示對應到該物件的節點下。 您可以遵循的步驟中[Siebel 配接器之 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-siebel/overview-of-the-wcf-service-model-with-the-siebel-adapter.md)產生 WCF 用戶端為目標的特定作業的商務元件，並使用用戶端來叫用這些作業的業務元件。  
  
> [!NOTE]
>  本主題提供有關執行基本作業 （插入、 更新、 查詢、 刪除） 在商務元件上的資訊。 如需執行關聯、 中斷、 和子記錄的查詢作業的詳細資訊，請參閱[MVG 欄位使用 WCF 服務模型的商務元件上執行的作業](../../adapters-and-accelerators/adapter-siebel/work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)  
  
 下列程式碼使用 WCF 用戶端執行帳戶商務物件的帳戶商務元件中的上一筆記錄的 Insert、 Update 和 Delete 作業。 之間每個作業，會執行查詢作業，來驗證結果。 在這個範例 WCF 用戶端會從組態檔所產生的初始化[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需產生的組態檔的範例，請參閱[設定 WCF 用戶端在 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)。  
  
```  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using microsoft.lobservices.siebel._2007._03.BusinessObjects;  
using microsoft.lobservices.siebel._2007._03;  
  
namespace Business_Component_Operations  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BusinessObjects_Account_Account_OperationClient client = null;  
  
            try  
            {  
  
                client = new BusinessObjects_Account_Account_OperationClient("SiebelBinding_BusinessObjects_Account_Account_Operation");  
                client.ClientCredentials.UserName.UserName = "YourUserName";  
                client.ClientCredentials.UserName.Password = "YourPassword";  
  
                Console.WriteLine("Opening connection to " + client.Endpoint.Address.Uri.Host);  
                client.Open();  
                AccountInsertRecord[] air = new AccountInsertRecord[1];  
                air[0] = new AccountInsertRecord();  
                Random r = new Random();  
                int count = r.Next();  
  
                air[0].Name = "Anil" + count.ToString();  
                Console.WriteLine("Inserting " + air[0].Name + " ...");  
                client.Insert(air);  
  
                //Query for the record.  
                Console.WriteLine("Querying to check inserted record ...");  
                AccountQueryInputRecord aqir = new AccountQueryInputRecord();  
                short viewmode = new short(); viewmode = 3;  
                string[] fields = new string[2];  
                fields[0] = "Name";  
                fields[1] = "Id";  
                aqir.QueryFields = fields;  
                aqir.SearchExpr = "[Name] LIKE \"Anil*\"";  
                AccountQueryRecord[] aqr = client.Query(viewmode, aqir);  
                Console.WriteLine(aqr.Length + " records returned");  
                string[] ids = new string[1];  
                AccountUpdateRecord[] aur = new AccountUpdateRecord[1];  
                aur[0] = new AccountUpdateRecord();  
                foreach (AccountQueryRecord rec in aqr)  
                {  
                    Console.WriteLine("Name: " + rec.Name);  
                    Console.WriteLine("Id: " + rec.Id);  
                    Console.WriteLine("");  
                    ids[0] = rec.Id;  
                    aur[0].Name = rec.Name;  
                    aur[0].Id = rec.Id;  
                }  
  
                //Update it.  
  
                aur[0].Name = "Anil" + count.ToString() + "modified";  
                Console.WriteLine("Update the record to " + aur[0].Name + " ...");  
                client.Update(viewmode, aur);  
                //query again  
                aqr = client.Query(viewmode, aqir);  
                Console.WriteLine(aqr.Length + " records returned");  
                foreach (AccountQueryRecord rec in aqr)  
                {  
                    Console.WriteLine("Name: " + rec.Name);  
                    Console.WriteLine("Id: " + rec.Id);  
                    Console.WriteLine("");  
                }  
  
                //Delete it.  
                Console.WriteLine("Deleting record ...");  
                client.Delete(viewmode, ids, "");  
  
                //Check again.  
                Console.WriteLine("Check that " + aur[0].Name + " is not present");  
                aqr = client.Query(viewmode, aqir);  
  
                Console.WriteLine(aqr.Length + " records returned");  
                foreach (AccountQueryRecord rec in aqr)  
                {  
                    Console.WriteLine(rec.Name);  
                    Console.WriteLine(rec.Id);  
  
                }  
  
                // Wait for <RETURN> to end sample.  
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