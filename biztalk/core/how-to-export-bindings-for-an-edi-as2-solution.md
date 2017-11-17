---
title: "如何匯出 EDI AS2 方案的繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 856ab630-66c4-4496-884a-fdbe641143c5
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aceeb81933324d5b3c164396290fe7b99cdc7295
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-bindings-for-an-edi-as2-solution"></a><span data-ttu-id="ceac4-102">如何匯出 EDI AS2 方案的繫結</span><span class="sxs-lookup"><span data-stu-id="ceac4-102">How to Export Bindings for an EDI-AS2 Solution</span></span>
<span data-ttu-id="ceac4-103">本主題說明如何從設定為 EDI 和 (或) AS2 方案的電腦匯出組態。</span><span class="sxs-lookup"><span data-stu-id="ceac4-103">This topic describes how to export the configuration from a computer set up as an EDI and/or AS2 solution.</span></span> <span data-ttu-id="ceac4-104">這可讓您以自動化的方式在另一部電腦上設定相同的組態。</span><span class="sxs-lookup"><span data-stu-id="ceac4-104">This enables you to set up the same configuration on another computer in an automated fashion.</span></span> <span data-ttu-id="ceac4-105">您可以從應用程式、群組或組件匯出繫結。</span><span class="sxs-lookup"><span data-stu-id="ceac4-105">You can export the bindings from an application, group, or assembly.</span></span>  
  
 <span data-ttu-id="ceac4-106">您可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台內建立繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="ceac4-106">You create a binding file from within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="ceac4-107">.xml 繫結檔案包含所有與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="ceac4-107">The .xml binding file contains all information pertinent to your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration.</span></span> <span data-ttu-id="ceac4-108">這包括所有的 EDI 和 AS2 組態屬性，但是不包含某些安全性資訊。</span><span class="sxs-lookup"><span data-stu-id="ceac4-108">This includes all EDI and AS2 configuration properties, with the exception of certain security information.</span></span> <span data-ttu-id="ceac4-109">如需繫結檔案 （包括 EDI 和 AS2 節點） 中的節點的詳細資訊，請參閱[繫結檔案的結構](../core/structure-of-a-binding-file.md)。</span><span class="sxs-lookup"><span data-stu-id="ceac4-109">For detailed information about the nodes in a binding file (including EDI and AS2 nodes), see [Structure of a Binding File](../core/structure-of-a-binding-file.md).</span></span> <span data-ttu-id="ceac4-110">如需 EDI/AS2 繫結的一般資訊，請參閱下面的「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 繫結檔案中的 EDI 和 AS2 節點」。</span><span class="sxs-lookup"><span data-stu-id="ceac4-110">For general information about the EDI/AS2 bindings, see "EDI and AS2 Nodes in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Binding File" below.</span></span>  
  
 <span data-ttu-id="ceac4-111">您也可以使用 .msi 檔，在匯出應用程式時一併匯出繫結。</span><span class="sxs-lookup"><span data-stu-id="ceac4-111">You can also export bindings as part of exporting an application using an .msi file.</span></span> <span data-ttu-id="ceac4-112">如需詳細資訊，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ceac4-112">For more information, see the [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).</span></span> <span data-ttu-id="ceac4-113">或者，您可以使用 BTSTask 命令匯出和匯入繫結。</span><span class="sxs-lookup"><span data-stu-id="ceac4-113">Or you can use the BTSTask command to export and import bindings.</span></span> <span data-ttu-id="ceac4-114">如需 BTSTask 的詳細資訊，請參閱[BTSTask 命令列參考](../core/btstask-command-line-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="ceac4-114">For more information about BTSTask, see [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md).</span></span>  
  
 <span data-ttu-id="ceac4-115">**匯出繫結**</span><span class="sxs-lookup"><span data-stu-id="ceac4-115">**Exporting Bindings**</span></span>  
  
 <span data-ttu-id="ceac4-116">在您匯出組態時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會自動匯出所有繫結合作對象的 EDI 屬性和其他合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="ceac4-116">When you export the configuration, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will automatically export the EDI Properties, and other party information, of all bound parties.</span></span> <span data-ttu-id="ceac4-117">如果您啟動匯出全域合作對象資訊的功能，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 也會匯出未繫結到協調流程之合作對象的屬性，以及全域 EDI 屬性。</span><span class="sxs-lookup"><span data-stu-id="ceac4-117">If you activate the exporting of global party information, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will also export properties for parties that are not bound to an orchestration, and global EDI properties.</span></span> <span data-ttu-id="ceac4-118">您可以利用三種方法來匯出全域合作對象資訊：</span><span class="sxs-lookup"><span data-stu-id="ceac4-118">You can export global party information in three ways:</span></span>  
  
-   <span data-ttu-id="ceac4-119">在 [匯出繫結] 對話方塊中核取 [匯出全域合作對象資訊] 屬性。</span><span class="sxs-lookup"><span data-stu-id="ceac4-119">By checking the Export Global Party Information property in the Export Bindings dialog box.</span></span>  
  
-   <span data-ttu-id="ceac4-120">在 [匯出 MSI 檔案精靈] 的 [選取資源] 窗格中核取 [全域合作對象] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ceac4-120">By checking the Global Parties checkbox in the Select Resources pane of the Export MSI File Wizard.</span></span>  
  
-   <span data-ttu-id="ceac4-121">在 BTSTask 命令列工具中使用 GlobalParties 參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ceac4-121">By using the GlobalParties switch in the BTSTask command line tool, as follows:</span></span>  
  
    ```  
    BTSTask ExportBindings -Destination:value ((([-ApplicationName:value] | [-AssemblyName:value]) [-GlobalParties]) | [-GroupLevel])  
    ```  
  
 <span data-ttu-id="ceac4-122">基於安全性理由，當您匯出繫結檔案，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]從檔案移除繫結密碼。</span><span class="sxs-lookup"><span data-stu-id="ceac4-122">For security reasons, when you export a binding file, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] removes the passwords for the bindings from the file.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ceac4-123">ISA1、 ISA2、 ISA3 和 ISA4 欄位，從 X12 與 EDIFACT 屬性移除 UNB6.1 和 UNB6.2 欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="ceac4-123"> removes UNB6.1 and UNB6.2 fields from EDIFACT Properties, and ISA1, ISA2, ISA3, and ISA4 fields from X12 Properties.</span></span>  
  
 <span data-ttu-id="ceac4-124">除了使用 export-bindings、export-application 或 BTSTask 命令之外，您也可以手動建立 XML 繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="ceac4-124">In addition to using the export-bindings, export-application, or BTSTask commands, you can create an XML binding file manually.</span></span> <span data-ttu-id="ceac4-125">透過這種方式，您可以從企業營運系統應用程式匯出合作對象和 EDI 設定。</span><span class="sxs-lookup"><span data-stu-id="ceac4-125">By doing so, you can export party and EDI settings from a line-of-business application.</span></span> <span data-ttu-id="ceac4-126">接著，您就可以使用 import-bindings 命令或 BTSTask 命令來匯入繫結。</span><span class="sxs-lookup"><span data-stu-id="ceac4-126">You could then import the bindings using the import-bindings command or the BTSTask command.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ceac4-127">必要條件</span><span class="sxs-lookup"><span data-stu-id="ceac4-127">Prerequisites</span></span>  
 <span data-ttu-id="ceac4-128">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶來登入。</span><span class="sxs-lookup"><span data-stu-id="ceac4-128">You must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span> <span data-ttu-id="ceac4-129">如需詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的＜部署和管理 BizTalk 應用程式所需的權限＞。</span><span class="sxs-lookup"><span data-stu-id="ceac4-129">For more information, see "Permissions Required for Deploying and Managing a BizTalk Application" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
### <a name="exporting-the-configuration-into-a-binding-file"></a><span data-ttu-id="ceac4-130">將組態匯出到繫結檔案</span><span class="sxs-lookup"><span data-stu-id="ceac4-130">Exporting the Configuration into a Binding File</span></span>  
  
1.  <span data-ttu-id="ceac4-131">在您要匯出組態的來源電腦上，開啟 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ceac4-131">On the computer that you want to export the configuration from, open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
2.  <span data-ttu-id="ceac4-132">以滑鼠右鍵按一下您想要複製的組態，指向 BizTalk 應用程式**匯出**，然後按一下 **繫結**。</span><span class="sxs-lookup"><span data-stu-id="ceac4-132">Right-click the BizTalk Application that you want to copy the configuration from, point to **Export**, and then click **Bindings**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ceac4-133">您也可以使用 BTSTask 公用程式匯出或匯入組態。</span><span class="sxs-lookup"><span data-stu-id="ceac4-133">You can also use the BTSTask utility to export or import the configuration.</span></span>  
  
3.  <span data-ttu-id="ceac4-134">選取匯出選項，包括選擇從目前的應用程式或群組匯出，或是匯出組件的繫結。</span><span class="sxs-lookup"><span data-stu-id="ceac4-134">Select the export option, selecting to export from the current application or group, or exporting bindings for an assembly.</span></span>  
  
4.  <span data-ttu-id="ceac4-135">如果您想要匯出所有合作對象及其非機密內容，即使協調流程未繫結，然後按一下**匯出全域合作對象資訊**。</span><span class="sxs-lookup"><span data-stu-id="ceac4-135">If you want to export all parties and their non-sensitive properties, even if an orchestration is not bound to them, click **Export Global Party information**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ceac4-136">如果您沒有按一下**匯出全域合作對象資訊**，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]匯出繫結至協調流程繫結檔案至任何合作對象屬性。</span><span class="sxs-lookup"><span data-stu-id="ceac4-136">If you do not click **Export Global Party information**, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will export properties for any parties that are bound to an orchestration, into the binding file.</span></span> <span data-ttu-id="ceac4-137">不過，它不會匯出任何合作對象未繫結至協調流程，除非您按一下**匯出全域合作對象資訊**。</span><span class="sxs-lookup"><span data-stu-id="ceac4-137">However, it will not export any parties that are not bound to an orchestration, unless you click **Export Global Party information**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ceac4-138">產生的繫結檔案時**匯出全域合作對象資訊**選取屬性會包含電腦上定義的所有合作對象的組態。</span><span class="sxs-lookup"><span data-stu-id="ceac4-138">The binding file generated while the **Export Global Party information** property is selected will include the configuration of all parties defined on the computer.</span></span> <span data-ttu-id="ceac4-139">在電腦定義的一組合作對象中，您將無法匯出其中一部分子集的組態。</span><span class="sxs-lookup"><span data-stu-id="ceac4-139">It is not possible to export the configuration of a subset of the complete set of parties defined on a computer.</span></span>  
  
5.  <span data-ttu-id="ceac4-140">按一下**確定**匯出繫結。</span><span class="sxs-lookup"><span data-stu-id="ceac4-140">Click **OK** to export the bindings.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ceac4-141"> 不會匯出任何 EDI 機密欄位，例如密碼或安全性/驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="ceac4-141"> will not export any EDI sensitive fields, such as passwords or security/authentication information.</span></span> <span data-ttu-id="ceac4-142">對於任何 EDI 機密欄位，它都會匯出空白字串。</span><span class="sxs-lookup"><span data-stu-id="ceac4-142">It will export a blank string for any EDI sensitive field.</span></span> <span data-ttu-id="ceac4-143">將繫結匯入至另一部電腦之後，您必須手動設定 EDI 機密欄位的值。</span><span class="sxs-lookup"><span data-stu-id="ceac4-143">After importing the bindings onto another computer, you must manually set the values for EDI sensitive fields.</span></span>  
  
6.  <span data-ttu-id="ceac4-144">手動記錄所有的 EDI 機密欄位，例如密碼或安全性/驗證資訊，以便稍後在匯入繫結的目標電腦上進行設定。</span><span class="sxs-lookup"><span data-stu-id="ceac4-144">Manually note any EDI sensitive fields, such as passwords or security/authentication information, for later setting on the computer that you import the bindings onto.</span></span>  
  
## <a name="edi-and-as2-nodes-in-the-biztalk-server-binding-file"></a><span data-ttu-id="ceac4-145">BizTalk Server 繫結檔案中的 EDI 和 AS2 節點</span><span class="sxs-lookup"><span data-stu-id="ceac4-145">EDI and AS2 Nodes in the BizTalk Server Binding File</span></span>  
 <span data-ttu-id="ceac4-146">如果您匯出組態**匯出全域合作對象資訊**屬性選取，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會產生繫結檔案具有下列節點：</span><span class="sxs-lookup"><span data-stu-id="ceac4-146">If you export your configuration with the **Export Global Party information** property selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate a binding file that has that following nodes:</span></span>  
  
```  
EdiData  
   PartyEDIProperties  
      PartnerAgreement  
         Contacts  
      PartnerEdifact  
         PartnerEdifactReceiverGroups  
         PartnerEdifactSenderGroups  
      PartnerAckValidation  
      PartnerX12  
      PartnerX12ReceiverGroups  
      PartnerX12SenderGroups  
      PartnerBatchUpdatable  
      PartnerAS2CommonUpdatable  
      PartnerAS2  
```  
  
 <span data-ttu-id="ceac4-147">EDI 全域屬性將會加入至繫結檔案的下列節點中。</span><span class="sxs-lookup"><span data-stu-id="ceac4-147">EDI global properties will be added to the binding file in the following nodes.</span></span>  
  
```  
EDIGlobalProperties  
   EDIGlobalProperties  
      GlobalCommon  
      GlobalEdiFact  
      GlobalX12  
```  
  
 <span data-ttu-id="ceac4-148">EDI 和 AS2 節點會加入至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 繫結檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="ceac4-148">EDI and AS2 nodes are added to the end of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] binding file.</span></span> <span data-ttu-id="ceac4-149">EdiData 節點會加入至 [合作對象集合] 節點底下的 [合作對象] 子節點，而且 EdiGlobalProperties 節點會加入 [合作對象集合] 後面 (與其位於相同層級)。</span><span class="sxs-lookup"><span data-stu-id="ceac4-149">The EdiData node is added to the Party subnode under the Party Collection node, and the EdiGlobalProperties node is added after, and at the same level as, the Party Collection node.</span></span> <span data-ttu-id="ceac4-150">如需 BizTalk 繫結檔案中的 EDI 和 AS2 節點的詳細資訊，請參閱[繫結檔案的結構](../core/structure-of-a-binding-file.md)。</span><span class="sxs-lookup"><span data-stu-id="ceac4-150">For more information about the EDI and AS2 nodes in the BizTalk binding file, see [Structure of a Binding File](../core/structure-of-a-binding-file.md).</span></span>  
  
 <span data-ttu-id="ceac4-151">EdiData 節點是選用項目。</span><span class="sxs-lookup"><span data-stu-id="ceac4-151">The EdiData node is optional.</span></span> <span data-ttu-id="ceac4-152">不過，如果有 EdiData 節點存在，則 EdiData 底下必須有子節點。</span><span class="sxs-lookup"><span data-stu-id="ceac4-152">However, if the EdiData node is present, the subnodes under EdiData are required.</span></span> <span data-ttu-id="ceac4-153">同樣地，EdiGlobalProperties 節點也是選用項目，但是如果有 EdiGlobalProperties 存在，其底下也必須有子節點。</span><span class="sxs-lookup"><span data-stu-id="ceac4-153">Likewise, the EdiGlobalProperties node is optional; however, if the EdiGlobalProperties node is present, the subnodes under it are required.</span></span>  
  
 <span data-ttu-id="ceac4-154">EDI 和 AS2 繫結檔案節點不會直接對應到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中夥伴協議管理員的屬性頁。</span><span class="sxs-lookup"><span data-stu-id="ceac4-154">EDI and AS2 binding file nodes do not correspond directly to the property pages in the Partner Agreement Manager in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="ceac4-155">某些 EDI 和 AS2 繫結檔案節點包括用於傳送者角色的屬性，以及用於接收者角色的屬性。</span><span class="sxs-lookup"><span data-stu-id="ceac4-155">Some EDI and AS2 binding file nodes include properties used for sender roles and properties used for receiver roles.</span></span> <span data-ttu-id="ceac4-156">角色是由節點中的 IsSender 屬性指定。</span><span class="sxs-lookup"><span data-stu-id="ceac4-156">The role is indicated by the IsSender property in the node.</span></span> <span data-ttu-id="ceac4-157">如果節點並未用於傳送者和接收者兩種角色 (PartnerAgreement、PartnerBatchUpdatable、PartnerAS2Updatable 和 GlobalCommon)，則 IsSender 一定是 False。</span><span class="sxs-lookup"><span data-stu-id="ceac4-157">For those nodes that are not used for both sender and receiver roles (PartnerAgreement, PartnerBatchUpdatable, PartnerAS2Updatable, and GlobalCommon), IsSender is always False.</span></span>  
  
 <span data-ttu-id="ceac4-158">不論 IsSender 設定為 True 或 False，PartnerEdifact 和 PartnerX12 節點都會包含用於接收者和傳送者兩種角色的屬性。</span><span class="sxs-lookup"><span data-stu-id="ceac4-158">The PartnerEdifact and PartnerX12 nodes contain properties for both the receiver and sender roles, whether or not IsSender is set to True or False.</span></span> <span data-ttu-id="ceac4-159">例如，即使 IsSender 是 True，PartnerEdifact 也會包含 Una1 欄位 (用於做為交換接收者的合作對象)，</span><span class="sxs-lookup"><span data-stu-id="ceac4-159">For example, PartnerEdifact will include a Una1 field (used for the party as an interchange receiver), even when IsSender is True.</span></span> <span data-ttu-id="ceac4-160">而即使 IsSender 是 False，PartnerEdifact 還是會包含 Unb5CheckDup 欄位 (用於做為交換傳送者的合作對象)。</span><span class="sxs-lookup"><span data-stu-id="ceac4-160">PartnerEdifact will also include a Unb5CheckDup field (used for the party as an interchange sender), even when IsSender is False.</span></span> <span data-ttu-id="ceac4-161">不過，當 IsSender 是 True 時，做為交換接收者之合作對象的欄位就不會在 UI 或引擎中使用，而會指定預設值。</span><span class="sxs-lookup"><span data-stu-id="ceac4-161">However, when IsSender is True, the fields for the party as an interchange receiver are not used in the UI or by the engine, but are given default values.</span></span> <span data-ttu-id="ceac4-162">同樣地，當 IsSender 為 False，做為交換傳送者合作對象的欄位不會在 UI 或引擎，但會指定預設值。</span><span class="sxs-lookup"><span data-stu-id="ceac4-162">Likewise, when IsSender is False, the fields for the party as an interchange sender are not used in the UI or by the engine, but are given default values.</span></span>  
  
 <span data-ttu-id="ceac4-163">如果屬性的預設值是空值，除非該欄位已指定值，否則便不會包含在繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="ceac4-163">If the default of a property is null, the field will not be included in the binding file unless that field has been given a value.</span></span>  
  
 <span data-ttu-id="ceac4-164">繫結檔案資料會儲存在 BizTalk 管理資料庫 (BizTalkMgmtDb) 的資料表中。</span><span class="sxs-lookup"><span data-stu-id="ceac4-164">Binding file data is saved in tables of the BizTalk Management database (BizTalkMgmtDb).</span></span>