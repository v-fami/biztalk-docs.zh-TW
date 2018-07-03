---
title: 步驟 10： 驗證端對端案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, verifying solution
ms.assetid: 24b74ba6-e303-4ab1-8a93-25a430e4894d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43d95e54bbcf0c7c716630305b85ba8b9bed1a52
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990343"
---
# <a name="step-10-verify-the-end-to-end-scenario"></a><span data-ttu-id="211e6-102">步驟 10： 驗證端對端案例</span><span class="sxs-lookup"><span data-stu-id="211e6-102">Step 10: Verify the End-to-End Scenario</span></span>
<span data-ttu-id="211e6-103">在此步驟中，您可以確認的端對端案例在本教學課程。</span><span class="sxs-lookup"><span data-stu-id="211e6-103">In this step, you verify the end-to-end scenario for this tutorial.</span></span>  
  
### <a name="to-verify-the-end-to-end-tutorial-scenario"></a><span data-ttu-id="211e6-104">若要確認端對端教學課程案例</span><span class="sxs-lookup"><span data-stu-id="211e6-104">To verify the end-to-end tutorial scenario</span></span>  
  
1. <span data-ttu-id="211e6-105">按一下 **開始**，指向**程式**，指向**附屬應用程式**，然後按一下**命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="211e6-105">Click **Start**, point to **Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
2. <span data-ttu-id="211e6-106">在 [命令提示字元] 視窗中，移至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="211e6-106">In the Command Prompt window, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**, and then press **Enter**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="211e6-107">如果找不到 SDK 資料夾下的 MLLP 公用程式 資料夾，可能不會安裝 MLLP 測試工具。</span><span class="sxs-lookup"><span data-stu-id="211e6-107">If you cannot find an MLLP Utilities folder under the SDK folder, the MLLP test tools may not be installed.</span></span> <span data-ttu-id="211e6-108">開啟 [控制台] 中，然後開啟**新增或移除程式**。</span><span class="sxs-lookup"><span data-stu-id="211e6-108">Open the Control Panel, and then open **Add or Remove Programs**.</span></span> <span data-ttu-id="211e6-109">選取  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後選取**變更**。</span><span class="sxs-lookup"><span data-stu-id="211e6-109">Select **Microsoft BizTalk \<version\> Accelerator for HL7**, and then select **Change**.</span></span> <span data-ttu-id="211e6-110">在 [BTAHL7 安裝程式精靈] 中，選取**修改**。</span><span class="sxs-lookup"><span data-stu-id="211e6-110">In the BTAHL7 setup wizard, select **Modify**.</span></span> <span data-ttu-id="211e6-111">依序展開**配接器**資料夾，以查看是否**MLLP 測試工具**已安裝。</span><span class="sxs-lookup"><span data-stu-id="211e6-111">Expand the **Adapter** folder to see whether the **MLLP Test Tool** has been installed.</span></span> <span data-ttu-id="211e6-112">否則，請安裝它。</span><span class="sxs-lookup"><span data-stu-id="211e6-112">If not, install it.</span></span>  
  
3. <span data-ttu-id="211e6-113">在 [命令提示字元] 視窗中，輸入**mllpreceive/p 14000**，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="211e6-113">In the Command Prompt window, type **mllpreceive /p 14000**, and then press **Enter**.</span></span> <span data-ttu-id="211e6-114">這會執行 MLLP 接聽端應用程式接聽連接埠 14000，並指定預設 EB、 SB 和 CR 字元 MLLP 的訊息，並顯示螢幕收到任何訊息。</span><span class="sxs-lookup"><span data-stu-id="211e6-114">This runs the MLLP listener application listening to port 14000 and specifying the default EB, SB, and CR characters of the MLLP message, and displays any messages received to the screen.</span></span>  
  
4. <span data-ttu-id="211e6-115">按一下 啟動額外的命令提示字元**開始**，指向**程式**，指向**附屬應用程式**，然後按一下 **命令提示字元**.</span><span class="sxs-lookup"><span data-stu-id="211e6-115">Start an additional command prompt by clicking **Start**, point to **Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
5. <span data-ttu-id="211e6-116">在第二個 [命令提示字元] 視窗中，移至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>HL7\SDK\MLLP 公用程式加速器**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="211e6-116">In the second Command Prompt window, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**, and then press **Enter**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="211e6-117">下列步驟將訊息傳送。</span><span class="sxs-lookup"><span data-stu-id="211e6-117">The following step sends the message.</span></span>  
  
6. <span data-ttu-id="211e6-118">在 [命令提示字元] 視窗中，輸入**mllpsend /SB 11 /EB 28 /CR 13 /f 」\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\端對端 Tutorial\ADT ^ A03.txt 」**，其中\<*磁碟機*\>是您的安裝磁碟機代號。</span><span class="sxs-lookup"><span data-stu-id="211e6-118">In the Command Prompt window, type **mllpsend /SB 11 /EB 28 /CR 13 /f "\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\ADT^A03.txt"**, where \<*drive*\> is your installation drive letter.</span></span> <span data-ttu-id="211e6-119">按 **Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="211e6-119">Press **Enter**.</span></span>  
  
7. <span data-ttu-id="211e6-120">確認您有下列結果：</span><span class="sxs-lookup"><span data-stu-id="211e6-120">Verify that you have the following results:</span></span>  
  
   -   <span data-ttu-id="211e6-121">MLLP 接聽端應用程式應該會顯示一則訊息。</span><span class="sxs-lookup"><span data-stu-id="211e6-121">The MLLP listener application should display a message.</span></span> <span data-ttu-id="211e6-122">訊息的第一行應該有下列值：</span><span class="sxs-lookup"><span data-stu-id="211e6-122">The first line of the message should have the following values:</span></span>  
  
       ```  
       MSH|^~\&|BTAHL7^IE^UUID|MCM|HI^System^GUID||199601121005||ADT^A04|000001|P|2.4|||SU|NE  
       ```  
  
   -   <span data-ttu-id="211e6-123">訊息會出現在\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>HL7\SDK\End 端對端 Tutorial\Tutorial_sendMsg_RX 的加速器。</span><span class="sxs-lookup"><span data-stu-id="211e6-123">A message appears in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendMsg_RX.</span></span> <span data-ttu-id="211e6-124">此訊息應該由 MLLP 接聽端應用程式所顯示的訊息相同。</span><span class="sxs-lookup"><span data-stu-id="211e6-124">This message should be the same as the message shown by the MLLP listener application.</span></span> <span data-ttu-id="211e6-125">確認訊息的第一行有相同的訊息值，如下所示。</span><span class="sxs-lookup"><span data-stu-id="211e6-125">Verify that the first line of the message has the same message values as follows.</span></span> <span data-ttu-id="211e6-126">請注意 MSH3 nd MSH5 下列程式碼中的值符合您指定 Tutorial_RXSystem 的值：</span><span class="sxs-lookup"><span data-stu-id="211e6-126">Note that the values for MSH3 a nd MSH5 in the following code match the values you specified for the Tutorial_RXSystem:</span></span>  
  
       ```  
       MSH|^~\&|BTAHL7|MCM|Tutorial_RXSystem||199601121005||ADT^A03|000001|P|2.3.1  
       ```  
  
   -   <span data-ttu-id="211e6-127">兩個訊息都會出現在\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>HL7\SDK\End 端對端 Tutorial\Tutorial_sendAck_ADT 的加速器。</span><span class="sxs-lookup"><span data-stu-id="211e6-127">Two messages appear in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendAck_ADT.</span></span> <span data-ttu-id="211e6-128">其中一個訊息是應用程式通知;另一個是認可通知。</span><span class="sxs-lookup"><span data-stu-id="211e6-128">One of these messages is an application acknowledgment; the other is a commit acknowledgment.</span></span> <span data-ttu-id="211e6-129">應用程式通知應該具有下列內容：</span><span class="sxs-lookup"><span data-stu-id="211e6-129">The application acknowledgment should have the following content:</span></span>  
  
       ```  
       MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|000001|P|2.3.1|||AL  
       MSA|AA|000001  
       ```  
  
   -   <span data-ttu-id="211e6-130">認可通知應該具有下列內容：</span><span class="sxs-lookup"><span data-stu-id="211e6-130">The commit acknowledgment should have the following content:</span></span>  
  
       ```  
       MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|100000|P|2.3.1  
       MSA|CA|000001  
       ```  
  
   > [!NOTE]
   >  <span data-ttu-id="211e6-131">如果訊息未正確顯示，使用 「 狀況與活動追蹤 (HAT) 工具來疑難排解錯誤。</span><span class="sxs-lookup"><span data-stu-id="211e6-131">If the messages do not appear correctly, use the Health and Activity Tracking (HAT) tool to troubleshoot the error.</span></span>  
  
   <span data-ttu-id="211e6-132">恭喜！</span><span class="sxs-lookup"><span data-stu-id="211e6-132">Congratulations!</span></span> <span data-ttu-id="211e6-133">您已順利完成 BTAHL7 端對端教學課程。</span><span class="sxs-lookup"><span data-stu-id="211e6-133">You have successfully completed the BTAHL7 End-to-End Tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="211e6-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="211e6-134">See Also</span></span>  
 [<span data-ttu-id="211e6-135">端對端教學課程</span><span class="sxs-lookup"><span data-stu-id="211e6-135">End-to-End Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)