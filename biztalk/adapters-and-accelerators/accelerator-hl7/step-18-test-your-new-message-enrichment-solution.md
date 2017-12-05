---
title: "步驟 18： 測試您的新訊息擴充方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message enrichment tutorial, testing solution
ms.assetid: 233fbf79-0ab1-4064-b828-6bbbb56cbec2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 035925684617e74608246aed99fa98e16d0668a4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-18-test-your-new-message-enrichment-solution"></a><span data-ttu-id="f1a71-102">步驟 18： 測試您的新訊息擴充方案</span><span class="sxs-lookup"><span data-stu-id="f1a71-102">Step 18: Test Your New Message Enrichment Solution</span></span>
<span data-ttu-id="f1a71-103">在此步驟中，您必須測試方案利用 WSClient 應用程式來傳送訊息給[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]以及查看 MLLPReceive 應用程式是否會如預期般收到 HL7 格式化的訊息。</span><span class="sxs-lookup"><span data-stu-id="f1a71-103">In this step, you test your solution by using the WSClient application to send a message to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and seeing if the MLLPReceive application receives an HL7-formatted message as expected.</span></span>  
  
### <a name="to-test-your-solution"></a><span data-ttu-id="f1a71-104">若要測試您的方案</span><span class="sxs-lookup"><span data-stu-id="f1a71-104">To test your solution</span></span>  
  
1.  <span data-ttu-id="f1a71-105">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f1a71-105">Open a command prompt.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f1a71-106">步驟 2 需要您已安裝使用的自訂安裝程序的 MLLP 測試工具。</span><span class="sxs-lookup"><span data-stu-id="f1a71-106">Step 2 requires that you have installed the MLLP Test tool using the custom installation procedure.</span></span> <span data-ttu-id="f1a71-107">如果您的電腦沒有目錄包含 MllpReceive.exe 和 MllpSend.exe \MLLP 公用程式就會將其安裝藉由執行自訂安裝。</span><span class="sxs-lookup"><span data-stu-id="f1a71-107">If the \MLLP Utilities directory containing MllpReceive.exe and MllpSend.exe does not exist on your computer, install them by performing a custom installation.</span></span> <span data-ttu-id="f1a71-108">如需資訊，請參閱[執行自訂安裝](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692)。</span><span class="sxs-lookup"><span data-stu-id="f1a71-108">For information, see [Performing a Custom Installation](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).</span></span>  
  
2.  <span data-ttu-id="f1a71-109">在命令提示字元中，輸入 **cd \<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式 ** (其中\<*磁碟機*\>是您安裝的磁碟機代號)，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="f1a71-109">At the command prompt, type **cd \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities** (where \<*drive*\> is your installation drive letter), and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="f1a71-110">在命令提示字元中，輸入**mllpreceive/p 11000 /eb 11 /sb 28 /cr 13**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="f1a71-110">At the command prompt, type **mllpreceive /p 11000 /eb 11 /sb 28 /cr 13**, and then press **Enter**.</span></span> <span data-ttu-id="f1a71-111">這會執行 MLLP 接聽應用程式接聽連接埠 11000，並指定預設 EB、 SB 和 CR 字元 MLLP 的訊息，並顯示螢幕收到任何訊息。</span><span class="sxs-lookup"><span data-stu-id="f1a71-111">This runs the MLLP listener application listening to port 11000 and specifying the default EB, SB, and CR characters of the MLLP message, and displays any messages received to the screen.</span></span>  
  
4.  <span data-ttu-id="f1a71-112">開啟第二個命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f1a71-112">Open a second command prompt.</span></span>  
  
5.  <span data-ttu-id="f1a71-113">在命令提示字元中，輸入 **cd \<*磁碟機*\>: \Tutorial\WSClient\bin\Debug**，，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="f1a71-113">At the command prompt, type **cd \<*drive*\>:\Tutorial\WSClient\bin\Debug**, and then press **Enter**.</span></span>  
  
6.  <span data-ttu-id="f1a71-114">在命令提示字元中，輸入**wsclient john henry smith 123456789**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="f1a71-114">At the command prompt, type **wsclient john henry smith 123456789**, and then press **Enter**.</span></span> <span data-ttu-id="f1a71-115">這會傳送訊息至 Web 服務，其中包含範例訊息為 John Henry Smith 病患名稱，且 123456789 範例社會安全號碼號碼。</span><span class="sxs-lookup"><span data-stu-id="f1a71-115">This sends a message to the Web service that contains a sample message with a patient name of John Henry Smith and a sample social security number of 123456789.</span></span>  
  
7.  <span data-ttu-id="f1a71-116">短暫的延遲之後 MLLPReceive 應用程式會顯示內送 MLLP 訊息。</span><span class="sxs-lookup"><span data-stu-id="f1a71-116">After a short pause, the MLLPReceive application displays the incoming MLLP message.</span></span> <span data-ttu-id="f1a71-117">訊息看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="f1a71-117">The message should look similar to the following:</span></span>  
  
    ```  
    MSH|^~\&|TestTrailing^Delimiters|srcFac^srcFacUid|dstApp^dstAppUid|dstFac^dstFacUid|200307092343|sec|ADT^A04|msgid2134|P|2.2PID|||123456789||smith^john  
    ```  
  
     <span data-ttu-id="f1a71-118">如果您沒有收到回應後幾分鐘的時間，您應該檢查應用程式事件記錄檔有任何錯誤，並開始進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="f1a71-118">If you do not receive a response after a few minutes, you should check the Application event log for any errors and begin troubleshooting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a71-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="f1a71-119">See Also</span></span>  
 [<span data-ttu-id="f1a71-120">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="f1a71-120">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)