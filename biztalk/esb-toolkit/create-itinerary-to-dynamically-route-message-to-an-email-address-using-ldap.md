---
title: 如何： 建立路線以動態方式將訊息路由至電子郵件地址，使用 LDAP 查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d9929dd-5e45-4b0d-90df-52a35e68b0ba
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93a2237b76524488d7a3903468ebb321d19ae623
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987599"
---
# <a name="how-to-create-an-itinerary-to-dynamically-route-a-message-to-an-email-address-using-an-ldap-query"></a><span data-ttu-id="7c0e1-102">如何： 建立路線以動態方式將訊息路由至電子郵件地址，使用 LDAP 查詢</span><span class="sxs-lookup"><span data-stu-id="7c0e1-102">How to: Create an Itinerary to Dynamically Route a Message to an Email Address Using an LDAP Query</span></span>
## <a name="goal"></a><span data-ttu-id="7c0e1-103">目標</span><span class="sxs-lookup"><span data-stu-id="7c0e1-103">Goal</span></span>  
 <span data-ttu-id="7c0e1-104">本節示範如何建立查詢透過 LDAP （輕量型目錄存取通訊協定） 的電子郵件地址，然後將電子郵件訊息傳送至使用 BizTalk Server SMTP 配接器的解析端點路線。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-104">This section demonstrates how to create an itinerary that queries an e-mail address through LDAP (Lightweight Directory Access Protocol) and then sends an e-mail message to the resolved endpoint using the BizTalk Server SMTP adapter.</span></span>  
  
 <span data-ttu-id="7c0e1-105">在本使用說明主題中，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7c0e1-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="7c0e1-106">建立動態路由傳送訊息，使用 LDAP 查詢路線傳閱名單。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-106">Create an itinerary routing slip to dynamically route a message using an LDAP query.</span></span>  
  
-   <span data-ttu-id="7c0e1-107">測試使用路線測試用戶端的範例應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-107">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7c0e1-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="7c0e1-108">Prerequisites</span></span>  
 <span data-ttu-id="7c0e1-109">本使用說明主題中的程序必須完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-109">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
 <span data-ttu-id="7c0e1-110">在其，您將完成本節中的電腦必須有 Microsoft Active Directory 目錄服務已設定並執行 (不需要電腦是網域控制站，但它必須連線到網域)。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-110">The computer on which you will complete this section must have Microsoft Active Directory directory service configured and running (it is not required that the computer is the domain controller, but it must be connected to the domain).</span></span> <span data-ttu-id="7c0e1-111">此外，SMTP 伺服器必須已設定且正在執行;若要測試本使用說明主題的結果，您必須具有要檢查的 ESB 所傳送的電子郵件的用戶端。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-111">Also, an SMTP server must be configured and running; in order to test the outcome of this How-to topic, you must have a client with which to check the e-mail sent by the ESB.</span></span>  
  
 <span data-ttu-id="7c0e1-112">在本節中的指示會假設有家名 Global Bank 網域為 globalbank.com，為與 Active Directory 組織單位名為 Employees，其中包含使用者 John Evans 名為有效的電子郵件地址，在他的設定檔 （例如johne@globalbank.com).</span><span class="sxs-lookup"><span data-stu-id="7c0e1-112">The instructions in this section assume an organization named Global Bank, with a domain of globalbank.com, with an Active Directory Organizational Unit named Employees that contains a user named John Evans with a valid e-mail address in his profile (such as johne@globalbank.com).</span></span> <span data-ttu-id="7c0e1-113">您不需要複寫這些環境因素;不過，基於重新建立您的環境中的這個實作，請考量下列因素，請視需要的替代項目。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-113">It is not necessary to replicate these environmental factors; however, for purposes of recreating this implementation in your environment, please account for these factors and make substitutions as necessary.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="7c0e1-114">步驟</span><span class="sxs-lookup"><span data-stu-id="7c0e1-114">Steps</span></span>  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model"></a><span data-ttu-id="7c0e1-115">若要建立的 ESB 路線的特定領域語言 (DSL) 模型</span><span class="sxs-lookup"><span data-stu-id="7c0e1-115">To create an ESB itinerary domain-specific language (DSL) model</span></span>  
  
1.  <span data-ttu-id="7c0e1-116">在 Visual Studio 中，開啟 [C:\HowTos\Patterns\Patterns.sln]。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-116">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="7c0e1-117">在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新路線**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-117">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="7c0e1-118">在 [**加入新項目**] 對話方塊中，輸入**LdapResolution**中**名稱**方塊，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-118">In the **Add New Item** dialog box, type **LdapResolution** in the **Name** box, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="7c0e1-119">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="7c0e1-119">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="7c0e1-120">在 Visual Studio 中，按一下設計介面**LdapResolution.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-120">In Visual Studio, click the design surface of **LdapResolution.itinerary**.</span></span> <span data-ttu-id="7c0e1-121">在 [ **LdapResolution**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7c0e1-121">In the **LdapResolution** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="7c0e1-122">在 **模型匯出工具**下拉式清單中，按一下**XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-122">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="7c0e1-123">底下**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性中，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-123">Under the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="7c0e1-124">在 [**選取 XML 檔案**] 對話方塊中，輸入**C:\HowTos\Itineraries\LdapResolution**中**檔名**方塊，然後再按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-124">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\LdapResolution** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="7c0e1-125">此步驟可讓您將匯出為 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-125">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="7c0e1-126">而不是匯出至本機檔案位置，路線，路線資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-126">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="7c0e1-127">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-127">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="7c0e1-128">若要定義的路線結構</span><span class="sxs-lookup"><span data-stu-id="7c0e1-128">To define the structure of the itinerary</span></span>  
  
1. <span data-ttu-id="7c0e1-129">從 [工具箱] 拖曳**匝道**模型項目到設計介面。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-129">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="7c0e1-130">在 [ **OnRamp1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7c0e1-130">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
   1.  <span data-ttu-id="7c0e1-131">按一下 **名稱**屬性，然後按**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-131">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
   2.  <span data-ttu-id="7c0e1-132">在  **Extender**下拉式清單中，按一下**匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-132">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
   3.  <span data-ttu-id="7c0e1-133">在  **BizTalk 應用程式**下拉式清單中，按一下**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-133">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
   4.  <span data-ttu-id="7c0e1-134">在 **接收埠**下拉式清單中，按一下**OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-134">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2. <span data-ttu-id="7c0e1-135">從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並再將其放置在右邊**匝道**模型項目。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-135">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="7c0e1-136">在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7c0e1-136">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
   1.  <span data-ttu-id="7c0e1-137">按一下 **名稱**屬性，然後按**RouteMessageEmail**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-137">Click the **Name** property, and then type **RouteMessageEmail**.</span></span>  
  
   2.  <span data-ttu-id="7c0e1-138">在 **路線服務的擴充項**下拉式清單中，按一下**傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-138">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="7c0e1-139">這個屬性會定義此程序需要 （傳訊） 的管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-139">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="7c0e1-140">或者，如果協調流程中的位置時，會進行的程序，設定**路線服務 Extender**屬性設**協調流程 Extender**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-140">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
   3.  <span data-ttu-id="7c0e1-141">在 **容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-141">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
   4.  <span data-ttu-id="7c0e1-142">在 **服務名稱**下拉式清單中，按一下**Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-142">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
3. <span data-ttu-id="7c0e1-143">以滑鼠右鍵按一下**解析**的集合**RouteMessageEmail**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-143">Right-click the **Resolver** collection of the **RouteMessageEmail** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="7c0e1-144">在 [ **Resolver1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7c0e1-144">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
   1.  <span data-ttu-id="7c0e1-145">按一下 **名稱**屬性，然後按**LdapResolver**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-145">Click the **Name** property, and then type **LdapResolver**.</span></span>  
  
   2.  <span data-ttu-id="7c0e1-146">在 **解析程式實作**下拉式清單中，按一下**LDAP 解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-146">In the **Resolver Implementation** drop-down list, click **LDAP Resolver Extension**.</span></span>  
  
   3.  <span data-ttu-id="7c0e1-147">在 **傳輸名稱**下拉式清單中，按一下**SMTP**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-147">In the **Transport Name** drop-down list, click **SMTP**.</span></span>  
  
   4.  <span data-ttu-id="7c0e1-148">按一下 **傳輸位置**屬性，然後按 **{郵件}**</span><span class="sxs-lookup"><span data-stu-id="7c0e1-148">Click the **Transport Location** property, and then type **{mail}**</span></span>  
  
   5.  <span data-ttu-id="7c0e1-149">按一下  **SearchRoot**屬性，然後按**ou = Employees，dc = globalbank，dc = com**</span><span class="sxs-lookup"><span data-stu-id="7c0e1-149">Click the **SearchRoot** property, and then type **ou=Employees,dc=globalbank,dc=com**</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="7c0e1-150">如果您不具有設定您的環境，根據規格，< 先決條件 > 一節中，取代先前的屬性中的值適用於您環境的。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-150">If you have not set up your environment according to the specifications in the "Prerequisites" section, replace the values in the preceding property with ones that are appropriate for your environment.</span></span>  
  
   6.  <span data-ttu-id="7c0e1-151">按一下 **篩選條件**屬性，然後將值變更為 **(&(objectClass=User) (&#124;(givenName = john)))**</span><span class="sxs-lookup"><span data-stu-id="7c0e1-151">Click the **Filter** property, and then change the value to **(&(objectClass=User)(&#124;(givenName=john)))**</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="7c0e1-152">輸入上述的值來取代現有的文字。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-152">Type the preceding value to replace the existing text.</span></span>  
  
   7.  <span data-ttu-id="7c0e1-153">在  **ThrowErrorIfNotFound**下拉式清單中，按一下 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-153">In the **ThrowErrorIfNotFound** drop-down list, click **True**.</span></span>  
  
4. <span data-ttu-id="7c0e1-154">在 [屬性] 視窗中，按一下**端點組態**屬性，然後按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-154">In the Properties window, click the **Endpoint Configuration** property, and then click the ellipsis button (...).</span></span>  
  
   1. <span data-ttu-id="7c0e1-155">在 [**端點組態**] 對話方塊中，按一下**EmailBodyText**屬性，然後按**訂單已就緒可供處理**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-155">In the **Endpoint Configuration** dialog box, click the **EmailBodyText** property, and then type **Order is ready to be processed**.</span></span>  
  
   2. <span data-ttu-id="7c0e1-156">按一下 **從**屬性，然後按<strong>orders@globalbank.com</strong>。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-156">Click the **From** property, and then type <strong>orders@globalbank.com</strong>.</span></span>  
  
   3. <span data-ttu-id="7c0e1-157">按一下  **MessagePartsAttachment**屬性，然後按**2**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-157">Click the **MessagePartsAttachment** property, and then type **2**.</span></span>  
  
   4. <span data-ttu-id="7c0e1-158">按一下 **主旨**屬性，然後按**順序 {givenName}**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-158">Click the **Subject** property, and then type **Order for {givenName}**.</span></span>  
  
   5. <span data-ttu-id="7c0e1-159">設定**SMTPAuthentication SMTPHost、 使用者名稱**並**密碼**為您的本機環境中使用的連接資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-159">Configure the **SMTPAuthentication, SMTPHost, UserName,** and **Password** properties using the connection information for your local environment.</span></span>  
  
   6. <span data-ttu-id="7c0e1-160">按一下 [ **[確定]** 以關閉**端點組態**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-160">Click **OK** to close the **Endpoint Configuration** dialog box.</span></span>  
  
5. <span data-ttu-id="7c0e1-161">以滑鼠右鍵按一下**LdapResolver**解析程式，然後再按一下**測試解析程式組態**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-161">Right-click the **LdapResolver** resolver, and then click **Test Resolver Configuration**.</span></span>  
  
6. <span data-ttu-id="7c0e1-162">在 輸出 視窗中，確認 已解析中的主體**端點組態**值是**john 順序**，然後確認已解析**傳輸位置**是電子郵件地址與 Active Directory 中的使用者帳戶相關聯 (例如johne@globalbank.com)。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-162">In the Output window, verify the subject in the resolved **Endpoint Configuration** value is **Order for John**, and then verify that the resolved **Transport Location** is the e-mail address associated with the user's account in Active Directory (for example, johne@globalbank.com).</span></span>  
  
7. <span data-ttu-id="7c0e1-163">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-163">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="7c0e1-164">拖曳連接，以從**ReceiveNAOrder**模型項目**RouteMessageEmail**模型項目。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-164">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessageEmail** model element.</span></span>  
  
8. <span data-ttu-id="7c0e1-165">從 [工具箱] 拖曳**出口匝**模型項目到設計介面，並再將其放置在右邊**RouteMessageEmail**模型項目。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-165">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteMessageEmail** model element.</span></span> <span data-ttu-id="7c0e1-166">在 [ **OffRamp1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7c0e1-166">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
   1.  <span data-ttu-id="7c0e1-167">按一下 **名稱**屬性，然後按**EmailNAOrderDoc**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-167">Click the **Name** property, and then type **EmailNAOrderDoc**.</span></span>  
  
   2.  <span data-ttu-id="7c0e1-168">在  **Extender**下拉式清單中，按一下**出口匝 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-168">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
   3.  <span data-ttu-id="7c0e1-169">在  **BizTalk 應用程式**下拉式清單中，按一下**GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-169">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
   4.  <span data-ttu-id="7c0e1-170">在 **傳送埠**下拉式清單中，按一下**DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-170">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
9. <span data-ttu-id="7c0e1-171">從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並將其之間放置**RouteMessageEmail**模型項目和**EmailNAOrderDoc**模型項目。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-171">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteMessageEmail** model element and the **EmailNAOrderDoc** model element.</span></span> <span data-ttu-id="7c0e1-172">在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7c0e1-172">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="7c0e1-173">按一下 **名稱**屬性，然後按**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-173">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="7c0e1-174">在 **路線服務的擴充項**下拉式清單中，按一下**出口匝 Extender**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-174">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="7c0e1-175">在 **出口匝**下拉式清單中，展開**EmailNAOrderDoc**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-175">In the **Off-Ramp** drop-down list, expand **EmailNAOrderDoc**, and then click **Send Handlers**.</span></span>  
  
10. <span data-ttu-id="7c0e1-176">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-176">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="7c0e1-177">拖曳連接，以從**RouteMessageEmail**模型項目**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-177">Drag a connection from the **RouteMessageEmail** model element to the **SendPortFilter** model element.</span></span>  
  
11. <span data-ttu-id="7c0e1-178">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-178">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="7c0e1-179">拖曳連接，以從**SendPortFilter**模型項目**EmailNAOrderDoc**模型項目。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-179">Drag a connection from the **SendPortFilter** model element to the **EmailNAOrderDoc** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="7c0e1-180">若要匯出使用路線測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="7c0e1-180">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="7c0e1-181">在 Visual Studio 中，以滑鼠右鍵按一下設計介面**LdapResolution**路線，，然後按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-181">In Visual Studio, right-click the design surface of the **LdapResolution** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7c0e1-182">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-182">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="7c0e1-183">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-183">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="7c0e1-184">在 Windows 檔案總管中，瀏覽至 C:\HowTos\Itineraries 並注意您的路線 XML (LdapResolution.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-184">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (LdapResolution.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="7c0e1-185">若要測試的路線</span><span class="sxs-lookup"><span data-stu-id="7c0e1-185">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="7c0e1-186">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-186">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="7c0e1-187">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後按一下**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-187">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="7c0e1-188">在 [**開啟路線檔案**] 對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-188">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="7c0e1-189">選取  **LdapResolution.xml**，然後按一下**開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-189">Select **LdapResolution.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="7c0e1-190">按一下  **確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-190">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="7c0e1-191">在路線測試用戶端中，按一下 [旁的省略符號按鈕 （...）**載入訊息**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-191">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="7c0e1-192">在 [**選取要載入的 XML 文件**] 對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-192">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="7c0e1-193">選取  **NAOrderDoc.xml**，然後按一下**開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-193">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="7c0e1-194">按一下 [**送出要求**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-194">Click the **Submit Request** button.</span></span> <span data-ttu-id="7c0e1-195">測試完成時，按一下**確定**關閉顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-195">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="7c0e1-196">開啟 Microsoft Outlook Express （或您選擇的郵件用戶端），並確認訊息傳送到 John Evans 的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="7c0e1-196">Open Microsoft Outlook Express (or the mail client of your choice) and verify delivery of the message to the e-mail of John Evans.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="7c0e1-197">其他資源</span><span class="sxs-lookup"><span data-stu-id="7c0e1-197">Additional Resources</span></span>  
 <span data-ttu-id="7c0e1-198">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="7c0e1-198">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="7c0e1-199">開發活動</span><span class="sxs-lookup"><span data-stu-id="7c0e1-199">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="7c0e1-200">使用動態解析和路由</span><span class="sxs-lookup"><span data-stu-id="7c0e1-200">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)