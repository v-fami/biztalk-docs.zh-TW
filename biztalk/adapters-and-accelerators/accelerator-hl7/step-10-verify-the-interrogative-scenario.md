---
title: 步驟 10： 確認 Interrogative 案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, verifying solution
ms.assetid: 1f28800b-4a1d-4f29-8123-5cdea4b4a365
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b932ab2f179faab1381609c007dcdd148f200f7e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="step-10-verify-the-interrogative-scenario"></a><span data-ttu-id="dce9e-102">步驟 10： 確認 Interrogative 案例</span><span class="sxs-lookup"><span data-stu-id="dce9e-102">Step 10: Verify the Interrogative Scenario</span></span>
<span data-ttu-id="dce9e-103">在此步驟中，您可以確認端對端案例本教學課程。</span><span class="sxs-lookup"><span data-stu-id="dce9e-103">In this step, you verify the end-to-end scenario for this tutorial.</span></span>  
  
### <a name="to-send-the-query-message"></a><span data-ttu-id="dce9e-104">傳送查詢訊息</span><span class="sxs-lookup"><span data-stu-id="dce9e-104">To send the query message</span></span>  
  
1.  <span data-ttu-id="dce9e-105">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="dce9e-105">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="dce9e-106">在命令提示字元中，移至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式**。</span><span class="sxs-lookup"><span data-stu-id="dce9e-106">In the command prompt, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**.</span></span>  
  
3.  <span data-ttu-id="dce9e-107">在命令提示字元中，輸入**MllpReceive/P 24000**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="dce9e-107">In the command prompt, type **MllpReceive /P 24000**, and then press **Enter**.</span></span> <span data-ttu-id="dce9e-108">這會執行接聽連接埠 24000 MLLP 接聽應用程式，並顯示螢幕收到任何訊息。</span><span class="sxs-lookup"><span data-stu-id="dce9e-108">This runs the MLLP listener application listening to port 24000 and displays any messages received to the screen.</span></span> <span data-ttu-id="dce9e-109">此應用程式會模擬醫院資訊系統。</span><span class="sxs-lookup"><span data-stu-id="dce9e-109">This application is simulating the Hospital Information System.</span></span>  
  
4.  <span data-ttu-id="dce9e-110">開啟額外的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="dce9e-110">Open an additional command prompt.</span></span>  
  
5.  <span data-ttu-id="dce9e-111">在第二個 [命令提示字元] 視窗中，移至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式**.</span><span class="sxs-lookup"><span data-stu-id="dce9e-111">In the second Command Prompt window, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**.</span></span>  
  
6.  <span data-ttu-id="dce9e-112">在第二個命令提示字元中，輸入**MllpSend /SB 11 /EB 28 /CR 13/TWOWAY/P 22000 /F"\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>快速鍵 HL7\SDK\Interrogative Tutorial\QRY^Q01.txt**，然後按下**Enter。**</span><span class="sxs-lookup"><span data-stu-id="dce9e-112">In the second command prompt, type **MllpSend /SB 11 /EB 28 /CR 13 /TWOWAY /P 22000 /F "\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial\QRY^Q01.txt**, and then press **Enter.**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dce9e-113">此命令會傳送查詢訊息，您建立此教學課程 MLLP 連接埠 22000 並等候回應 （通知） 的開頭。</span><span class="sxs-lookup"><span data-stu-id="dce9e-113">This command sends the query message you created at the beginning of this tutorial to MLLP port 22000 and waits for a response (acknowledgment).</span></span> <span data-ttu-id="dce9e-114">ADT 接收埠會拾取此訊息，並予以處理。</span><span class="sxs-lookup"><span data-stu-id="dce9e-114">The ADT receive port picks up this message and processes it.</span></span>  
  
7.  <span data-ttu-id="dce9e-115">請確認您有下列結果：</span><span class="sxs-lookup"><span data-stu-id="dce9e-115">Verify that you have the following results:</span></span>  
  
    -   <span data-ttu-id="dce9e-116">MLLP 接聽應用程式應該會顯示訊息，以使用下列值：</span><span class="sxs-lookup"><span data-stu-id="dce9e-116">The MLLP listener application should display a message with the following values:</span></span>  
  
        ```  
        MSH|^~\&|ADT||HIS||19990303||QRY^Q01|MSG00001|P|2.4  
        QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
        ```  
  
    -   <span data-ttu-id="dce9e-117">此外，MllpSend 公用程式建立通知檔案中的\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\名為 QRY^Q01.txt.RESPONSE interrogative 教學課程的資料夾。</span><span class="sxs-lookup"><span data-stu-id="dce9e-117">In addition, the MllpSend utility creates an acknowledgment file in the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial folder named QRY^Q01.txt.RESPONSE.</span></span> <span data-ttu-id="dce9e-118">這個檔案包含下列資訊為通知：</span><span class="sxs-lookup"><span data-stu-id="dce9e-118">This file contains the following information as the acknowledgment:</span></span>  
  
        ```  
        MSH|^~\&|HIS||ADT||20040331154031.2222-0800||ACK^Q01^ACK|10000GSM|P|2.4  
        MSA|CA|MSG00001  
        ****END ACK****  
        ```  
  
### <a name="to-send-the-response-message"></a><span data-ttu-id="dce9e-119">若要傳送回應訊息</span><span class="sxs-lookup"><span data-stu-id="dce9e-119">To send the response message</span></span>  
  
1.  <span data-ttu-id="dce9e-120">在命令提示字元中執行 MllpReceive 應用程式，請按**CTRL-C**取消先前的作業。</span><span class="sxs-lookup"><span data-stu-id="dce9e-120">In the command prompt running the MllpReceive application, press **Ctrl-C** to cancel the previous operation.</span></span>  
  
2.  <span data-ttu-id="dce9e-121">在命令提示字元中，輸入**MllpReceive/P 25000**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="dce9e-121">At the command prompt, type **MllpReceive /P 25000**, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dce9e-122">步驟 2 執行接聽連接埠 25000 MLLP 接聽應用程式，並顯示螢幕收到任何訊息。</span><span class="sxs-lookup"><span data-stu-id="dce9e-122">Step 2 runs the MLLP listener application listening to port 25000 and displays any messages received to the screen.</span></span> <span data-ttu-id="dce9e-123">此應用程式會模擬 ADT 系統。</span><span class="sxs-lookup"><span data-stu-id="dce9e-123">This application is simulating the ADT system.</span></span>  
  
3.  <span data-ttu-id="dce9e-124">在第二個命令提示字元中，輸入**MllpSend /SB 11 /EB 28 /CR 13/P 23000 /F"\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator forHL7\SDK\Interrogative Tutorial\DSR.txt"**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="dce9e-124">In the second command prompt, type **MllpSend /SB 11 /EB 28 /CR 13 /P 23000 /F "\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial\DSR.txt"**, then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dce9e-125">步驟 3 傳送回應訊息建立 MLLP 連接埠 23000 本教學課程的起始處。</span><span class="sxs-lookup"><span data-stu-id="dce9e-125">Step 3 sends the response message you created at the beginning of this tutorial to MLLP port 23000.</span></span> <span data-ttu-id="dce9e-126">HIS 接收埠會拾取此訊息，並予以處理。</span><span class="sxs-lookup"><span data-stu-id="dce9e-126">The HIS receive port picks up this message and processes it.</span></span>  
  
4.  <span data-ttu-id="dce9e-127">請確認您有下列結果：</span><span class="sxs-lookup"><span data-stu-id="dce9e-127">Verify that you have the following results:</span></span>  
  
    -   <span data-ttu-id="dce9e-128">MLLP 接聽應用程式應該會顯示訊息，以使用下列值：</span><span class="sxs-lookup"><span data-stu-id="dce9e-128">The MLLP listener application should display a message with the following values:</span></span>  
  
        ```  
        MSH|^~\&|HIS||ADT||19990505||DSR^Q01|ZXT23469|P|2.4  
        MSA|AA|MSG00003  
        QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
        DSP|||RESULTS FOR PATIENT#12233 SMITH, JOHN H. 07/23/03  
        DSP|||SPECIMEN#H85 COLLECTED 07/22/03 /07/0/0  
        DSP|||ELECTROLYTES  
        DSP||| SODIUM 136 [135-148] MEQ/L STAT  
        DSP||| POTASSIUM 4.2 [3.5-5.0] MEQ/L STAT  
        DSP||| CHLORIDE 91 [95-111] MEQ/L STAT  
        DSP||| CO2 25 [20-30] MEQ/L STAT  
        DSP|||CO2 25 [20-30] MEQ/L STAT|LB  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="dce9e-129">如果未正確顯示上述的訊息，使用 「 狀況與活動追蹤 (HAT) 工具來疑難排解錯誤。</span><span class="sxs-lookup"><span data-stu-id="dce9e-129">If the messages above do not appear correctly, use the Health and Activity Tracking (HAT) tool to troubleshoot the error.</span></span>  
  
 <span data-ttu-id="dce9e-130">恭喜！</span><span class="sxs-lookup"><span data-stu-id="dce9e-130">Congratulations!</span></span> <span data-ttu-id="dce9e-131">您已順利完成 BTAHL7 Interrogative 教學課程。</span><span class="sxs-lookup"><span data-stu-id="dce9e-131">You have successfully completed the BTAHL7 Interrogative Tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce9e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dce9e-132">See Also</span></span>  
 <span data-ttu-id="dce9e-133">[批次的教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="dce9e-133">[Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span></span>  
 <span data-ttu-id="dce9e-134">[端對端教學課程](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md) </span><span class="sxs-lookup"><span data-stu-id="dce9e-134">[End-to-End Tutorial](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md) </span></span>  
 [<span data-ttu-id="dce9e-135">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="dce9e-135">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)