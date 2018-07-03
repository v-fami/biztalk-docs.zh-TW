---
title: '逐步解說 (EDIFACT): 接收 EDI 交換並傳回通知 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 02751f0c-8e7e-4879-93e4-8bc475640756
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b221d47a64f603db697b99c7e5a60b1cb1a67bd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018888"
---
# <a name="walkthrough-edifact-receiving-edi-interchanges-and-sending-back-an-acknowledgement"></a><span data-ttu-id="f5b78-102">逐步解說 (EDIFACT)：接收 EDI 交換並傳回通知</span><span class="sxs-lookup"><span data-stu-id="f5b78-102">Walkthrough (EDIFACT): Receiving EDI Interchanges and Sending Back an Acknowledgement</span></span>
<span data-ttu-id="f5b78-103">本逐步解說提供一組逐步執行的程序，來使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 建立可接收 EDIFACT 交換的解決方案。</span><span class="sxs-lookup"><span data-stu-id="f5b78-103">This walkthrough provides a set of step-by-step procedures that creates a solution for receiving EDIFACT interchanges using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="f5b78-104">在這個解決方案中，EDIFACT 交換會從一個交易夥伴 (Fabrikam) 傳送至另一個交易夥伴 (Contoso)。</span><span class="sxs-lookup"><span data-stu-id="f5b78-104">In this solution, an EDIFACT interchange is sent from a trading partner, Fabrikam, to another trading partner, Contoso.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="f5b78-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="f5b78-105">Prerequisites</span></span>  
 <span data-ttu-id="f5b78-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="f5b78-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  

## <a name="how-the-solution-receives-edifact-interchanges"></a><span data-ttu-id="f5b78-107">解決方案如何接收 EDIFACT 交換</span><span class="sxs-lookup"><span data-stu-id="f5b78-107">How the Solution Receives EDIFACT Interchanges</span></span>  
 <span data-ttu-id="f5b78-108">解決方案會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f5b78-108">The solution will do the following:</span></span>  

> [!NOTE]
>  <span data-ttu-id="f5b78-109">這份清單中的事件可能不會按照所示的順序發生。</span><span class="sxs-lookup"><span data-stu-id="f5b78-109">The events in this list may not occur in the order shown.</span></span>  

1.  <span data-ttu-id="f5b78-110">從交易夥伴 Fabrikam 接收一般檔案 EDIFACT 交換。</span><span class="sxs-lookup"><span data-stu-id="f5b78-110">Receive a flat-file EDIFACT interchange from the trading partner Fabrikam.</span></span>  

2.  <span data-ttu-id="f5b78-111">將 EDIFACT 交換比對其結構描述來進行驗證、將訊息解譯到 XML 中，並將訊息 XML 放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="f5b78-111">Validate the EDIFACT interchange against its schema, disassemble the message into XML, and drop the message XML into the MessageBox.</span></span>  

3.  <span data-ttu-id="f5b78-112">產生表示已收到 EDI 交換的技術通知 (訊息回條)，並將其放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="f5b78-112">Generate a technical acknowledgement (receipt of message) to the received EDI interchange, and drop it in the MessageBox.</span></span>  

4.  <span data-ttu-id="f5b78-113">產生表示接受或拒絕接收 EDI 交換的功能通知，並將其放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="f5b78-113">Generate a functional acknowledgment (acceptance or rejection of the received EDI interchange), and drop it in the MessageBox.</span></span>  

5.  <span data-ttu-id="f5b78-114">透過單向 FILE 傳送埠拾取訊息 XML，並組合訊息 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="f5b78-114">Pick up the message XML by a one-way FILE send port, and assemble the message EDI interchange.</span></span>  

6.  <span data-ttu-id="f5b78-115">傳送 EDI 交換至 Contoso 本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-115">Send the EDI interchange to Contoso local folder.</span></span>  

7.  <span data-ttu-id="f5b78-116">透過單向 FILE 傳送埠拾取技術通知，並組合交換。</span><span class="sxs-lookup"><span data-stu-id="f5b78-116">Pick up the technical acknowledgement by a one-way FILE send port, and assemble the interchange.</span></span>  

8.  <span data-ttu-id="f5b78-117">傳送技術通知至 Fabrikam 本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-117">Send the technical acknowledgement to the Fabrikam local folder.</span></span>  

9. <span data-ttu-id="f5b78-118">透過單向 FILE 傳送埠拾取功能通知，並組合交換。</span><span class="sxs-lookup"><span data-stu-id="f5b78-118">Pick up the functional acknowledgement by a one-way FILE send port, and assemble the interchange.</span></span>  

10. <span data-ttu-id="f5b78-119">傳送功能通知至 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="f5b78-119">Send the functional acknowledgement to Fabrikam.</span></span>  

## <a name="the-functionality-in-this-solution"></a><span data-ttu-id="f5b78-120">此解決方案中的功能</span><span class="sxs-lookup"><span data-stu-id="f5b78-120">The Functionality in this Solution</span></span>  
 <span data-ttu-id="f5b78-121">為了完成這個逐步解說，將會啟用下列功能：</span><span class="sxs-lookup"><span data-stu-id="f5b78-121">For the purposes of this walkthrough, the following functionality will be enabled:</span></span>  

- <span data-ttu-id="f5b78-122">這個解決方案是專為使用 EDIFACT 編碼的交換而設計。</span><span class="sxs-lookup"><span data-stu-id="f5b78-122">The solution is designed for interchanges using EDIFACT encoding</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="f5b78-123">如需有關如何建立類似的解決方案，為 X12 交換的指示，請參閱[逐步解說 (X12)： 接收 EDI 交換和傳送，將通知傳回](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)。</span><span class="sxs-lookup"><span data-stu-id="f5b78-123">For instructions on how to create a similar solution for X12 interchanges, see [Walkthrough (X12): Receiving EDI Interchanges and Sending Back an Acknowledgement](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md).</span></span>  

- <span data-ttu-id="f5b78-124">將針對內送交換執行 EDI 類型和擴充驗證。</span><span class="sxs-lookup"><span data-stu-id="f5b78-124">EDI type and extended validation will be performed on the incoming interchange.</span></span>  

- <span data-ttu-id="f5b78-125">將會產生技術和功能通知，以傳回給交換傳送者。</span><span class="sxs-lookup"><span data-stu-id="f5b78-125">Technical and functional acknowledgments will be generated for returning to the sender of the interchange.</span></span>  

- <span data-ttu-id="f5b78-126">這個解決方案使用單向接收位置與 FILE 傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="f5b78-126">The solution uses a one-way receive location with a FILE transport type.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="f5b78-127">您可以使用雙向請求回應接收埠和位置來接收訊息，但是如果這樣做的話，就不能對接收位置使用 FILE 傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="f5b78-127">You can use a two-way solicit response receive port and location to receive the message, but if you do so, you will not be able to use a FILE transport type for the receive location.</span></span> <span data-ttu-id="f5b78-128">如需詳細資訊，請參閱 <<c0> [ 設定連接埠來接收 EDI 訊息和通知](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md)。</span><span class="sxs-lookup"><span data-stu-id="f5b78-128">For more information, see [Configuring a Port to Receive EDI Messages and Acknowledgments](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md).</span></span>  

- <span data-ttu-id="f5b78-129">EDI 報告將會啟用，並會儲存交易集，以從交換狀態報告進行檢視。</span><span class="sxs-lookup"><span data-stu-id="f5b78-129">EDI reporting will be enabled, and transaction sets will be saved for viewing from the interchange status report.</span></span>  

- <span data-ttu-id="f5b78-130">為了測試目的，解決方案會使用三個傳送埠，將 EDIFACT 交換和建立的通知傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-130">For testing purposes, the solution uses three send ports to send the EDIFACT interchange and the ACKs created to local folders.</span></span>  

  <span data-ttu-id="f5b78-131">下圖顯示這個解決方案的架構：</span><span class="sxs-lookup"><span data-stu-id="f5b78-131">The following figure shows the architecture for this solution:</span></span>  

  <span data-ttu-id="f5b78-132">![接收 EDIFACT 交換及傳送通知](../core/media/edifact-walkthrough.gif "EDIFACT_Walkthrough")</span><span class="sxs-lookup"><span data-stu-id="f5b78-132">![Receiving EDIFACT interchange and sending an ACK](../core/media/edifact-walkthrough.gif "EDIFACT_Walkthrough")</span></span>  

## <a name="configuring-and-testing-the-walkthrough"></a><span data-ttu-id="f5b78-133">設定和測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="f5b78-133">Configuring and Testing the Walkthrough</span></span>  
 <span data-ttu-id="f5b78-134">這個解決方案所需的程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f5b78-134">The procedures required for this solution include the following:</span></span>  

- <span data-ttu-id="f5b78-135">將必要的訊息結構描述加入 BizTalk 專案，然後建置並部署此專案，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用該結構描述來處理收到的交換。</span><span class="sxs-lookup"><span data-stu-id="f5b78-135">Add the required message schema(s) to a BizTalk project, and then build and deploy the project, making the schema(s) available for use by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in processing the received interchange.</span></span>  

- <span data-ttu-id="f5b78-136">建立單向接收埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 從交易夥伴接收 EDIFACT 交換並產生通知。</span><span class="sxs-lookup"><span data-stu-id="f5b78-136">Create a one-way receive port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive the EDIFACT interchange from the trading partner and generate an acknowledgment.</span></span> <span data-ttu-id="f5b78-137">此接收位置繫結至 Fabrikam 用來放置要傳送到 Contoso 的 EDIFACT 交換的檔案資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-137">This receive location is tied to the file folder where Fabrikam drops the EDIFACT interchange to be sent to Contoso.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="f5b78-138">您可以使用雙向請求回應接收埠和位置來接收訊息，但是如果這樣做的話，就不能對接收位置使用 FILE 傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="f5b78-138">You can use a two-way solicit response receive port and location to receive the message, but if you do, you will not be able to use a FILE transport type for the receive location.</span></span>  

- <span data-ttu-id="f5b78-139">建立兩個傳送埠，一個會將 EDI 交換傳送到 Contoso 本機資料夾，而另一個會將技術與功能通知傳送到 Fabrikam 本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-139">Create one send port that sends the EDI interchange to a local Contoso folder and another that sends the technical and functional acknowledgements to a local Fabrikam folder.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="f5b78-140">和 X12 通知不同，功能與技術通知的訊息類型是一樣的。</span><span class="sxs-lookup"><span data-stu-id="f5b78-140">Unlike X12 acknowledgements, the message types for both the functional and technical acknowledgements are same.</span></span> <span data-ttu-id="f5b78-141">因此，使用 `BTS.MessageType` 內容屬性建立的傳送埠篩選條件會篩選這兩種通知，並將它們傳送到相同的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-141">Hence, the send port filter created using the `BTS.MessageType` context property filters both the acknowledgements and delivers them to the same folder.</span></span>  

- <span data-ttu-id="f5b78-142">為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。</span><span class="sxs-lookup"><span data-stu-id="f5b78-142">Create a party (trading partner) for both Fabrikam and Contoso.</span></span>  

- <span data-ttu-id="f5b78-143">分別為兩個交易夥伴建立商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="f5b78-143">Create a business profile each for both the trading partners.</span></span>  

- <span data-ttu-id="f5b78-144">為要接收的訊息和要傳送的通知設定 EDI 屬性，來在兩個設定檔之間建立協議。</span><span class="sxs-lookup"><span data-stu-id="f5b78-144">Create an agreement between the two profiles by configuring the EDI properties for the message to be received and the acknowledgment to be sent.</span></span>  

- <span data-ttu-id="f5b78-145">使用測試 EDIFACT 交換以測試逐步解說。</span><span class="sxs-lookup"><span data-stu-id="f5b78-145">Test the walkthrough using a test EDIFACT interchange.</span></span> <span data-ttu-id="f5b78-146">就本逐步解說而言，您可以將下列程式碼複製並貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="f5b78-146">For this walkthrough, you can copy-paste the following into a text file.</span></span> <span data-ttu-id="f5b78-147">此檔案的結構描述為 EFACT_D98A_APERAK.xsd。</span><span class="sxs-lookup"><span data-stu-id="f5b78-147">The schema for this file is EFACT_D98A_APERAK.xsd.</span></span>  

  ```  
  UNA:+,?*'  
  UNB+UNOB:1+7654321:ZZZ+1234567:ZZZ+353501:3023+UNB5'  
  UNG+INVOIC+UNG2.1:ZZZ+UNG3.1:ZZZ+060413:2314+UNG5+UN+D:98B'  
  UNH+UNH1+APERAK:D:98A:UN++13+UNH5.1+UNH6.1+UNH7.1'  
  BGM+1+C10601'  
  DTM+10'  
  FTX+AAA++C10701+C10801'  
  CNT+1:14'  
  RFF+AAA'  
  DTM+10'  
  NAD+AA+C08201+C05801+C08001+C05901'  
  CTA++C05601'  
  COM+C07601:AA'  
  ERC+C90101'  
  FTX+AAA++C10701+C10801'  
  RFF+AAA'  
  FTX+AAA++C10701+C10801'  
  UNT+15+UNH1'  
  UNE+1+UNG5'  
  UNZ+1+UNB5'  
  ```  

### <a name="configuring-the-walkthrough"></a><span data-ttu-id="f5b78-148">設定逐步解說</span><span class="sxs-lookup"><span data-stu-id="f5b78-148">Configuring the Walkthrough</span></span>  
 <span data-ttu-id="f5b78-149">本節說明設定逐步解說的程序。</span><span class="sxs-lookup"><span data-stu-id="f5b78-149">This section describes the procedures to configure the walkthrough.</span></span>  

##### <a name="to-deploy-the-message-schema"></a><span data-ttu-id="f5b78-150">若要部署訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="f5b78-150">To deploy the message schema</span></span>  

1. <span data-ttu-id="f5b78-151">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f5b78-151">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create or open a BizTalk project.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f5b78-152">本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)，</span><span class="sxs-lookup"><span data-stu-id="f5b78-152">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="f5b78-153">如果沒有，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="f5b78-153">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  

2. <span data-ttu-id="f5b78-154">以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下**現有項目**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-154">Right-click your project, point to **Add**, and then click **Existing Item**.</span></span> <span data-ttu-id="f5b78-155">移至結構描述的資料夾[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\EDIFACT\D98A，，然後按兩下您的結構描述 (**EFACT_D98A_APERAK.xsd**)。</span><span class="sxs-lookup"><span data-stu-id="f5b78-155">Move to the folder that your schema is in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\EDIFACT\D98A, and then double-click your schema (**EFACT_D98A_APERAK.xsd**).</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f5b78-156">如果您使用本主題所提供的範例測試訊息，您必須使用**EFACT_D98A_APERAK.xsd**結構描述。</span><span class="sxs-lookup"><span data-stu-id="f5b78-156">If you are using the sample test message provided in this topic, you must use the **EFACT_D98A_APERAK.xsd** schema.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f5b78-157">如果 EDI 結構描述尚未解壓縮至 \XSD_Schema\EDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** \XSD_Schema\EDI 資料夾結構描述解壓縮至預設資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="f5b78-157">If the EDI schemas have not been unzipped into the \XSD_Schema\EDI folders, execute the **MicrosoftEdiXSDTemplates.exe** file in the \XSD_Schema\EDI folder to unzip the schemas into the default folder.</span></span>  

3. <span data-ttu-id="f5b78-158">將組件金鑰檔案加入專案，然後建置並部署組件。</span><span class="sxs-lookup"><span data-stu-id="f5b78-158">Add the assembly key file to the project, and then build and deploy the assembly.</span></span>  

##### <a name="to-create-a-one-way-receive-port-for-fabrikam-to-receive-the-edi-interchange"></a><span data-ttu-id="f5b78-159">建立單向接收埠 (供 Fabrikam 使用) 以接收 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="f5b78-159">To create a one-way receive port (for Fabrikam) to receive the EDI interchange</span></span>  

1. <span data-ttu-id="f5b78-160">在 Windows 檔案總管中，建立本機資料夾，以接收交換。</span><span class="sxs-lookup"><span data-stu-id="f5b78-160">In Windows Explorer, create a local folder to receive the interchange.</span></span>  

2. <span data-ttu-id="f5b78-161">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-161">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Receive Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **One-way Receive Port**.</span></span>  

3. <span data-ttu-id="f5b78-162">將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="f5b78-162">Name the receive port, and then click **Receive Locations** in the console tree.</span></span>  

4. <span data-ttu-id="f5b78-163">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-163">Click **New**.</span></span>  

5. <span data-ttu-id="f5b78-164">接收位置命名，選取**檔案**for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-164">Name the receive location, select **FILE** for **Type**, and then click **Configure**.</span></span>  

6. <span data-ttu-id="f5b78-165">瀏覽至資料夾**接收資料夾**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f5b78-165">Browse to a folder for **Receive folder** text box.</span></span> <span data-ttu-id="f5b78-166">您已在此程序的步驟 1 中，建立此資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-166">You created this folder in step 1 of this procedure.</span></span> <span data-ttu-id="f5b78-167">輸入檔案遮罩，例如 **\*.edi**或是 **\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-167">Enter a file mask, such as **\*.edi** or **\*.txt**.</span></span>  

7. <span data-ttu-id="f5b78-168">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="f5b78-168">Click **OK**.</span></span>  

8. <span data-ttu-id="f5b78-169">針對**接收管線**，選取**EdiReceive**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-169">For **Receive pipeline**, select **EdiReceive**.</span></span>  

9. <span data-ttu-id="f5b78-170">按一下 [ **[確定]** 中**接收位置屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f5b78-170">Click **OK** in the **Receive Location Properties** dialog box.</span></span> <span data-ttu-id="f5b78-171">按一下 [ **[確定]** 中再次**接收埠屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f5b78-171">Click **OK** again in the **Receive Port Properties** dialog box.</span></span>  

10. <span data-ttu-id="f5b78-172">在主控台樹狀目錄中，按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-172">In the console tree, click **Receive Locations**.</span></span> <span data-ttu-id="f5b78-173">在 **接收位置**窗格中，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-173">In the **Receive Locations** pane, right-click your receive location, and then click **Enable**.</span></span>  

##### <a name="to-create-a-static-one-way-send-port-for-contoso-to-send-the-edi-interchange"></a><span data-ttu-id="f5b78-174">建立靜態單向傳送埠 (供 Contoso 使用) 以傳送 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="f5b78-174">To create a static one-way send port (for Contoso) to send the EDI interchange</span></span>  

1. <span data-ttu-id="f5b78-175">在 Windows 檔案總管中，建立本機資料夾，以便將測試交換傳送至此本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-175">In Windows Explorer, create a local folder to send the test interchange to.</span></span>  

2. <span data-ttu-id="f5b78-176">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-176">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static One-way Send Port**.</span></span>  

3. <span data-ttu-id="f5b78-177">在 [**傳送埠屬性**] 對話方塊中，傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b78-177">In the **Send Port Properties** dialog box, name the send port.</span></span>  

4. <span data-ttu-id="f5b78-178">在 **傳輸**區段中，選取**檔案**的**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-178">In the **Transport** section, select **FILE** for **Type**, and then click **Configure**.</span></span>  

5. <span data-ttu-id="f5b78-179">針對**目的地資料夾**，瀏覽至要接收交換的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-179">For **Destination folder**, browse to the folder to receive the interchange.</span></span> <span data-ttu-id="f5b78-180">您已在此程序的步驟 1 中，建立此資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-180">You created this folder in step 1 of this procedure.</span></span> <span data-ttu-id="f5b78-181">針對**檔案遮罩**，輸入交換格式，例如 **\*.edi**或是 **\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-181">For **File mask**, enter the interchange format, such as **\*.edi** or **\*.txt**.</span></span>  

6. <span data-ttu-id="f5b78-182">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="f5b78-182">Click **OK**.</span></span>  

7. <span data-ttu-id="f5b78-183">在 **傳送管線**，選取**EdiSend**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-183">In **Send pipeline**, select **EdiSend**.</span></span>  

8. <span data-ttu-id="f5b78-184">在主控台樹狀目錄中，選取**篩選器**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-184">In the console tree, select **Filters**.</span></span> <span data-ttu-id="f5b78-185">輸入訂閱 EDI 交換的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="f5b78-185">Enter a filter to subscribe to the EDI interchange.</span></span> <span data-ttu-id="f5b78-186">例如，對於**屬性**，輸入**BTS。MessageType**; 對於**運算子**，輸入**==**; 及針對**值**輸入交換的結構描述`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006#EFACT_D98A_APERAK`。</span><span class="sxs-lookup"><span data-stu-id="f5b78-186">For example, for **Property**, enter **BTS.MessageType**; for **Operator**, enter **==**; and for **Value** enter the schema for the interchange, `http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006#EFACT_D98A_APERAK`.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f5b78-187">上述篩選條件設定可以確保會將交換 (而非通知) 傳送到與此傳送埠相關的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-187">The above filter setting ensures that interchanges, not acknowledgments, will be sent to the folder associated with this send port.</span></span>  

9. <span data-ttu-id="f5b78-188">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="f5b78-188">Click **OK**.</span></span>  

10. <span data-ttu-id="f5b78-189">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-189">In the console tree, click **Send Ports**.</span></span> <span data-ttu-id="f5b78-190">在 **傳送埠**窗格中，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-190">In the **Send Ports** pane, right-click your send port, and then click **Start**.</span></span>  

##### <a name="to-create-a-static-one-way-send-port-to-send-the-acknowledgments"></a><span data-ttu-id="f5b78-191">若要建立靜態單向傳送埠以傳送通知</span><span class="sxs-lookup"><span data-stu-id="f5b78-191">To create a static one-way send port to send the acknowledgments</span></span>  

1. <span data-ttu-id="f5b78-192">在 Windows 檔案總管中，建立本機資料夾，以便傳送技術與功能通知至此本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-192">In Windows Explorer, create a local folder to send the technical and functional acknowledgments to.</span></span>  

2. <span data-ttu-id="f5b78-193">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-193">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static One-way Send Port**.</span></span>  

3. <span data-ttu-id="f5b78-194">在 [**傳送埠屬性**] 對話方塊中，傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b78-194">In the **Send Port Properties** dialog box, name the send port.</span></span>  

4. <span data-ttu-id="f5b78-195">在 **傳輸**區段中，選取**檔案**的**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-195">In the **Transport** section, select **FILE** for **Type**, and then click **Configure**.</span></span>  

5. <span data-ttu-id="f5b78-196">針對**目的地資料夾**，瀏覽至要接收兩個通知的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-196">For **Destination folder**, browse to a folder to receive the two acknowledgments.</span></span> <span data-ttu-id="f5b78-197">您已在此程序的步驟 1 中，建立此資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-197">You created this folder in step 1 of this procedure.</span></span> <span data-ttu-id="f5b78-198">針對**檔案遮罩**，輸入交換格式，例如 **\*.edi**或是 **\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-198">For **File mask**, enter the interchange format, such as **\*.edi** or **\*.txt**.</span></span>  

6. <span data-ttu-id="f5b78-199">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="f5b78-199">Click **OK**.</span></span>  

7. <span data-ttu-id="f5b78-200">在 **傳送管線**，選取**EdiSend**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-200">In **Send pipeline**, select **EdiSend**.</span></span>  

8. <span data-ttu-id="f5b78-201">在主控台樹狀目錄中，選取**篩選器**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-201">In the console tree, select **Filters**.</span></span> <span data-ttu-id="f5b78-202">輸入訂閱通知的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="f5b78-202">Enter a filter to subscribe to acknowledgments.</span></span> <span data-ttu-id="f5b78-203">例如，對於**屬性**，輸入**BTS。MessageType**; 對於**運算子**，輸入**==**; 以及**值**通知中，輸入的結構描述`http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`。</span><span class="sxs-lookup"><span data-stu-id="f5b78-203">For example, for **Property**, enter **BTS.MessageType**; for **Operator**, enter **==**; and for **Value** enter the schema for the acknowledgment, `http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`.</span></span>  

9. <span data-ttu-id="f5b78-204">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="f5b78-204">Click **OK**.</span></span>  

10. <span data-ttu-id="f5b78-205">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-205">In the console tree, click **Send Ports**.</span></span> <span data-ttu-id="f5b78-206">在 **傳送埠**窗格中，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-206">In the **Send Ports** pane, right-click your send port, and then click **Start**.</span></span>  

##### <a name="to-create-a-party-and-a-business-profile-for-fabrikam"></a><span data-ttu-id="f5b78-207">若要為 Fabrikam 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="f5b78-207">To create a party and a business profile for Fabrikam</span></span>  

1. <span data-ttu-id="f5b78-208">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-208">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  

2. <span data-ttu-id="f5b78-209">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-209">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f5b78-210">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f5b78-210">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="f5b78-211">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="f5b78-211">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="f5b78-212">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="f5b78-212">However, for this walkthrough, you can leave this check box selected.</span></span>  

3. <span data-ttu-id="f5b78-213">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-213">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  

4. <span data-ttu-id="f5b78-214">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**fabrikam_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f5b78-214">In the **Profile Properties** dialog box, on the **General** page, enter **Fabrikam_Profile** in the **Name** text box.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f5b78-215">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="f5b78-215">When you create a party, a profile is also created.</span></span> <span data-ttu-id="f5b78-216">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="f5b78-216">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="f5b78-217">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-217">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="f5b78-218">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b78-218">In the **General** page, specify a name for the profile.</span></span>  

##### <a name="to-create-a-party-and-a-business-profile-for-contoso"></a><span data-ttu-id="f5b78-219">若要為 Contoso 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="f5b78-219">To create a party and a business profile for Contoso</span></span>  

1. <span data-ttu-id="f5b78-220">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-220">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  

2. <span data-ttu-id="f5b78-221">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-221">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f5b78-222">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f5b78-222">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="f5b78-223">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="f5b78-223">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="f5b78-224">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="f5b78-224">However, for this walkthrough, you can leave this check box selected.</span></span>  

3. <span data-ttu-id="f5b78-225">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-225">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  

4. <span data-ttu-id="f5b78-226">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**contoso_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f5b78-226">In the **Profile Properties** dialog box, on the **General** page, enter **Contoso_Profile** in the **Name** text box.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f5b78-227">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="f5b78-227">When you create a party, a profile is also created.</span></span> <span data-ttu-id="f5b78-228">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="f5b78-228">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="f5b78-229">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-229">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="f5b78-230">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b78-230">In the **General** page, specify a name for the profile.</span></span>  

##### <a name="to-create-an-agreement-between-the-two-business-profiles"></a><span data-ttu-id="f5b78-231">在兩個商務設定檔之間建立協議</span><span class="sxs-lookup"><span data-stu-id="f5b78-231">To create an agreement between the two business profiles</span></span>  

1. <span data-ttu-id="f5b78-232">以滑鼠右鍵按一下 **[fabrikam_profile]**，指向**新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-232">Right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.</span></span>  

2. <span data-ttu-id="f5b78-233">在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b78-233">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  

3. <span data-ttu-id="f5b78-234">從**通訊協定**下拉式清單中，選取**EDIFACT**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-234">From the **Protocol** drop-down list, select **EDIFACT**.</span></span>  

4. <span data-ttu-id="f5b78-235">在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Contoso**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-235">In the **Second Partner** section, from the **Name** drop-down list, select **Contoso**.</span></span>  

5. <span data-ttu-id="f5b78-236">在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-236">In the **Second Partner** section, from the **Profile** drop-down list, select **Contoso_Profile**.</span></span>  

    <span data-ttu-id="f5b78-237">您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向協議，而每個單向協議各代表一筆完整的訊息交易 (包含訊息傳輸與通知傳輸)。</span><span class="sxs-lookup"><span data-stu-id="f5b78-237">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way agreement and each one-way agreement represents one complete transaction of message (including message transfer and acknowledgement transfer).</span></span>  

6. <span data-ttu-id="f5b78-238">在 **一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，，然後選取 **儲存訊息內容 reporting**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-238">In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**, and then select **Store message payload for reporting**.</span></span>  

7. <span data-ttu-id="f5b78-239">在上執行下列工作**Fabrikam-> Contoso**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f5b78-239">Perform the following tasks on the **Fabrikam->Contoso** tab.</span></span>  

   1. <span data-ttu-id="f5b78-240">上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**UNB2.1**， **UNB2.2**， **UNB3.1**，以及**UNB3.2**) 對應到您的測試訊息中那些標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="f5b78-240">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**UNB2.1**, **UNB2.2**, **UNB3.1**, and **UNB3.2**) that correspond to the values for those header fields in your test message.</span></span>  

      > [!NOTE]
      >  <span data-ttu-id="f5b78-241">對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。</span><span class="sxs-lookup"><span data-stu-id="f5b78-241">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires the qualifier and identifier fields for sender and receiver in order to perform agreement resolution.</span></span> <span data-ttu-id="f5b78-242">它會比對的值**UNB2.1**， **UNB2.2**， **UNB3.1**，以及**UNB3.2**交換標頭中的屬性協議。</span><span class="sxs-lookup"><span data-stu-id="f5b78-242">It will match the values of **UNB2.1**, **UNB2.2**, **UNB3.1**, and **UNB3.2** in the interchange header with those in the properties of an agreement.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f5b78-243"> 會比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 也解析協議。</span><span class="sxs-lookup"><span data-stu-id="f5b78-243"> will also resolve the agreement by matching the sender qualifier and identifier (without the receiver qualifier and identifier).</span></span> <span data-ttu-id="f5b78-244">若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。</span><span class="sxs-lookup"><span data-stu-id="f5b78-244">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement, it will use the fallback agreement properties.</span></span>  
      > 
      > [!NOTE]
      >  <span data-ttu-id="f5b78-245">如果您使用的稍早在本主題，做為測試訊息中提供的範例訊息，設定**UNB2.1**要**7654321**， **UNB2.2**至**ZZZ – 使用者相互定義**， **UNB3.1**要**1234567**，和**UNB3.2**至**ZZZ – 使用者相互定義**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-245">If you are using the sample message provided earlier in this topic as your test message, set **UNB2.1** to **7654321**, **UNB2.2** to **ZZZ – Mutually Defined**, **UNB3.1** to **1234567**, and **UNB3.2** to **ZZZ – Mutually Defined**.</span></span>  

   2. <span data-ttu-id="f5b78-246">在上**通知**頁面**交換設定** 區段中，核取**訊息回條 (CONTRL 預期)** 和**通知 (預期有 CONTRL)**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-246">On the **Acknowledgements** page under the **Interchange Settings** section, check **Receipt of message (CONTRL) expected** and **Acknowledgement (CONTRL) expected**.</span></span>  

   3. <span data-ttu-id="f5b78-247">上**信封**下方的頁面上**交換設定** 區段中，核取**套用 UNA 區段 （字串服務建議）** 和**套用 UNG 區段 （功能群組標頭）**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-247">On the **Envelopes** page under the **Interchange Settings** section, check **Apply UNA segment (String service advice)** and **Apply UNG segments (Functional group header)**.</span></span>  

   4. <span data-ttu-id="f5b78-248">上**驗證**下方的頁面上**交換設定**區段中，確定**交換控制編號 (UNB5)** 選項未核取。</span><span class="sxs-lookup"><span data-stu-id="f5b78-248">On the **Validation** page under the **Interchange Settings** section, make sure **Interchange Control Number (UNB5)** option is unchecked.</span></span>  

      > [!NOTE]
      >  <span data-ttu-id="f5b78-249">清除**交換控制編號 (UNB5)** 屬性可讓您接收相同訊息的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="f5b78-249">Clearing the **Interchange Control Number (UNB5)** property enables you to receive multiple instances of the same message.</span></span>  

   5. <span data-ttu-id="f5b78-250">上**字元集和分隔符號**下方的頁面上**交換設定**區段中，選取**CR LF**選項**UNA6 尾碼**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-250">On the **Charset and Separators** page under the **Interchange Settings** section, select the **CR LF** option for **UNA6 Suffix**.</span></span>  

   6. <span data-ttu-id="f5b78-251">在上**本機主機設定**下方的頁面上**交換設定**區段中，清除**通知的路由設定為傳送管線在要求-回應接收埠**選項。</span><span class="sxs-lookup"><span data-stu-id="f5b78-251">On the **Local Host Settings** page under the **Interchange Settings** section, clear the **Route ACK to send pipeline on request-response receive port** option.</span></span>  

      > [!NOTE]
      >  <span data-ttu-id="f5b78-252">如果您使用雙向接收埠以接收交換並傳回通知，您會檢查**通知的路由設定為傳送管線在要求-回應接收埠**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-252">If you were using a two-way receive port to receive the interchange and return the acknowledgment, you would check **Route ACK to send pipeline on request-response receive port**.</span></span>  

   7. <span data-ttu-id="f5b78-253">上**傳送埠**下方的頁面上**交換設定**區段中，將會接收來自 Fabrikam 交換的傳送埠和接收的傳送埠建立關聯從 Contoso 的通知。</span><span class="sxs-lookup"><span data-stu-id="f5b78-253">On the **Send Ports** page under the **Interchange Settings** section, associate the send ports that will be receiving the interchange from Fabrikam and the send ports that will be receiving the acknowledgements from Contoso.</span></span> <span data-ttu-id="f5b78-254">在 **傳送埠**格線下方**名稱** 欄中，按一下空白儲存格，並從下拉式清單中，選取 建立從 Fabrikam 接收 EDI 交換的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f5b78-254">In the **Send ports** grid, under the **Name** column, click an empty cell, and from the drop-down list, select the send port created for receiving the EDI interchange from Fabrikam.</span></span> <span data-ttu-id="f5b78-255">針對為了接收技術與功能通知而建立的傳送埠，重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="f5b78-255">Repeat the step for the send port created for receiving the technical and functional acknowledgements.</span></span>  

   8. <span data-ttu-id="f5b78-256">上**驗證**下方的頁面上**交易集設定**區段中，保留**EDI 類型驗證**核取，並檢查**擴充類型驗證**.</span><span class="sxs-lookup"><span data-stu-id="f5b78-256">On the **Validation** page under the **Transaction Set Settings** section, leave **EDI type Validation** checked and check **Extended Type Validation**.</span></span>  

   9. <span data-ttu-id="f5b78-257">如果您使用其中一個隨附之標準結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請在**本機主機設定**頁面下**交易集設定**區段中，選取要用來將結構描述的命名空間處理內送交換。</span><span class="sxs-lookup"><span data-stu-id="f5b78-257">If you are using one of the standard schemas shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], on the **Local Host Settings** page under the **Transaction Set Settings** section, select the namespace for the schema to be used to process the incoming interchange.</span></span> <span data-ttu-id="f5b78-258">如果使用自訂的結構描述，請輸入中的值**自訂目標命名空間**方格中，以便[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以判斷命名空間使用群組和交易集標頭值。</span><span class="sxs-lookup"><span data-stu-id="f5b78-258">If using a custom schema, enter values in the **Customize Target namespace** grid, so that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can determine the namespace using group and transaction set header values.</span></span>  

   10. <span data-ttu-id="f5b78-259">在上**信封**下方的頁面上**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。</span><span class="sxs-lookup"><span data-stu-id="f5b78-259">On the **Envelopes** page under the **Transaction Set Settings** section, enter values for all columns in the first line of the grid.</span></span>  


       |          <span data-ttu-id="f5b78-260">使用</span><span class="sxs-lookup"><span data-stu-id="f5b78-260">Use this</span></span>           |                                <span data-ttu-id="f5b78-261">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="f5b78-261">To do this</span></span>                                 |
       |-----------------------------|---------------------------------------------------------------------------|
       |         <span data-ttu-id="f5b78-262">**預設值**</span><span class="sxs-lookup"><span data-stu-id="f5b78-262">**Default**</span></span>         |                            <span data-ttu-id="f5b78-263">選取 **預設**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-263">Select **Default**.</span></span>                            |
       | <span data-ttu-id="f5b78-264">**針對訊息類型 UNH2.1**</span><span class="sxs-lookup"><span data-stu-id="f5b78-264">**For message type UNH2.1**</span></span> |         <span data-ttu-id="f5b78-265">選取測試訊息，訊息類型**APERAK**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-265">Select the message type of your test message, **APERAK**.</span></span>         |
       |         <span data-ttu-id="f5b78-266">**UNH2.2**</span><span class="sxs-lookup"><span data-stu-id="f5b78-266">**UNH2.2**</span></span>          |                       <span data-ttu-id="f5b78-267">輸入 EDI 版本， **D**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-267">Enter the EDI version, **D**.</span></span>                       |
       |         <span data-ttu-id="f5b78-268">**UNH2.3**</span><span class="sxs-lookup"><span data-stu-id="f5b78-268">**UNH2.3**</span></span>          |                    <span data-ttu-id="f5b78-269">輸入版本號碼， **98A**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-269">Enter the release number, **98A**.</span></span>                     |
       |         <span data-ttu-id="f5b78-270">**UNH2.5**</span><span class="sxs-lookup"><span data-stu-id="f5b78-270">**UNH2.5**</span></span>          |                         <span data-ttu-id="f5b78-271">您可以讓此處保持空白。</span><span class="sxs-lookup"><span data-stu-id="f5b78-271">You can leave this blank.</span></span>                         |
       |    <span data-ttu-id="f5b78-272">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="f5b78-272">**Target namespace**</span></span>     |          <span data-ttu-id="f5b78-273">選取  **<http://schemas.microsoft.com/Edi/Edifact>**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-273">Select **<http://schemas.microsoft.com/Edi/Edifact>**.</span></span>           |
       |          <span data-ttu-id="f5b78-274">**UNG1**</span><span class="sxs-lookup"><span data-stu-id="f5b78-274">**UNG1**</span></span>           |               <span data-ttu-id="f5b78-275">指定功能群組識別碼**INVOIC**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-275">Specify the functional group ID, **INVOIC**.</span></span>                |
       |         <span data-ttu-id="f5b78-276">**UNG2.1**</span><span class="sxs-lookup"><span data-stu-id="f5b78-276">**UNG2.1**</span></span>          |         <span data-ttu-id="f5b78-277">輸入應用程式傳送者識別的值。</span><span class="sxs-lookup"><span data-stu-id="f5b78-277">Enter a value for the application sender identification.</span></span>          |
       |         <span data-ttu-id="f5b78-278">**UNG2.1**</span><span class="sxs-lookup"><span data-stu-id="f5b78-278">**UNG2.1**</span></span>          | <span data-ttu-id="f5b78-279">輸入值，應用程式傳送者代碼辨識符號，如**ZZZ**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-279">Enter a value for the application sender code qualifier, such as **ZZZ**.</span></span> |
       |         <span data-ttu-id="f5b78-280">**UNG3.1**</span><span class="sxs-lookup"><span data-stu-id="f5b78-280">**UNG3.1**</span></span>          |          <span data-ttu-id="f5b78-281">輸入應用程式接收者識別的值。</span><span class="sxs-lookup"><span data-stu-id="f5b78-281">Enter a value for application receiver identification.</span></span>           |
       |         <span data-ttu-id="f5b78-282">**UNG3.2**</span><span class="sxs-lookup"><span data-stu-id="f5b78-282">**UNG3.2**</span></span>          |  <span data-ttu-id="f5b78-283">值，輸入應用程式接收者代碼辨識符號，例如**ZZZ**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-283">Enter a value for application receiver code qualifier, such as **ZZZ**.</span></span>  |
       |          <span data-ttu-id="f5b78-284">**UNG6**</span><span class="sxs-lookup"><span data-stu-id="f5b78-284">**UNG6**</span></span>           |        <span data-ttu-id="f5b78-285">輸入控管單位的值。</span><span class="sxs-lookup"><span data-stu-id="f5b78-285">Enter a value for the controlling agency.</span></span> <span data-ttu-id="f5b78-286">範例中，**取消**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-286">Example, **UN**.</span></span>         |
       |         <span data-ttu-id="f5b78-287">**UNG7.1**</span><span class="sxs-lookup"><span data-stu-id="f5b78-287">**UNG7.1**</span></span>          |          <span data-ttu-id="f5b78-288">輸入訊息類型版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f5b78-288">Enter the message type version number.</span></span> <span data-ttu-id="f5b78-289">範例中， **D**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-289">Example, **D**.</span></span>           |
       |         <span data-ttu-id="f5b78-290">**UNG7.2**</span><span class="sxs-lookup"><span data-stu-id="f5b78-290">**UNG7.2**</span></span>          |         <span data-ttu-id="f5b78-291">輸入訊息類型版次號碼。</span><span class="sxs-lookup"><span data-stu-id="f5b78-291">Enter the message type release number.</span></span> <span data-ttu-id="f5b78-292">範例中， **98A**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-292">Example, **98A**.</span></span>          |
       |         <span data-ttu-id="f5b78-293">**UNG7.3**</span><span class="sxs-lookup"><span data-stu-id="f5b78-293">**UNG7.3**</span></span>          |                         <span data-ttu-id="f5b78-294">您可以讓此處保持空白。</span><span class="sxs-lookup"><span data-stu-id="f5b78-294">You can leave this blank.</span></span>                         |
       |          <span data-ttu-id="f5b78-295">**UNG8**</span><span class="sxs-lookup"><span data-stu-id="f5b78-295">**UNG8**</span></span>           |                         <span data-ttu-id="f5b78-296">您可以讓此處保持空白。</span><span class="sxs-lookup"><span data-stu-id="f5b78-296">You can leave this blank.</span></span>                         |


8. <span data-ttu-id="f5b78-297">在上執行下列工作**Contoso-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f5b78-297">Perform the following tasks on the **Contoso->Fabrikam** tab.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f5b78-298">在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。</span><span class="sxs-lookup"><span data-stu-id="f5b78-298">In this walkthrough, we specify the required value in the tab so that an agreement can be successfully created.</span></span> <span data-ttu-id="f5b78-299">若要成功建立協議，兩個單向協議索引標籤必須已定義的值**UNG2.1**， **UNG2.2**， **UNG3.1**，和**UNG3.2**.</span><span class="sxs-lookup"><span data-stu-id="f5b78-299">To successfully create an agreement, both one-way agreement tabs must have values defined for **UNG2.1**, **UNG2.2**, **UNG3.1**, and **UNG3.2**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f5b78-300">雖然通知屬於同一個訊息交易的一部分，在中設定通知的產生方式的相關的屬性**Contoso-> Fabrikam**  索引標籤。這是必要的因為通知內容屬性傳送者和接收者限定詞設定為您在指定的值相反**Contoso-> Fabrikam**  索引標籤。比方說，如果傳送者和接收者識別碼設為 7654321 與 1234567 中的**Fabrikam-> Contoso**  索引標籤、 寄件者與接收者內容屬性會在通知中設為 1234567 與 7654321。</span><span class="sxs-lookup"><span data-stu-id="f5b78-300">Even though the acknowledgement is part of the same message transaction, the properties related to how the acknowledgement should be generated are configured in the **Contoso->Fabrikam** tab. This is required because the acknowledgement context properties for the sender and receiver qualifiers are set to the opposite of the values you specified in the **Contoso->Fabrikam** tab. For example, if sender and receiver identifiers are set to 7654321 and 1234567 in the **Fabrikam->Contoso** tab, the sender and receiver context properties will be set to 1234567 and 7654321 in the acknowledgement.</span></span> <span data-ttu-id="f5b78-301">另外那一個單向協議索引標籤通常也會分別將傳送者與接收者識別碼設為 1234567 與 7654321。</span><span class="sxs-lookup"><span data-stu-id="f5b78-301">Typically, the other one-way agreement tab would also have the sender and receiver identifiers set to 1234567 and 7654321 respectively.</span></span> <span data-ttu-id="f5b78-302">因此，通知訊息會解析成該協議，並將挑選屬性設定。</span><span class="sxs-lookup"><span data-stu-id="f5b78-302">Hence, the acknowledgement message would resolve to that agreement and the properties setting will be picked.</span></span> <span data-ttu-id="f5b78-303">因此，如果您想要讓通知使用不同的項目分隔符號，或如果您想要讓通知使用 CR LF，指定中的屬性**Contoso-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f5b78-303">So, if you want to have the acknowledgement to use different element separators or if you want to have the acknowledgement to use CR LF, specify the properties in the **Contoso->Fabrikam** tab.</span></span>  
   >   
   >  <span data-ttu-id="f5b78-304">在概念上，將會從傳送者與接收者辨識符號與在通知的內容屬性中所設定值相同的任一個單向協議索引標籤中挑選通知的屬性。</span><span class="sxs-lookup"><span data-stu-id="f5b78-304">Conceptually, the properties for the acknowledgement will be picked from any one-way agreement tab that has the same sender and receiver qualifiers as set in the acknowledgement’s context properties.</span></span> <span data-ttu-id="f5b78-305">但為便於實際應用，通常會在您所建立由交換解析而成之協議的其他單向協議索引標籤中設定此屬性。</span><span class="sxs-lookup"><span data-stu-id="f5b78-305">However, for ease of practical use, you would typically set this in the other one-way agreement tab of the agreement that you created to which the interchange would have resolved.</span></span>  

   1.  <span data-ttu-id="f5b78-306">上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**UNG2.1**， **UNG2.2**， **UNG3.1**，以及**UNG3.2**) 對應到您的測試訊息中那些標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="f5b78-306">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**UNG2.1**, **UNG2.2**, **UNG3.1**, and **UNG3.2**) that correspond to the values for those header fields in your test message.</span></span>  

       > [!NOTE]
       >  <span data-ttu-id="f5b78-307">如果您使用的稍早在本主題，做為測試訊息中提供的範例訊息，設定**UNB2.1**要**1234567**， **UNB2.2**至**ZZZ – 使用者相互定義**， **UNB3.1**要**7654321**，和**UNB3.2**至**ZZZ – 使用者相互定義**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-307">If you are using the sample message provided earlier in this topic as your test message, set **UNB2.1** to **1234567**, **UNB2.2** to **ZZZ – Mutually Defined**, **UNB3.1** to **7654321**, and **UNB3.2** to **ZZZ – Mutually Defined**.</span></span>  

9. <span data-ttu-id="f5b78-308">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="f5b78-308">Click **Apply**.</span></span>  

10. <span data-ttu-id="f5b78-309">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="f5b78-309">Click **OK**.</span></span> <span data-ttu-id="f5b78-310">中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="f5b78-310">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="f5b78-311">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="f5b78-311">The newly added agreement is enabled by default.</span></span>  

### <a name="testing-the-walkthrough"></a><span data-ttu-id="f5b78-312">測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="f5b78-312">Testing the Walkthrough</span></span>  
 <span data-ttu-id="f5b78-313">本節提供關於如何測試逐步解說的資訊。</span><span class="sxs-lookup"><span data-stu-id="f5b78-313">This section provides information on how to test the walkthrough.</span></span>  

##### <a name="to-test-the-walkthrough"></a><span data-ttu-id="f5b78-314">若要測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="f5b78-314">To test the walkthrough</span></span>  

1. <span data-ttu-id="f5b78-315">在 Windows 檔案總管中，將測試 EDI 交換置放到本機接收資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f5b78-315">In Windows Explorer, drop the test EDI interchange into your local receive folder.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f5b78-316">對於測試訊息，您可以使用本主題先前提供的範例訊息。</span><span class="sxs-lookup"><span data-stu-id="f5b78-316">For a test message, you can use the sample message provided earlier in this topic.</span></span> <span data-ttu-id="f5b78-317">將訊息複製到文字檔，並以 .txt 副檔名儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="f5b78-317">Copy the message to a text file and save the file with a .txt extension.</span></span> <span data-ttu-id="f5b78-318">如果您使用此訊息，則必須部署 EFACT_D98A_APERAK.xsd 結構描述。</span><span class="sxs-lookup"><span data-stu-id="f5b78-318">If you use this message, you must have deployed the EFACT_D98A_APERAK.xsd schema.</span></span> <span data-ttu-id="f5b78-319">結構描述使用，請執行**MicrosoftEdiXSDTemplates.exe**檔案 （位於 \XSD_Schema\EDI 資料夾中），將結構描述解壓縮至預設資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5b78-319">The schema is available by executing the **MicrosoftEdiXSDTemplates.exe** file (in the \XSD_Schema\EDI folder) to unzip the schemas into the default folder.</span></span> <span data-ttu-id="f5b78-320">然後，[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\EDIFACT\D98A 下就會出現 EFACT_D98A_APERAK.xsd 結構描述。</span><span class="sxs-lookup"><span data-stu-id="f5b78-320">The EFACT_D98A_APERAK.xsd schema is then available under [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\EDIFACT\D98A.</span></span>  

2. <span data-ttu-id="f5b78-321">開啟與交換傳送埠相關聯的資料夾，並確認其中有包含 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="f5b78-321">Open the folder that you associated with the send port for interchanges, and verify that it contains the EDI interchange.</span></span>  

3. <span data-ttu-id="f5b78-322">開啟與通知傳送埠相關聯的資料夾，並確認其中包含技術與功能通知。</span><span class="sxs-lookup"><span data-stu-id="f5b78-322">Open the folder that you associated with the send port for the acknowledgements, and verify that it contains the technical and functional acknowledgements.</span></span>  

## <a name="see-also"></a><span data-ttu-id="f5b78-323">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5b78-323">See Also</span></span>  
 [<span data-ttu-id="f5b78-324">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="f5b78-324">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)