---
title: 步驟 10： 確認端對端案例 |Microsoft 文件
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
ms.openlocfilehash: d38f137625554bd689477964e3a969142eca0658
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25961588"
---
# <a name="step-10-verify-the-end-to-end-scenario"></a><span data-ttu-id="35c93-102">步驟 10： 確認端對端案例</span><span class="sxs-lookup"><span data-stu-id="35c93-102">Step 10: Verify the End-to-End Scenario</span></span>
<span data-ttu-id="35c93-103">在此步驟中，您可以確認端對端案例本教學課程。</span><span class="sxs-lookup"><span data-stu-id="35c93-103">In this step, you verify the end-to-end scenario for this tutorial.</span></span>  
  
### <a name="to-verify-the-end-to-end-tutorial-scenario"></a><span data-ttu-id="35c93-104">若要確認端對端教學課程案例</span><span class="sxs-lookup"><span data-stu-id="35c93-104">To verify the end-to-end tutorial scenario</span></span>  
  
1.  <span data-ttu-id="35c93-105">按一下**啟動**，指向 **程式**，指向 **附屬應用程式**，然後按一下 **命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="35c93-105">Click **Start**, point to **Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="35c93-106">在 [命令提示字元] 視窗中，移至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="35c93-106">In the Command Prompt window, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="35c93-107">如果找不到 SDK 資料夾下的 MLLP 公用資料夾，可能未安裝 MLLP 測試工具。</span><span class="sxs-lookup"><span data-stu-id="35c93-107">If you cannot find an MLLP Utilities folder under the SDK folder, the MLLP test tools may not be installed.</span></span> <span data-ttu-id="35c93-108">開啟 [控制台] 中，然後開啟**新增或移除程式**。</span><span class="sxs-lookup"><span data-stu-id="35c93-108">Open the Control Panel, and then open **Add or Remove Programs**.</span></span> <span data-ttu-id="35c93-109">選取**Microsoft BizTalk\<版本\>Accelerator for HL7**，然後選取**變更**。</span><span class="sxs-lookup"><span data-stu-id="35c93-109">Select **Microsoft BizTalk \<version\> Accelerator for HL7**, and then select **Change**.</span></span> <span data-ttu-id="35c93-110">在 BTAHL7 安裝程式精靈中，選取**修改**。</span><span class="sxs-lookup"><span data-stu-id="35c93-110">In the BTAHL7 setup wizard, select **Modify**.</span></span> <span data-ttu-id="35c93-111">展開**配接器**資料夾，以查看是否**MLLP 測試工具**已安裝。</span><span class="sxs-lookup"><span data-stu-id="35c93-111">Expand the **Adapter** folder to see whether the **MLLP Test Tool** has been installed.</span></span> <span data-ttu-id="35c93-112">否則，請安裝它。</span><span class="sxs-lookup"><span data-stu-id="35c93-112">If not, install it.</span></span>  
  
3.  <span data-ttu-id="35c93-113">在命令提示字元 視窗中，輸入**mllpreceive/p 14000**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="35c93-113">In the Command Prompt window, type **mllpreceive /p 14000**, and then press **Enter**.</span></span> <span data-ttu-id="35c93-114">這會執行 MLLP 接聽應用程式接聽連接埠 14000 並指定預設 EB、 SB 和 CR 字元 MLLP 的訊息，並顯示螢幕收到任何訊息。</span><span class="sxs-lookup"><span data-stu-id="35c93-114">This runs the MLLP listener application listening to port 14000 and specifying the default EB, SB, and CR characters of the MLLP message, and displays any messages received to the screen.</span></span>  
  
4.  <span data-ttu-id="35c93-115">啟動額外的命令提示字元，依序按一下**啟動**，指向**程式**，指向 **附屬應用程式**，然後按一下 **命令提示字元**.</span><span class="sxs-lookup"><span data-stu-id="35c93-115">Start an additional command prompt by clicking **Start**, point to **Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
5.  <span data-ttu-id="35c93-116">在第二個 [命令提示字元] 視窗中，移至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="35c93-116">In the second Command Prompt window, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="35c93-117">下列步驟來傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="35c93-117">The following step sends the message.</span></span>  
  
6.  <span data-ttu-id="35c93-118">在命令提示字元 視窗中，輸入**mllpsend /SB 11 /EB 28 /CR 13 /f"\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\端對端 Tutorial\ADT ^ A03.txt"**，其中\<*磁碟機*\>是您安裝的磁碟機代號。</span><span class="sxs-lookup"><span data-stu-id="35c93-118">In the Command Prompt window, type **mllpsend /SB 11 /EB 28 /CR 13 /f "\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\ADT^A03.txt"**, where \<*drive*\> is your installation drive letter.</span></span> <span data-ttu-id="35c93-119">按 **Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="35c93-119">Press **Enter**.</span></span>  
  
7.  <span data-ttu-id="35c93-120">請確認您有下列結果：</span><span class="sxs-lookup"><span data-stu-id="35c93-120">Verify that you have the following results:</span></span>  
  
    -   <span data-ttu-id="35c93-121">MLLP 接聽應用程式應該會顯示一則訊息。</span><span class="sxs-lookup"><span data-stu-id="35c93-121">The MLLP listener application should display a message.</span></span> <span data-ttu-id="35c93-122">訊息的第一行應該具有下列值：</span><span class="sxs-lookup"><span data-stu-id="35c93-122">The first line of the message should have the following values:</span></span>  
  
        ```  
        MSH|^~\&|BTAHL7^IE^UUID|MCM|HI^System^GUID||199601121005||ADT^A04|000001|P|2.4|||SU|NE  
        ```  
  
    -   <span data-ttu-id="35c93-123">訊息會出現在\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>的端對端 HL7\SDK\End Tutorial\Tutorial_sendMsg_RX 加速器。</span><span class="sxs-lookup"><span data-stu-id="35c93-123">A message appears in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendMsg_RX.</span></span> <span data-ttu-id="35c93-124">此訊息應該 MLLP 接聽程式的應用程式所顯示的訊息相同。</span><span class="sxs-lookup"><span data-stu-id="35c93-124">This message should be the same as the message shown by the MLLP listener application.</span></span> <span data-ttu-id="35c93-125">確認訊息的第一行具有相同的訊息值，如下所示。</span><span class="sxs-lookup"><span data-stu-id="35c93-125">Verify that the first line of the message has the same message values as follows.</span></span> <span data-ttu-id="35c93-126">請注意 MSH3 nd MSH5 下列程式碼中的值符合您指定 Tutorial_RXSystem 的值：</span><span class="sxs-lookup"><span data-stu-id="35c93-126">Note that the values for MSH3 a nd MSH5 in the following code match the values you specified for the Tutorial_RXSystem:</span></span>  
  
        ```  
        MSH|^~\&|BTAHL7|MCM|Tutorial_RXSystem||199601121005||ADT^A03|000001|P|2.3.1  
        ```  
  
    -   <span data-ttu-id="35c93-127">兩個訊息會出現在\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>的端對端 HL7\SDK\End Tutorial\Tutorial_sendAck_ADT 加速器。</span><span class="sxs-lookup"><span data-stu-id="35c93-127">Two messages appear in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendAck_ADT.</span></span> <span data-ttu-id="35c93-128">其中一個訊息是應用程式通知。另一個方法是將認可通知。</span><span class="sxs-lookup"><span data-stu-id="35c93-128">One of these messages is an application acknowledgment; the other is a commit acknowledgment.</span></span> <span data-ttu-id="35c93-129">應用程式通知應該具有下列內容：</span><span class="sxs-lookup"><span data-stu-id="35c93-129">The application acknowledgment should have the following content:</span></span>  
  
        ```  
        MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|000001|P|2.3.1|||AL  
        MSA|AA|000001  
        ```  
  
    -   <span data-ttu-id="35c93-130">認可通知應該具有下列內容：</span><span class="sxs-lookup"><span data-stu-id="35c93-130">The commit acknowledgment should have the following content:</span></span>  
  
        ```  
        MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|100000|P|2.3.1  
        MSA|CA|000001  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="35c93-131">如果未正確顯示訊息，使用 「 狀況與活動追蹤 (HAT) 工具來疑難排解錯誤。</span><span class="sxs-lookup"><span data-stu-id="35c93-131">If the messages do not appear correctly, use the Health and Activity Tracking (HAT) tool to troubleshoot the error.</span></span>  
  
 <span data-ttu-id="35c93-132">恭喜！</span><span class="sxs-lookup"><span data-stu-id="35c93-132">Congratulations!</span></span> <span data-ttu-id="35c93-133">您已順利完成 BTAHL7 端對端教學課程。</span><span class="sxs-lookup"><span data-stu-id="35c93-133">You have successfully completed the BTAHL7 End-to-End Tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c93-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35c93-134">See Also</span></span>  
 [<span data-ttu-id="35c93-135">端對端教學課程</span><span class="sxs-lookup"><span data-stu-id="35c93-135">End-to-End Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)