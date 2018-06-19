---
title: 如何： 建立以動態方式將訊息路由傳送電子郵件地址，使用 LDAP 查詢行程 |Microsoft 文件
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
ms.openlocfilehash: 751eaf381b762372652bb77ddf6f00ffe43971c2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010111"
---
# <a name="how-to-create-an-itinerary-to-dynamically-route-a-message-to-an-email-address-using-an-ldap-query"></a><span data-ttu-id="e8c21-102">如何： 建立以動態方式將訊息路由傳送電子郵件地址，使用 LDAP 查詢的行程</span><span class="sxs-lookup"><span data-stu-id="e8c21-102">How to: Create an Itinerary to Dynamically Route a Message to an Email Address Using an LDAP Query</span></span>
## <a name="goal"></a><span data-ttu-id="e8c21-103">目標</span><span class="sxs-lookup"><span data-stu-id="e8c21-103">Goal</span></span>  
 <span data-ttu-id="e8c21-104">本節示範如何建立查詢透過 LDAP （輕量型目錄存取通訊協定） 的電子郵件地址，然後再將電子郵件訊息傳送至已解決的端點使用 BizTalk Server SMTP 配接器的行程。</span><span class="sxs-lookup"><span data-stu-id="e8c21-104">This section demonstrates how to create an itinerary that queries an e-mail address through LDAP (Lightweight Directory Access Protocol) and then sends an e-mail message to the resolved endpoint using the BizTalk Server SMTP adapter.</span></span>  
  
 <span data-ttu-id="e8c21-105">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e8c21-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="e8c21-106">建立動態路由傳送訊息，使用 LDAP 查詢計劃的路由受控滑動。</span><span class="sxs-lookup"><span data-stu-id="e8c21-106">Create an itinerary routing slip to dynamically route a message using an LDAP query.</span></span>  
  
-   <span data-ttu-id="e8c21-107">測試使用路線測試用戶端範例應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="e8c21-107">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e8c21-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="e8c21-108">Prerequisites</span></span>  
 <span data-ttu-id="e8c21-109">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="e8c21-109">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
 <span data-ttu-id="e8c21-110">您將在其完成本節的電腦必須有 Microsoft Active Directory 目錄服務設定且正在執行 (不需要電腦是網域控制站，但必須連線到網域)。</span><span class="sxs-lookup"><span data-stu-id="e8c21-110">The computer on which you will complete this section must have Microsoft Active Directory directory service configured and running (it is not required that the computer is the domain controller, but it must be connected to the domain).</span></span> <span data-ttu-id="e8c21-111">此外，SMTP 伺服器必須設定並執行。若要測試此 「 如何 」 主題的結果，您必須用來檢查 ESB 所傳送的電子郵件用戶端。</span><span class="sxs-lookup"><span data-stu-id="e8c21-111">Also, an SMTP server must be configured and running; in order to test the outcome of this How-to topic, you must have a client with which to check the e-mail sent by the ESB.</span></span>  
  
 <span data-ttu-id="e8c21-112">本節中的指示會假設名為 Active Directory 組織單位名為 Employees 包含名為 John Evans 且有效的電子郵件位址 （例如他設定檔中的使用者與全域銀行globalbank.com，網域的組織johne@globalbank.com).</span><span class="sxs-lookup"><span data-stu-id="e8c21-112">The instructions in this section assume an organization named Global Bank, with a domain of globalbank.com, with an Active Directory Organizational Unit named Employees that contains a user named John Evans with a valid e-mail address in his profile (such as johne@globalbank.com).</span></span> <span data-ttu-id="e8c21-113">不需要複寫這些環境的因素。不過，基於重新建立這項實作您的環境中，請考慮這些因素，請視需要的替代項目。</span><span class="sxs-lookup"><span data-stu-id="e8c21-113">It is not necessary to replicate these environmental factors; however, for purposes of recreating this implementation in your environment, please account for these factors and make substitutions as necessary.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="e8c21-114">步驟</span><span class="sxs-lookup"><span data-stu-id="e8c21-114">Steps</span></span>  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model"></a><span data-ttu-id="e8c21-115">若要建立 ESB 路線網域特定領域語言 (DSL) 模型</span><span class="sxs-lookup"><span data-stu-id="e8c21-115">To create an ESB itinerary domain-specific language (DSL) model</span></span>  
  
1.  <span data-ttu-id="e8c21-116">在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="e8c21-116">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="e8c21-117">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-117">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="e8c21-118">在**加入新項目** 對話方塊中，輸入**LdapResolution**中**名稱**方塊，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-118">In the **Add New Item** dialog box, type **LdapResolution** in the **Name** box, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="e8c21-119">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="e8c21-119">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="e8c21-120">在 Visual Studio 中，按一下設計介面的**LdapResolution.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-120">In Visual Studio, click the design surface of **LdapResolution.itinerary**.</span></span> <span data-ttu-id="e8c21-121">在**LdapResolution**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e8c21-121">In the **LdapResolution** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="e8c21-122">在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-122">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="e8c21-123">下**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性中，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="e8c21-123">Under the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="e8c21-124">在**選取 XML 檔案** 對話方塊中，輸入**C:\HowTos\Itineraries\LdapResolution**中**檔案名稱**方塊，然後再按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-124">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\LdapResolution** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="e8c21-125">這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="e8c21-125">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="e8c21-126">藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="e8c21-126">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="e8c21-127">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="e8c21-127">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="e8c21-128">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="e8c21-128">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="e8c21-129">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="e8c21-129">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="e8c21-130">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e8c21-130">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="e8c21-131">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-131">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="e8c21-132">在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-132">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="e8c21-133">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-133">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="e8c21-134">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-134">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="e8c21-135">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**上手**模型項目。</span><span class="sxs-lookup"><span data-stu-id="e8c21-135">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="e8c21-136">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e8c21-136">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="e8c21-137">按一下**名稱**屬性，，然後輸入**RouteMessageEmail**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-137">Click the **Name** property, and then type **RouteMessageEmail**.</span></span>  
  
    2.  <span data-ttu-id="e8c21-138">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-138">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="e8c21-139">這個屬性會定義程序將需要 (messaging) 在管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="e8c21-139">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="e8c21-140">或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-140">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="e8c21-141">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-141">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="e8c21-142">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-142">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
3.  <span data-ttu-id="e8c21-143">以滑鼠右鍵按一下**解析程式**集合**RouteMessageEmail**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-143">Right-click the **Resolver** collection of the **RouteMessageEmail** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="e8c21-144">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e8c21-144">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="e8c21-145">按一下**名稱**屬性，，然後輸入**LdapResolver**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-145">Click the **Name** property, and then type **LdapResolver**.</span></span>  
  
    2.  <span data-ttu-id="e8c21-146">在**解析程式實作**下拉式清單中，按一下  **LDAP 解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-146">In the **Resolver Implementation** drop-down list, click **LDAP Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="e8c21-147">在**傳輸名稱**下拉式清單中，按一下  **SMTP**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-147">In the **Transport Name** drop-down list, click **SMTP**.</span></span>  
  
    4.  <span data-ttu-id="e8c21-148">按一下**傳輸位置**屬性，，然後輸入 **{mail}**</span><span class="sxs-lookup"><span data-stu-id="e8c21-148">Click the **Transport Location** property, and then type **{mail}**</span></span>  
  
    5.  <span data-ttu-id="e8c21-149">按一下**SearchRoot**屬性，，然後輸入**ou = 員工，dc = globalbank，dc = com**</span><span class="sxs-lookup"><span data-stu-id="e8c21-149">Click the **SearchRoot** property, and then type **ou=Employees,dc=globalbank,dc=com**</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="e8c21-150">如果您尚未在 < 先決條件 > 一節中設定您的環境，根據規格，取代先前的屬性中的值適用於您的環境。</span><span class="sxs-lookup"><span data-stu-id="e8c21-150">If you have not set up your environment according to the specifications in the "Prerequisites" section, replace the values in the preceding property with ones that are appropriate for your environment.</span></span>  
  
    6.  <span data-ttu-id="e8c21-151">按一下**篩選**屬性，然後將變更的值 **(&(objectClass=User) (&#124;(givenName=john)))**</span><span class="sxs-lookup"><span data-stu-id="e8c21-151">Click the **Filter** property, and then change the value to **(&(objectClass=User)(&#124;(givenName=john)))**</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="e8c21-152">輸入上面的值來取代現有的文字。</span><span class="sxs-lookup"><span data-stu-id="e8c21-152">Type the preceding value to replace the existing text.</span></span>  
  
    7.  <span data-ttu-id="e8c21-153">在**ThrowErrorIfNotFound**下拉式清單中，按一下  **True**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-153">In the **ThrowErrorIfNotFound** drop-down list, click **True**.</span></span>  
  
4.  <span data-ttu-id="e8c21-154">在 [屬性] 視窗中，按一下**端點組態**屬性，然後按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="e8c21-154">In the Properties window, click the **Endpoint Configuration** property, and then click the ellipsis button (...).</span></span>  
  
    1.  <span data-ttu-id="e8c21-155">在**端點組態**對話方塊中，按一下  **EmailBodyText**屬性，，然後輸入**順序已準備好處理**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-155">In the **Endpoint Configuration** dialog box, click the **EmailBodyText** property, and then type **Order is ready to be processed**.</span></span>  
  
    2.  <span data-ttu-id="e8c21-156">按一下**從**屬性，，然後輸入 **orders@globalbank.com** 。</span><span class="sxs-lookup"><span data-stu-id="e8c21-156">Click the **From** property, and then type **orders@globalbank.com**.</span></span>  
  
    3.  <span data-ttu-id="e8c21-157">按一下**MessagePartsAttachment**屬性，，然後輸入**2**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-157">Click the **MessagePartsAttachment** property, and then type **2**.</span></span>  
  
    4.  <span data-ttu-id="e8c21-158">按一下**主旨**屬性，，然後輸入**順序 {givenName}**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-158">Click the **Subject** property, and then type **Order for {givenName}**.</span></span>  
  
    5.  <span data-ttu-id="e8c21-159">設定**SMTPAuthentication、 SMTPHost、 使用者名稱、** 和**密碼**屬性的本機環境中使用的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="e8c21-159">Configure the **SMTPAuthentication, SMTPHost, UserName,** and **Password** properties using the connection information for your local environment.</span></span>  
  
    6.  <span data-ttu-id="e8c21-160">按一下**確定**關閉**端點組態** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e8c21-160">Click **OK** to close the **Endpoint Configuration** dialog box.</span></span>  
  
5.  <span data-ttu-id="e8c21-161">以滑鼠右鍵按一下**LdapResolver**解析程式，然後再按一下**測試解析程式組態**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-161">Right-click the **LdapResolver** resolver, and then click **Test Resolver Configuration**.</span></span>  
  
6.  <span data-ttu-id="e8c21-162">在 輸出 視窗中，確認 已解析中的主體**端點組態**值是**john 順序**，然後確認已解析**傳輸位置**是電子郵件地址與 Active Directory 中使用者的帳戶相關聯 (例如， johne@globalbank.com)。</span><span class="sxs-lookup"><span data-stu-id="e8c21-162">In the Output window, verify the subject in the resolved **Endpoint Configuration** value is **Order for John**, and then verify that the resolved **Transport Location** is the e-mail address associated with the user's account in Active Directory (for example, johne@globalbank.com).</span></span>  
  
7.  <span data-ttu-id="e8c21-163">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-163">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="e8c21-164">拖曳連接**ReceiveNAOrder**模型項目的**RouteMessageEmail**模型項目。</span><span class="sxs-lookup"><span data-stu-id="e8c21-164">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessageEmail** model element.</span></span>  
  
8.  <span data-ttu-id="e8c21-165">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**RouteMessageEmail**模型項目。</span><span class="sxs-lookup"><span data-stu-id="e8c21-165">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteMessageEmail** model element.</span></span> <span data-ttu-id="e8c21-166">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e8c21-166">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="e8c21-167">按一下**名稱**屬性，，然後輸入**EmailNAOrderDoc**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-167">Click the **Name** property, and then type **EmailNAOrderDoc**.</span></span>  
  
    2.  <span data-ttu-id="e8c21-168">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-168">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="e8c21-169">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-169">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="e8c21-170">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-170">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
9. <span data-ttu-id="e8c21-171">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**RouteMessageEmail**模型項目和**EmailNAOrderDoc**模型項目。</span><span class="sxs-lookup"><span data-stu-id="e8c21-171">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteMessageEmail** model element and the **EmailNAOrderDoc** model element.</span></span> <span data-ttu-id="e8c21-172">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e8c21-172">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="e8c21-173">按一下**名稱**屬性，，然後輸入**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-173">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="e8c21-174">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-174">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="e8c21-175">在**匝道**下拉式清單中，展開**EmailNAOrderDoc**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-175">In the **Off-Ramp** drop-down list, expand **EmailNAOrderDoc**, and then click **Send Handlers**.</span></span>  
  
10. <span data-ttu-id="e8c21-176">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-176">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="e8c21-177">拖曳連接**RouteMessageEmail**模型項目的**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="e8c21-177">Drag a connection from the **RouteMessageEmail** model element to the **SendPortFilter** model element.</span></span>  
  
11. <span data-ttu-id="e8c21-178">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-178">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="e8c21-179">拖曳連接**SendPortFilter**模型項目的**EmailNAOrderDoc**模型項目。</span><span class="sxs-lookup"><span data-stu-id="e8c21-179">Drag a connection from the **SendPortFilter** model element to the **EmailNAOrderDoc** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="e8c21-180">若要匯出的行程測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="e8c21-180">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="e8c21-181">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**LdapResolution**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-181">In Visual Studio, right-click the design surface of the **LdapResolution** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e8c21-182">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="e8c21-182">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="e8c21-183">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="e8c21-183">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="e8c21-184">在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (LdapResolution.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="e8c21-184">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (LdapResolution.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="e8c21-185">若要測試路線</span><span class="sxs-lookup"><span data-stu-id="e8c21-185">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="e8c21-186">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="e8c21-186">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="e8c21-187">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="e8c21-187">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="e8c21-188">在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="e8c21-188">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="e8c21-189">選取**LdapResolution.xml**，然後按一下 **開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="e8c21-189">Select **LdapResolution.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="e8c21-190">按一下**確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="e8c21-190">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="e8c21-191">在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。</span><span class="sxs-lookup"><span data-stu-id="e8c21-191">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="e8c21-192">在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="e8c21-192">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="e8c21-193">選取**NAOrderDoc.xml**，然後按一下 **開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="e8c21-193">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="e8c21-194">按一下**送出要求** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e8c21-194">Click the **Submit Request** button.</span></span> <span data-ttu-id="e8c21-195">測試完成時，按一下**確定**解除顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="e8c21-195">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="e8c21-196">開啟 Microsoft Outlook Express （或您選擇的郵件用戶端），並確認 John Evans 的電子郵件訊息的傳遞。</span><span class="sxs-lookup"><span data-stu-id="e8c21-196">Open Microsoft Outlook Express (or the mail client of your choice) and verify delivery of the message to the e-mail of John Evans.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="e8c21-197">其他資源</span><span class="sxs-lookup"><span data-stu-id="e8c21-197">Additional Resources</span></span>  
 <span data-ttu-id="e8c21-198">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="e8c21-198">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="e8c21-199">開發活動</span><span class="sxs-lookup"><span data-stu-id="e8c21-199">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="e8c21-200">使用動態解析和路由</span><span class="sxs-lookup"><span data-stu-id="e8c21-200">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)