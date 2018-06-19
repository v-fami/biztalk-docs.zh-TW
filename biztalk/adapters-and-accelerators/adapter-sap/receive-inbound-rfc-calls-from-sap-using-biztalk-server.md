---
title: 從 SAP 使用 BizTalk Server 接收輸入 RFC 呼叫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RFC calls, receiving using BizTalk Server
ms.assetid: 822fd9fb-772f-4910-a11e-25c1d5dca6e1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b949ae0d6d5938493c78ed542a67d3c8bd09b48
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967748"
---
# <a name="receive-inbound-rfc-calls-from-sap-using-biztalk-server"></a><span data-ttu-id="393f0-102">從 SAP 使用 BizTalk Server 接收輸入 RFC 呼叫</span><span class="sxs-lookup"><span data-stu-id="393f0-102">Receive Inbound RFC Calls from SAP using BizTalk Server</span></span>
<span data-ttu-id="393f0-103">在 RFC 伺服器案例中，有三個實體：</span><span class="sxs-lookup"><span data-stu-id="393f0-103">In an RFC server scenario, there are three entities:</span></span>  
  
-   <span data-ttu-id="393f0-104">SAP 用戶端傳送要求給 SAP RFC 叫用。</span><span class="sxs-lookup"><span data-stu-id="393f0-104">An SAP client that sends a request to SAP to invoke an RFC.</span></span> <span data-ttu-id="393f0-105">這無法叫用使用 SAP GUI，或進行 RFC 用戶端，透過呼叫[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="393f0-105">This could be invoked either by using the SAP GUI or by making an RFC client call through the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
-   <span data-ttu-id="393f0-106">SAP 系統，其中包含 SAP 用戶端叫用的 RFC 函式定義。</span><span class="sxs-lookup"><span data-stu-id="393f0-106">The SAP system that contains an RFC function definition that the SAP client invokes.</span></span> <span data-ttu-id="393f0-107">SAP 系統將傳遞至 RFC 伺服器 （配接器） 的 在要求上。</span><span class="sxs-lookup"><span data-stu-id="393f0-107">The SAP system passes on the request to the RFC server (the adapter).</span></span> <span data-ttu-id="393f0-108">這是配接器用來取得 RFC 呼叫使配接器到 SAP 伺服器的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="393f0-108">This is used by the adapter to get the metadata of the RFC call that the SAP server makes into the adapter.</span></span>  
  
-   <span data-ttu-id="393f0-109">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ，做為 RFC 伺服器，並在裝載實際的 RFC。</span><span class="sxs-lookup"><span data-stu-id="393f0-109">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] that acts as the RFC server and hosts the actual RFC.</span></span>  
  
 <span data-ttu-id="393f0-110">在本主題不討論第一個實體，也就是 SAP 用戶端。</span><span class="sxs-lookup"><span data-stu-id="393f0-110">The first entity, the SAP client, is not discussed in this topic.</span></span> <span data-ttu-id="393f0-111">如果您用來叫用 RFC，SAP GUI，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="393f0-111">If you are using the SAP GUI to invoke an RFC, refer to SAP documentation.</span></span> <span data-ttu-id="393f0-112">如果您使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]要叫用 RFC，請參閱[叫用的 Rfc，SAP 使用 BizTalk server 中](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-112">If you are using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to invoke an RFC, see [Invoke RFCs in SAP by Using BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="393f0-113">本節提供如何使用配接器收到 RFC 伺服器呼叫，一旦 RFC 叫用由 SAP 用戶端上的指示。</span><span class="sxs-lookup"><span data-stu-id="393f0-113">This section provides instructions on how to use the adapter to receive an RFC server call, once the RFC is invoked by an SAP client.</span></span> <span data-ttu-id="393f0-114">如需有關如何配接器支援接收 RFC 伺服器呼叫使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[作業中 SAP Rfc](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-114">For more information on how the adapter supports receiving RFC server calls using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Operations on RFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md).</span></span>  
  
## <a name="how-to-receive-an-inbound-rfc-call-from-the-sap-system"></a><span data-ttu-id="393f0-115">如何從 SAP 系統接收輸入的 RFC 呼叫？</span><span class="sxs-lookup"><span data-stu-id="393f0-115">How to Receive an Inbound RFC Call from the SAP System?</span></span>  
 <span data-ttu-id="393f0-116">執行 SAP 系統使用的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立的 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-116">Performing an operation on an SAP system using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves procedural tasks described in [Building blocks to create SAP applications](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md).</span></span> <span data-ttu-id="393f0-117">若要從 SAP 系統接收的 RFC 呼叫，這些工作包括：</span><span class="sxs-lookup"><span data-stu-id="393f0-117">To receive an RFC call from the SAP system, these tasks are:</span></span>  
  
1.  <span data-ttu-id="393f0-118">設定 SAP 系統，在此情況下傳送至外部應用程式的 RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="393f0-118">Configure your SAP system to send RFC to an external application, in this case the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="393f0-119">建立 BizTalk 專案，並產生結構描述，如 RFC，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]將接收從 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="393f0-119">Create a BizTalk project and generate schema for the RFC that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] will be receiving from the SAP system.</span></span>  
  
3.  <span data-ttu-id="393f0-120">從 SAP 系統接收訊息，並傳送回應的 BizTalk 專案中建立訊息。</span><span class="sxs-lookup"><span data-stu-id="393f0-120">Create messages in the BizTalk project for receiving messages from the SAP system and sending responses.</span></span>  
  
4.  <span data-ttu-id="393f0-121">建立協調流程，以接收來自 SAP 系統的 RFC、 處理它，並傳送回應給 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="393f0-121">Create an orchestration to receive an RFC from the SAP system, process it, and send the response to the SAP system.</span></span>  
  
5.  <span data-ttu-id="393f0-122">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="393f0-122">Build and deploy the BizTalk project.</span></span>  
  
6.  <span data-ttu-id="393f0-123">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="393f0-123">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
7.  <span data-ttu-id="393f0-124">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="393f0-124">Start the BizTalk application.</span></span>  
  
 <span data-ttu-id="393f0-125">本主題提供執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="393f0-125">This topic provides instructions to perform these tasks.</span></span>  
  
## <a name="activities-on-the-sap-system"></a><span data-ttu-id="393f0-126">SAP 系統上的活動</span><span class="sxs-lookup"><span data-stu-id="393f0-126">Activities on the SAP System</span></span>  
 <span data-ttu-id="393f0-127">使用之前[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]若要從 SAP 系統接收傳入的 RFC 呼叫時，請確定您已完成的 SAP 系統上的下列工作。</span><span class="sxs-lookup"><span data-stu-id="393f0-127">Before using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to receive inbound RFC calls from the SAP system, make sure you complete the following tasks on the SAP system.</span></span>  
  
-   <span data-ttu-id="393f0-128">必須存在 SAP 配接器的 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="393f0-128">An RFC destination for the SAP adapter must exist.</span></span> <span data-ttu-id="393f0-129">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]接收從 SAP 系統，透過 SAP 系統上所定義的 RFC 目的地的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="393f0-129">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] receives RFCs from the SAP system through an RFC destination defined on the SAP system.</span></span> <span data-ttu-id="393f0-130">RFC 目的地包含 SAP 閘道器主機 SAP 閘道器服務，您必須在程式碼中指定連線 URI SAP 程式 ID。</span><span class="sxs-lookup"><span data-stu-id="393f0-130">The RFC destination contains the SAP Gateway Host, the SAP Gateway Service, and the SAP Program ID that you must specify in the connection URI in your code.</span></span> <span data-ttu-id="393f0-131">如需如何設定 SAP RFC 目的地資訊，請參閱[建立 RFC、 RFC 目的地並傳送從 SAP 系統的 RFC](creating-an-rfc-in-an-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-131">For information about how to setup an RFC destination on SAP, see [Create an RFC, RFC destination, and send an RFC from SAP system](creating-an-rfc-in-an-sap-system.md).</span></span>  
  
-   <span data-ttu-id="393f0-132">您必須建立定義 RFC，SAP 系統的函式模組。</span><span class="sxs-lookup"><span data-stu-id="393f0-132">You must create a function module that defines the RFC on the SAP system.</span></span> <span data-ttu-id="393f0-133">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 RFC 定義 SAP 系統上擷取 RFC （兩者都在設計階段和執行階段） 有關的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="393f0-133">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the RFC definition on the SAP system to retrieve metadata about the RFC (both at design-time and at runtime).</span></span> <span data-ttu-id="393f0-134">如需詳細資訊，請參閱[SAP 系統中建立 RFC](../../adapters-and-accelerators/adapter-sap/creating-an-rfc-in-an-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-134">For more information see [Creating an RFC in an SAP System](../../adapters-and-accelerators/adapter-sap/creating-an-rfc-in-an-sap-system.md).</span></span>  
  
     <span data-ttu-id="393f0-135">以下是原始程式碼的將兩個整數並傳回其結果的 RFC 之 SAP 系統上的範例。</span><span class="sxs-lookup"><span data-stu-id="393f0-135">The following is an example of the source code on the SAP system for an RFC that adds two integers and returns their result.</span></span> <span data-ttu-id="393f0-136">程式碼只會將 RFC 呼叫透過指定的目的地。</span><span class="sxs-lookup"><span data-stu-id="393f0-136">The code merely calls the RFC through a specified destination.</span></span> <span data-ttu-id="393f0-137">函式的實作方式是 SAP 配接器用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="393f0-137">The implementation of the function is done by the SAP adapter client code.</span></span>  
  
    ```  
    FUNCTION Z_RFC_ADD.  
    *"------------------------------------------------------------------  
    *"  
    *"Local interface:  
    *"  IMPORTING  
    *"     VALUE(X) TYPE  INT4  
    *"     VALUE(Y) TYPE  INT4  
    *"     VALUE(DEST) TYPE  CHAR20 DEFAULT 'SAPADAPTER'  
    *"  EXPORTING  
    *"     VALUE(RESULT) TYPE  INT4  
    *"------------------------------------------------------------------  
    CALL FUNCTION 'Z_RFC_ADD' DESTINATION DEST  
      EXPORTING X = X  
                Y = Y  
      IMPORTING RESULT = RESULT.  
  
    ENDFUNCTION.  
    ```  
  
## <a name="sample-based-on-this-topic"></a><span data-ttu-id="393f0-138">根據本主題的範例</span><span class="sxs-lookup"><span data-stu-id="393f0-138">Sample Based On This Topic</span></span>  
 <span data-ttu-id="393f0-139">基礎的範例，RFCServer，本主題也會提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="393f0-139">A sample, RFCServer, based on this topic is also provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="393f0-140">如需詳細資訊，請參閱[適用於 SAP 配接器範例](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-140">For more information, see [Samples for the SAP adapter](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).</span></span>  
  
## <a name="generating-the-schema"></a><span data-ttu-id="393f0-141">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="393f0-141">Generating the Schema</span></span>  
 <span data-ttu-id="393f0-142">本主題中，以示範如何從 SAP 系統中，會收到輸入的 RFC 呼叫我們產生的結構描述*Z_RFC_ADD* RFC。</span><span class="sxs-lookup"><span data-stu-id="393f0-142">In this topic, to demonstrate how to receive an inbound RFC call from the SAP system, we generate the schema for *Z_RFC_ADD* RFC.</span></span> <span data-ttu-id="393f0-143">您在上一個步驟中建立這個 RFC。</span><span class="sxs-lookup"><span data-stu-id="393f0-143">You created this RFC in the previous step.</span></span> <span data-ttu-id="393f0-144">這個 RFC 會接受兩個整數值做為輸入參數。</span><span class="sxs-lookup"><span data-stu-id="393f0-144">This RFC takes two integer values as input parameters.</span></span>  
  
 <span data-ttu-id="393f0-145">請參閱[瀏覽、 搜尋和 get 中繼資料中 SAP RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)如需有關如何產生結構描述特定的 RFC 的指示。</span><span class="sxs-lookup"><span data-stu-id="393f0-145">See [Browse, search, and get Metadata for RFC Operations in SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md) for instructions on how to generate schema for a particular RFC.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="393f0-146">因為您正在產生輸入 RFC 呼叫的結構描述，請確定您選取**服務 （輸入作業）** 從**選取合約型別**下拉式清單中的[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="393f0-146">Because you are generating the schema for an inbound RFC call, make sure you select **Service (Inbound operation)** from the **Select contract type** drop-down list in the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="393f0-147">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="393f0-147">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="393f0-148">您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="393f0-148">The schema that you generated earlier describes the "types" required for the messages in the orchestration.</span></span> <span data-ttu-id="393f0-149">訊息通常是為其型別由對應的結構描述所定義的變數。</span><span class="sxs-lookup"><span data-stu-id="393f0-149">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="393f0-150">您必須連結產生的結構描述您在第一個步驟中的訊息從 BizTalk 專案的協調流程檢視。</span><span class="sxs-lookup"><span data-stu-id="393f0-150">You must link the schema you generated in the first step to the messages from the Orchestration view of the BizTalk project.</span></span>  
  
 <span data-ttu-id="393f0-151">本主題中，您必須建立兩個訊息，一個用於接收從 SAP 系統，並將回應傳送至 SAP 系統的其他訊息。</span><span class="sxs-lookup"><span data-stu-id="393f0-151">For this topic, you must create two messages—one to receive messages from the SAP system and the other to send a response to the SAP system.</span></span>  
  
 <span data-ttu-id="393f0-152">執行下列步驟來建立訊息，並將其連結至結構描述：</span><span class="sxs-lookup"><span data-stu-id="393f0-152">Perform the following steps to create messages and link them to the schema:</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="393f0-153">建立訊息，以及連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="393f0-153">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="393f0-154">將新的協調流程加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="393f0-154">Add a new orchestration to the BizTalk project.</span></span>  
  
2.  <span data-ttu-id="393f0-155">開啟協調流程檢視 BizTalk 專案中，如果未開啟。</span><span class="sxs-lookup"><span data-stu-id="393f0-155">Open the orchestration view the BizTalk project, if not already open.</span></span> <span data-ttu-id="393f0-156">按一下**檢視**，指向 **其他視窗**，然後按一下**協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="393f0-156">Click **View**, point to **Other Windows**, and click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="393f0-157">在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="393f0-157">In the **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="393f0-158">以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="393f0-158">Right-click the newly create message and select **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="393f0-159">在**屬性**窗格**Message_1**，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="393f0-159">In the **Properties** pane for **Message_1**, do the following.</span></span>  
  
    |<span data-ttu-id="393f0-160">使用</span><span class="sxs-lookup"><span data-stu-id="393f0-160">Use this</span></span>|<span data-ttu-id="393f0-161">動作</span><span class="sxs-lookup"><span data-stu-id="393f0-161">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="393f0-162">識別碼</span><span class="sxs-lookup"><span data-stu-id="393f0-162">Identifier</span></span>|<span data-ttu-id="393f0-163">型別**要求**。</span><span class="sxs-lookup"><span data-stu-id="393f0-163">Type **Request**.</span></span>|  
    |<span data-ttu-id="393f0-164">訊息類型</span><span class="sxs-lookup"><span data-stu-id="393f0-164">Message Type</span></span>|<span data-ttu-id="393f0-165">從下拉式清單中，展開 **結構描述**，然後選取*RFCServer.SAPBindingSchema.Z_RFC_ADD*，其中*RFCServer*是您的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="393f0-165">From the drop-down list, expand **Schemas**, and select *RFCServer.SAPBindingSchema.Z_RFC_ADD*, where *RFCServer* is the name of your BizTalk project.</span></span> <span data-ttu-id="393f0-166">*SAPBindingSchema*是結構描述產生的 RFC *Z_RFC_ADD*。</span><span class="sxs-lookup"><span data-stu-id="393f0-166">*SAPBindingSchema* is the schema generated for the RFC *Z_RFC_ADD*.</span></span>|  
  
6.  <span data-ttu-id="393f0-167">重複步驟 2 來建立新的訊息。</span><span class="sxs-lookup"><span data-stu-id="393f0-167">Repeat step 2 to create a new message.</span></span> <span data-ttu-id="393f0-168">在**屬性**窗格新訊息中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="393f0-168">In the **Properties** pane for the new message, do the following.</span></span>  
  
    |<span data-ttu-id="393f0-169">使用</span><span class="sxs-lookup"><span data-stu-id="393f0-169">Use this</span></span>|<span data-ttu-id="393f0-170">動作</span><span class="sxs-lookup"><span data-stu-id="393f0-170">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="393f0-171">識別碼</span><span class="sxs-lookup"><span data-stu-id="393f0-171">Identifier</span></span>|<span data-ttu-id="393f0-172">型別**回應**。</span><span class="sxs-lookup"><span data-stu-id="393f0-172">Type **Response**.</span></span>|  
    |<span data-ttu-id="393f0-173">訊息類型</span><span class="sxs-lookup"><span data-stu-id="393f0-173">Message Type</span></span>|<span data-ttu-id="393f0-174">從下拉式清單中，展開 **結構描述**，然後選取*RFCServer.SAPBindingSchema.Z_RFC_ADDResponse*。</span><span class="sxs-lookup"><span data-stu-id="393f0-174">From the drop-down list, expand **Schemas**, and select *RFCServer.SAPBindingSchema.Z_RFC_ADDResponse*.</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="393f0-175">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="393f0-175">Setting up the Orchestration</span></span>  
 <span data-ttu-id="393f0-176">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 SAP 系統接收 RFC 伺服器呼叫。</span><span class="sxs-lookup"><span data-stu-id="393f0-176">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for receiving RFC server calls from the SAP system.</span></span> <span data-ttu-id="393f0-177">例如，假設其中 RFC 用戶端將要求傳送至 SAP 系統加入兩個整數。</span><span class="sxs-lookup"><span data-stu-id="393f0-177">For this example, consider a scenario where an RFC client sends a request to the SAP system to add two integers.</span></span> <span data-ttu-id="393f0-178">SAP 系統收到要求，具有輸入參數，並將它傳遞至外部所裝載的 RFC 伺服器[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="393f0-178">The SAP system takes the request, with the input parameters, and passes it on to the external RFC server hosted by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="393f0-179">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]從 SAP 系統中，處理序要求以加入兩個整數，接收要求和產生回應。</span><span class="sxs-lookup"><span data-stu-id="393f0-179">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] receives the request from the SAP system, process the request to add two integers, and generates a response.</span></span> <span data-ttu-id="393f0-180">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會傳遞至 SAP 系統，接著會傳遞至 RFC 用戶端的回應。</span><span class="sxs-lookup"><span data-stu-id="393f0-180">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] passes the response to the SAP system, which in turn, is passed on to the RFC client.</span></span>  
  
 <span data-ttu-id="393f0-181">若要達到此協調流程的一部分，必須包含協調流程：</span><span class="sxs-lookup"><span data-stu-id="393f0-181">To achieve this as part of an orchestration, the orchestration must contain:</span></span>  
  
-   <span data-ttu-id="393f0-182">雙向接收埠以接收來自 SAP 系統的 RFC 伺服器要求並傳送回應。</span><span class="sxs-lookup"><span data-stu-id="393f0-182">A two-way receive port to receive the RFC server request from the SAP system and send the response.</span></span>  
  
-   <span data-ttu-id="393f0-183">傳送和接收圖形。</span><span class="sxs-lookup"><span data-stu-id="393f0-183">Send and Receive shapes.</span></span>  
  
-   <span data-ttu-id="393f0-184">建構訊息圖形，並在訊息指派圖形，來處理 RFC 伺服器要求來自 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="393f0-184">Construct Message shape, and within that a Message Assignment shape, to process the RFC server request coming from the SAP system.</span></span>  
  
 <span data-ttu-id="393f0-185">RFC 伺服器呼叫範例協調流程如下。</span><span class="sxs-lookup"><span data-stu-id="393f0-185">A sample orchestration for an RFC server call resembles the following.</span></span>  
  
 <span data-ttu-id="393f0-186">![進行 RFC 伺服器呼叫的協調流程](../../adapters-and-accelerators/adapter-sap/media/f5da2947-56d6-41f0-b411-c8e6eacf68cd.gif "f5da2947-56d6-41f0-b411-c8e6eacf68cd")</span><span class="sxs-lookup"><span data-stu-id="393f0-186">![Orchestration to make RFC server call](../../adapters-and-accelerators/adapter-sap/media/f5da2947-56d6-41f0-b411-c8e6eacf68cd.gif "f5da2947-56d6-41f0-b411-c8e6eacf68cd")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="393f0-187">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="393f0-187">Adding Message Shapes</span></span>  
 <span data-ttu-id="393f0-188">請確定您針對每個訊息圖形指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="393f0-188">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="393f0-189">所列的名稱*圖形*資料行名稱就是訊息圖形顯示在上述的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="393f0-189">The names listed in the *Shape* column are the names of the message shapes as displayed in the preceding orchestration.</span></span>  
  
|<span data-ttu-id="393f0-190">形狀圖</span><span class="sxs-lookup"><span data-stu-id="393f0-190">Shape</span></span>|<span data-ttu-id="393f0-191">圖形類型</span><span class="sxs-lookup"><span data-stu-id="393f0-191">Shape Type</span></span>|<span data-ttu-id="393f0-192">屬性</span><span class="sxs-lookup"><span data-stu-id="393f0-192">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="393f0-193">ListenToSAP</span><span class="sxs-lookup"><span data-stu-id="393f0-193">ListenToSAP</span></span>|<span data-ttu-id="393f0-194">Receive</span><span class="sxs-lookup"><span data-stu-id="393f0-194">Receive</span></span>|<span data-ttu-id="393f0-195">-設定**名稱**至*ListenToSAP*</span><span class="sxs-lookup"><span data-stu-id="393f0-195">-   Set **Name** to *ListenToSAP*</span></span><br /><span data-ttu-id="393f0-196">-設定**啟動**至 *，則為 True*</span><span class="sxs-lookup"><span data-stu-id="393f0-196">-   Set **Activate** to *True*</span></span>|  
|<span data-ttu-id="393f0-197">SendResponse</span><span class="sxs-lookup"><span data-stu-id="393f0-197">SendResponse</span></span>|<span data-ttu-id="393f0-198">Send</span><span class="sxs-lookup"><span data-stu-id="393f0-198">Send</span></span>|<span data-ttu-id="393f0-199">-設定**名稱**至*SendResponse*</span><span class="sxs-lookup"><span data-stu-id="393f0-199">-   Set **Name** to *SendResponse*</span></span>|  
  
### <a name="adding-construct-message-shape"></a><span data-ttu-id="393f0-200">新增 建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="393f0-200">Adding Construct Message Shape</span></span>  
 <span data-ttu-id="393f0-201">為了處理內送的 RFC 呼叫加入兩個整數值，您必須新增建構訊息 」 圖形，並在訊息指派 」 圖形至協調流程中，兩者之間傳送圖形。</span><span class="sxs-lookup"><span data-stu-id="393f0-201">To process the incoming RFC call to add two integer values, you must add a Construct Message shape and within that a Message Assignment shape to your orchestration, between the two send shapes.</span></span> <span data-ttu-id="393f0-202">針對此範例中，「 訊息指派 」 圖形會叫用加入兩個整數。</span><span class="sxs-lookup"><span data-stu-id="393f0-202">For this example, the Message Assignment shape invokes to add two integers.</span></span> <span data-ttu-id="393f0-203">「 訊息指派 」 圖形也會設定為傳送到 SAP 系統的回應動作。</span><span class="sxs-lookup"><span data-stu-id="393f0-203">The Message Assignment shape also sets the action for the response to be sent to the SAP system.</span></span>  
  
 <span data-ttu-id="393f0-204">「 建構訊息 」 圖形，設定**建構訊息**屬性**回應**。</span><span class="sxs-lookup"><span data-stu-id="393f0-204">For the Construct Message shape, set the **Message Constructed** property to **Response**.</span></span>  
  
 <span data-ttu-id="393f0-205">處理 RFC 要求程式碼可能是您的 BizTalk 專案相同的 Visual Studio 方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="393f0-205">The code to process the RFC request could be part of the same Visual Studio solution as your BizTalk project.</span></span> <span data-ttu-id="393f0-206">將兩個整數的範例程式碼看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="393f0-206">A sample code for adding two integers looks like this.</span></span>  
  
```  
namespace RFCServerResponseCreator  
{  
    public class RFCServerResponseCreator  
    {  
        private static XmlDocument messageIn;  
        private static XmlDocument messageOut;  
        public static XmlDocument CreateRequest(int a, int b, string destination)  
        {  
            messageIn = new XmlDocument();  
            messageIn.LoadXml(  "<Z_RFC_ADD xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\">" +  
                                "<DEST>" + destination + "</DEST>" +  
                                "<X>" + a + "</X>" +  
                                "<Y>" + b + "</Y>" +   
                                "</Z_RFC_ADD>"  
                             );  
            return messageIn;  
        }  
        public static XmlDocument CreateResponse(int a, int b)  
        {  
            int c = a + b;  
            messageOut = new XmlDocument();  
            messageOut.LoadXml( "<Z_RFC_ADDResponse xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\">" +  
                                "<RESULT>" + c + "</RESULT>" +   
                                "</Z_RFC_ADDResponse>"  
                              );  
            return messageOut;  
        }  
    }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="393f0-207">建置專案之後，會建立 RFCServerResponseCreator.dll 專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="393f0-207">After you build the project, RFCServerResponseCreator.dll will be created in the project directory.</span></span> <span data-ttu-id="393f0-208">您必須將此 DLL 加入全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="393f0-208">You must add this DLL to the global assembly cache (GAC).</span></span>  
  
 <span data-ttu-id="393f0-209">加入下列運算式叫用此程式碼從 「 訊息指派 」 圖形，並設定傳送到 SAP 系統的回應動作。</span><span class="sxs-lookup"><span data-stu-id="393f0-209">Add the following expression to invoke this code from the Message Assignment shape and to set the action for the response sent to the SAP system.</span></span> <span data-ttu-id="393f0-210">若要新增運算式，請按兩下訊息指派 」 圖形以開啟運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="393f0-210">To add an expression, double-click the Message Assignment shape to open the Expression Editor.</span></span>  
  
```  
Response = RFCServerResponseCreator.RFCServerResponseCreator.CreateResponse(Request.X, Request.Y);  
Response(WCF.Action) = "http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADD/response";  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="393f0-211">您必須明確設定回應訊息上的動作。</span><span class="sxs-lookup"><span data-stu-id="393f0-211">You must explicitly set the action on the response message.</span></span> <span data-ttu-id="393f0-212">如果您未設定此動作，Wcf-custom 配接器到達動作訊息藉由附加 「 回應 」 要求的動作。</span><span class="sxs-lookup"><span data-stu-id="393f0-212">If you do not set the action, WCF-Custom adapter arrives at the action message by appending “Response” to the request action.</span></span> <span data-ttu-id="393f0-213">因此，回應訊息的動作會變成`http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADDResponse`。</span><span class="sxs-lookup"><span data-stu-id="393f0-213">So, the action for the response message becomes `http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADDResponse`.</span></span> <span data-ttu-id="393f0-214">不過，sapBinding 預期的回應動作藉由附加"/ 回應 」 至要求的動作，例如`http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADD/response`。</span><span class="sxs-lookup"><span data-stu-id="393f0-214">However, the sapBinding expects the response action by appending “/response” to the request action, for example `http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADD/response`.</span></span>  
  
### <a name="adding-ports"></a><span data-ttu-id="393f0-215">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="393f0-215">Adding Ports</span></span>  
 <span data-ttu-id="393f0-216">請確定您指定的邏輯連接埠的下列屬性。</span><span class="sxs-lookup"><span data-stu-id="393f0-216">Make sure you specify the following properties for the logical port.</span></span> <span data-ttu-id="393f0-217">中所列的名稱*連接埠*資料行是顯示在協調流程中的連接埠名稱。</span><span class="sxs-lookup"><span data-stu-id="393f0-217">The name listed in the *Port* column is the name of the port as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="393f0-218">通訊埠</span><span class="sxs-lookup"><span data-stu-id="393f0-218">Port</span></span>|<span data-ttu-id="393f0-219">屬性</span><span class="sxs-lookup"><span data-stu-id="393f0-219">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="393f0-220">RFCServerPort</span><span class="sxs-lookup"><span data-stu-id="393f0-220">RFCServerPort</span></span>|<span data-ttu-id="393f0-221">-設定**識別碼**至*RFCServerPort*</span><span class="sxs-lookup"><span data-stu-id="393f0-221">-   Set **Identifier** to *RFCServerPort*</span></span><br /><span data-ttu-id="393f0-222">-設定**類型**至*RFCServerPortType*</span><span class="sxs-lookup"><span data-stu-id="393f0-222">-   Set **Type** to *RFCServerPortType*</span></span><br /><span data-ttu-id="393f0-223">-設定**通訊模式**至*要求-回應*</span><span class="sxs-lookup"><span data-stu-id="393f0-223">-   Set **Communication Pattern** to *Request-Response*</span></span><br /><span data-ttu-id="393f0-224">-設定**通訊方向**至*接收傳送*</span><span class="sxs-lookup"><span data-stu-id="393f0-224">-   Set **Communication Direction** to *Receive-Send*</span></span>|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a><span data-ttu-id="393f0-225">指定動作圖形訊息並連接至連接埠</span><span class="sxs-lookup"><span data-stu-id="393f0-225">Specify Messages for Action Shapes and Connect to Ports</span></span>  
 <span data-ttu-id="393f0-226">下表指定屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="393f0-226">The following table specifies the properties and their values to be set to specify messages for action shapes and linking them to the ports.</span></span> <span data-ttu-id="393f0-227">所列的名稱*圖形*資料行名稱就是訊息圖形顯示在上述的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="393f0-227">The names listed in the *Shape* column are the names of the message shapes as displayed in the preceding orchestration.</span></span>  
  
|<span data-ttu-id="393f0-228">形狀圖</span><span class="sxs-lookup"><span data-stu-id="393f0-228">Shape</span></span>|<span data-ttu-id="393f0-229">屬性</span><span class="sxs-lookup"><span data-stu-id="393f0-229">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="393f0-230">ListenToSAP</span><span class="sxs-lookup"><span data-stu-id="393f0-230">ListenToSAP</span></span>|<span data-ttu-id="393f0-231">-設定**訊息**至*要求*</span><span class="sxs-lookup"><span data-stu-id="393f0-231">-   Set **Message** to *Request*</span></span><br /><span data-ttu-id="393f0-232">-設定**作業**至*RFCServerPort.Add.Request*</span><span class="sxs-lookup"><span data-stu-id="393f0-232">-   Set **Operation** to *RFCServerPort.Add.Request*</span></span>|  
|<span data-ttu-id="393f0-233">SendResponse</span><span class="sxs-lookup"><span data-stu-id="393f0-233">SendResponse</span></span>|<span data-ttu-id="393f0-234">-設定**訊息**至*FuncResponse*</span><span class="sxs-lookup"><span data-stu-id="393f0-234">-   Set **Message** to *FuncResponse*</span></span><br /><span data-ttu-id="393f0-235">-設定**作業**至*RFCServerPort.Add.Response*</span><span class="sxs-lookup"><span data-stu-id="393f0-235">-   Set **Operation** to *RFCServerPort.Add.Response*</span></span>|  
  
 <span data-ttu-id="393f0-236">您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="393f0-236">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="393f0-237">您必須現在可以建置 BizTalk 方案，然後再將它部署至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="393f0-237">You must now build the BizTalk solution and then deploy it to a BizTalk Server.</span></span> <span data-ttu-id="393f0-238">如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-238">For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).</span></span>
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="393f0-239">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="393f0-239">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="393f0-240">部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。</span><span class="sxs-lookup"><span data-stu-id="393f0-240">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the **Orchestrations** pane in the BizTalk Server Administration console.</span></span> <span data-ttu-id="393f0-241">您必須使用 BizTalk Server 管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="393f0-241">You must use the BizTalk Server Administration console to configure the application.</span></span> <span data-ttu-id="393f0-242">如需有關如何設定應用程式的詳細資訊，請參閱[如何設定應用程式](../../core/how-to-configure-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-242">For more information about configuring an application, see [How to Configure an Application](../../core/how-to-configure-an-application.md).</span></span>
  
 <span data-ttu-id="393f0-243">設定應用程式包括：</span><span class="sxs-lookup"><span data-stu-id="393f0-243">Configuring an application involves:</span></span>  
  
-   <span data-ttu-id="393f0-244">選取應用程式的主機。</span><span class="sxs-lookup"><span data-stu-id="393f0-244">Selecting a host for the application.</span></span>  
  
-   <span data-ttu-id="393f0-245">對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="393f0-245">Mapping the ports that you created in your orchestration to physical ports in the BizTalk Server Administration console.</span></span> <span data-ttu-id="393f0-246">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="393f0-246">For this orchestration you must:</span></span>  
  
    -   <span data-ttu-id="393f0-247">定義 WCF 自訂或 WCF SAP 接收埠。</span><span class="sxs-lookup"><span data-stu-id="393f0-247">Define a WCF-Custom or WCF-SAP receive port.</span></span> <span data-ttu-id="393f0-248">此連接埠會從 SAP 系統接收傳入的 RFC 呼叫時，會傳送回應給 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="393f0-248">This port will receive inbound RFC calls from the SAP system and will send the response back to the SAP system.</span></span> <span data-ttu-id="393f0-249">如需如何建立連接埠相關資訊，請參閱[以手動方式設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-249">For information about how to create ports, see [Manually configure a physical port binding to the SAP adapter](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="393f0-250">產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="393f0-250">Generating the schema using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] also creates a binding file containing information about the ports and the actions to be set for those ports.</span></span> <span data-ttu-id="393f0-251">您可以從 BizTalk 管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （適用於進行傳入呼叫時），以匯入此繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="393f0-251">You can import this binding file from the BizTalk Administration Console to create send ports (for outbound calls) or receive ports (for inbound calls).</span></span> <span data-ttu-id="393f0-252">如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-252">For more information, see [Configure a physical port binding using a port binding file to SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).</span></span>
  
 <span data-ttu-id="393f0-253">您也必須將 RFCServerResponseCreator 專案的組件加入您的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="393f0-253">You must also add the assembly for the RFCServerResponseCreator project to your BizTalk application.</span></span> <span data-ttu-id="393f0-254">您建立此專案來處理從 SAP 系統接收到 RFC 呼叫。</span><span class="sxs-lookup"><span data-stu-id="393f0-254">You created this project to process the RFC call received from the SAP system.</span></span> <span data-ttu-id="393f0-255">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="393f0-255">To do so:</span></span>  
  
1.  <span data-ttu-id="393f0-256">在 BizTalk Server 管理主控台的 匯入繫結的 BizTalk 應用程式的左半部的主控台樹狀目錄中以滑鼠右鍵按一下**資源**，指向 **新增**，然後按一下**BizTalk 組件**。</span><span class="sxs-lookup"><span data-stu-id="393f0-256">In the console tree on the left side of the BizTalk Server Administration console, under the BizTalk application where you imported the bindings, right-click **Resources**, point to **Add**, and then click **BizTalk Assemblies**.</span></span>  
  
2.  <span data-ttu-id="393f0-257">在**新增資源**對話方塊中，按一下**新增**，然後瀏覽至包含 RFCServerResponseCreator.dll 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="393f0-257">In the **Add Resources** dialog box, Click **Add**, and then navigate to the folder containing RFCServerResponseCreator.dll.</span></span> <span data-ttu-id="393f0-258">選取檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="393f0-258">Select the file and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="393f0-259">在**新增資源**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="393f0-259">In the **Add Resources** dialog box, click **OK**.</span></span>  
  
## <a name="starting-the-application"></a><span data-ttu-id="393f0-260">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="393f0-260">Starting the Application</span></span>  
 <span data-ttu-id="393f0-261">您必須啟動從 SAP 系統接收輸入的 RFC 呼叫的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="393f0-261">You must start the BizTalk application for receiving inbound RFC calls from an SAP system.</span></span> <span data-ttu-id="393f0-262">如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)，和[如何啟動應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-262">For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md), and [How to start an application](../../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>
  
 <span data-ttu-id="393f0-263">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="393f0-263">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="393f0-264">Wcf-custom 或 WCF SAP 接收埠以接收 RFC 呼叫從 SAP 系統正在執行。</span><span class="sxs-lookup"><span data-stu-id="393f0-264">The WCF-Custom or WCF-SAP receive port to receive RFC calls from the SAP system is running.</span></span>  
  
-   <span data-ttu-id="393f0-265">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="393f0-265">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="393f0-266">執行作業</span><span class="sxs-lookup"><span data-stu-id="393f0-266">Executing the Operation</span></span>  
 <span data-ttu-id="393f0-267">執行應用程式之後，您必須傳送至 RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="393f0-267">After you run the application, you must send an RFC to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="393f0-268">您可以藉由執行 SAP 系統上的交易 SE37 來這麼做。</span><span class="sxs-lookup"><span data-stu-id="393f0-268">You can do so by executing the transaction SE37 on the SAP system.</span></span> <span data-ttu-id="393f0-269">您也必須指定於 RFC 呼叫的輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="393f0-269">You must also specify the input parameters for the RFC call.</span></span> <span data-ttu-id="393f0-270">配接器接收的呼叫和參數、 加以處理，並傳送回應給 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="393f0-270">The adapter receives the call along with the parameters, processes it, and sends the response back to the SAP system.</span></span> <span data-ttu-id="393f0-271">您可以針對相同的交易從 RFC 的傳送位置查看回應。</span><span class="sxs-lookup"><span data-stu-id="393f0-271">You will be able to see the response on the same transaction from where you sent the RFC.</span></span>  
  
## <a name="possible-exceptions"></a><span data-ttu-id="393f0-272">可能的例外狀況</span><span class="sxs-lookup"><span data-stu-id="393f0-272">Possible Exceptions</span></span>  
 <span data-ttu-id="393f0-273">如需例外狀況的資訊可能會遇到的 SAP 系統，使用 BizTalk Server 從接收的 RFC 伺服器呼叫時，請參閱[例外狀況和錯誤處理與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-273">For information about the exceptions you might encounter while receiving an RFC server call from an SAP system using BizTalk Server, see [Exceptions and Error Handling with the SAP adapter](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="393f0-274">最佳作法</span><span class="sxs-lookup"><span data-stu-id="393f0-274">Best Practices</span></span>  
 <span data-ttu-id="393f0-275">您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。</span><span class="sxs-lookup"><span data-stu-id="393f0-275">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the bindings file.</span></span> <span data-ttu-id="393f0-276">一旦產生繫結檔案時，您可以匯入組態設定從檔案，因此您不需要建立傳送埠、 接收埠，等。 針對相同的協調流程。</span><span class="sxs-lookup"><span data-stu-id="393f0-276">Once you generate a bindings file, you can import the configuration settings from the file so that you do not need to create the send ports, receive ports, etc. for the same orchestration.</span></span> <span data-ttu-id="393f0-277">如需繫結檔案的詳細資訊，請參閱[重複使用的 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="393f0-277">For more information about binding files, see [Reuse SAP adapter bindings](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="393f0-278">請參閱</span><span class="sxs-lookup"><span data-stu-id="393f0-278">See Also</span></span>  
[<span data-ttu-id="393f0-279">開發 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="393f0-279">Develop BizTalk applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)