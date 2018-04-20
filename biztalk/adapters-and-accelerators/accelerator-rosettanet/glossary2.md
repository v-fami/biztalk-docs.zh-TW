---
title: RosettaNet 加速器，BizTalk Server 中的詞彙 |Microsoft 文件
description: 一般詞彙和定義必須知道並了解如何使用 BizTalk Accelerator for RosettaNet
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d98a5ed4-adc5-4ca9-b9d9-38ab02a0bda6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd89d75b0d36359fcf59f7edae0bb950a7196ca7
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="glossary"></a><span data-ttu-id="e92e9-103">詞彙</span><span class="sxs-lookup"><span data-stu-id="e92e9-103">Glossary</span></span>
[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]<span data-ttu-id="e92e9-104"> 使用下列字彙術語和定義。</span><span class="sxs-lookup"><span data-stu-id="e92e9-104"> uses the following glossary terms and definitions.</span></span>  

  
## <a name="a"></a><span data-ttu-id="e92e9-105">只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，</span><span class="sxs-lookup"><span data-stu-id="e92e9-105">A</span></span>  
 <span data-ttu-id="e92e9-106">**應用程式配接器**</span><span class="sxs-lookup"><span data-stu-id="e92e9-106">**application adapter**</span></span>  
 <span data-ttu-id="e92e9-107">實作應用程式配接器介面的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-107">An application that implements the application adapter interface.</span></span> <span data-ttu-id="e92e9-108">對於內送動作訊息 (要求或回應) 之認可的通知機制，會叫用應用程式配接器。</span><span class="sxs-lookup"><span data-stu-id="e92e9-108">The notification mechanism on the acceptance of an incoming action message (request or response) invokes the application adapter.</span></span> <span data-ttu-id="e92e9-109">它會實作兩種方法：`BeginNotify`和`EndNotify`。</span><span class="sxs-lookup"><span data-stu-id="e92e9-109">It implements two methods: `BeginNotify` and `EndNotify`.</span></span> <span data-ttu-id="e92e9-110">公用回應者會叫用 `BeginNotify` 方法，而現成的私用回應者則會叫用 `EndNotify` 方法。</span><span class="sxs-lookup"><span data-stu-id="e92e9-110">The public responder invokes the `BeginNotify` method, whereas the out-of-the-box private responder invokes the `EndNotify` method.</span></span> <span data-ttu-id="e92e9-111">只要呼叫 `Notify` 方法，就表示訊息已經成功儲存到 MessagesToLOB 資料表中。</span><span class="sxs-lookup"><span data-stu-id="e92e9-111">The call to the `Notify` method means that the message was successfully saved into the MessagesToLOB table.</span></span>  
  
 <span data-ttu-id="e92e9-112">**動作 URL**</span><span class="sxs-lookup"><span data-stu-id="e92e9-112">**action URL**</span></span>  
 <span data-ttu-id="e92e9-113">要為主要組織傳輸動作訊息在非同步的過程中，例如，交易夥伴 URL http://FabrikamServer/BTARNApp/RNIFReceive.aspx。</span><span class="sxs-lookup"><span data-stu-id="e92e9-113">The partner URL to which the home organization transmits an action message during an asynchronous process, for example, http://FabrikamServer/BTARNApp/RNIFReceive.aspx.</span></span>  
  
## <a name="b"></a><span data-ttu-id="e92e9-114">B</span><span class="sxs-lookup"><span data-stu-id="e92e9-114">B</span></span>  
 <span data-ttu-id="e92e9-115">**BizTalk Accelerator for RosettaNet**</span><span class="sxs-lookup"><span data-stu-id="e92e9-115">**BizTalk Accelerator for RosettaNet**</span></span>  
 <span data-ttu-id="e92e9-116">BizTalk Server，可協助組織建立與 RosettaNet 實作架構 (RNIF) 的附加產品-相容解決方案。</span><span class="sxs-lookup"><span data-stu-id="e92e9-116">An add-on product to BizTalk Server that helps organizations to build RosettaNet Implementation Framework (RNIF)-compliant solutions.</span></span>  
  
 <span data-ttu-id="e92e9-117">**[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 系統管理**</span><span class="sxs-lookup"><span data-stu-id="e92e9-117">**[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Administration**</span></span>  
 <span data-ttu-id="e92e9-118">可讓您描述程序範本及管理交易夥伴協議的 Microsoft [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-118">A Microsoft [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] application that lets you describe process templates and manage partner agreements.</span></span>  
  
 <span data-ttu-id="e92e9-119">**BizTalk 編輯器**</span><span class="sxs-lookup"><span data-stu-id="e92e9-119">**BizTalk Editor**</span></span>  
 <span data-ttu-id="e92e9-120">可以用來建立、編輯和管理規格的工具。</span><span class="sxs-lookup"><span data-stu-id="e92e9-120">A tool with which you can create, edit, and manage specifications.</span></span> <span data-ttu-id="e92e9-121">您可以使用 BizTalk 編輯器，根據規格範本、現有的結構描述、特定類型的文件執行個體，或是空白規格來建立規格。</span><span class="sxs-lookup"><span data-stu-id="e92e9-121">With BizTalk Editor you can create a specification based on a specification template, an existing schema, certain types of document instances, or a blank specification.</span></span>  
  
 <span data-ttu-id="e92e9-122">**BizTalk 協調流程設計師**</span><span class="sxs-lookup"><span data-stu-id="e92e9-122">**BizTalk Orchestration Designer**</span></span>  
 <span data-ttu-id="e92e9-123">設計工具，可以用來建立描寫長時間執行、偶合鬆散以及可執行之商務程序的繪圖。</span><span class="sxs-lookup"><span data-stu-id="e92e9-123">A design tool you can use to create drawings that describe long running, loosely coupled, executable business processes.</span></span> <span data-ttu-id="e92e9-124">XLANG 排程繪圖是在您用來執行自動化的商務程序的 XLANG 排程中編譯。</span><span class="sxs-lookup"><span data-stu-id="e92e9-124">The XLANG schedule drawing is compiled in an XLANG schedule that you use to run the automated business process.</span></span>  
  
 <span data-ttu-id="e92e9-125">**BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="e92e9-125">**BizTalk Server**</span></span>  
 <span data-ttu-id="e92e9-126">商務程序自動化和應用程式整合中及企業間之 Microsoft 產品。</span><span class="sxs-lookup"><span data-stu-id="e92e9-126">A Microsoft product for business-process automation and application integration both in and between businesses.</span></span> <span data-ttu-id="e92e9-127">BizTalk Server 提供功能強大的 Web 架構開發和執行環境，可整合鬆散偶合、 長時間執行商務程序，和企業之間。</span><span class="sxs-lookup"><span data-stu-id="e92e9-127">BizTalk Server provides a powerful Web-based development and execution environment that integrates loosely coupled, long-running business processes, both in and between businesses.</span></span>  
  
 <span data-ttu-id="e92e9-128">BizTalk Server 功能包括新的和現有的 XLANG 排程; 組合在現有的應用程式; 之間的整合文件規格和規格轉換，定義監視和執行階段活動的記錄。</span><span class="sxs-lookup"><span data-stu-id="e92e9-128">BizTalk Server features include the composition of new and existing XLANG schedules; integration among existing applications; the definition of document specifications and specification transformations; and the monitoring and logging of run-time activity.</span></span>  
  
 <span data-ttu-id="e92e9-129">這個伺服器會提供標準的閘道，經由網際網路傳送和接收文件，並提供許多服務，幫助確認資料的完整性、傳遞性、安全性以及對 BizTalk Framework 和其他重要文件格式的支援。</span><span class="sxs-lookup"><span data-stu-id="e92e9-129">The server provides a standard gateway for sending and receiving documents across the Internet, and provides a range of services that help to ensure data integrity, delivery, security, and support for the BizTalk Framework and other key document formats.</span></span>  
  
 <span data-ttu-id="e92e9-130">**BtarnClean**</span><span class="sxs-lookup"><span data-stu-id="e92e9-130">**BtarnClean**</span></span>  
 <span data-ttu-id="e92e9-131">清除電腦中 BTARN 成品的公用程式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-131">A utility to clean BTARN artifacts off a computer.</span></span>  
  
 <span data-ttu-id="e92e9-132">**商務動作**</span><span class="sxs-lookup"><span data-stu-id="e92e9-132">**business action**</span></span>  
 <span data-ttu-id="e92e9-133">含有商務內容的 RosettaNet 訊息，例如訂單要求或報價要求。</span><span class="sxs-lookup"><span data-stu-id="e92e9-133">A RosettaNet message that contains business content such as a purchase order request or a request for a quote.</span></span> <span data-ttu-id="e92e9-134">配合商務信號，這些動作便會產生所需的項目，以便完成特定「交易夥伴介面程序 (PIP)」所指定的商務活動。</span><span class="sxs-lookup"><span data-stu-id="e92e9-134">Together with business signals, these actions make up the necessary elements to complete the business activity specified by a particular Partner Interface Process (PIP).</span></span>  
  
 <span data-ttu-id="e92e9-135">**商務活動監控 (BAM)**</span><span class="sxs-lookup"><span data-stu-id="e92e9-135">**Business Activity Monitoring (BAM)**</span></span>  
 <span data-ttu-id="e92e9-136">[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 的功能，用來提供商務使用者對於異質商務程序的即時檢視，</span><span class="sxs-lookup"><span data-stu-id="e92e9-136">A [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] feature that gives business users a real-time view of their heterogeneous business processes.</span></span> <span data-ttu-id="e92e9-137">以便進行重要的商務決策。</span><span class="sxs-lookup"><span data-stu-id="e92e9-137">This enables them to make important business decisions.</span></span>  
  
 <span data-ttu-id="e92e9-138">**商務信號**</span><span class="sxs-lookup"><span data-stu-id="e92e9-138">**business signal**</span></span>  
 <span data-ttu-id="e92e9-139">在兩個 RosettaNet 網路應用程式之間進行交換的 RosettaNet 訊息 (像是 ReceiptAcknowledgement 或例外狀況)，用來在執行 PIP 執行個體時，溝通特定的事件。</span><span class="sxs-lookup"><span data-stu-id="e92e9-139">A RosettaNet message, such as a ReceiptAcknowledgement or Exception, exchanged between two RosettaNet network applications to communicate certain events in the execution of a PIP instance.</span></span> <span data-ttu-id="e92e9-140">配合商務動作，這些信號便會產生所需的項目，以便完成特定 PIP 所指定的商務活動。</span><span class="sxs-lookup"><span data-stu-id="e92e9-140">Together with business actions, these signals make up the necessary elements to complete the business activity specified by a particular PIP.</span></span>  
 
  
## <a name="c"></a><span data-ttu-id="e92e9-141">C</span><span class="sxs-lookup"><span data-stu-id="e92e9-141">C</span></span>  
 <span data-ttu-id="e92e9-142">**CertWizard**</span><span class="sxs-lookup"><span data-stu-id="e92e9-142">**CertWizard**</span></span>  
 <span data-ttu-id="e92e9-143">用來從 .pfx (.p12) 或 .cer (.der) 檔案，將簽章或加密憑證匯入私用或公用儲存區，以便與 BTARN 搭配使用的公用程式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-143">A utility to import a signing or encryption certificate from a .pfx (.p12) or .cer (.der) file into a private or public store for use with BTARN.</span></span> <span data-ttu-id="e92e9-144">由於具有用於解密或簽章的私密金鑰，.pfx 檔 (也就是個人資訊交換 – PKCS #12) 通常都會由密碼加以保護。</span><span class="sxs-lookup"><span data-stu-id="e92e9-144">A .pfx file, also known as Personal Information Exchange–PKCS #12, is typically protected by a password as it holds a private key that is used for decryption or signing.</span></span> <span data-ttu-id="e92e9-145">.cer 檔 (憑證檔) 則具有公開金鑰，用來進行簽章的加密和驗證。</span><span class="sxs-lookup"><span data-stu-id="e92e9-145">A .cer file (certificate file) holds the public key for encryption and validation of the signature.</span></span>  
  
 <span data-ttu-id="e92e9-146">**化學資料交換 (CIDX) Chem eStandards**</span><span class="sxs-lookup"><span data-stu-id="e92e9-146">**Chemical Data Exchange (CIDX) Chem eStandards**</span></span>  
 <span data-ttu-id="e92e9-147">資料交換的統一標準，為了用於化學藥品的買賣交易和運送而特別開發。</span><span class="sxs-lookup"><span data-stu-id="e92e9-147">Uniform standards of data exchange developed specifically for the buying, selling, and delivery of chemicals.</span></span> <span data-ttu-id="e92e9-148">這些標準是以普遍能接受辨識的電子資料交換標準—XML 為基礎。</span><span class="sxs-lookup"><span data-stu-id="e92e9-148">These standards are based on the universally recognized standards for electronic data exchange—XML.</span></span> <span data-ttu-id="e92e9-149">BTARN 能支援 CIDX Chem eStandards。</span><span class="sxs-lookup"><span data-stu-id="e92e9-149">BTARN supports CIDX Chem eStandards.</span></span>  
  
 <span data-ttu-id="e92e9-150">**叢集**</span><span class="sxs-lookup"><span data-stu-id="e92e9-150">**cluster**</span></span>  
 <span data-ttu-id="e92e9-151">高層級的商務程序群組，例如訂單管理、存貨管理或服務與支援。</span><span class="sxs-lookup"><span data-stu-id="e92e9-151">A group of high-level business processes, such as order management, inventory management, or service and support.</span></span> <span data-ttu-id="e92e9-152">RosettaNet 所處理的叢集能顯示出供應鏈產業的核心商務程序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-152">The clusters addressed by RosettaNet represent core business processes for the supply chain industry.</span></span>  
  
## <a name="d"></a><span data-ttu-id="e92e9-153">D</span><span class="sxs-lookup"><span data-stu-id="e92e9-153">D</span></span>  
 <span data-ttu-id="e92e9-154">**數值資料通用編號系統 (A-U-N-S)**</span><span class="sxs-lookup"><span data-stu-id="e92e9-154">**Data Universal Numbering System (D-U-N-S) number**</span></span>  
 <span data-ttu-id="e92e9-155">循序產生的九位數編號，可以獨一無二地識別全球企業的位置。</span><span class="sxs-lookup"><span data-stu-id="e92e9-155">A sequentially generated nine-digit number that uniquely identifies business locations, and is global in scope.</span></span>  
  
 <span data-ttu-id="e92e9-156">**傳遞標頭**</span><span class="sxs-lookup"><span data-stu-id="e92e9-156">**delivery header**</span></span>  
 <span data-ttu-id="e92e9-157">RosettaNet 訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="e92e9-157">A part of a RosettaNet message.</span></span> <span data-ttu-id="e92e9-158">傳遞標頭是能識別訊息傳送者、收件者和訊息執行個體資訊的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e92e9-158">The delivery header is an XML document that identifies the message sender, the recipient, and message instance information.</span></span>  
  
 <span data-ttu-id="e92e9-159">**目的地組織**</span><span class="sxs-lookup"><span data-stu-id="e92e9-159">**destination organization**</span></span>  
 <span data-ttu-id="e92e9-160">在傳訊連接埠中，指定用來做為文件傳送目的地的組織。</span><span class="sxs-lookup"><span data-stu-id="e92e9-160">An organization that has been designated in a messaging port as the destination for documents.</span></span>  
  
 <span data-ttu-id="e92e9-161">**數位演算法**</span><span class="sxs-lookup"><span data-stu-id="e92e9-161">**digital algorithms**</span></span>  
 <span data-ttu-id="e92e9-162">採用訊息做為輸入，並產生該訊息之雜湊或摘要的演算法，根據訊息內容的不同，具有固定長度，且類型極為複雜的位元組。</span><span class="sxs-lookup"><span data-stu-id="e92e9-162">An algorithm that takes a message as input and produces a hash or digest of it, a fixed-length set of bits that depend on the message contents in some highly complex manner.</span></span> <span data-ttu-id="e92e9-163">這種演算法的設計準則，就是要讓任何人都難以偽造摘要；或是難以在不變更摘要的情況下變更其訊息。</span><span class="sxs-lookup"><span data-stu-id="e92e9-163">Design criteria include making it extremely difficult for anyone to counterfeit a digest or to change a message without changing its digest.</span></span> <span data-ttu-id="e92e9-164">在訊息驗證和數位簽章配置中的應用程式，通常都會使用摘要演算法。</span><span class="sxs-lookup"><span data-stu-id="e92e9-164">Applications that typically use digest algorithms are in message authentication and digital signature schemes.</span></span> <span data-ttu-id="e92e9-165">廣泛使用的演算法包括 MD5 和 SHA1。</span><span class="sxs-lookup"><span data-stu-id="e92e9-165">Widely used algorithms include MD5 and SHA1.</span></span> <span data-ttu-id="e92e9-166">對於內送訊息，BTARN 支援 MD5 和 SHA1；對於外寄訊息，則只支援 SHA1。</span><span class="sxs-lookup"><span data-stu-id="e92e9-166">BTARN supports both MD5 and SHA1 for incoming messages, and only SHA1 for outgoing messages.</span></span>  
  
 <span data-ttu-id="e92e9-167">**文件定義**</span><span class="sxs-lookup"><span data-stu-id="e92e9-167">**document definition**</span></span>  
 <span data-ttu-id="e92e9-168">表示特定文件的屬性集。</span><span class="sxs-lookup"><span data-stu-id="e92e9-168">A set of properties that represents a specific document.</span></span> <span data-ttu-id="e92e9-169">文件定義屬性包括文件規格的指標，並且可以包含全域追蹤欄位和選取準則。</span><span class="sxs-lookup"><span data-stu-id="e92e9-169">Document definition properties include a pointer to a document specification and can include global tracking fields and selection criteria.</span></span>  
  
 <span data-ttu-id="e92e9-170">**文件執行個體**</span><span class="sxs-lookup"><span data-stu-id="e92e9-170">**document instance**</span></span>  
 <span data-ttu-id="e92e9-171">傳送至 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 之實際資料的表示法。</span><span class="sxs-lookup"><span data-stu-id="e92e9-171">A representation of the actual data that is sent to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="e92e9-172">文件執行個體和文件規格不同處在於，規格會定義資料的結構，而文件執行個體則是包含在結構中之特定資料的表示法。</span><span class="sxs-lookup"><span data-stu-id="e92e9-172">A document instance differs from a document specification in that the specification defines the structure of the data, while a document instance is a representation of the specific data that is contained in a structure.</span></span>  
  
 <span data-ttu-id="e92e9-173">**文件類型定義 (DTD)**</span><span class="sxs-lookup"><span data-stu-id="e92e9-173">**document type definition (DTD)**</span></span>  
 <span data-ttu-id="e92e9-174">用來指定其他項目和屬性中，所要顯示的項目和屬性，以及指定這些項目和屬性之順序、發生頻率和內容之條件約束的標準定義。</span><span class="sxs-lookup"><span data-stu-id="e92e9-174">A standard definition that specifies which elements and attributes might be present in other elements and attributes and that specifies any constraints on their ordering, frequency, and content.</span></span>  
  
 <span data-ttu-id="e92e9-175">**雙向動作交易** </span><span class="sxs-lookup"><span data-stu-id="e92e9-175">**double action transaction** </span></span>  
 <span data-ttu-id="e92e9-176">啟動者傳送要求動作、接收信號，然後回應者發生回應動作的程序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-176">A process where an initiator sends a request action, receives a signal, followed by a response action from the responder.</span></span> <span data-ttu-id="e92e9-177">啟動者傳送信號至回應動作，即完成該程序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-177">The initiator finishes the process by sending a signal to the response action.</span></span>  
  
## <a name="e"></a><span data-ttu-id="e92e9-178">E</span><span class="sxs-lookup"><span data-stu-id="e92e9-178">E</span></span>  
 <span data-ttu-id="e92e9-179">**可延伸標記語言 (XML)**</span><span class="sxs-lookup"><span data-stu-id="e92e9-179">**Extensible Markup Language (XML)**</span></span>  
 <span data-ttu-id="e92e9-180">由全球資訊網協會 (W3C) 所開發的規格，讓程式設計人員能建立超越標準 HTML 功能的自訂標籤。</span><span class="sxs-lookup"><span data-stu-id="e92e9-180">A specification developed by the World Wide Web Consortium (W3C) that enables designers to create customized tags beyond the capabilities of standard HTML.</span></span> <span data-ttu-id="e92e9-181">當 HTML 只能使用預先定義的標籤，描述頁面中的項目時，XML 卻能讓網頁開發人員自行定義標籤。</span><span class="sxs-lookup"><span data-stu-id="e92e9-181">While HTML uses only predefined tags to describe elements in the page, XML enables tags to be defined by the developer of the page.</span></span> <span data-ttu-id="e92e9-182">對於任何虛擬的資料項目 (例如產品或到期金額)，標籤都可以針對特定的應用程式來使用。</span><span class="sxs-lookup"><span data-stu-id="e92e9-182">Tags for virtually any data item, such as a product or an amount due, can be used for specific applications.</span></span> <span data-ttu-id="e92e9-183">這讓網頁也可以具有和資料庫記錄相同的功能。</span><span class="sxs-lookup"><span data-stu-id="e92e9-183">This enables Web pages to function as database records.</span></span>  
  
 <span data-ttu-id="e92e9-184">**可延伸樣式表語言 (XSL)**</span><span class="sxs-lookup"><span data-stu-id="e92e9-184">**Extensible Stylesheet Language (XSL)**</span></span>  
 <span data-ttu-id="e92e9-185">用於 XML 文件的樣式表格式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-185">A style sheet format for XML documents.</span></span> <span data-ttu-id="e92e9-186">XSL 用來定義 XML 的顯示，就像階層式樣式表 (CSS) 用來定義 HTML 的顯示。</span><span class="sxs-lookup"><span data-stu-id="e92e9-186">XSL is used to define the display of XML just like cascading style sheets (CSS) are used to define the display of HTML.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e92e9-187"> 使用 XSL 當做翻譯語言，這兩種規格之間。</span><span class="sxs-lookup"><span data-stu-id="e92e9-187"> uses XSL as the translation language between two specifications.</span></span>  
  
## <a name="g"></a><span data-ttu-id="e92e9-188">G</span><span class="sxs-lookup"><span data-stu-id="e92e9-188">G</span></span>  
 <span data-ttu-id="e92e9-189">**全球商務識別碼 (GBI)**</span><span class="sxs-lookup"><span data-stu-id="e92e9-189">**Global Business Identification (GBI)**</span></span>  
 <span data-ttu-id="e92e9-190">用來識別交易合作對象的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="e92e9-190">A unique identifier to identify trading parties.</span></span> <span data-ttu-id="e92e9-191">RosettaNet 會使用九位數的鄧白氏編號系統 (DUNS，Dun and Bradstreet Numbering System) 做為 GBI。</span><span class="sxs-lookup"><span data-stu-id="e92e9-191">RosettaNet uses the nine-digit Dun and Bradstreet Numbering System (DUNS) as the GBI.</span></span>  
  
## <a name="h"></a><span data-ttu-id="e92e9-192">H</span><span class="sxs-lookup"><span data-stu-id="e92e9-192">H</span></span>  
 <span data-ttu-id="e92e9-193">**主要組織** </span><span class="sxs-lookup"><span data-stu-id="e92e9-193">**home organization** </span></span>  
 <span data-ttu-id="e92e9-194">用來識別您的組織之別名。</span><span class="sxs-lookup"><span data-stu-id="e92e9-194">An alias to identify your organization.</span></span>  
  
## <a name="i"></a><span data-ttu-id="e92e9-195">I</span><span class="sxs-lookup"><span data-stu-id="e92e9-195">I</span></span>  
 <span data-ttu-id="e92e9-196">**起始端**</span><span class="sxs-lookup"><span data-stu-id="e92e9-196">**initiator**</span></span>  
 <span data-ttu-id="e92e9-197">首先對交易夥伴引發程序的交易或通知程序中，組織所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="e92e9-197">The role of an organization in a transaction or notification process that initiates a process to a trading partner.</span></span>  
  
## <a name="l"></a><span data-ttu-id="e92e9-198">L</span><span class="sxs-lookup"><span data-stu-id="e92e9-198">L</span></span>  
 <span data-ttu-id="e92e9-199">**企業營運 (LOB) 應用程式**</span><span class="sxs-lookup"><span data-stu-id="e92e9-199">**Line of Business (LOB) Application**</span></span>  
 <span data-ttu-id="e92e9-200">做為後端系統，用來與 BTARN 進行溝通的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-200">The application that communicates with BTARN as the backend system.</span></span>  
  
 <span data-ttu-id="e92e9-201">**回送公用程式**</span><span class="sxs-lookup"><span data-stu-id="e92e9-201">**Loopback utility**</span></span>  
 <span data-ttu-id="e92e9-202">供程式開發人員用來自動產生回送協議 (組織對夥伴協議的鏡像複本) 的公用程式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-202">A utility for developers to automatically generate a loopback agreement that is a mirror copy of a home-to-partner agreement.</span></span> <span data-ttu-id="e92e9-203">這讓您可以在單一電腦上，執行組織對夥伴以及夥伴對組織的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="e92e9-203">This lets you perform home-to-partner and partner-to-home message exchanges on a single computer.</span></span>  
  
## <a name="m"></a><span data-ttu-id="e92e9-204">M</span><span class="sxs-lookup"><span data-stu-id="e92e9-204">M</span></span>  
 <span data-ttu-id="e92e9-205">**對應**</span><span class="sxs-lookup"><span data-stu-id="e92e9-205">**map**</span></span>  
 <span data-ttu-id="e92e9-206">在一規格中的記錄和欄位以及其他規格中的記錄和欄位之間，定義對應關係的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="e92e9-206">An XML file that defines the correspondence between the records and fields in one specification and the records and fields in another specification.</span></span> <span data-ttu-id="e92e9-207">對應含有 XSL 樣式表，讓 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 用來執行該對應中描述的轉換資訊。</span><span class="sxs-lookup"><span data-stu-id="e92e9-207">A map contains an XSL style sheet that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] uses to perform the transformation described in the map.</span></span> <span data-ttu-id="e92e9-208">對應是建立於 BizTalk 對應工具中。</span><span class="sxs-lookup"><span data-stu-id="e92e9-208">Maps are created in BizTalk Mapper.</span></span>
  
 <span data-ttu-id="e92e9-209">**我的組織**</span><span class="sxs-lookup"><span data-stu-id="e92e9-209">**my organization**</span></span>  
 <span data-ttu-id="e92e9-210">會在交易夥伴協議中顯示您的組織。</span><span class="sxs-lookup"><span data-stu-id="e92e9-210">Represents your organization in a trading partner agreement.</span></span>   
  
 <span data-ttu-id="e92e9-211">**多用途網際網路郵件延伸 (標準 MIME)**</span><span class="sxs-lookup"><span data-stu-id="e92e9-211">**Multi-Purpose Internet Mail Extensions (MIME)**</span></span>  
 <span data-ttu-id="e92e9-212">可讓您的網際網路電子郵件通訊協定的延伸模組會使用通訊協定交換不同種類的網際網路上的資料檔案： 音訊、 視訊、 影像和應用程式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-212">An extension of the Internet e-mail protocol that lets you use the protocol to exchange different kinds of data files on the Internet: audio, video, images, and application programs.</span></span>  
  
## <a name="n"></a><span data-ttu-id="e92e9-213">N</span><span class="sxs-lookup"><span data-stu-id="e92e9-213">N</span></span>  
 <span data-ttu-id="e92e9-214">**不可否認性**</span><span class="sxs-lookup"><span data-stu-id="e92e9-214">**non-repudiation**</span></span>  
 <span data-ttu-id="e92e9-215">用來確認訊息傳送者不能在訊息傳送後，否認傳送過這個訊息，而收件者也不能否認接收過這個訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-215">A way to make sure that the sender of a message cannot later refuse to recognize that the sender sent the message and that the recipient cannot deny having received the message.</span></span> <span data-ttu-id="e92e9-216">內送訊息的不可否認功能需要收件者儲存訊息，而訊息也必須具有使用傳送者之簽章憑證的數位簽章，確保其正確性。</span><span class="sxs-lookup"><span data-stu-id="e92e9-216">Non-repudiation of an incoming message requires that the message be saved by the receiver, and that the message should carry a digital signature using the signing certificate of the sender to ensure its authenticity.</span></span> <span data-ttu-id="e92e9-217">外寄訊息的不可否認功能則需要儲存認可訊息 (來自第一個訊息之收件者的內送訊息)，而訊息也必須具有使用收件者之簽章憑證的數位簽章 (原始訊息之摘要的簽章)。</span><span class="sxs-lookup"><span data-stu-id="e92e9-217">Non-repudiation of an outgoing message requires saving the acknowledgement message (incoming message from the recipient of the first message), and that the message should carry the digital signature of the digest of the original message using the signing certificate of the recipient.</span></span>   
  
 <span data-ttu-id="e92e9-218">**通知**</span><span class="sxs-lookup"><span data-stu-id="e92e9-218">**notification**</span></span>  
 <span data-ttu-id="e92e9-219">啟動者以單一訊息通知回應者的 RNIF 1.1 程序類型。</span><span class="sxs-lookup"><span data-stu-id="e92e9-219">An RNIF 1.1 process type where the initiator notifies the responder with a single message.</span></span> <span data-ttu-id="e92e9-220">回應者必須要以商務信號做為認可來回應。</span><span class="sxs-lookup"><span data-stu-id="e92e9-220">The responder is expected to reply with a business signal as an acknowledgement.</span></span>  
  
 <span data-ttu-id="e92e9-221">**失敗 (PIP 0A1) 的通知**</span><span class="sxs-lookup"><span data-stu-id="e92e9-221">**Notification of Failure (PIP 0A1)**</span></span>  
 <span data-ttu-id="e92e9-222">指出未預期之程序錯誤的 PIP。</span><span class="sxs-lookup"><span data-stu-id="e92e9-222">A special PIP that indicates unexpected process failures.</span></span> <span data-ttu-id="e92e9-223">不管是啟動者或是回應者，都可以發出失敗通知。</span><span class="sxs-lookup"><span data-stu-id="e92e9-223">The initiator or the responder can initiate a Notification of Failure.</span></span> <span data-ttu-id="e92e9-224">它可以針對現有或是之前所交換的程序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-224">It refers to an existing or previously exchanged process.</span></span> <span data-ttu-id="e92e9-225">根據收到的 0A1，接收合作對象即可確認所參考的程序會視為無效。</span><span class="sxs-lookup"><span data-stu-id="e92e9-225">Upon receipt of a 0A1, the receiving party makes sure that the referenced process is considered not valid.</span></span>  
  
## <a name="o"></a><span data-ttu-id="e92e9-226">O</span><span class="sxs-lookup"><span data-stu-id="e92e9-226">O</span></span>  
 <span data-ttu-id="e92e9-227">**組織**</span><span class="sxs-lookup"><span data-stu-id="e92e9-227">**organization**</span></span>  
 <span data-ttu-id="e92e9-228">可以主導商務交易的交易夥伴或是業務單位。</span><span class="sxs-lookup"><span data-stu-id="e92e9-228">A trading partner or a business unit that can conduct business transactions.</span></span>  
  
## <a name="p"></a><span data-ttu-id="e92e9-229">P</span><span class="sxs-lookup"><span data-stu-id="e92e9-229">P</span></span>  
 <span data-ttu-id="e92e9-230">**封裝**</span><span class="sxs-lookup"><span data-stu-id="e92e9-230">**packaging**</span></span>  
 <span data-ttu-id="e92e9-231">將 RosettaNet 訊息與其 XML 呈現方式互相轉換的程序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-231">The process of converting a RosettaNet message in its XML representation and vice versa.</span></span>  
  
 <span data-ttu-id="e92e9-232">**交易夥伴介面程序 (PIP)**</span><span class="sxs-lookup"><span data-stu-id="e92e9-232">**Partner Interface Process (PIP)**</span></span>  
 <span data-ttu-id="e92e9-233">PIP 會描述詳細的商務文件和協議集，其中包含文件的詳細內容。</span><span class="sxs-lookup"><span data-stu-id="e92e9-233">A PIP describes a set of business documents and agreement details, including document content details.</span></span>  
  
 <span data-ttu-id="e92e9-234">**PIP 規格文件**</span><span class="sxs-lookup"><span data-stu-id="e92e9-234">**PIP Specification document**</span></span>  
 <span data-ttu-id="e92e9-235">包含關於在 BTARN 管理主控台中建立程序組態時，所需設定的指導文件。</span><span class="sxs-lookup"><span data-stu-id="e92e9-235">A document that contains guidance about the settings to use when you create a process configuration in the BTARN Management Console.</span></span> <span data-ttu-id="e92e9-236">您可以從 RosettaNet 組織 (RosettaNet.org) 下載 PIP 規格文件和該 PIP。包含關於在 BTARN 管理主控台中建立程序組態時，所需設定的指導文件。</span><span class="sxs-lookup"><span data-stu-id="e92e9-236">You download the PIP Specification document and the PIP from the RosettaNet organization, from RosettaNet.org. A document that contains guidance about the settings to use when you create a process configuration in the BTARN Management Console.</span></span> <span data-ttu-id="e92e9-237">您可以從 RosettaNet 組織 (RosettaNet.org) 下載 PIP 規格文件和該 PIP。</span><span class="sxs-lookup"><span data-stu-id="e92e9-237">You download the PIP Specification document and the PIP from the RosettaNet organization, from RosettaNet.org.</span></span>  
  
 <span data-ttu-id="e92e9-238">**前序標頭**</span><span class="sxs-lookup"><span data-stu-id="e92e9-238">**preamble header**</span></span>  
 <span data-ttu-id="e92e9-239">XML 節點，能識別與商務訊息相容之標準的名稱和版本。</span><span class="sxs-lookup"><span data-stu-id="e92e9-239">An XML node that identifies the name and version of the standard with which a business message is compliant.</span></span> <span data-ttu-id="e92e9-240">它會與其他標頭一起進行封裝，以便形成完整的 RosettaNet 訊息。</span><span class="sxs-lookup"><span data-stu-id="e92e9-240">It is packaged together with other headers to form a complete RosettaNet Message.</span></span> <span data-ttu-id="e92e9-241">這也稱為前序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-241">Also named preamble.</span></span>  
  
 <span data-ttu-id="e92e9-242">**私用程序** </span><span class="sxs-lookup"><span data-stu-id="e92e9-242">**private process** </span></span>  
 <span data-ttu-id="e92e9-243">組織內部的商務程序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-243">Business processes that are internal to an organization.</span></span> <span data-ttu-id="e92e9-244">BTARN 會實作私用程序，做為長期執行的 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="e92e9-244">BTARN implements private processes as long-running BizTalk orchestrations.</span></span>  
  
 <span data-ttu-id="e92e9-245">**處理序組態設定 (PCS) 設定檔**</span><span class="sxs-lookup"><span data-stu-id="e92e9-245">**Process Configuration Setting (PCS) profile**</span></span>  
 <span data-ttu-id="e92e9-246">決定交易夥伴協議執行的方式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-246">Determines how a partner agreement runs.</span></span> <span data-ttu-id="e92e9-247">使用 PCS 設定檔，便能輸入 RosettaNet「交易夥伴介面程序 (PIP)」的詳細組態設定。</span><span class="sxs-lookup"><span data-stu-id="e92e9-247">You use the PCS profile to enter the configuration details of a RosettaNet Partner Interface Process (PIP).</span></span> <span data-ttu-id="e92e9-248">所有在 RosettaNet PIP 規格中指定的組態設定值，都會對應到 PCS 設定檔中的某個項目。</span><span class="sxs-lookup"><span data-stu-id="e92e9-248">All configuration values specified in a RosettaNet PIP specification map to one element in the PCS profile.</span></span> <span data-ttu-id="e92e9-249">因此，您可以使用一個 PCS 設定檔，處理多項交易夥伴協議。</span><span class="sxs-lookup"><span data-stu-id="e92e9-249">You can use one PCS profile for multiple partner agreements.</span></span>  
  
 <span data-ttu-id="e92e9-250">**port**</span><span class="sxs-lookup"><span data-stu-id="e92e9-250">**port**</span></span>  
 <span data-ttu-id="e92e9-251">使用特定實作方式的具名位置。</span><span class="sxs-lookup"><span data-stu-id="e92e9-251">A named location that uses a specific implementation.</span></span> <span data-ttu-id="e92e9-252">在「BizTalk 協調流程設計師」中，連接埠是由傳送或接收訊息的位置以及用來實作通訊動作的技術加以定義。</span><span class="sxs-lookup"><span data-stu-id="e92e9-252">In BizTalk Orchestration Designer, a port is defined by the location to which messages are sent or from which messages are received, and the technology that is used to implement the communication action.</span></span> <span data-ttu-id="e92e9-253">這個位置只會由這個連接埠的名稱唯一識別。</span><span class="sxs-lookup"><span data-stu-id="e92e9-253">The location is uniquely identified by the name of the port.</span></span>  
  
 <span data-ttu-id="e92e9-254">**公開程序** </span><span class="sxs-lookup"><span data-stu-id="e92e9-254">**public process** </span></span>  
 <span data-ttu-id="e92e9-255">包含與交易夥伴進行整合成為公開程序的商務程序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-255">Business processes that involve integration with trading partners as public processes.</span></span> <span data-ttu-id="e92e9-256">BTARN 會實作公開程序，做為長期執行的 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="e92e9-256">BTARN implements public processes as long-running BizTalk orchestrations.</span></span> <span data-ttu-id="e92e9-257">一個公開程序協調流程會在啟動者端執行，另一個則是在回應者端執行。</span><span class="sxs-lookup"><span data-stu-id="e92e9-257">One public-process orchestration runs on the initiator side and one on the responder side.</span></span> <span data-ttu-id="e92e9-258">BTARN 安裝程式為 RNIF 1.1 與 RNIF 2.01 都提供了啟動者及回應者公開程序協調流程版本。</span><span class="sxs-lookup"><span data-stu-id="e92e9-258">The BTARN Setup program provides versions of the initiator and responder public-process orchestrations for both RNIF 1.1 and RNIF 2.01.</span></span> <span data-ttu-id="e92e9-259">這些公開程序協調流程會實作所有的 RNIF 程序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-259">These public-process orchestrations implement all RNIF processes.</span></span> <span data-ttu-id="e92e9-260">公開程序對其餘的元件隱藏了 RNIF 的複雜性。</span><span class="sxs-lookup"><span data-stu-id="e92e9-260">Public processes hide the complexity of RNIF from the rest of the components.</span></span> <span data-ttu-id="e92e9-261">這種公開程序除了強制與 RNIF 相容的訊息流程之外，也決定了預設追蹤設定，並提供執行階段的程序狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="e92e9-261">Besides enforcing the RNIF-compliant message flow, the public process also determines default-tracking settings and provides process state information at runtime.</span></span>  
  
## <a name="r"></a><span data-ttu-id="e92e9-262">R</span><span class="sxs-lookup"><span data-stu-id="e92e9-262">R</span></span>  
 <span data-ttu-id="e92e9-263">**回應者**</span><span class="sxs-lookup"><span data-stu-id="e92e9-263">**responder**</span></span>  
 <span data-ttu-id="e92e9-264">在交易或通知程序中回應交易夥伴之要求的組織角色。</span><span class="sxs-lookup"><span data-stu-id="e92e9-264">The role of an organization in a transaction or notification process that responds to a request by a trading partner.</span></span>  
  
 <span data-ttu-id="e92e9-265">**RosettaNet 實作架構 (RNIF)**</span><span class="sxs-lookup"><span data-stu-id="e92e9-265">**RosettaNet Implementation Framework (RNIF)**</span></span>  
 <span data-ttu-id="e92e9-266">對於想要建立能執行 PIP，且可互相合作之軟體應用程式元件的公司，提供他們實作指導的標準架構。</span><span class="sxs-lookup"><span data-stu-id="e92e9-266">A standards framework that provides implementation guidelines for those companies that want to create interoperable software application components that run PIPs.</span></span>  
  
 <span data-ttu-id="e92e9-267">**RosettaNet 訊息**</span><span class="sxs-lookup"><span data-stu-id="e92e9-267">**RosettaNet message**</span></span>  
 <span data-ttu-id="e92e9-268">包含前序標頭、傳遞標頭 (就 RNIF 2.0 而言)、服務標頭和服務內容的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="e92e9-268">The logical grouping of the preamble header, delivery header (in the case of RNIF 2.0), service header, and service content.</span></span>  
  
 <span data-ttu-id="e92e9-269">**RosettaNet 物件**</span><span class="sxs-lookup"><span data-stu-id="e92e9-269">**RosettaNet object**</span></span>  
 <span data-ttu-id="e92e9-270">包裝後要以 RosettaNet 實作架構 1.1 版之格式進行傳送的 RosettaNet 訊息。</span><span class="sxs-lookup"><span data-stu-id="e92e9-270">A RosettaNet message enveloped for delivery in RosettaNet Implementation Framework version 1.1.</span></span>  
  
## <a name="s"></a><span data-ttu-id="e92e9-271">S</span><span class="sxs-lookup"><span data-stu-id="e92e9-271">S</span></span>  
 <span data-ttu-id="e92e9-272">**schema**</span><span class="sxs-lookup"><span data-stu-id="e92e9-272">**schema**</span></span>  
 <span data-ttu-id="e92e9-273">XML 檔案結構的定義。</span><span class="sxs-lookup"><span data-stu-id="e92e9-273">The definition of the structure of an XML file.</span></span> <span data-ttu-id="e92e9-274">結構描述包含有屬性資訊，就像它屬於結構中的記錄和欄位一樣。</span><span class="sxs-lookup"><span data-stu-id="e92e9-274">A schema contains property information as it pertains to the records and fields in the structure.</span></span>  
  
 <span data-ttu-id="e92e9-275">**服務內容**</span><span class="sxs-lookup"><span data-stu-id="e92e9-275">**service content**</span></span>  
 <span data-ttu-id="e92e9-276">RosettaNet 訊息的主要元件。</span><span class="sxs-lookup"><span data-stu-id="e92e9-276">The primary component of the RosettaNet message.</span></span> <span data-ttu-id="e92e9-277">它是一個 XML 節點，表示特定 PIP 所指定的商務內容。</span><span class="sxs-lookup"><span data-stu-id="e92e9-277">It is an XML node that represents the business content specified by a particular PIP.</span></span>  
  
 <span data-ttu-id="e92e9-278">**服務標頭**</span><span class="sxs-lookup"><span data-stu-id="e92e9-278">**service header**</span></span>  
 <span data-ttu-id="e92e9-279">用來識別與商務訊息有關部分的 XML 文件，這些部分包括 PIP、商務活動和動作、傳送和接收服務、交易夥伴，以及角色。</span><span class="sxs-lookup"><span data-stu-id="e92e9-279">An XML document that identifies the parts associated with a business message, including the PIP, business activity and action, sending and receiving services, trading partners, and roles.</span></span>  
  
 <span data-ttu-id="e92e9-280">**信號 URL**</span><span class="sxs-lookup"><span data-stu-id="e92e9-280">**signal URL**</span></span>  
 <span data-ttu-id="e92e9-281">主要組織傳輸信號訊息的目標 URL。</span><span class="sxs-lookup"><span data-stu-id="e92e9-281">The URL to which the home organization transmits a signal message.</span></span> <span data-ttu-id="e92e9-282">例如， http://FabrikamServer/BTARNApp/RNIFReceive.aspx。</span><span class="sxs-lookup"><span data-stu-id="e92e9-282">For example, http://FabrikamServer/BTARNApp/RNIFReceive.aspx.</span></span>  
  
 <span data-ttu-id="e92e9-283">**單向動作通知**</span><span class="sxs-lookup"><span data-stu-id="e92e9-283">**single action notification**</span></span>  
 <span data-ttu-id="e92e9-284">啟動者傳送單一動作訊息，然後回應者以訊息進行回覆的程序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-284">A process where the initiator sends a single action message and the responder replies with a message.</span></span>  
  
 <span data-ttu-id="e92e9-285">**規格**</span><span class="sxs-lookup"><span data-stu-id="e92e9-285">**specification**</span></span>  
 <span data-ttu-id="e92e9-286">[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 特有的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="e92e9-286">A [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]-specific XML schema.</span></span> <span data-ttu-id="e92e9-287">您可以在 BizTalk 編輯器中，根據產業標準 (例如 EDIFACT、X12 和 XML) 或一般檔案 (分隔資料、位置資料，或是分隔和位置資料) 建立規格。</span><span class="sxs-lookup"><span data-stu-id="e92e9-287">You create specifications in BizTalk Editor and can be based on industry standards, such as EDIFACT, X12, and XML, or on flat files, such as delimited, positional, or delimited and positional.</span></span> <span data-ttu-id="e92e9-288">BizTalk 對應工具會使用規格建立對應，這些規格和來源規格以及目的規格一樣都屬於開放式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-288">BizTalk Mapper uses specifications, opened as source specifications and destination specifications, to create maps.</span></span>  
  
 <span data-ttu-id="e92e9-289">**同步 URL**</span><span class="sxs-lookup"><span data-stu-id="e92e9-289">**sync URL**</span></span>  
 <span data-ttu-id="e92e9-290">主要組織會使用來建立與夥伴，例如，同步交易的 URL http://FabikamServer/BTARNApp/RNIFReceive.aspx。</span><span class="sxs-lookup"><span data-stu-id="e92e9-290">The URL that the home organization uses to establish synchronous transactions with the partner, for example, http://FabikamServer/BTARNApp/RNIFReceive.aspx.</span></span>  
  
 <span data-ttu-id="e92e9-291">**同步交易**</span><span class="sxs-lookup"><span data-stu-id="e92e9-291">**synchronous transaction**</span></span>  
 <span data-ttu-id="e92e9-292">啟動者在相同的 HTTP 狀態傳回回應 (雙向動作) 或信號 (單向動作)，而不關閉連線的程序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-292">A process where the initiator returns a response (double-action) or signal (single-action) on the same HTTP state without closing the connection.</span></span>  
  
## <a name="t"></a><span data-ttu-id="e92e9-293">T</span><span class="sxs-lookup"><span data-stu-id="e92e9-293">T</span></span>  
 <span data-ttu-id="e92e9-294">**交易夥伴**</span><span class="sxs-lookup"><span data-stu-id="e92e9-294">**trading partner**</span></span>  
 <span data-ttu-id="e92e9-295">與您的組織交換電子資料的外部組織。</span><span class="sxs-lookup"><span data-stu-id="e92e9-295">An external organization with which your organization exchanges electronic data.</span></span>  
  
 <span data-ttu-id="e92e9-296">**交易夥伴協議**</span><span class="sxs-lookup"><span data-stu-id="e92e9-296">**trading partner agreement**</span></span>  
 <span data-ttu-id="e92e9-297">您的組織與交易夥伴之間的協議。</span><span class="sxs-lookup"><span data-stu-id="e92e9-297">An agreement between your organization and your trading partner.</span></span> <span data-ttu-id="e92e9-298">交易夥伴協議會參考「程序組態設定」設定檔、主要組織和交易夥伴，並包含協議特殊的組態設定。</span><span class="sxs-lookup"><span data-stu-id="e92e9-298">A trading partner agreement references a Process Configuration Setting profile, home organization, partner, and contains agreement specific configuration settings.</span></span>  
  
 <span data-ttu-id="e92e9-299">**交易**</span><span class="sxs-lookup"><span data-stu-id="e92e9-299">**transaction**</span></span>  
 <span data-ttu-id="e92e9-300">啟動者傳送 RosettaNet 訊息、接收信號、接收 RosettaNet 訊息做為回答，以及傳送認可信號的 RNIF 1.1 程序。</span><span class="sxs-lookup"><span data-stu-id="e92e9-300">An RNIF 1.1 process where the initiator sends a RosettaNet message, receives a signal, receives a RosettaNet message as an answer, and sends a signal for acknowledgement.</span></span>  
  
## <a name="v"></a><span data-ttu-id="e92e9-301">V</span><span class="sxs-lookup"><span data-stu-id="e92e9-301">V</span></span>  
 <span data-ttu-id="e92e9-302">**驗證配接器**</span><span class="sxs-lookup"><span data-stu-id="e92e9-302">**validation adapter**</span></span>  
 <span data-ttu-id="e92e9-303">實作驗證配接器介面的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e92e9-303">An application that implements the Validation Adapter interface.</span></span> <span data-ttu-id="e92e9-304">當公開回應者收到動作訊息 (要求或回應) 時，便會叫用「驗證配接器」。</span><span class="sxs-lookup"><span data-stu-id="e92e9-304">The public responder invokes the Validation Adapter when it receives an action message (request or response).</span></span> <span data-ttu-id="e92e9-305">它可以包含企業在接受內送訊息前，所需的任何驗證規則集。</span><span class="sxs-lookup"><span data-stu-id="e92e9-305">It can include any set of validation rules that a business may require before accepting an incoming message.</span></span> <span data-ttu-id="e92e9-306">BTARN 本身就會在接收管線和公用協調流程中執行驗證。</span><span class="sxs-lookup"><span data-stu-id="e92e9-306">BTARN natively performs validation in the receive pipeline, and in public orchestrations.</span></span>  
  
## <a name="x"></a><span data-ttu-id="e92e9-307">X</span><span class="sxs-lookup"><span data-stu-id="e92e9-307">X</span></span>  
 <span data-ttu-id="e92e9-308">**XLANG 排程**</span><span class="sxs-lookup"><span data-stu-id="e92e9-308">**XLANG schedule**</span></span>  
 <span data-ttu-id="e92e9-309">用來描述商務程序與後端整合的特定 XML 語言。</span><span class="sxs-lookup"><span data-stu-id="e92e9-309">A specific XML language that describes business processes and back-end integration.</span></span> <span data-ttu-id="e92e9-310">BTARN 中的特定商務程序會以 XLANG 語言加以表示。</span><span class="sxs-lookup"><span data-stu-id="e92e9-310">Specific business processes in BTARN are expressed in the XLANG language.</span></span> <span data-ttu-id="e92e9-311">XLANG 排程是以 .skx 做為副檔名進行儲存。</span><span class="sxs-lookup"><span data-stu-id="e92e9-311">An XLANG schedule is saved with the file name extension .skx.</span></span>  
  
