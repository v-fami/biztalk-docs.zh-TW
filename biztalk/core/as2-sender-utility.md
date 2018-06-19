---
title: AS2 傳送者公用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e2a88fc-67fd-4801-a6f8-1e7c92098eaf
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e69f70e2a404c92393fb02b301b58abf2d97da2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232278"
---
# <a name="as2-sender-utility"></a><span data-ttu-id="e81be-102">AS2 傳送者公用程式</span><span class="sxs-lookup"><span data-stu-id="e81be-102">AS2 Sender Utility</span></span>
<span data-ttu-id="e81be-103">隨附於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 AS2 傳送者公用程式可讓您將 AS2 訊息傳送到單一電腦上的網站。</span><span class="sxs-lookup"><span data-stu-id="e81be-103">The AS2 Sender utility shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to send an AS2 message to a Web site on a single computer.</span></span> <span data-ttu-id="e81be-104">這個公用程式可模擬從個別電腦傳送 AS2 訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="e81be-104">This utility simulates the sending of an AS2 message from a separate computer.</span></span>  
  
 <span data-ttu-id="e81be-105">AS2 傳送者公用程式檔案位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender 中。</span><span class="sxs-lookup"><span data-stu-id="e81be-105">The AS2 Sender utility files are located in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e81be-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="e81be-106">Prerequisites</span></span>  
 <span data-ttu-id="e81be-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="e81be-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
## <a name="what-this-utility-does"></a><span data-ttu-id="e81be-108">這個公用程式的作用</span><span class="sxs-lookup"><span data-stu-id="e81be-108">What This Utility Does</span></span>  
 <span data-ttu-id="e81be-109">AS2 傳送者公用程式會使用 EDI 內容建置 AS2 訊息，並將該訊息傳送到使用 BTSHTTPReceive ISAPI 篩選器的網站。</span><span class="sxs-lookup"><span data-stu-id="e81be-109">The AS2 Sender utility builds an AS2 message with an EDI payload, and sends that message to a Web site that uses the BTSHTTPReceive ISAPI filter.</span></span> <span data-ttu-id="e81be-110">根據預設，教學課程執行的作業包括：</span><span class="sxs-lookup"><span data-stu-id="e81be-110">By default the tutorial does the following:</span></span>  
  
-   <span data-ttu-id="e81be-111">傳送名為 X12_00401_864.edi 且具有 864 X12 編碼內容的 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="e81be-111">Sends an AS2 message named X12_00401_864.edi with an 864 X12-encoded payload.</span></span> <span data-ttu-id="e81be-112">此訊息位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial 資料夾內。</span><span class="sxs-lookup"><span data-stu-id="e81be-112">This message is located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial folder.</span></span>  
  
-   <span data-ttu-id="e81be-113">提示非同步 MDN 以回應 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="e81be-113">Prompts an asynchronous MDN in response to the AS2 message.</span></span> <span data-ttu-id="e81be-114">這是由傳送的訊息決定，而且可以變更。</span><span class="sxs-lookup"><span data-stu-id="e81be-114">This is determined by the message sent, and can be changed.</span></span>  
  
-   <span data-ttu-id="e81be-115">透過 Contoso 虛擬目錄將 AS2 訊息傳送至接收位置。</span><span class="sxs-lookup"><span data-stu-id="e81be-115">Sends the AS2 message to a receive location through the Contoso virtual directory.</span></span>  
  
 <span data-ttu-id="e81be-116">您可以修改公用程式來變更這種特定行為。</span><span class="sxs-lookup"><span data-stu-id="e81be-116">The utility can be modified to change this specific behavior.</span></span> <span data-ttu-id="e81be-117">請參閱[如何自訂 AS2 傳送者公用程式](../core/as2-sender-utility.md#BKMK_Custom)下一節。</span><span class="sxs-lookup"><span data-stu-id="e81be-117">See the [How to Customize the AS2 Sender Utility](../core/as2-sender-utility.md#BKMK_Custom) section below.</span></span>  
  
## <a name="how-to-set-up-a-solution-using-the-as2-sender-utility"></a><span data-ttu-id="e81be-118">如何設定使用 A2 傳送者公用程式的方案</span><span class="sxs-lookup"><span data-stu-id="e81be-118">How to Set Up a Solution Using the AS2 Sender Utility</span></span>  
 <span data-ttu-id="e81be-119">若要將方案設定成使用 AS2 傳送者公用程式，您必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e81be-119">To set up a solution to use the AS2 Sender utility, you need to do the following.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e81be-120">AS2 教學課程與兩個 AS2 傳送端逐步解說中都示範了這些步驟。</span><span class="sxs-lookup"><span data-stu-id="e81be-120">These steps are demonstrated in the AS2 Tutorial and two AS2 send-side walkthroughs.</span></span> <span data-ttu-id="e81be-121">如需詳細資訊，請參閱[教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)，[逐步解說 (AS2): 使用同步 MDN 透過 AS2 傳送的 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md)，和[逐步解說 (AS2): 使用非同步透過 AS2 傳送的 EDIMDN](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md)。</span><span class="sxs-lookup"><span data-stu-id="e81be-121">For more information, see [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md), [Walkthrough (AS2): Sending EDI over AS2 with a Synchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md), and [Walkthrough (AS2): Sending EDI over AS2 with an Asynchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md).</span></span>  
  
-   <span data-ttu-id="e81be-122">啟用 BTSHTTPReceive ISAPI 篩選器。</span><span class="sxs-lookup"><span data-stu-id="e81be-122">Enable the BTSHTTPReceive ISAPI filter.</span></span>  
  
-   <span data-ttu-id="e81be-123">設定用來接收 AS2 訊息的網頁和接收位置。</span><span class="sxs-lookup"><span data-stu-id="e81be-123">Configure a Web page and a receive location to receive the AS2 message.</span></span> <span data-ttu-id="e81be-124">在預設的 AS2 傳送者公用程式中，此網頁為 Contoso 網頁。</span><span class="sxs-lookup"><span data-stu-id="e81be-124">In the default AS2 Sender utility, the Web page is the Contoso Web page.</span></span>  
  
-   <span data-ttu-id="e81be-125">部署您要傳送成 AS2 訊息內容之 EDI 交換的結構描述。</span><span class="sxs-lookup"><span data-stu-id="e81be-125">Deploy the schema for the EDI interchange that you will send as a payload of the AS2 message.</span></span>  
  
-   <span data-ttu-id="e81be-126">設定適當的 AS2 和 EDI 合作對象屬性。</span><span class="sxs-lookup"><span data-stu-id="e81be-126">Set the appropriate AS2 and EDI party properties.</span></span>  
  
##  <a name="BKMK_Custom"></a><span data-ttu-id="e81be-127">如何自訂 AS2 傳送者公用程式</span><span class="sxs-lookup"><span data-stu-id="e81be-127">How to Customize the AS2 Sender Utility</span></span>  
 <span data-ttu-id="e81be-128">預設的 AS2 傳送者公用程式會透過 AS2 將測試 864 EDI 交換傳送到使用 BTSHTTPReceive ISAPI 篩選器的 Contoso 網頁。</span><span class="sxs-lookup"><span data-stu-id="e81be-128">The default AS2 Sender utility sends a test 864 EDI interchange over AS2 to a Contoso Web page using the BTSHTTPReceive ISAPI filter.</span></span> <span data-ttu-id="e81be-129">AS2 訊息 (名稱為 X12_00401_864.edi) 會提示非同步的 MDN。</span><span class="sxs-lookup"><span data-stu-id="e81be-129">The AS2 message, named X12_00401_864.edi, prompts an asynchronous MDN.</span></span> <span data-ttu-id="e81be-130">AS2 傳送者公用程式程式碼位於 HttpSender.cs 中[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]AS2 Tutorial\Sender 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e81be-130">The AS2 Sender utility code is located in HttpSender.cs in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]AS2 Tutorial\Sender folder.</span></span> <span data-ttu-id="e81be-131">HttpSender.cs 中的下面這行程式碼會傳送預設的 864 測試檔案：</span><span class="sxs-lookup"><span data-stu-id="e81be-131">The following line of code in HttpSender.cs sends the default 864 test file:</span></span>  
  
```  
Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864.edi", FileMode.Open, FileAccess.Read);  
```  
  
> [!NOTE]
>  <span data-ttu-id="e81be-132">您可以使用不同的檔案名稱和不同的路徑來修改這行程式碼。</span><span class="sxs-lookup"><span data-stu-id="e81be-132">You can modify this line with a different file name and different path.</span></span>  
  
 <span data-ttu-id="e81be-133">HttpSender.cs 中的下列一行會傳送名為 x12_00401_864-sync.edi 的 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="e81be-133">The following line in HttpSender.cs sends an AS2 message named X12_00401_864-Sync.edi.</span></span> <span data-ttu-id="e81be-134">這個訊息會提示同步的 MDN。</span><span class="sxs-lookup"><span data-stu-id="e81be-134">This message prompts a synchronous MDN.</span></span> <span data-ttu-id="e81be-135">根據預設，HttpSender.cs 中這一行程式碼已標記為註解，改由傳送 X12_00401_864.edi 的程式碼代替。</span><span class="sxs-lookup"><span data-stu-id="e81be-135">By default, this line of code in HttpSender.cs is commented out in favor of the line that sends X12_00401_864.edi.</span></span> <span data-ttu-id="e81be-136">若要傳送 X12_00401_864-Sync.edi，請移除 X12_00401_864-Sync.edi 一行的註解標記，並將 X12_00401_864.edi 一行標記為註解。</span><span class="sxs-lookup"><span data-stu-id="e81be-136">To send X12_00401_864-Sync.edi, uncomment the X12_00401_864-Sync.edi line and comment out the X12_00401_864.edi line.</span></span>  
  
```  
Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864-Sync.edi", FileMode.Open, FileAccess.Read);  
```  
  
 <span data-ttu-id="e81be-137">HttpSender.cs 中的下面這行程式碼會將訊息傳送至 Contoso 網頁：</span><span class="sxs-lookup"><span data-stu-id="e81be-137">The following line of code in HttpSender.cs sends the message to the Contoso Web page:</span></span>  
  
```  
HttpSender TestSender = new HttpSender("http://localhost/Contoso/BTSHttpReceive.dll");  
```  
  
> [!NOTE]
>  <span data-ttu-id="e81be-138">您可以使用不同的虛擬目錄和 ISAPI 篩選器來修改這行程式碼。</span><span class="sxs-lookup"><span data-stu-id="e81be-138">You can modify this line with a different virtual directory and ISAPI filter.</span></span>  
  
### <a name="to-build-the-as2-sender-sample"></a><span data-ttu-id="e81be-139">若要建置 AS2 傳送者範例</span><span class="sxs-lookup"><span data-stu-id="e81be-139">To build the AS2 Sender sample</span></span>  
  
1.  <span data-ttu-id="e81be-140">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender 資料夾中的 Sender.csproj 專案。</span><span class="sxs-lookup"><span data-stu-id="e81be-140">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the Sender.csproj project in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender folder.</span></span>  
  
2.  <span data-ttu-id="e81be-141">開啟 Sender 專案中的 HttpSender.cs，並使用適當的網頁和適當的 EDI 檔案名稱和路徑自訂傳送者程式碼。</span><span class="sxs-lookup"><span data-stu-id="e81be-141">Open HttpSender.cs in the Sender project, and customize the Sender code with the appropriate receiving Web page and the appropriate EDI filename and path.</span></span>  
  
3.  <span data-ttu-id="e81be-142">以滑鼠右鍵按一下 [Sender] 專案，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="e81be-142">Right-click the Sender project, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="e81be-143">按一下**簽署**左邊的主控台中。</span><span class="sxs-lookup"><span data-stu-id="e81be-143">Click **Signing** in the left-hand console.</span></span> <span data-ttu-id="e81be-144">請確認**簽署組件**已選取，而且強式名稱金鑰檔設為**Sender.snk**。</span><span class="sxs-lookup"><span data-stu-id="e81be-144">Ensure that **Sign the assembly** is selected, and the strong name key file is set to **Sender.snk**.</span></span> <span data-ttu-id="e81be-145">請確定**延遲簽署只能**已清除。</span><span class="sxs-lookup"><span data-stu-id="e81be-145">Make sure that **Delay sign only** is cleared.</span></span>  
  
5.  <span data-ttu-id="e81be-146">建置專案。</span><span class="sxs-lookup"><span data-stu-id="e81be-146">Build the project.</span></span>  
  
### <a name="to-run-the-as2-sender-sample"></a><span data-ttu-id="e81be-147">若要執行 AS2 傳送者範例</span><span class="sxs-lookup"><span data-stu-id="e81be-147">To run the AS2 Sender sample</span></span>  
  
1.  <span data-ttu-id="e81be-148">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e81be-148">Open a command prompt.</span></span> <span data-ttu-id="e81be-149">移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug。</span><span class="sxs-lookup"><span data-stu-id="e81be-149">Move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug.</span></span>  
  
2.  <span data-ttu-id="e81be-150">Enter **Sender.exe**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="e81be-150">Enter **Sender.exe**, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="e81be-151">確認您看到一則訊息，指出 AS2 訊息已傳送成功，然後再關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e81be-151">Verify that you see a message indicating that an AS2 message was successfully sent, and then close the command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e81be-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e81be-152">See Also</span></span>  
 <span data-ttu-id="e81be-153">[教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="e81be-153">[Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md) </span></span>  
 <span data-ttu-id="e81be-154">[逐步解說 (AS2): 使用同步 MDN 透過 AS2 傳送 EDI](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md) </span><span class="sxs-lookup"><span data-stu-id="e81be-154">[Walkthrough (AS2): Sending EDI over AS2 with a Synchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md) </span></span>  
 [<span data-ttu-id="e81be-155">逐步解說 (AS2): 使用非同步 MDN 透過 AS2 傳送 EDI</span><span class="sxs-lookup"><span data-stu-id="e81be-155">Walkthrough (AS2): Sending EDI over AS2 with an Asynchronous MDN</span></span>](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md)