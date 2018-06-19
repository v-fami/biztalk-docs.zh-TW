---
title: 部署和啟動協調流程的新版本，以程式設計的方式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f90025ec-3641-49ef-8918-88238d6ad420
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26887b70a09d4a7af8d41a4385dffda20e964690
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239022"
---
# <a name="deploying-and-starting-a-new-version-of-an-orchestration-programmatically"></a>以程式設計的方式部署和啟動新版本的協調流程
本主題中的程式碼說明如何快速部署和啟動新版本的協調流程。 由於手動作業可能要花費數秒鐘才能執行，所以如果用手動方式取消登錄協調流程，然後再啟動新版本的協調流程，可能會導致訊息擱置或重複。 本主題所說明的程式設計方法，可讓您用快上許多的速度來執行這些作業 (並降低訊息擱置或重複的可能性)，而且會以單一交易的方式完成作業，所以如果一項作業失敗，則兩個協調流程都會保留為初始時的相同狀態。  
  
> [!NOTE]
>  在極少數的情況下，當您要使用新的版本更新協調流程在負載過高，運作時某些訊息可能會擱置即使您取消登錄，以程式設計方式登錄協調流程。  我們建議您在執行這些作業之後, 檢查擱置的訊息佇列，並繼續擱置的訊息。  
  
 下列程式碼範例說明如何使用 Explorer OM API 來取消登錄現有的協調流程，並啟動新版本的協調流程。  
  
```  
using System;  
using Microsoft.BizTalk.ExplorerOM;  
#endregion  
namespace OrchestrationBinding  
{  
class OrchestrationBinding  
{  
static void Main(string[] args)  
{  
            UpdateOrchestration();  
}  
        static public void UpdateOrchestration()  
        {  
            // Create the root object and set the connection string  
            BtsCatalogExplorer catalog = new BtsCatalogExplorer();  
            catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI";  
            string orchestrationAssemblyV1 = "HelloWorld, Version=1.0.0.0, Culture=neutral, PublicKeyToken=99561c477e487f14";  
            string orchestrationAssemblyV2 = "HelloWorld, Version=2.0.0.0, Culture=neutral, PublicKeyToken=99561c477e487f14";  
            string orchestrationName = "Microsoft.Samples.BizTalk.HelloWorld.HelloSchedule";  
            try  
            {  
                BtsAssembly assemblyV1 = FindAssemblyByFullName(catalog.Assemblies, orchestrationAssemblyV1);  
                BtsAssembly assemblyV2 = FindAssemblyByFullName(catalog.Assemblies, orchestrationAssemblyV2);  
                BtsOrchestration orchestrationV1 = assemblyV1.Orchestrations[orchestrationName];  
                BtsOrchestration orchestrationV2 = assemblyV2.Orchestrations[orchestrationName];  
                orchestrationV1.Status = OrchestrationStatus.Unenlisted;  
                orchestrationV2.Status = OrchestrationStatus.Started;  
                // Commit the accumulated changes transactionally  
                catalog.SaveChanges();  
            }  
            catch (Exception e)  
            {  
                catalog.DiscardChanges();  
                throw;  
            }  
        }  
        static BtsAssembly FindAssemblyByFullName(BtsAssemblyCollection assemblies, string fullName)  
        {  
            foreach (BtsAssembly assembly in assemblies)  
            {  
                if (assembly.DisplayName == fullName)  
                    return assembly;  
            }  
            return null;  
        }  
}  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)   
 [如何登錄協調流程](../core/how-to-enlist-an-orchestration.md)   
 [如何取消登錄協調流程](../core/how-to-unenlist-an-orchestration.md)