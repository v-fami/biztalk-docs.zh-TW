---
title: 設定 Oracle E-business Suite 中使用訊息內容屬性的應用程式內容 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51b76788-5c81-4bb4-8ef6-b1439955ea97
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71920920c11028adb1f699e3faee463876399b36
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003999"
---
# <a name="configure-the-application-context-using-message-context-properties-in-oracle-e-business-suite"></a><span data-ttu-id="043a6-102">設定 Oracle E-business Suite 中使用訊息內容屬性的應用程式內容</span><span class="sxs-lookup"><span data-stu-id="043a6-102">Configure the application context using message context properties in Oracle E-Business Suite</span></span>
<span data-ttu-id="043a6-103">若要使用的 Oracle E-business Suite 成品上執行作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須適當設定的應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="043a6-103">To perform operations on Oracle E-Business Suite artifacts using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must set the application context appropriately.</span></span> <span data-ttu-id="043a6-104">您可以透過下列方式設定應用程式內容：</span><span class="sxs-lookup"><span data-stu-id="043a6-104">You can set the application context in the following ways:</span></span>  
  
- <span data-ttu-id="043a6-105">藉由指定配接器所公開的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="043a6-105">By specifying the binding properties that the adapter exposes.</span></span> <span data-ttu-id="043a6-106">如需詳細資訊，請參閱 <<c0> [ 設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="043a6-106">For more information, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
- <span data-ttu-id="043a6-107">使用配接器所公開的訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="043a6-107">By using message context properties that the adapter exposes.</span></span> <span data-ttu-id="043a6-108">使用訊息內容屬性中設定應用程式內容時，您必須考慮下列。</span><span class="sxs-lookup"><span data-stu-id="043a6-108">You must consider the following when setting the application context by using message context properties.</span></span>  
  
  -   <span data-ttu-id="043a6-109">您可以設定值，僅適用於**ApplicationShortName**， **OrganizationID**， **ResponsibilityKey**，以及**ResponsibilityName**使用訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="043a6-109">You can set values only for **ApplicationShortName**, **OrganizationID**, **ResponsibilityKey**, and **ResponsibilityName** by using message context properties.</span></span> <span data-ttu-id="043a6-110">使用者名稱和密碼，您必須使用的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="043a6-110">For the user name and password, you must use the binding properties.</span></span> <span data-ttu-id="043a6-111">指定的值**ResponsibilityKey**訊息內容屬性會覆寫的指定值**ResponsibilityName**訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="043a6-111">The value specified for the **ResponsibilityKey** message context property overrides the value specified for the **ResponsibilityName** message context property.</span></span>  
  
  -   <span data-ttu-id="043a6-112">如果您設定應用程式內容使用繫結屬性和訊息內容屬性，指定訊息內容屬性的值更高的優先順序，並覆寫指定的繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="043a6-112">If you set the application context using both the binding properties and message context properties, the values specified for message context properties take precedence and override the values specified for the binding properties.</span></span> <span data-ttu-id="043a6-113">不過，比方說，如果您指定的應用程式簡短名稱，為訊息內容屬性，以及組織識別碼和責任名稱做為繫結屬性時，只有應用程式的簡短名稱的值是取自訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="043a6-113">However, for example, if you specify the application short name as a message context property, and the organization ID and responsibility name as binding properties, only the value for the application short name is taken from the message context property.</span></span> <span data-ttu-id="043a6-114">其餘部分會挑選從相關的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="043a6-114">The rest are picked from the relevant binding properties.</span></span>  
  
  <span data-ttu-id="043a6-115">為何要使用訊息內容屬性，透過繫結來設定應用程式內容的屬性？</span><span class="sxs-lookup"><span data-stu-id="043a6-115">Why use message context properties over binding properties to set the application context?</span></span> <span data-ttu-id="043a6-116">如果您設定應用程式內容繫結屬性，Wcf-custom 傳送埠[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可用僅適用於特定的組織識別碼、 責任和您指定的繫結屬性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="043a6-116">If you set the application context using binding properties, the WCF-Custom send port for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] can be used only for the specific organization ID, responsibility, and application that you specified for the binding properties.</span></span> <span data-ttu-id="043a6-117">相反的如果您使用訊息內容屬性，您可以設定 「 一般 」 的 Wcf-custom 傳送埠，並在訊息層級設定的應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="043a6-117">On the contrary, if you use the message context property, you can configure a “generic” WCF-Custom send port, and set the application context at the message level.</span></span>  
  
  <span data-ttu-id="043a6-118">配接器用戶端必須設定訊息內容屬性傳送到 Oracle E-business Suite 來叫用 Oracle E-business suite 作業的訊息。</span><span class="sxs-lookup"><span data-stu-id="043a6-118">Adapter clients must set the message context properties on the message that is sent to Oracle E-Business Suite to invoke an operation on Oracle E-Business Suite.</span></span> <span data-ttu-id="043a6-119">中的訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]是固定不變。</span><span class="sxs-lookup"><span data-stu-id="043a6-119">The messages in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] are immutable.</span></span> <span data-ttu-id="043a6-120">因此，用戶端必須先從現有的訊息，建立一則訊息，然後將訊息內容屬性在新的訊息。</span><span class="sxs-lookup"><span data-stu-id="043a6-120">Hence, clients must first create a message from the existing message, and then set the message context properties on the new message.</span></span> <span data-ttu-id="043a6-121">在本節中所述的程序，假設現有的訊息，會呼叫**要求**，而新的訊息稱為**New_Request**。</span><span class="sxs-lookup"><span data-stu-id="043a6-121">For the procedure described in this section, assume that the existing message is called **Request**, and the new message is called **New_Request**.</span></span>  
  
## <a name="set-the-message-context-properties-for-biztalk-applications"></a><span data-ttu-id="043a6-122">設定訊息的 BizTalk 應用程式的內容屬性</span><span class="sxs-lookup"><span data-stu-id="043a6-122">Set the message context properties for BizTalk applications</span></span>  
  
1. <span data-ttu-id="043a6-123">開啟 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="043a6-123">Open the BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
2. <span data-ttu-id="043a6-124">在 [方案總管] 中，以滑鼠右鍵按一下**參考**，然後按一下**新增參考**。</span><span class="sxs-lookup"><span data-stu-id="043a6-124">In Solution Explorer, right-click **References**, and then click **Add References**.</span></span>  
  
3. <span data-ttu-id="043a6-125">在**加入參考** 對話方塊中，按一下**瀏覽**索引標籤，然後再瀏覽至位置，BizTalk 屬性結構描述 DLL 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可用。</span><span class="sxs-lookup"><span data-stu-id="043a6-125">In the **Add Reference** dialog box, click the **Browse** tab, and then browse to the location where the BizTalk property schema DLL for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is available.</span></span>  
  
    <span data-ttu-id="043a6-126">此 DLL `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`，會安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]在\<*安裝磁碟機*\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin。</span><span class="sxs-lookup"><span data-stu-id="043a6-126">This DLL, `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`, is installed by the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] at \<*installation drive*\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin.</span></span>  
  
4. <span data-ttu-id="043a6-127">選取 DLL，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="043a6-127">Select the DLL, and then click **Add**.</span></span>  
  
5. <span data-ttu-id="043a6-128">在 BizTalk 協調流程中，將訊息，新增**New_Request**。</span><span class="sxs-lookup"><span data-stu-id="043a6-128">In the BizTalk orchestration, add a message, **New_Request**.</span></span> <span data-ttu-id="043a6-129">針對**訊息類型**屬性，請確定您選取相同的型別做為現有的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="043a6-129">For the **Message Type** property, make sure you select the same type as the existing request message.</span></span>  
  
6. <span data-ttu-id="043a6-130">「 傳送 」 圖形之前使用訊息傳送至傳送埠中，新增 「 建構訊息 」 圖形，並在其中，「 訊息指派 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="043a6-130">Before the Send shape using which the message is sent to the send port, add a Construct Message shape and within that, a Message Assignment shape.</span></span>  
  
7. <span data-ttu-id="043a6-131">按兩下訊息指派圖形，以開啟**BizTalk 運算式編輯器**。</span><span class="sxs-lookup"><span data-stu-id="043a6-131">Double-click the Message Assignment shape to open **BizTalk Expression Editor**.</span></span>  
  
8. <span data-ttu-id="043a6-132">在  **BizTalk 運算式編輯器**，新增下列程式碼，然後按一下 **確定**:</span><span class="sxs-lookup"><span data-stu-id="043a6-132">In **BizTalk Expression Editor**, add the following, and then click **OK**:</span></span>  
  
   ```  
   New_Request = Request;  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ApplicationShortName) = "AR";  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ResponsibilityKey) = "RECEIVABLES_VISION_OPERATIONS";  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.ResponsibilityName) = "Receivables, Vision Operations (USA)";  
   New_Request(Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.OrganizationId) = "204";  
   ```  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="043a6-133">指定的值**ResponsibilityKey**訊息內容屬性會覆寫的指定值**ResponsibilityName**訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="043a6-133">The value specified for the **ResponsibilityKey** message context property overrides the value specified for the **ResponsibilityName** message context property.</span></span>  
  
9. <span data-ttu-id="043a6-134">請確定協調流程進一步處理是藉由使用**New_Request**訊息。</span><span class="sxs-lookup"><span data-stu-id="043a6-134">Make sure further processing of the orchestration is done by using the **New_Request** message.</span></span>  
  
10. <span data-ttu-id="043a6-135">您可以部署在此協調流程之前[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須將組件參考新增`Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`中，您會部署 「 協調流程的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="043a6-135">Before you can deploy this orchestration in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must add the assembly reference for `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll` in the BizTalk application where you will be deploying the orchestration.</span></span> <span data-ttu-id="043a6-136">若要部署中的組件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="043a6-136">To deploy an assembly in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]:</span></span>  
  
    1. <span data-ttu-id="043a6-137">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="043a6-137">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
    2. <span data-ttu-id="043a6-138">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，，然後您要新增 BizTalk 組件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="043a6-138">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then the application to which you want to add a BizTalk assembly.</span></span>  
  
    3. <span data-ttu-id="043a6-139">您可以要求您想要的資料表**做為回應的一部分傳回。</span><span class="sxs-lookup"><span data-stu-id="043a6-139">Right-click **Resources**, point to **Add**, and then click **BizTalk Assemblies**.</span></span>  
  
    4. <span data-ttu-id="043a6-140">在 [**新增資源**] 對話方塊中，按一下**新增**，瀏覽至包含 BizTalk 組件檔案，也就是資料夾\<*安裝磁碟機*\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin。</span><span class="sxs-lookup"><span data-stu-id="043a6-140">In the **Add Resources** dialog box, click **Add**, navigate to the folder containing the BizTalk assembly file, which is \<*installation drive*\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\bin.</span></span> <span data-ttu-id="043a6-141">選取 `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll`檔案，然後再按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="043a6-141">Select the `Microsoft.Adapters.OracleEBS.BiztalkPropertySchema.dll` file, and then click **Open**.</span></span>  
  
    5. <span data-ttu-id="043a6-142">在 **選項**索引標籤上，指定 BizTalk 組件安裝到全域組件快取 (GAC) 的選項，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="043a6-142">On the **Options** tab, specify the options for installing the BizTalk assembly to the global assembly cache (GAC), and then click **OK**.</span></span>  
  
## <a name="set-the-language-for-performing-operations"></a><span data-ttu-id="043a6-143">設定執行作業的語言</span><span class="sxs-lookup"><span data-stu-id="043a6-143">Set the Language for Performing Operations</span></span>  
 <span data-ttu-id="043a6-144">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援 Oracle E-business Suite、 多國語言支援 (MLS) 功能，並可讓您在執行作業時指定的語言。</span><span class="sxs-lookup"><span data-stu-id="043a6-144">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports the Multi-Language Support (MLS) feature of Oracle E-Business Suite, and allows you to specify a language while performing operations.</span></span> <span data-ttu-id="043a6-145">配接器會公開**語言**訊息內容屬性來指定執行作業的語言。</span><span class="sxs-lookup"><span data-stu-id="043a6-145">The adapter exposes the **Language** message context property to specify a language for performing operations.</span></span>  
  
 <span data-ttu-id="043a6-146">指定的值**語言**訊息內容屬性會覆寫的值**語言**下的屬性繫結**MlsSettings**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="043a6-146">The value specified for the **Language** message context property overrides the value of the **Language** binding property under the **MlsSettings** binding property.</span></span> <span data-ttu-id="043a6-147">如需詳細資訊**MlsSettings**繫結屬性，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="043a6-147">For more information about the **MlsSettings** binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
