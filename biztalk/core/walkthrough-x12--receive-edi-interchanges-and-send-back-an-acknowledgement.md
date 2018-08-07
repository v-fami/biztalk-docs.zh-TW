---
title: 逐步解說 (X12)： 接收 EDI 交換並傳回通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 25d2b5f3-6bd1-413c-aace-e4dd71f80403
caps.latest.revision: 45
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2951f0aa07875adcbdd7d4effbf1c4663435dc6a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003071"
---
# <a name="walkthrough-x12-receiving-edi-interchanges-and-sending-back-an-acknowledgement"></a><span data-ttu-id="7d560-102">逐步解說 (X12)：接收 EDI 交換並傳回通知</span><span class="sxs-lookup"><span data-stu-id="7d560-102">Walkthrough (X12): Receiving EDI Interchanges and Sending Back an Acknowledgement</span></span>
<span data-ttu-id="7d560-103">本逐步解說提供一組逐步執行的程序，來使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 建立可接收 EDI 交換的解決方案。</span><span class="sxs-lookup"><span data-stu-id="7d560-103">This walkthrough provides a set of step-by-step procedures that creates a solution for receiving EDI interchanges using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="7d560-104">在此解決方案中，EDI 交換是從交易夥伴 Fabrikam 傳送給另一個交易夥伴 Contoso。</span><span class="sxs-lookup"><span data-stu-id="7d560-104">In this solution, an EDI interchange is sent from a trading partner, Fabrikam, to another trading partner, Contoso.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="7d560-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="7d560-105">Prerequisites</span></span>  
 <span data-ttu-id="7d560-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="7d560-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  

## <a name="how-the-solution-receives-edi-interchanges"></a><span data-ttu-id="7d560-107">解決方案如何接收 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="7d560-107">How the Solution Receives EDI Interchanges</span></span>  
 <span data-ttu-id="7d560-108">解決方案會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="7d560-108">The solution will do the following:</span></span>  

> [!NOTE]
>  <span data-ttu-id="7d560-109">這份清單中的事件可能不會按照所示的順序發生。</span><span class="sxs-lookup"><span data-stu-id="7d560-109">The events in this list may not occur in the order shown.</span></span>  

1.  <span data-ttu-id="7d560-110">從交易夥伴 Fabrikam 接收一般檔案的 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="7d560-110">Receive a flat-file EDI interchange from the trading partner Fabrikam.</span></span>  

2.  <span data-ttu-id="7d560-111">驗證 EDI 交換 (根據其結構描述)、將訊息解譯成 XML，並將訊息 XML 放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="7d560-111">Validate the EDI interchange against its schema, disassemble the message into XML, and drop the message XML into the MessageBox.</span></span>  

3.  <span data-ttu-id="7d560-112">產生 997 通知給接收的 EDI 交換，並將其放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="7d560-112">Generate a 997 acknowledgment to the received EDI interchange, and drop it in the MessageBox.</span></span>  

4.  <span data-ttu-id="7d560-113">產生 TA1 通知給接收 EDI 交換，並將其放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="7d560-113">Generate a TA1 acknowledgment to the received EDI interchange, and drop it in the MessageBox.</span></span>  

5.  <span data-ttu-id="7d560-114">透過單向傳送埠拾取訊息 XML，並組合訊息 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="7d560-114">Pick up the message XML by a one-way send port, and assemble the message EDI interchange.</span></span>  

6.  <span data-ttu-id="7d560-115">傳送 EDI 交換給 Contoso。</span><span class="sxs-lookup"><span data-stu-id="7d560-115">Send the EDI interchange to Contoso.</span></span>  

7.  <span data-ttu-id="7d560-116">透過單向傳送埠收取 997 XML，並組合 997 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="7d560-116">Pick up the 997 XML by a one-way send port, and assemble the 997 EDI interchange.</span></span>  

8.  <span data-ttu-id="7d560-117">傳送 997 交換給 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="7d560-117">Send the 997 interchange to Fabrikam.</span></span>  

9. <span data-ttu-id="7d560-118">透過單向傳送埠拾取 TA1 XML，並組合 TA1 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="7d560-118">Pick up the TA1 XML by a one-way send port, and assemble the TA1 EDI interchange.</span></span>  

10. <span data-ttu-id="7d560-119">傳送 TA1 交換給 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="7d560-119">Send the TA1 interchange to Fabrikam.</span></span>  

## <a name="the-functionality-in-this-solution"></a><span data-ttu-id="7d560-120">此解決方案中的功能</span><span class="sxs-lookup"><span data-stu-id="7d560-120">The Functionality in this Solution</span></span>  
 <span data-ttu-id="7d560-121">為了完成這個逐步解說，將會啟用下列功能：</span><span class="sxs-lookup"><span data-stu-id="7d560-121">For the purposes of this walkthrough, the following functionality will be enabled:</span></span>  

- <span data-ttu-id="7d560-122">這個解決方案是專為使用 X12 編碼 (而非 EDIFACT 編碼) 的交換所設計。</span><span class="sxs-lookup"><span data-stu-id="7d560-122">The solution is designed for interchanges using X12 encoding, not EDIFACT encoding.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="7d560-123">針對 HIPAA 使用的組態與針對 X12 編碼使用的組態近乎相同。</span><span class="sxs-lookup"><span data-stu-id="7d560-123">The configuration used for HIPAA closely parallel to that used for X12 encoding.</span></span> <span data-ttu-id="7d560-124">如需有關如何針對 EDIFACT 建立相似之解決方案的指示，請參閱 <<c0> [ 逐步解說 (EDIFACT): 接收 EDI 交換和傳送，將通知傳回](../core/walkthrough-edifact--receive-edi-interchanges-and-send-an-acknowledgement.md)。</span><span class="sxs-lookup"><span data-stu-id="7d560-124">For instructions on how to create a similar solution for EDIFACT, see [Walkthrough (EDIFACT): Receiving EDI Interchanges and Sending Back an Acknowledgement](../core/walkthrough-edifact--receive-edi-interchanges-and-send-an-acknowledgement.md).</span></span>  

- <span data-ttu-id="7d560-125">將針對內送交換執行 EDI 類型和擴充驗證。</span><span class="sxs-lookup"><span data-stu-id="7d560-125">EDI type and extended validation will be performed on the incoming interchange.</span></span>  

- <span data-ttu-id="7d560-126">將會產生技術和功能通知，以傳回給交換傳送者。</span><span class="sxs-lookup"><span data-stu-id="7d560-126">Technical and functional acknowledgments will be generated for returning to the sender of the interchange.</span></span>  

- <span data-ttu-id="7d560-127">這個解決方案使用單向接收位置與 FILE 傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="7d560-127">The solution uses a one-way receive location with a FILE transport type.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="7d560-128">您可以使用雙向請求回應接收埠和位置來接收訊息，但是如果這樣做的話，就不能對接收位置使用 FILE 傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="7d560-128">You can use a two-way solicit response receive port and location to receive the message, but if you do so, you will not be able to use a FILE transport type for the receive location.</span></span> <span data-ttu-id="7d560-129">如需詳細資訊，請參閱 <<c0> [ 設定連接埠來接收 EDI 訊息和通知](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md)。</span><span class="sxs-lookup"><span data-stu-id="7d560-129">For more information, see [Configuring a Port to Receive EDI Messages and Acknowledgments](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md).</span></span>  

- <span data-ttu-id="7d560-130">EDI 報告將會啟用，並會儲存交易集，以從交換狀態報告進行檢視。</span><span class="sxs-lookup"><span data-stu-id="7d560-130">EDI reporting will be enabled, and transaction sets will be saved for viewing from the interchange status report.</span></span>  

- <span data-ttu-id="7d560-131">為了測試目的，解決方案會使用三個傳送埠，將 EDI 交換和建立的通知傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-131">For testing purposes, the solution uses three send ports to send the EDI interchange and the ACKs created to local folders.</span></span>  

  <span data-ttu-id="7d560-132">下圖顯示這個解決方案的架構：</span><span class="sxs-lookup"><span data-stu-id="7d560-132">The following figure shows the architecture for this solution:</span></span>  

  <span data-ttu-id="7d560-133">![接收 EDI 交換](../core/media/c54cca56-c658-4081-9e2f-bf28ba647cda.gif "c54cca56-c658-4081-9e2f-bf28ba647cda")</span><span class="sxs-lookup"><span data-stu-id="7d560-133">![Receiving EDI interchanges](../core/media/c54cca56-c658-4081-9e2f-bf28ba647cda.gif "c54cca56-c658-4081-9e2f-bf28ba647cda")</span></span>  

## <a name="configuring-and-testing-the-walkthrough"></a><span data-ttu-id="7d560-134">設定和測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="7d560-134">Configuring and Testing the Walkthrough</span></span>  
 <span data-ttu-id="7d560-135">這個解決方案所需的程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7d560-135">The procedures required for this solution include the following:</span></span>  

- <span data-ttu-id="7d560-136">將必要的訊息結構描述加入 BizTalk 專案，然後建置並部署此專案，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用該結構描述來處理收到的交換。</span><span class="sxs-lookup"><span data-stu-id="7d560-136">Add the required message schema(s) to a BizTalk project, and then build and deploy the project, making the schema(s) available for use by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in processing the received interchange.</span></span>  

- <span data-ttu-id="7d560-137">建立單向接收埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 從交易夥伴接收 EDI 交換並產生通知。</span><span class="sxs-lookup"><span data-stu-id="7d560-137">Create a one-way receive port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive the EDI interchange from the trading partner and generate an acknowledgment.</span></span> <span data-ttu-id="7d560-138">此接收位置繫結至檔案資料夾，而 Fabrikam 會在此資料夾放置要傳送給 Contoso 的 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="7d560-138">This receive location is tied to the file folder where Fabrikam drops the EDI interchange to be sent to Contoso.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="7d560-139">您可以使用雙向請求回應接收埠和位置來接收訊息，但是如果這樣做的話，就不能對接收位置使用 FILE 傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="7d560-139">You can use a two-way solicit response receive port and location to receive the message, but if you do, you will not be able to use a FILE transport type for the receive location.</span></span>  

- <span data-ttu-id="7d560-140">建立三個傳送埠，一個會將 EDI 交換傳送到 Contoso 本機資料夾、另一個會將 997 通知傳送到 Fabrikam 本機資料夾，而另一個則將 TA1 通知傳送到 Fabrikam 本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-140">Create one send port that sends the EDI interchange to a local Contoso folder, another that sends the 997 ACK to a local Fabrikam folder, and another that sends the TA1 ACK to a local Fabrikam folder.</span></span>  

- <span data-ttu-id="7d560-141">為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。</span><span class="sxs-lookup"><span data-stu-id="7d560-141">Create a party (trading partner) for both Fabrikam and Contoso.</span></span>  

- <span data-ttu-id="7d560-142">分別為兩個交易夥伴建立商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="7d560-142">Create a business profile each for both the trading partners.</span></span>  

- <span data-ttu-id="7d560-143">為要接收的訊息和要傳送的通知設定 EDI 屬性，來在兩個設定檔之間建立協議。</span><span class="sxs-lookup"><span data-stu-id="7d560-143">Create an agreement between the two profiles by configuring the EDI properties for the message to be received and the acknowledgment to be sent.</span></span>  

- <span data-ttu-id="7d560-144">使用測試 EDI 交換以測試逐步解說。</span><span class="sxs-lookup"><span data-stu-id="7d560-144">Test the walkthrough using a test EDI interchange.</span></span>  

  > [!NOTE]
  >  <span data-ttu-id="7d560-145">對於測試訊息，您可以使用 EDI 介面開發人員教學課程中所使用的 SamplePO.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="7d560-145">For a test message, you can use the SamplePO.txt file that is used in the EDI Interface Developer tutorial.</span></span> <span data-ttu-id="7d560-146">該檔案隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="7d560-146">That file is shipped in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ folder.</span></span> <span data-ttu-id="7d560-147">這是 X12 850 訊息。</span><span class="sxs-lookup"><span data-stu-id="7d560-147">This is an X12 850 message.</span></span>  

### <a name="configuring-the-walkthrough"></a><span data-ttu-id="7d560-148">設定逐步解說</span><span class="sxs-lookup"><span data-stu-id="7d560-148">Configuring the Walkthrough</span></span>  
 <span data-ttu-id="7d560-149">本節說明設定逐步解說的程序。</span><span class="sxs-lookup"><span data-stu-id="7d560-149">This section describes the procedures to configure the walkthrough.</span></span>  

##### <a name="to-deploy-the-message-schema"></a><span data-ttu-id="7d560-150">若要部署訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="7d560-150">To deploy the message schema</span></span>  

1. <span data-ttu-id="7d560-151">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="7d560-151">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create or open a BizTalk project.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="7d560-152">本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)，</span><span class="sxs-lookup"><span data-stu-id="7d560-152">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="7d560-153">如果沒有，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="7d560-153">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  

2. <span data-ttu-id="7d560-154">以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下**現有項目**。</span><span class="sxs-lookup"><span data-stu-id="7d560-154">Right-click your project, point to **Add**, and then click **Existing Item**.</span></span> <span data-ttu-id="7d560-155">移至結構描述所在的資料夾 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI，然後按兩下該結構描述。</span><span class="sxs-lookup"><span data-stu-id="7d560-155">Move to the folder that your schema is in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI, and then double-click your schema.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="7d560-156">如果 EDI 結構描述尚未解壓縮至 \XSD_Schema\EDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** \XSD_Schema\EDI 資料夾結構描述解壓縮至預設資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="7d560-156">If the EDI schemas have not been unzipped into the \XSD_Schema\EDI folders, execute the **MicrosoftEdiXSDTemplates.exe** file in the \XSD_Schema\EDI folder to unzip the schemas into the default folder.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="7d560-157">如果您使用 EDI 介面開發人員教學課程中所用的 SamplePO.txt 檔案，則必須使用隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 資料夾中的 X12_00401_850.xsd 結構描述。</span><span class="sxs-lookup"><span data-stu-id="7d560-157">If you use the SamplePO.txt file that is used in the EDI Interface Developer tutorial, you must use the X12_00401_850.xsd schema that is shipped in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI folder.</span></span> <span data-ttu-id="7d560-158">您不得使用 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema 資料夾中的 X12 850 結構描述。</span><span class="sxs-lookup"><span data-stu-id="7d560-158">You must not use the X12 850 schema in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema folder.</span></span>  

3. <span data-ttu-id="7d560-159">將組件金鑰檔案加入專案，然後建置並部署組件。</span><span class="sxs-lookup"><span data-stu-id="7d560-159">Add the assembly key file to the project, and then build and deploy the assembly.</span></span>  

##### <a name="to-create-a-one-way-receive-port-for-fabrikam-to-receive-the-edi-interchange"></a><span data-ttu-id="7d560-160">建立單向接收埠 (供 Fabrikam 使用) 以接收 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="7d560-160">To create a one-way receive port (for Fabrikam) to receive the EDI interchange</span></span>  

1. <span data-ttu-id="7d560-161">在 Windows 檔案總管中，建立本機資料夾，以接收交換。</span><span class="sxs-lookup"><span data-stu-id="7d560-161">In Windows Explorer, create a local folder to receive the interchange.</span></span>  

2. <span data-ttu-id="7d560-162">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="7d560-162">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Receive Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **One-way Receive Port**.</span></span>  

3. <span data-ttu-id="7d560-163">將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="7d560-163">Name the receive port, and then click **Receive Locations** in the console tree.</span></span>  

4. <span data-ttu-id="7d560-164">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="7d560-164">Click **New**.</span></span>  

5. <span data-ttu-id="7d560-165">接收位置命名，選取**檔案**for**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="7d560-165">Name the receive location, select **FILE** for **Type**, and then click **Configure**.</span></span>  

6. <span data-ttu-id="7d560-166">瀏覽至資料夾**接收資料夾**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="7d560-166">Browse to a folder for **Receive folder** text box.</span></span> <span data-ttu-id="7d560-167">您已在此程序的步驟 1 中，建立此資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-167">You created this folder in step 1 of this procedure.</span></span> <span data-ttu-id="7d560-168">輸入檔案遮罩，例如 **\*.edi**或是 **\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="7d560-168">Enter a file mask, such as **\*.edi** or **\*.txt**.</span></span>  

7. <span data-ttu-id="7d560-169">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="7d560-169">Click **OK**.</span></span>  

8. <span data-ttu-id="7d560-170">針對**接收管線**，選取**EdiReceive**。</span><span class="sxs-lookup"><span data-stu-id="7d560-170">For **Receive pipeline**, select **EdiReceive**.</span></span>  

9. <span data-ttu-id="7d560-171">按一下 [ **[確定]** 中**接收位置屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7d560-171">Click **OK** in the **Receive Location Properties** dialog box.</span></span> <span data-ttu-id="7d560-172">按一下 [ **[確定]** 中再次**接收埠屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7d560-172">Click **OK** again in the **Receive Port Properties** dialog box.</span></span>  

10. <span data-ttu-id="7d560-173">在主控台樹狀目錄中，按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="7d560-173">In the console tree, click **Receive Locations**.</span></span> <span data-ttu-id="7d560-174">在 **接收位置**窗格中，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="7d560-174">In the **Receive Locations** pane, right-click your receive location, and then click **Enable**.</span></span>  

##### <a name="to-create-a-static-one-way-send-port-for-contoso-to-send-the-edi-interchange"></a><span data-ttu-id="7d560-175">建立靜態單向傳送埠 (供 Contoso 使用) 以傳送 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="7d560-175">To create a static one-way send port (for Contoso) to send the EDI interchange</span></span>  

1. <span data-ttu-id="7d560-176">在 Windows 檔案總管中，建立本機資料夾，以便將測試交換傳送至此本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-176">In Windows Explorer, create a local folder to send the test interchange to.</span></span>  

2. <span data-ttu-id="7d560-177">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="7d560-177">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static One-way Send Port**.</span></span>  

3. <span data-ttu-id="7d560-178">在 [**傳送埠屬性**] 對話方塊中，傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d560-178">In the **Send Port Properties** dialog box, name the send port.</span></span>  

4. <span data-ttu-id="7d560-179">在 **傳輸**區段中，選取**檔案**的**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="7d560-179">In the **Transport** section, select **FILE** for **Type**, and then click **Configure**.</span></span>  

5. <span data-ttu-id="7d560-180">針對**目的地資料夾**，瀏覽至要接收交換的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-180">For **Destination folder**, browse to the folder to receive the interchange.</span></span> <span data-ttu-id="7d560-181">您已在此程序的步驟 1 中，建立此資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-181">You created this folder in step 1 of this procedure.</span></span> <span data-ttu-id="7d560-182">針對**檔案遮罩**，輸入交換格式，例如 **\*.edi**或是 **\*.xml**。</span><span class="sxs-lookup"><span data-stu-id="7d560-182">For **File mask**, enter the interchange format, such as **\*.edi** or **\*.xml**.</span></span>  

6. <span data-ttu-id="7d560-183">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="7d560-183">Click **OK**.</span></span>  

7. <span data-ttu-id="7d560-184">在 **傳送管線**，選取**EdiSend**。</span><span class="sxs-lookup"><span data-stu-id="7d560-184">In **Send pipeline**, select **EdiSend**.</span></span>  

8. <span data-ttu-id="7d560-185">在主控台樹狀目錄中，選取**篩選器**。</span><span class="sxs-lookup"><span data-stu-id="7d560-185">In the console tree, select **Filters**.</span></span> <span data-ttu-id="7d560-186">輸入訂閱 EDI 交換的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="7d560-186">Enter a filter to subscribe to the EDI interchange.</span></span> <span data-ttu-id="7d560-187">例如，對於**屬性**，輸入**BTS。MessageType**; 對於**運算子**，輸入**==**; 以及**值**的交換中，輸入結構描述，例如 http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_850 .</span><span class="sxs-lookup"><span data-stu-id="7d560-187">For example, for **Property**, enter **BTS.MessageType**; for **Operator**, enter **==**; and for **Value** enter the schema for the interchange, for example, http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_850.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="7d560-188">上述篩選條件設定可以確保會將交換 (而非通知) 傳送到與此傳送埠相關的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-188">The above filter setting ensures that interchanges, not acknowledgments, will be sent to the folder associated with this send port.</span></span>  

9. <span data-ttu-id="7d560-189">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="7d560-189">Click **OK**.</span></span>  

10. <span data-ttu-id="7d560-190">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="7d560-190">In the console tree, click **Send Ports**.</span></span> <span data-ttu-id="7d560-191">在 **傳送埠**窗格中，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="7d560-191">In the **Send Ports** pane, right-click your send port, and then click **Start**.</span></span>  

##### <a name="to-create-a-static-one-way-send-port-to-send-the-997n-acknowledgment"></a><span data-ttu-id="7d560-192">若要建立靜態單向傳送埠以傳送 997n 通知</span><span class="sxs-lookup"><span data-stu-id="7d560-192">To create a static one-way send port to send the 997n acknowledgment</span></span>  

1. <span data-ttu-id="7d560-193">在 Windows 檔案總管中，建立本機資料夾，以便傳送 997 通知至此本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-193">In Windows Explorer, create a local folder to send the 997 acknowledgment to.</span></span>  

2. <span data-ttu-id="7d560-194">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="7d560-194">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static One-way Send Port**.</span></span>  

3. <span data-ttu-id="7d560-195">在 [**傳送埠屬性**] 對話方塊中，傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d560-195">In the **Send Port Properties** dialog box, name the send port.</span></span>  

4. <span data-ttu-id="7d560-196">在 **傳輸**區段中，選取**檔案**的**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="7d560-196">In the **Transport** section, select **FILE** for **Type**, and then click **Configure**.</span></span>  

5. <span data-ttu-id="7d560-197">針對**目的地資料夾**，瀏覽至要接收 997 通知的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-197">For **Destination folder**, browse to a folder to receive the 997 acknowledgment.</span></span> <span data-ttu-id="7d560-198">您已在此程序的步驟 1 中，建立此資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-198">You created this folder in step 1 of this procedure.</span></span> <span data-ttu-id="7d560-199">針對**檔案遮罩**，輸入交換格式，例如 **\*.edi**或是 **\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="7d560-199">For **File mask**, enter the interchange format, such as **\*.edi** or **\*.txt**.</span></span>  

6. <span data-ttu-id="7d560-200">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="7d560-200">Click **OK**.</span></span>  

7. <span data-ttu-id="7d560-201">在 **傳送管線**，選取**EdiSend**。</span><span class="sxs-lookup"><span data-stu-id="7d560-201">In **Send pipeline**, select **EdiSend**.</span></span>  

8. <span data-ttu-id="7d560-202">在主控台樹狀目錄中，選取**篩選器**。</span><span class="sxs-lookup"><span data-stu-id="7d560-202">In the console tree, select **Filters**.</span></span> <span data-ttu-id="7d560-203">輸入訂閱 997 通知的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="7d560-203">Enter a filter to subscribe to the 997 acknowledgment.</span></span> <span data-ttu-id="7d560-204">例如，對於**屬性**，輸入**BTS。MessageType**; 對於**運算子**，輸入**==**; 及針對**值**比方說，在通知中，輸入的結構描述 `http://schemas.microsoft.com/Edi/X12#X12_997_Root` .</span><span class="sxs-lookup"><span data-stu-id="7d560-204">For example, for **Property**, enter **BTS.MessageType**; for **Operator**, enter **==**; and for **Value** enter the schema for the acknowledgment, for example, `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.</span></span>  

9. <span data-ttu-id="7d560-205">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="7d560-205">Click **OK**.</span></span>  

10. <span data-ttu-id="7d560-206">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="7d560-206">In the console tree, click **Send Ports**.</span></span> <span data-ttu-id="7d560-207">在 **傳送埠**窗格中，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="7d560-207">In the **Send Ports** pane, right-click your send port, and then click **Start**.</span></span>  

##### <a name="to-create-a-static-one-way-send-port-to-send-the-ta1-acknowledgment"></a><span data-ttu-id="7d560-208">若要建立靜態單向傳送埠以傳送 TA1 通知</span><span class="sxs-lookup"><span data-stu-id="7d560-208">To create a static one-way send port to send the TA1 acknowledgment</span></span>  

1. <span data-ttu-id="7d560-209">在 Windows 檔案總管中，建立本機資料夾，以便傳送 TA1 通知至此本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-209">In Windows Explorer, create a local folder to send the TA1 acknowledgment to.</span></span>  

2. <span data-ttu-id="7d560-210">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="7d560-210">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static One-way Send Port**.</span></span>  

3. <span data-ttu-id="7d560-211">在 [**傳送埠屬性**] 對話方塊中，傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d560-211">In the **Send Port Properties** dialog box, name the send port.</span></span>  

4. <span data-ttu-id="7d560-212">在 **傳輸**區段中，選取**檔案**的**型別**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="7d560-212">In the **Transport** section, select **FILE** for **Type**, and then click **Configure**.</span></span>  

5. <span data-ttu-id="7d560-213">針對**目的地資料夾**，瀏覽至要接收 TA1 通知的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-213">For **Destination folder**, browse to a folder to receive the TA1 acknowledgment.</span></span> <span data-ttu-id="7d560-214">您已在此程序的步驟 1 中，建立此資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d560-214">You created this folder in step 1 of this procedure.</span></span> <span data-ttu-id="7d560-215">針對**檔案遮罩**，輸入交換格式，例如 **\*.edi**或是 **\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="7d560-215">For **File mask**, enter the interchange format, such as **\*.edi** or **\*.txt**.</span></span>  

6. <span data-ttu-id="7d560-216">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="7d560-216">Click **OK**.</span></span>  

7. <span data-ttu-id="7d560-217">在 **傳送管線**，選取**EdiSend**。</span><span class="sxs-lookup"><span data-stu-id="7d560-217">In **Send pipeline**, select **EdiSend**.</span></span>  

8. <span data-ttu-id="7d560-218">在主控台樹狀目錄中，選取**篩選器**。</span><span class="sxs-lookup"><span data-stu-id="7d560-218">In the console tree, select **Filters**.</span></span> <span data-ttu-id="7d560-219">輸入訂閱 TA1 通知的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="7d560-219">Enter a filter to subscribe to the TA1 acknowledgment.</span></span> <span data-ttu-id="7d560-220">例如，對於**屬性**，輸入**BTS。MessageType**; 對於**運算子**，輸入**==**; 及針對**值**比方說，在通知中，輸入的結構描述 http://schemas.microsoft.com/Edi/X12#X12_TA1_Root .</span><span class="sxs-lookup"><span data-stu-id="7d560-220">For example, for **Property**, enter **BTS.MessageType**; for **Operator**, enter **==**; and for **Value** enter the schema for the acknowledgment, for example, http://schemas.microsoft.com/Edi/X12#X12_TA1_Root.</span></span>  

9. <span data-ttu-id="7d560-221">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="7d560-221">Click **OK**.</span></span>  

10. <span data-ttu-id="7d560-222">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="7d560-222">In the console tree, click **Send Ports**.</span></span> <span data-ttu-id="7d560-223">在 **傳送埠**窗格中，以滑鼠右鍵按一下您的傳送埠，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="7d560-223">In the **Send Ports** pane, right-click your send port, and then click **Start**.</span></span>  

##### <a name="to-create-a-party-and-a-business-profile-for-fabrikam"></a><span data-ttu-id="7d560-224">若要為 Fabrikam 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="7d560-224">To create a party and a business profile for Fabrikam</span></span>  

1. <span data-ttu-id="7d560-225">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="7d560-225">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  

2. <span data-ttu-id="7d560-226">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7d560-226">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="7d560-227">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7d560-227">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="7d560-228">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="7d560-228">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="7d560-229">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="7d560-229">However, for this walkthrough, you can leave this check box selected.</span></span>  

3. <span data-ttu-id="7d560-230">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="7d560-230">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  

4. <span data-ttu-id="7d560-231">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**fabrikam_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="7d560-231">In the **Profile Properties** dialog box, on the **General** page, enter **Fabrikam_Profile** in the **Name** text box.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="7d560-232">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="7d560-232">When you create a party, a profile is also created.</span></span> <span data-ttu-id="7d560-233">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="7d560-233">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="7d560-234">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="7d560-234">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="7d560-235">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d560-235">In the **General** page, specify a name for the profile.</span></span>  

##### <a name="to-create-a-party-and-a-business-profile-for-contoso"></a><span data-ttu-id="7d560-236">若要為 Contoso 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="7d560-236">To create a party and a business profile for Contoso</span></span>  

1. <span data-ttu-id="7d560-237">以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="7d560-237">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  

2. <span data-ttu-id="7d560-238">輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7d560-238">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="7d560-239">藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7d560-239">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="7d560-240">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="7d560-240">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="7d560-241">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="7d560-241">However, for this walkthrough, you can leave this check box selected.</span></span>  

3. <span data-ttu-id="7d560-242">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="7d560-242">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  

4. <span data-ttu-id="7d560-243">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**contoso_profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="7d560-243">In the **Profile Properties** dialog box, on the **General** page, enter **Contoso_Profile** in the **Name** text box.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="7d560-244">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="7d560-244">When you create a party, a profile is also created.</span></span> <span data-ttu-id="7d560-245">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="7d560-245">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="7d560-246">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="7d560-246">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="7d560-247">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d560-247">In the **General** page, specify a name for the profile.</span></span>  

##### <a name="to-create-an-agreement-between-the-two-business-profiles"></a><span data-ttu-id="7d560-248">在兩個商務設定檔之間建立協議</span><span class="sxs-lookup"><span data-stu-id="7d560-248">To create an agreement between the two business profiles</span></span>  

1. <span data-ttu-id="7d560-249">以滑鼠右鍵按一下 **[fabrikam_profile]**，指向**新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="7d560-249">Right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.</span></span>  

2. <span data-ttu-id="7d560-250">在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d560-250">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  

3. <span data-ttu-id="7d560-251">從**通訊協定**下拉式清單中，選取**X12**。</span><span class="sxs-lookup"><span data-stu-id="7d560-251">From the **Protocol** drop-down list, select **X12**.</span></span>  

4. <span data-ttu-id="7d560-252">在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Contoso**。</span><span class="sxs-lookup"><span data-stu-id="7d560-252">In the **Second Partner** section, from the **Name** drop-down list, select **Contoso**.</span></span>  

5. <span data-ttu-id="7d560-253">在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。</span><span class="sxs-lookup"><span data-stu-id="7d560-253">In the **Second Partner** section, from the **Profile** drop-down list, select **Contoso_Profile**.</span></span>  

    <span data-ttu-id="7d560-254">您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向協議，而每個單向協議各代表一筆完整的訊息交易 (包含訊息傳輸與通知傳輸)。</span><span class="sxs-lookup"><span data-stu-id="7d560-254">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way agreement and each one-way agreement represents one complete transaction of message (including message transfer and acknowledgement transfer).</span></span>  

6. <span data-ttu-id="7d560-255">在 **一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，，然後選取 **儲存訊息內容 reporting**。</span><span class="sxs-lookup"><span data-stu-id="7d560-255">In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**, and then select **Store message payload for reporting**.</span></span>  

7. <span data-ttu-id="7d560-256">在上執行下列工作**Fabrikam-> Contoso**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7d560-256">Perform the following tasks on the **Fabrikam->Contoso** tab.</span></span>  

   1. <span data-ttu-id="7d560-257">上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="7d560-257">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  

      > [!NOTE]
      >  <span data-ttu-id="7d560-258">對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。</span><span class="sxs-lookup"><span data-stu-id="7d560-258">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires the qualifier and identifier fields for sender and receiver in order to perform agreement resolution.</span></span> <span data-ttu-id="7d560-259">它會比對的值**ISA5**， **ISA6**， **ISA7**，以及**ISA8**交換標頭與協議屬性中。</span><span class="sxs-lookup"><span data-stu-id="7d560-259">It will match the values of **ISA5**, **ISA6**, **ISA7**, and **ISA8** in the interchange header with those in the properties of an agreement.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7d560-260"> 會比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 也解析協議。</span><span class="sxs-lookup"><span data-stu-id="7d560-260"> will also resolve the agreement by matching the sender qualifier and identifier (without the receiver qualifier and identifier).</span></span> <span data-ttu-id="7d560-261">若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。</span><span class="sxs-lookup"><span data-stu-id="7d560-261">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement, it will use the fallback agreement properties.</span></span>  
      > 
      > [!NOTE]
      >  <span data-ttu-id="7d560-262">如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**要**ZZ**， **ISA6**至**THEM**， **ISA7**要**ZZ**，和**ISA8**至**美國**。</span><span class="sxs-lookup"><span data-stu-id="7d560-262">If you are using the SamplePO.txt file from the “EDI Interface Developer Tutorial” as your test message, set **ISA5** to **ZZ**, **ISA6** to **THEM**, **ISA7** to **ZZ**, and **ISA8** to **US**.</span></span>  

   2. <span data-ttu-id="7d560-263">上**收條**頁面**交換設定** 區段中，核取**預期 TA1**並**預期 997**。</span><span class="sxs-lookup"><span data-stu-id="7d560-263">On the **Acknowledgement** page under the **Interchange Settings** section, check **TA1 Expected** and **997 Expected**.</span></span>  

   3. <span data-ttu-id="7d560-264">上**驗證**下方的頁面上**交換設定**區段中，確定**檢查 ISA13 是否重複**選項未核取。</span><span class="sxs-lookup"><span data-stu-id="7d560-264">On the **Validation** page under the **Interchange Settings** section, make sure **Check for duplicate ISA13** option is unchecked.</span></span>  

      > [!NOTE]
      >  <span data-ttu-id="7d560-265">清除**檢查 ISA13 是否重複**屬性可讓您接收相同訊息的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="7d560-265">Clearing the **Check for duplicate ISA13** property enables you to receive multiple instances of the same message.</span></span>  

   4. <span data-ttu-id="7d560-266">在上**字元集和分隔符號**下方的頁面上**交換設定**區段中，選取**CR LF**選項。</span><span class="sxs-lookup"><span data-stu-id="7d560-266">On the **Charset and Separators** page under the **Interchange Settings** section, select the **CR LF** option.</span></span>  

   5. <span data-ttu-id="7d560-267">在上**本機主機設定**下方的頁面上**交換設定**區段中，清除**通知的路由設定為傳送管線在要求-回應接收埠**選項。</span><span class="sxs-lookup"><span data-stu-id="7d560-267">On the **Local Host Settings** page under the **Interchange Settings** section, clear the **Route ACK to send pipeline on request-response receive port** option.</span></span>  

      > [!NOTE]
      >  <span data-ttu-id="7d560-268">如果您使用雙向接收埠以接收交換並傳回通知，您會檢查**通知的路由設定為傳送管線在要求-回應接收埠**。</span><span class="sxs-lookup"><span data-stu-id="7d560-268">If you were using a two-way receive port to receive the interchange and return the acknowledgment, you would check **Route ACK to send pipeline on request-response receive port**.</span></span>  

   6. <span data-ttu-id="7d560-269">上**傳送埠**下方的頁面上**交換設定**區段中，將會接收來自 Fabrikam 交換的傳送埠和接收的傳送埠建立關聯從 Contoso 的通知。</span><span class="sxs-lookup"><span data-stu-id="7d560-269">On the **Send Ports** page under the **Interchange Settings** section, associate the send ports that will be receiving the interchange from Fabrikam and the send ports that will be receiving the acknowledgements from Contoso.</span></span> <span data-ttu-id="7d560-270">在 **傳送埠**格線下方**名稱** 欄中，按一下空白儲存格，並從下拉式清單中，選取 建立從 Fabrikam 接收 EDI 交換的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="7d560-270">In the **Send ports** grid, under the **Name** column, click an empty cell, and from the drop-down list, select the send port created for receiving the EDI interchange from Fabrikam.</span></span> <span data-ttu-id="7d560-271">針對建立來接收 TA1 通知的傳送埠與建立來接收 997 通知的傳送埠，重複執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="7d560-271">Repeat the step for the send port created for receiving the TA1 acknowledgement and the send port created for receiving the 997 acknowledgement.</span></span>  

   7. <span data-ttu-id="7d560-272">上**驗證**下方的頁面上**交易集設定**區段中，保留**EDI 類型驗證**核取，並檢查**擴充驗證**.</span><span class="sxs-lookup"><span data-stu-id="7d560-272">On the **Validation** page under the **Transaction Set Settings** section, leave **EDI Type Validation** checked and check **Extended validation**.</span></span>  

   8. <span data-ttu-id="7d560-273">如果您使用其中一個隨附之標準結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請在**本機主機設定**頁面下**交易集設定**區段中，選取要用來將結構描述的命名空間處理內送交換。</span><span class="sxs-lookup"><span data-stu-id="7d560-273">If you are using one of the standard schemas shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], on the **Local Host Settings** page under the **Transaction Set Settings** section, select the namespace for the schema to be used to process the incoming interchange.</span></span> <span data-ttu-id="7d560-274">如果使用自訂的結構描述，請輸入中的值**自訂目標命名空間**方格中，以便[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以判斷命名空間使用群組和交易集標頭值。</span><span class="sxs-lookup"><span data-stu-id="7d560-274">If using a custom schema, enter values in the **Customize Target namespace** grid, so that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can determine the namespace using group and transaction set header values.</span></span>  

   9. <span data-ttu-id="7d560-275">在上**信封**下方的頁面上**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。</span><span class="sxs-lookup"><span data-stu-id="7d560-275">On the **Envelopes** page under the **Transaction Set Settings** section, enter values for all columns in the first line of the grid.</span></span>  


      |       <span data-ttu-id="7d560-276">使用</span><span class="sxs-lookup"><span data-stu-id="7d560-276">Use this</span></span>       |                                                                                                                                    <span data-ttu-id="7d560-277">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="7d560-277">To do this</span></span>                                                                                                                                    |
      |----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |     <span data-ttu-id="7d560-278">**預設值**</span><span class="sxs-lookup"><span data-stu-id="7d560-278">**Default**</span></span>      |   <span data-ttu-id="7d560-279">選取 **預設**。</span><span class="sxs-lookup"><span data-stu-id="7d560-279">Select **Default**.</span></span> <span data-ttu-id="7d560-280">**注意：** 當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **[gs7]**，以及**GS8**習慣即使的值**交易型別**，**版本/版次**，和**目標命名空間**不相符的訊息。</span><span class="sxs-lookup"><span data-stu-id="7d560-280">**Note:**  When you select this row as the default, the values for **GS1**, **GS2**, **GS3**, **GS7**, and **GS8** are used even if the values for **Transaction Type**, **Version/Release**, and  **Target namespace** are not a match for the message.</span></span>   |
      | <span data-ttu-id="7d560-281">**交易類型**</span><span class="sxs-lookup"><span data-stu-id="7d560-281">**Transaction Type**</span></span> |                                                                                                     <span data-ttu-id="7d560-282">選取測試訊息，訊息類型**850-Purchase Order**。</span><span class="sxs-lookup"><span data-stu-id="7d560-282">Select the message type of your test message, **850 - Purchase Order**.</span></span>                                                                                                      |
      | <span data-ttu-id="7d560-283">**版本/版次**</span><span class="sxs-lookup"><span data-stu-id="7d560-283">**Version/Release**</span></span>  |                                                                                                                        <span data-ttu-id="7d560-284">輸入 EDI 版本， **00401**。</span><span class="sxs-lookup"><span data-stu-id="7d560-284">Enter the EDI version, **00401**.</span></span>                                                                                                                         |
      | <span data-ttu-id="7d560-285">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="7d560-285">**Target namespace**</span></span> |                                                                                                                <span data-ttu-id="7d560-286">選取  **<http://schemas.microsoft.com/Edi/X12>**。</span><span class="sxs-lookup"><span data-stu-id="7d560-286">Select **<http://schemas.microsoft.com/Edi/X12>**.</span></span>                                                                                                                |
      |       <span data-ttu-id="7d560-287">**GS1**</span><span class="sxs-lookup"><span data-stu-id="7d560-287">**GS1**</span></span>        |                                                                                           <span data-ttu-id="7d560-288">確認已選取測試訊息的訊息類型， **PO-Purchase Order (850)**。</span><span class="sxs-lookup"><span data-stu-id="7d560-288">Verify that the message type of the test message is selected, **PO - Purchase Order (850)**.</span></span>                                                                                           |
      |       <span data-ttu-id="7d560-289">**GS2**</span><span class="sxs-lookup"><span data-stu-id="7d560-289">**GS2**</span></span>        |                                                                                                                    <span data-ttu-id="7d560-290">輸入應用程式傳送者的值。</span><span class="sxs-lookup"><span data-stu-id="7d560-290">Enter a value for the Application sender.</span></span>                                                                                                                     |
      |       <span data-ttu-id="7d560-291">**GS3**</span><span class="sxs-lookup"><span data-stu-id="7d560-291">**GS3**</span></span>        |                                                                                                                   <span data-ttu-id="7d560-292">輸入應用程式接收者的值。</span><span class="sxs-lookup"><span data-stu-id="7d560-292">Enter a value for the Application receiver.</span></span>                                                                                                                    |
      |       <span data-ttu-id="7d560-293">**GS4**</span><span class="sxs-lookup"><span data-stu-id="7d560-293">**GS4**</span></span>        | <span data-ttu-id="7d560-294">選取您想要的日期格式。</span><span class="sxs-lookup"><span data-stu-id="7d560-294">Select the date format that you want.</span></span> <span data-ttu-id="7d560-295">**注意：** 您必須在下拉式清單中選取值，不只是按一下要顯示預設值的欄位。</span><span class="sxs-lookup"><span data-stu-id="7d560-295">**Note:**  You have to select the value in the drop-down list, not just click in the field to display the default.</span></span> <span data-ttu-id="7d560-296">如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。</span><span class="sxs-lookup"><span data-stu-id="7d560-296">If you click in the field without selecting the value from the drop-down list, the value will not actually be selected.</span></span> |
      |       <span data-ttu-id="7d560-297">**GS5**</span><span class="sxs-lookup"><span data-stu-id="7d560-297">**GS5**</span></span>        |                                                                                                                      <span data-ttu-id="7d560-298">選擇您要的時間格式。</span><span class="sxs-lookup"><span data-stu-id="7d560-298">Select the time format that you want.</span></span>                                                                                                                       |
      |       <span data-ttu-id="7d560-299">**[GS7]**</span><span class="sxs-lookup"><span data-stu-id="7d560-299">**GS7**</span></span>        |                                                                                                                <span data-ttu-id="7d560-300">選取  **X-Accredited 的 Standards Committee X12**。</span><span class="sxs-lookup"><span data-stu-id="7d560-300">Select **X - Accredited Standards Committee X12**.</span></span>                                                                                                                |
      |       <span data-ttu-id="7d560-301">**GS8**</span><span class="sxs-lookup"><span data-stu-id="7d560-301">**GS8**</span></span>        |                                                                                                             <span data-ttu-id="7d560-302">確認已輸入 EDI 版本， **00401**。</span><span class="sxs-lookup"><span data-stu-id="7d560-302">Verify that the EDI version has been entered, **00401**.</span></span>                                                                                                             |

      > [!NOTE]
      >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7d560-303"> 將設定值，如 GS01，GS02，GS03、 GS04、 GS05、 GS07 和輸出的輸入值為基礎的通知的 GS08**交易類型**，**版本/版次**，和**目標命名空間**。</span><span class="sxs-lookup"><span data-stu-id="7d560-303"> will set the values for GS01, GS02, GS03, GS04, GS05, GS07, and GS08 of the outbound acknowledgments based on the values entered for **Transaction Type**, **Version/Release**, and **Target namespace**.</span></span> <span data-ttu-id="7d560-304">傳送管線會嘗試將交易集類型、X12 版本和目標命名空間，與訊息標頭中的對應值進行比對。</span><span class="sxs-lookup"><span data-stu-id="7d560-304">The send pipeline attempts to match the transaction set type, the X12 version, and the target namespace with the corresponding values in the header of the message.</span></span> <span data-ttu-id="7d560-305">如果成功，則會使用相關聯的 GS 值**交易類型**，**版本/版次**，並**目標命名空間**值。</span><span class="sxs-lookup"><span data-stu-id="7d560-305">If successful, it uses the GS values associated with the **Transaction Type**, **Version/Release**, and **Target namespace** values.</span></span>  

8. <span data-ttu-id="7d560-306">在上執行下列工作**Contoso-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7d560-306">Perform the following tasks on the **Contoso->Fabrikam** tab.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="7d560-307">在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。</span><span class="sxs-lookup"><span data-stu-id="7d560-307">In this walkthrough, we specify the required value in the tab so that an agreement can be successfully created.</span></span> <span data-ttu-id="7d560-308">若要成功建立協議，兩個單向協議索引標籤必須已定義的值**ISA5**， **ISA6**， **ISA7**，以及**ISA8**。</span><span class="sxs-lookup"><span data-stu-id="7d560-308">To successfully create an agreement, both one-way agreement tabs must have values defined for **ISA5**, **ISA6**, **ISA7**, and **ISA8**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="7d560-309">雖然通知屬於同一個訊息交易的一部分，在中設定通知的產生方式的相關的屬性**Contoso-> Fabrikam**  索引標籤。這是必要的因為通知內容屬性傳送者和接收者限定詞設定為您在指定的值相反**Contoso-> Fabrikam**  索引標籤。例如，如果傳送者和接收者識別碼設為 THEM 與 US 中的**Fabrikam-> Contoso**  索引標籤、 寄件者與接收者內容屬性會設定為 US 與在通知中。</span><span class="sxs-lookup"><span data-stu-id="7d560-309">Even though the acknowledgement is part of the same message transaction, the properties related to how the acknowledgement should be generated are configured in the **Contoso->Fabrikam** tab. This is required because the acknowledgement context properties for the sender and receiver qualifiers are set to the opposite of the values you specified in the **Contoso->Fabrikam** tab. For example, if sender and receiver identifiers are set to THEM and US in the **Fabrikam->Contoso** tab, the sender and receiver context properties will be set to US and THEM in the acknowledgement.</span></span> <span data-ttu-id="7d560-310">一般而言，其他單向協議索引標籤也會分別將傳送者與接收者識別項設定為 US 與 THEM。</span><span class="sxs-lookup"><span data-stu-id="7d560-310">Typically, the other one-way agreement tab would also have the sender and receiver identifiers set to US and THEM respectively.</span></span> <span data-ttu-id="7d560-311">因此，通知訊息會解析成該協議，並將挑選屬性設定。</span><span class="sxs-lookup"><span data-stu-id="7d560-311">Hence, the acknowledgement message would resolve to that agreement and the properties setting will be picked.</span></span> <span data-ttu-id="7d560-312">因此，如果您想要讓通知使用不同的項目分隔符號，或如果您想要讓通知使用 CR LF，指定中的屬性**Contoso-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7d560-312">So, if you want to have the acknowledgement to use different element separators or if you want to have the acknowledgement to use CR LF, specify the properties in the **Contoso->Fabrikam** tab.</span></span>  
   >   
   >  <span data-ttu-id="7d560-313">在概念上，將會從傳送者與接收者辨識符號與在通知的內容屬性中所設定值相同的任一個單向協議索引標籤中挑選通知的屬性。</span><span class="sxs-lookup"><span data-stu-id="7d560-313">Conceptually, the properties for the acknowledgement will be picked from any one-way agreement tab that has the same sender and receiver qualifiers as set in the acknowledgement’s context properties.</span></span> <span data-ttu-id="7d560-314">但為便於實際應用，通常會在您所建立由交換解析而成之協議的其他單向協議索引標籤中設定此屬性。</span><span class="sxs-lookup"><span data-stu-id="7d560-314">However, for ease of practical use, you would typically set this in the other one-way agreement tab of the agreement that you created to which the interchange would have resolved.</span></span>  

   1.  <span data-ttu-id="7d560-315">上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="7d560-315">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  

       > [!NOTE]
       >  <span data-ttu-id="7d560-316">如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**要**ZZ**， **ISA6**至**美國**， **ISA7**要**ZZ**，和**ISA8**至**THEM**。</span><span class="sxs-lookup"><span data-stu-id="7d560-316">If you are using the SamplePO.txt file from the “EDI Interface Developer Tutorial” as your test message, set **ISA5** to **ZZ**, **ISA6** to **US**, **ISA7** to **ZZ**, and **ISA8** to **THEM**.</span></span>  

9. <span data-ttu-id="7d560-317">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="7d560-317">Click **Apply**.</span></span>  

10. <span data-ttu-id="7d560-318">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="7d560-318">Click **OK**.</span></span> <span data-ttu-id="7d560-319">中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="7d560-319">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="7d560-320">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="7d560-320">The newly added agreement is enabled by default.</span></span>  

### <a name="testing-the-walkthrough"></a><span data-ttu-id="7d560-321">測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="7d560-321">Testing the Walkthrough</span></span>  
 <span data-ttu-id="7d560-322">本節提供關於如何測試逐步解說的資訊。</span><span class="sxs-lookup"><span data-stu-id="7d560-322">This section provides information on how to test the walkthrough.</span></span>  

##### <a name="to-test-the-walkthrough"></a><span data-ttu-id="7d560-323">若要測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="7d560-323">To test the walkthrough</span></span>  

1. <span data-ttu-id="7d560-324">在 Windows 檔案總管中，將測試 EDI 交換置放到本機接收資料夾中。</span><span class="sxs-lookup"><span data-stu-id="7d560-324">In Windows Explorer, drop the test EDI interchange into your local receive folder.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="7d560-325">對於測試訊息，您可以使用 EDI 介面開發人員教學課程中所使用的 SamplePO.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="7d560-325">For a test message, you can use the SamplePO.txt file that is used in the EDI Interface Developer tutorial.</span></span> <span data-ttu-id="7d560-326">該檔案隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="7d560-326">That file is shipped in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial folder.</span></span> <span data-ttu-id="7d560-327">這是 X12 850 訊息。</span><span class="sxs-lookup"><span data-stu-id="7d560-327">This is an X12 850 message.</span></span> <span data-ttu-id="7d560-328">如果您使用這個訊息，則必須完成 X12_00401_850.xsd 結構描述的部署 (該結構描述隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 資料夾)。</span><span class="sxs-lookup"><span data-stu-id="7d560-328">If you use this message, you must have deployed the X12_00401_850.xsd schema that is shipped in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI folder.</span></span> <span data-ttu-id="7d560-329">您不得使用 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema 資料夾中的 X12 850 結構描述。</span><span class="sxs-lookup"><span data-stu-id="7d560-329">You must not use the X12 850 schema in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema folder.</span></span>  

2. <span data-ttu-id="7d560-330">開啟與交換傳送埠相關聯的資料夾，並確認其中有包含 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="7d560-330">Open the folder that you associated with the send port for interchanges, and verify that it contains the EDI interchange.</span></span>  

3. <span data-ttu-id="7d560-331">開啟與 997 通知傳送埠相關聯的資料夾，並確認其中有包含 997 通知。</span><span class="sxs-lookup"><span data-stu-id="7d560-331">Open the folder that you associated with the send port for the 997 acknowledgment, and verify that it contains a 997 acknowledgment.</span></span>  

4. <span data-ttu-id="7d560-332">開啟與 TA1 通知傳送埠相關聯的資料夾，並確認其中有包含 TA1 通知。</span><span class="sxs-lookup"><span data-stu-id="7d560-332">Open the folder that you associated with the send port for the TA1 acknowledgment, and verify that it contains a TA1 acknowledgment.</span></span>  

## <a name="see-also"></a><span data-ttu-id="7d560-333">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d560-333">See Also</span></span>  
 [<span data-ttu-id="7d560-334">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="7d560-334">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)