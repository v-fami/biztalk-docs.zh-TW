---
title: 協調流程如何處理具型別的的錯誤合約 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- typed fault contracts [orchestrations]
- WCF services, orchestrations
- orchestrations, typed fault contracts
- orchestrations, WCF services
ms.assetid: 5a1a7d22-b0ff-4d09-bebf-4995229784b0
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a7643c4a39785018368572d721eed3ef6545c6b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "25970764"
---
# <a name="how-to-handle-typed-fault-contracts-in-orchestrations"></a><span data-ttu-id="fc81b-102">如何在協調流程中處理類型錯誤的合約</span><span class="sxs-lookup"><span data-stu-id="fc81b-102">How to Handle Typed Fault Contracts in Orchestrations</span></span>
<span data-ttu-id="fc81b-103">本主題描述如何在使用 WCF 服務時，從協調流程內處理類型錯誤的合約。</span><span class="sxs-lookup"><span data-stu-id="fc81b-103">This topic describes how to handle typed fault contracts when consuming WCF services from within orchestrations.</span></span> <span data-ttu-id="fc81b-104">若要處理協調流程中的具類型的錯誤例外狀況，您使用的 WCF 服務必須具有**FaultContractAttribute**套用至服務作業; 因此，則會發生錯誤，可能會擲回使用**FaultException**\<T\>其中 T 可以是任何有效的資料合約或可序列化的型別從 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="fc81b-104">To handle typed fault exceptions in orchestrations, the WCF services that you are consuming must have the **FaultContractAttribute** applied to the service operations; therefore, the faults can be thrown by using **FaultException**\<T\> where T can be any valid data contract or serializable type from the WCF services.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="fc81b-105">程序</span><span class="sxs-lookup"><span data-stu-id="fc81b-105">Procedures</span></span>  
  
#### <a name="to-handle-typed-fault-contracts-in-orchestrations"></a><span data-ttu-id="fc81b-106">若要在協調流程中處理類型錯誤的合約</span><span class="sxs-lookup"><span data-stu-id="fc81b-106">To handle typed fault contracts in orchestrations</span></span>  
  
1.  <span data-ttu-id="fc81b-107">在您的 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk 專案，在 [方案總管] 中，以滑鼠右鍵按一下您的專案中，按一下**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="fc81b-107">In your Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, in Solution Explorer, right-click your project, click **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="fc81b-108">在**新增產生的項目- \<***專案名稱***\>** 對話方塊中，於**範本**區段中，選取**取用 WCF服務**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="fc81b-108">In the **Add Generated Items - \<***Project name***\>** dialog box, in the **Templates** section, select **Consume WCF Service**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="fc81b-109">在 **歡迎使用 BizTalk WCF 服務使用精靈** 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="fc81b-109">On the **Welcome to the BizTalk WCF Service Consuming Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="fc81b-110">在 **中繼資料來源** 頁面上，選取 **中繼資料交換 (MEX) 端點**, ，然後按一下  **下一步**。</span><span class="sxs-lookup"><span data-stu-id="fc81b-110">On the **Metadata source** page, select **Metadata Exchange (MEX) endpoint**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="fc81b-111">在 **中繼資料端點** 頁面上，指定執行中的服務提供透過 Ws-metadata Exchange 或 Http-get 下載的中繼資料的 URL，例如 http://localhost:8005。</span><span class="sxs-lookup"><span data-stu-id="fc81b-111">On the **Metadata Endpoint** page, specify the URL for the running service that provides metadata for download through WS-Metadata Exchange or Http-Get—for example, http://localhost:8005.</span></span> <span data-ttu-id="fc81b-112">若要從 URL 取得中繼資料文件，請按一下  **取得**。</span><span class="sxs-lookup"><span data-stu-id="fc81b-112">To get the metadata document from the URL, click **Get**.</span></span> <span data-ttu-id="fc81b-113">如果執行中的服務需要基本驗證配置的使用者認證，請按一下  **編輯** 開啟 **BizTalk WCF 服務使用精靈** 可以提供使用者名稱和密碼來存取執行中的服務時使用的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fc81b-113">If the running service requires a user credential with the basic authentication scheme, click **Edit** to open the **BizTalk WCF Service Consuming Wizard** dialog box in which you can supply the user name and password to use when accessing the running service.</span></span> <span data-ttu-id="fc81b-114">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="fc81b-114">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="fc81b-115">在 **匯入 WCF 服務中繼資料摘要** 頁面上，檢閱您的設定。</span><span class="sxs-lookup"><span data-stu-id="fc81b-115">On the **Import WCF Service Metadata Summary** page, review your settings.</span></span> <span data-ttu-id="fc81b-116">您可以按一下 **回** 進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="fc81b-116">You can click **Back** to make any changes.</span></span> <span data-ttu-id="fc81b-117">然後按一下  **匯入** 建立 BizTalk 成品和使用 WCF 服務使用的型別。</span><span class="sxs-lookup"><span data-stu-id="fc81b-117">Then click **Import** to create the BizTalk artifacts and types to be used for consuming the WCF service.</span></span>  
  
7.  <span data-ttu-id="fc81b-118">在 **完成 BizTalk WCF 服務使用精靈** 頁面上，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="fc81b-118">On the **Completing the BizTalk WCF Service Consuming Wizard** page, click **Finish**.</span></span>  
  
8.  <span data-ttu-id="fc81b-119">假設您使用的 WCF 服務擲回下列錯誤例外狀況：</span><span class="sxs-lookup"><span data-stu-id="fc81b-119">Suppose that the WCF service that you are consuming throws the following fault exception:</span></span>  
  
    ```  
    throw new FaultException<MyOperationException>(divideException);  
    ```  
  
     <span data-ttu-id="fc81b-120">傳送埠上的錯誤作業預期類型的訊息 **MyOperationException**, ，但 WCF 回應訊息包含完整錯誤內文。</span><span class="sxs-lookup"><span data-stu-id="fc81b-120">The fault operation on the send port expects a message of type **MyOperationException**, but the WCF response message contains the whole fault body.</span></span> <span data-ttu-id="fc81b-121">因此，您需要擷取 **MyOperationException** 從藉由設定訊息部分 **輸入 BizTalk 訊息內文** 傳輸屬性 對話方塊中的選項。</span><span class="sxs-lookup"><span data-stu-id="fc81b-121">Therefore, you need to extract the **MyOperationException** part from the message by configuring the **Inbound BizTalk message body** option in the transport properties dialog box.</span></span> <span data-ttu-id="fc81b-122">例如，</span><span class="sxs-lookup"><span data-stu-id="fc81b-122">For example,</span></span>  
  
    -   <span data-ttu-id="fc81b-123">選取 **路徑--內容由內文路徑定位**。</span><span class="sxs-lookup"><span data-stu-id="fc81b-123">Select **Path -- content located by body path**.</span></span>  
  
    -   <span data-ttu-id="fc81b-124">將內文路徑運算式設定如下：</span><span class="sxs-lookup"><span data-stu-id="fc81b-124">Set the Body path expression to the following:</span></span>  
  
        ```  
        /*[local-name()='Fault']/*[local-name()='Detail']/* | /*[local-name()='DivideResponse']  
        ```  
  
    -   <span data-ttu-id="fc81b-125">選取 **Xml** 從 **節點編碼** 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="fc81b-125">Select **Xml** from the **Node encoding** drop-down list.</span></span>  
  
9. <span data-ttu-id="fc81b-126">在協調流程中，您必須新增範圍和兩個例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="fc81b-126">In the orchestration, you will need to add a scope and two exception handlers.</span></span> <span data-ttu-id="fc81b-127">例外狀況處理常式是錯誤作業類似於 **MyOperationException** 在上述範例中，顯示其他例外狀況處理常式會攔截泛型 **SOAPExceptions**。</span><span class="sxs-lookup"><span data-stu-id="fc81b-127">One exception handler is for the Fault operation, similar to **MyOperationException** shown in the preceding example; the other exception handler is for catching generic **SOAPExceptions**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc81b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc81b-128">See Also</span></span>  
 <span data-ttu-id="fc81b-129">[如何從協調流程發佈為 WCF 服務擲回錯誤例外狀況](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="fc81b-129">[How to Throw Fault Exceptions from Orchestrations Published as WCF Services](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md) </span></span>  
 [<span data-ttu-id="fc81b-130">如何使用 BizTalk WCF 服務使用精靈來取用 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="fc81b-130">How to Use the BizTalk WCF Service Consuming Wizard to Consume a WCF Service</span></span>](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)