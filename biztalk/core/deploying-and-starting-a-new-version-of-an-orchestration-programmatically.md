---
title: "部署和啟動協調流程的新版本，以程式設計的方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f90025ec-3641-49ef-8918-88238d6ad420
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26887b70a09d4a7af8d41a4385dffda20e964690
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-and-starting-a-new-version-of-an-orchestration-programmatically"></a><span data-ttu-id="a40e1-102">以程式設計的方式部署和啟動新版本的協調流程</span><span class="sxs-lookup"><span data-stu-id="a40e1-102">Deploying and Starting a New Version of an Orchestration Programmatically</span></span>
<span data-ttu-id="a40e1-103">本主題中的程式碼說明如何快速部署和啟動新版本的協調流程。</span><span class="sxs-lookup"><span data-stu-id="a40e1-103">The code in this topic illustrates how to quickly deploy and start a new version of the orchestration.</span></span> <span data-ttu-id="a40e1-104">由於手動作業可能要花費數秒鐘才能執行，所以如果用手動方式取消登錄協調流程，然後再啟動新版本的協調流程，可能會導致訊息擱置或重複。</span><span class="sxs-lookup"><span data-stu-id="a40e1-104">Because manual operations can take a few seconds to perform, manually unenlisting an orchestration and then starting a new version of it can result in suspended or duplicate messages.</span></span> <span data-ttu-id="a40e1-105">本主題所說明的程式設計方法，可讓您用快上許多的速度來執行這些作業 (並降低訊息擱置或重複的可能性)，而且會以單一交易的方式完成作業，所以如果一項作業失敗，則兩個協調流程都會保留為初始時的相同狀態。</span><span class="sxs-lookup"><span data-stu-id="a40e1-105">The programmatic method illustrated in this topic allows you to perform these operations much more quickly – reducing the likelihood of suspended and duplicate messages – and as a single transaction, so that if one operation fails, both orchestrations are left in the same state as they were at the beginning.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a40e1-106">在極少數的情況下，當您要使用新的版本更新協調流程在負載過高，運作時某些訊息可能會擱置即使您取消登錄，以程式設計方式登錄協調流程。</span><span class="sxs-lookup"><span data-stu-id="a40e1-106">In rare cases, when the orchestration you are updating with a new version is operating under high load, some messages can become suspended even when you unenlist and enlist the orchestrations programmatically.</span></span>  <span data-ttu-id="a40e1-107">我們建議您在執行這些作業之後, 檢查擱置的訊息佇列，並繼續擱置的訊息。</span><span class="sxs-lookup"><span data-stu-id="a40e1-107">We recommend that after performing these operations, you check your suspended message queue and resume any suspended messages.</span></span>  
  
 <span data-ttu-id="a40e1-108">下列程式碼範例說明如何使用 Explorer OM API 來取消登錄現有的協調流程，並啟動新版本的協調流程。</span><span class="sxs-lookup"><span data-stu-id="a40e1-108">The following code sample illustrates how to use the Explorer OM API to unenlist an existing orchestration and start the new version of the orchestration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a40e1-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a40e1-109">See Also</span></span>  
 <span data-ttu-id="a40e1-110">[更新 BizTalk 應用程式](../core/updating-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="a40e1-110">[Updating BizTalk Applications](../core/updating-biztalk-applications.md) </span></span>  
 <span data-ttu-id="a40e1-111">[如何登錄協調流程](../core/how-to-enlist-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="a40e1-111">[How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md) </span></span>  
 [<span data-ttu-id="a40e1-112">如何取消登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="a40e1-112">How to Unenlist an Orchestration</span></span>](../core/how-to-unenlist-an-orchestration.md)