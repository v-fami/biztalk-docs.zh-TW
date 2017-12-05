---
title: "PartnerManagement （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83e2a84f-ab25-4a7c-b8d7-0ba2dfa93095
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2ffc9e84e8c31ed1e1feb4c768498e817ad474c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="partnermanagement-biztalk-server-sample"></a><span data-ttu-id="2d2da-102">PartnerManagement （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="2d2da-102">PartnerManagement (BizTalk Server Sample)</span></span>
<span data-ttu-id="2d2da-103">PartnerManagement 範例示範如何管理合作對象中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境使用**ExplorerOM**管理物件。</span><span class="sxs-lookup"><span data-stu-id="2d2da-103">The PartnerManagement sample demonstrates how to manage parties in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment by using the **ExplorerOM** administration objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2d2da-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="2d2da-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="2d2da-105">您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="2d2da-105">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="2d2da-106">Windows PowerShell 指令碼需要 Windows PowerShell 執行原則以允許執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="2d2da-106">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="2d2da-107">如需詳細資訊，請參閱 [檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。</span><span class="sxs-lookup"><span data-stu-id="2d2da-107">For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="2d2da-108">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="2d2da-108">What This Sample Does</span></span>  
 <span data-ttu-id="2d2da-109">此範例將示範如何使用系統管理類別從**Microsoft.BizTalk.ExplorerOM**管理合作對象的命名空間。</span><span class="sxs-lookup"><span data-stu-id="2d2da-109">This sample demonstrates using the administrative classes from the **Microsoft.BizTalk.ExplorerOM** namespace to manage parties.</span></span> <span data-ttu-id="2d2da-110">合作對象代表交易夥伴或後端應用程式可以與之互動的商務程序。</span><span class="sxs-lookup"><span data-stu-id="2d2da-110">Parties represent trading partners or back-end applications with which a business process can interact.</span></span> <span data-ttu-id="2d2da-111">如需有關合作對象一般情況下，請參閱文件[合作對象](../core/parties.md)或[角色連結和服務連結角色](../core/role-links-and-service-link-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="2d2da-111">For more information about parties in general, see the documentation for [Parties](../core/parties.md) or [Role Links and Service Link Roles](../core/role-links-and-service-link-roles.md).</span></span> <span data-ttu-id="2d2da-112">此範例以 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2d2da-112">The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span></span> <span data-ttu-id="2d2da-113">本主題也包含 Windows PowerShell 範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="2d2da-113">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="2d2da-114">此範例會示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="2d2da-114">The sample demonstrates the following operations:</span></span>  
  
-   <span data-ttu-id="2d2da-115">建立新的合作對象的自訂或標準的別名，並加入現有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳送埠到合作對象。</span><span class="sxs-lookup"><span data-stu-id="2d2da-115">Creating a new party with a custom or standard alias and adding existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send ports to the party.</span></span>  
  
-   <span data-ttu-id="2d2da-116">登錄 BizTalk server 上的現有角色連結的新合作對象。</span><span class="sxs-lookup"><span data-stu-id="2d2da-116">Enlisting the new party with an existing role link on the BizTalk server.</span></span>  
  
-   <span data-ttu-id="2d2da-117">取消登錄新的合作對象。</span><span class="sxs-lookup"><span data-stu-id="2d2da-117">Un-enlisting the new party.</span></span>  
  
-   <span data-ttu-id="2d2da-118">正在刪除新的合作對象。</span><span class="sxs-lookup"><span data-stu-id="2d2da-118">Deleting the new party.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="2d2da-119">此範例的位置</span><span class="sxs-lookup"><span data-stu-id="2d2da-119">Where To Find This Sample</span></span>  
 <span data-ttu-id="2d2da-120">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="2d2da-120">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="2d2da-121">\<*範例路徑*\>\Admin\ExplorerOM\PartnerManagement</span><span class="sxs-lookup"><span data-stu-id="2d2da-121">\<*Samples Path*\>\Admin\ExplorerOM\PartnerManagement</span></span>  
  
 <span data-ttu-id="2d2da-122">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="2d2da-122">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="2d2da-123">檔案</span><span class="sxs-lookup"><span data-stu-id="2d2da-123">File(s)</span></span>|<span data-ttu-id="2d2da-124">Description</span><span class="sxs-lookup"><span data-stu-id="2d2da-124">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d2da-125">PartnerManagement.cs</span><span class="sxs-lookup"><span data-stu-id="2d2da-125">PartnerManagement.cs</span></span>|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]<span data-ttu-id="2d2da-126">這個範例中示範的作業的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="2d2da-126"> source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="2d2da-127">PartnerManagement.sln 和 PartnerManagement.csproj</span><span class="sxs-lookup"><span data-stu-id="2d2da-127">PartnerManagement.sln and PartnerManagement.csproj</span></span>|<span data-ttu-id="2d2da-128">此範例的方案和專案檔。</span><span class="sxs-lookup"><span data-stu-id="2d2da-128">Solution and project files for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="2d2da-129">建置和執行此範例</span><span class="sxs-lookup"><span data-stu-id="2d2da-129">Building and Running This Sample</span></span>  
 <span data-ttu-id="2d2da-130">建立範例之前，您需要四個自訂 BizTalk server 的 「 範例修改程式碼。</span><span class="sxs-lookup"><span data-stu-id="2d2da-130">Before you build the sample, you need to make four code modifications to customize the sample for the BizTalk server.</span></span> <span data-ttu-id="2d2da-131">這是必要的因為此範例會使用與合作對象和登記任意的角色名稱相關聯的傳送埠的任意名稱。</span><span class="sxs-lookup"><span data-stu-id="2d2da-131">This is necessary because the sample uses arbitrary names for send ports associated with the party and an arbitrary role name for the enlistment.</span></span> <span data-ttu-id="2d2da-132">因此，您需要提供範例的有效名稱。</span><span class="sxs-lookup"><span data-stu-id="2d2da-132">Therefore you need to provide valid names to the sample.</span></span> <span data-ttu-id="2d2da-133">為了示範這個範例，本主題說明如何先建置 PartyResolution 範例從下列目錄： \<*範例路徑*\>\Orchestrations\PartyResolution。</span><span class="sxs-lookup"><span data-stu-id="2d2da-133">To demonstrate this sample, this topic describes first building the PartyResolution sample from the following directory: \<*Samples Path*\>\Orchestrations\PartyResolution.</span></span> <span data-ttu-id="2d2da-134">這種方法用來確定有效的角色名稱，然後傳送連接埠名稱會出現在 BizTalk server 來示範的範例程序上。</span><span class="sxs-lookup"><span data-stu-id="2d2da-134">This approach is used to make sure a valid role name and send port names are present on the BizTalk server to demonstrate the sample procedures.</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="2d2da-135">建置此範例</span><span class="sxs-lookup"><span data-stu-id="2d2da-135">To build this sample</span></span>  
  
1.  <span data-ttu-id="2d2da-136">先確定已建置和初始化，才會有效的角色名稱和傳送連接埠名稱可由範例 PartyResolution 範例。</span><span class="sxs-lookup"><span data-stu-id="2d2da-136">First make sure the PartyResolution sample has been built and initialized so that a valid role name and send port names can be used by the sample.</span></span> <span data-ttu-id="2d2da-137">這在標題為 「 建置和初始化此範例 」 一節記載[PartyResolution （BizTalk Server 範例）](../core/partyresolution-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="2d2da-137">This is documented in the section entitled “Building and Initializing This Sample” in  [PartyResolution (BizTalk Server Sample)](../core/partyresolution-biztalk-server-sample.md).</span></span>  
  
2.  <span data-ttu-id="2d2da-138">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 PartnerManagement.sln。</span><span class="sxs-lookup"><span data-stu-id="2d2da-138">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file PartnerManagement.sln.</span></span>  
  
3.  <span data-ttu-id="2d2da-139">在 [方案總管] 中開啟原始程式檔 PartnerManagement.cs。</span><span class="sxs-lookup"><span data-stu-id="2d2da-139">In Solution Explorer, open the source file PartnerManagement.cs.</span></span>  
  
4.  <span data-ttu-id="2d2da-140">向下捲動至名為函式**CreateParty**和插入兩個傳送連接埠名稱，從 PartyResolution 範例，或使用 BizTalk server 環境中的有效名稱。</span><span class="sxs-lookup"><span data-stu-id="2d2da-140">Scroll down into the function named **CreateParty** and insert the two send port names from the PartyResolution sample or use valid names from the BizTalk server environment.</span></span> <span data-ttu-id="2d2da-141">下列程式碼範例示範使用 PartyResolution 範例傳送埠的變更。</span><span class="sxs-lookup"><span data-stu-id="2d2da-141">The following code example demonstrates the change using the send ports from the PartyResolution sample.</span></span>  
  
    ```  
    // Replacing arbitrary send port names with PartyResolution send port names ===  
  
    //            myParty.SendPorts.Add(catalog.SendPorts["NormalDelivery"]);  
    //            myParty.SendPorts.Add(catalog.SendPorts["ExpressDelivery"]);  
                myParty.SendPorts.Add(catalog.SendPorts["SP_FilesToShipmentAgency1"]);  
                myParty.SendPorts.Add(catalog.SendPorts["SP_FilesToShipmentAgency2"]);  
  
    ```  
  
5.  <span data-ttu-id="2d2da-142">向下捲動至名為函式**EnlistParty**和變更，讓它搜尋名為"ShipmentRole 」 角色的供應商組件的 「 foreach 迴圈 」 使用登記。</span><span class="sxs-lookup"><span data-stu-id="2d2da-142">Scroll down into the function named **EnlistParty** and change the foreach loop so that it searches the Supplier assembly for a role named “ShipmentRole” to use with the enlistment.</span></span> <span data-ttu-id="2d2da-143">下列程式碼範例示範如何使用來自 PartyResolution 範例 ShipmentRole 變更。</span><span class="sxs-lookup"><span data-stu-id="2d2da-143">The following code example demonstrates the change to use the ShipmentRole from the PartyResolution sample.</span></span>  
  
    ```  
                // Search for the “Shipmentrole” instead of “shipperRole”  
                Role svcRole = null;  
    //===       foreach (Role role in catalog.Assemblies[0].Roles)  
                foreach (Role role in catalog.Assemblies["Supplier"].Roles)  
                {  
    //===          if (role.Name == "ShipperRole")  
                   if (role.Name == "ShipmentRole")  
                   {  
                      svcRole = role;  
                      break;  
                   }  
                }  
  
    ```  
  
6.  <span data-ttu-id="2d2da-144">向下捲動至名為函式**UnenlistParty**和變更搜尋 ShipmentRole 的供應商組件的 「 foreach 迴圈 」。</span><span class="sxs-lookup"><span data-stu-id="2d2da-144">Scroll down into the function named **UnenlistParty** and change the foreach loop to search the Supplier assembly for the ShipmentRole.</span></span> <span data-ttu-id="2d2da-145">下列程式碼範例示範這項變更。</span><span class="sxs-lookup"><span data-stu-id="2d2da-145">The following code example demonstrates this change.</span></span>  
  
    ```  
                // Search for the “ShipmentRole” instead of “shipperRole”  
                Role svcRole = null;  
    //===       foreach (Role role in catalog.Assemblies[0].Roles)  
                foreach (Role role in catalog.Assemblies["Supplier"].Roles)  
                {  
    //===          if (role.Name == "ShipperRole")  
                   if (role.Name == "ShipmentRole")  
                   {  
                      svcRole = role;  
                      break;  
                   }  
                }  
  
    ```  
  
7.  <span data-ttu-id="2d2da-146">在建立並登錄 ShipmentRole 的新合作對象之後, 的範例為了立即取消-登錄合作對象，並將它刪除。</span><span class="sxs-lookup"><span data-stu-id="2d2da-146">After creating and enlisting the new party with the ShipmentRole, the sample is designed to immediately un-enlist the party and delete it.</span></span> <span data-ttu-id="2d2da-147">將下列程式碼變更加入至主要程序，暫停執行，並讓您檢視建立新的合作對象中登記[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2d2da-147">Add the following code change to the main procedure to pause execution and allow you to view the created enlistment for the new party in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
       CreateParty();     
       EnlistParty();     
  
       Console.WriteLine("\nNew Party created and enlisted.\n\nPress <Enter> to unenlist and delete.\n");  
       Console.ReadLine();  
  
       UnenlistParty();   
       DeleteParty();  
    }  
  
    ```  
  
8.  <span data-ttu-id="2d2da-148">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="2d2da-148">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="2d2da-149">執行此範例</span><span class="sxs-lookup"><span data-stu-id="2d2da-149">To run this sample</span></span>  
  
1.  <span data-ttu-id="2d2da-150">開啟命令視窗並巡覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="2d2da-150">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="2d2da-151">\<*範例路徑*\>\Admin\ExplorerOM\PartnerManagement\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="2d2da-151">\<*Samples Path*\>\Admin\ExplorerOM\PartnerManagement\bin\Debug</span></span>  
  
2.  <span data-ttu-id="2d2da-152">執行檔案 PartnerManagement.exe。</span><span class="sxs-lookup"><span data-stu-id="2d2da-152">Run the file PartnerManagement.exe.</span></span>  
  
3.  <span data-ttu-id="2d2da-153">此範例會顯示訊息，建立並登錄新的合作對象，當開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，然後檢視命名為新的合作對象**fedex 寄送**下**合作對象**節點。</span><span class="sxs-lookup"><span data-stu-id="2d2da-153">When the sample displays the message that the new party is created and enlisted, open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console and view the new party named **FedEx** under the **Parties** node.</span></span>  
  
4.  <span data-ttu-id="2d2da-154">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，瀏覽樹狀檢視**ShipmentRole**下**Applications\BizTalk 應用程式 1\Role 連結**。</span><span class="sxs-lookup"><span data-stu-id="2d2da-154">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, navigate the tree view to the **ShipmentRole** under **Applications\BizTalk Application 1\Role Links**.</span></span> <span data-ttu-id="2d2da-155">按兩下**ShipmentRole** ，並注意**ShipmentAgency1**對應至**SupplierAdvice**作業和**ShipmentAgency2**對應至**SupplierOrder**登記中的作業。</span><span class="sxs-lookup"><span data-stu-id="2d2da-155">Double-click **ShipmentRole** and notice **ShipmentAgency1** mapped to the **SupplierAdvice** operation and **ShipmentAgency2** mapped to the **SupplierOrder** operation in the enlistment.</span></span>  
  
5.  <span data-ttu-id="2d2da-156">在命令視窗中，按下 ENTER，以允許取消範例-登錄並刪除新的合作對象。</span><span class="sxs-lookup"><span data-stu-id="2d2da-156">In the command window, press ENTER to allow the sample to un-enlist and delete the new party.</span></span>  
  
6.  <span data-ttu-id="2d2da-157">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，確認已從取消登錄的合作對象**ShipmentRole**和刪除從**合作對象**節點。</span><span class="sxs-lookup"><span data-stu-id="2d2da-157">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, verify the party was un-enlisted from the **ShipmentRole** and deleted from the **Parties** node.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="2d2da-158">Windows PowerShell 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="2d2da-158">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="2d2da-159">下列 Windows PowerShell 指令碼範例可以用於示範的相同功能**ExplorerOM**類別：</span><span class="sxs-lookup"><span data-stu-id="2d2da-159">The following Windows PowerShell script example can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
```  
#===============================================================#  
#===                                                         ===#  
#=== Create a new party named "FedEx" as an example.         ===#  
#===                                                         ===#  
#=== Two Shipment agency send ports from the PartyResolution ===#  
#=== sample will be added to the party.                      ===#  
#===                                                         ===#  
#===============================================================#  
Function CreateParty  
{  
  #=== Create a party =====================#  
  $myParty = $Catalog.AddNewParty()  
  $myParty.Name = "FedEx"  
  
  #=== create a standard alias ==========================#  
  $standardAlias = $myParty.AddNewAlias()  
  $standardAlias.Name = "D-U-N-S (Dun & Bradstreet)"  
  $standardAlias.Value = "Value1"  
  
  #=== Create a custom alias ==================#  
  $customAlias = $myParty.AddNewAlias()  
  $customAlias.Name = "Telephone"  
  $customAlias.Qualifier = "100"  
  $customAlias.Value = "4255550234"  
  
  #=== Add party send ports =====================================================#  
  
  #===============================================================#  
  #=== Have to use IList directly on this sendports collection ===#  
  #=== to work around a PowerShell issue.                      ===#  
  #===============================================================#  
  $iList = [System.Collections.IList]  
  
  $sendport1 = $Catalog.SendPorts["SP_FilesToShipmentAgency1"]  
  [void] $iList.GetMethod("Add").Invoke($myParty.SendPorts,$sendport1)  
  
  $sendport2 = $Catalog.SendPorts["SP_FilesToShipmentAgency2"]  
  [void] $iList.GetMethod("Add").Invoke($myParty.SendPorts,$sendport2)  
  
  #=== Specify a signature certificate, make sure the certificate is available ===#  
  #=== in the AddressBook store of the Local Machine                           ===#  
  
  foreach ($certificate in $Catalog.Certificates)  
  {  
    if ($certificate.ShortName -eq "BR, Certisign Certificadora Digital Ltda., Certisign - Autoridade Certificadora - AC2")  
    {  
      $myParty.SignatureCert = $certificate  
    }  
  }  
  
  #=== Commit the changes ===#  
  $catalog.SaveChanges()  
}  
  
#===============================================================#  
#===                                                         ===#  
#=== Delete the party named "FedEx"                          ===#  
#===                                                         ===#  
#===============================================================#  
Function DeleteParty  
{  
  $Catalog.RemoveParty($Catalog.Parties["FedEx"])  
  
  #=== Commit the changes ===#  
  $catalog.SaveChanges()  
}  
  
#===============================================================#  
#===                                                         ===#  
#=== Enlist the "FedEx" party with the "ShipmentRole"        ===#  
#===                                                         ===#  
#===============================================================#  
Function EnlistParty  
{  
  $myParty = $Catalog.Parties["FedEx"]  
  
  #=== Get the "ShipmentRole" in the Supplier assembly.        ===#  
  $svcRole = $Catalog.Assemblies["Supplier"].Roles["ShipmentRole"]  
  
  #=== Enlist the party under the shipper role ===#  
  $enlistedParty = $svcRole.AddNewEnlistedParty($myParty)  
  
  #===============================================================#  
  #=== Have to use IList directly on this sendports collection ===#  
  #=== to work around a PowerShell issue.                      ===#  
  #===============================================================#  
  $iList = [System.Collections.IList]   
  
  #===============================================================#  
  #=== Example port to be used for the role's "SupplierAdvice" ===#  
  #=== operation.                                              ===#  
  #=== Using the first send port added to the new party which  ===#  
  #=== is "SP_FilesToShipmentAgency1" at index 0 in the        ===#  
  #=== sendports collection.                                   ===#  
  #===============================================================#  
  $enlistedParty.Mappings[0].SendPort = $iList.GetProperty("Item").GetValue($myParty.SendPorts,0)  
  
  #===============================================================#  
  #=== Example port to be used for the role's "SupplierOrder"  ===#  
  #=== operation.                                              ===#  
  #=== Using the second send port added to the new party which ===#  
  #=== is "SP_FilesToShipmentAgency2" at index 1 in the        ===#  
  #=== sendports collection.                                   ===#  
  #===============================================================#  
  $enlistedParty.Mappings[1].SendPort = $iList.GetProperty("Item").GetValue($myParty.SendPorts,1)  
  
  #=== Commit the changes ===#  
  $Catalog.SaveChanges()  
}  
  
#===============================================================#  
#===                                                         ===#  
#=== Unenlist the "FedEx" party from the ShipmentRole        ===#  
#===                                                         ===#  
#===============================================================#  
Function UnenlistParty  
{  
  #=== Get the "ShipmentRole" from the Supplier assembly. ===#  
  $svcRole = $Catalog.Assemblies["Supplier"].Roles["ShipmentRole"]  
  
  #=== Remove the "FedEx" party ===#  
  foreach ($enlistedparty in $svcRole.EnlistedParties)  
  {  
    if ($enlistedparty.Party.Name -eq "FedEx")  
    {  
      $svcRole.RemoveEnlistedParty($enlistedparty)  
      break  
    }  
  }  
  
  #=== Commit the changes ===#  
  $Catalog.SaveChanges()  
}  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=== This sample expects the PartyResolution sample to be built and deployed  ===#  
#=== to the BizTalk Server.                                                   ===#  
  
write-host `r`nMake sure the "PartyResolution" sample application from the Orchestrations   
write-host sample directory is deployed and running.  
write-host By default it will be listed in the BizTalk Server Administration Console  
write-host with the application name: `"BizTalk.Application.1`"`r`n  
  
$SupplierAssembly = $Catalog.Assemblies["Supplier"]  
  
#==================================================================#  
#=== Register a trap handler to discard changes on exceptions   ===#  
#=== Execution will continue in the event we want to unenlist,  ===#  
#=== and delete the party.                                      ===#  
#==================================================================#  
  
$Script:NoExceptionOccurred = $true  
$ErrorActionPreference="silentlycontinue"  
trap   
{   
  $Script:NoExceptionOccurred = $false  
  "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes and continuing execution so we can attempt to clean up the party...`r`n"  
  $Catalog.DiscardChanges()  
}  
  
CreateParty  
EnlistParty  
  
if ($Script:NoExceptionOccurred)  
{  
  Write-Host "`r`nExample Party `"FedEx`" should be created and enlisted with the `"ShipmentRole`".`r`n"  
  Write-Host You can view the results in the BizTalk Server Administration console.`r`n  
  Write-Host "Press <Enter> to unenlist and delete...`r`n"  
  Read-Host  
}  
  
UnenlistParty  
DeleteParty  
  
```  
  
 <span data-ttu-id="2d2da-160">以下是從執行中的 PowerShell 範例指令碼的範例輸出。</span><span class="sxs-lookup"><span data-stu-id="2d2da-160">Here is example output from running the PowerShell example script.</span></span> <span data-ttu-id="2d2da-161">如果指令碼執行失敗，請確定已啟用 PowerShell 指令碼根據需求注意，本主題的頂端。</span><span class="sxs-lookup"><span data-stu-id="2d2da-161">If the script fails to run, make sure PowerShell scripting is enabled according to the requirements note at the top of this topic.</span></span>  
  
```  
PS C:\> .\PartnerManagement.ps1  
  
Make sure the PartyResolution sample application from the Orchestrations  
sample directory is deployed and running.  
By default it will be listed in the BizTalk Server Administration Console  
with the application name: "BizTalk.Application.1"  
  
Example Party "FedEx" should be created and enlisted with the "ShipmentRole".  
  
You can view the results in the BizTalk Server Administration console.  
  
Press <Enter> to unenlist and delete...  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d2da-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="2d2da-162">See Also</span></span>  
 <span data-ttu-id="2d2da-163">[合作對象](../core/parties.md) </span><span class="sxs-lookup"><span data-stu-id="2d2da-163">[Parties](../core/parties.md) </span></span>  
 <span data-ttu-id="2d2da-164">[角色連結和服務連結角色](../core/role-links-and-service-link-roles.md) </span><span class="sxs-lookup"><span data-stu-id="2d2da-164">[Role Links and Service Link Roles](../core/role-links-and-service-link-roles.md) </span></span>  
 [<span data-ttu-id="2d2da-165">Admin (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="2d2da-165">Admin (BizTalk Server Samples Folder)</span></span>](../core/admin-biztalk-server-samples-folder.md)