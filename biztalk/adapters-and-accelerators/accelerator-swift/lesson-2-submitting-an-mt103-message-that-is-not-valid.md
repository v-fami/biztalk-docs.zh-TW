---
title: 課程 2： 提交無效的 MT103 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, invalid messages
- submitting, invalid messages
- submitting, MT103 messages
- MT103 messages
- messages, MT103 messages
ms.assetid: 4b070ae1-c400-421a-b2f6-b7b1f22c0e41
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cb8f0539f3a832e3b54a6fa45b300558a8e39a1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014879"
---
# <a name="lesson-2-submitting-an-mt103-message-that-is-not-valid"></a><span data-ttu-id="3262d-102">課程 2： 提交無效的 MT103 訊息</span><span class="sxs-lookup"><span data-stu-id="3262d-102">Lesson 2: Submitting an MT103 Message That Is Not Valid</span></span>
<span data-ttu-id="3262d-103">在這一課，您送出無效的 MT103 訊息，然後您疑難排解使用您的系統工具產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3262d-103">In this lesson, you submit an MT103 message that is not valid and then you troubleshoot the resulting error using your System Tools.</span></span>  
  
### <a name="to-submit-an-mt103-message-that-is-not-valid"></a><span data-ttu-id="3262d-104">送出無效的 MT103 訊息</span><span class="sxs-lookup"><span data-stu-id="3262d-104">To submit an MT103 message that is not valid</span></span>  
  
1. <span data-ttu-id="3262d-105">將檔案 MT103_Invalid_Sample.txt 複製從\<*磁碟機：*\>\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial 來\<*磁碟機*\>: \Labs\Inbound\FlatFile 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3262d-105">Copy the file MT103_Invalid_Sample.txt from \<*drive:*\>\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial to \<*drive*\>:\Labs\Inbound\FlatFile folder.</span></span> <span data-ttu-id="3262d-106">請注意，您將檔案拖放到資料夾的時間。</span><span class="sxs-lookup"><span data-stu-id="3262d-106">Note the time that you drop the file into the folder.</span></span>  
  
2. <span data-ttu-id="3262d-107">開啟\<*磁碟機：*\>\Labs\Outbound 以確認沒有 MT103_Invalid_Sample.txt 對應的 XML 檔案的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3262d-107">Open \<*drive:*\>\Labs\Outbound to verify that no XML file corresponding to MT103_Invalid_Sample.txt is in the folder.</span></span> <span data-ttu-id="3262d-108">（對應至有效的 MT103_Sample.txt 訊息的 XML 檔案仍應該為該資料夾中）。</span><span class="sxs-lookup"><span data-stu-id="3262d-108">(The XML file corresponding to the valid MT103_Sample.txt message should still be in that folder.)</span></span>  
  
3. <span data-ttu-id="3262d-109">在 記事本 開啟 檔案 MT103_Invalid_Sample.txt 中\<*磁碟機：*\>\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial。</span><span class="sxs-lookup"><span data-stu-id="3262d-109">In Notepad, open the file MT103_Invalid_Sample.txt in \<*drive:*\>\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial.</span></span>  
  
4. <span data-ttu-id="3262d-110">開始**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="3262d-110">Start **BizTalk Server Administration**.</span></span>  
  
5. <span data-ttu-id="3262d-111">在 BizTalk Server 管理主控台中，展開**事件檢視器 （本機）**，然後按一下**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="3262d-111">In the BizTalk Server Administration Console, expand **Event Viewer (Local)**, and then click **Application**.</span></span>  
  
6. <span data-ttu-id="3262d-112">尋找具有來源 BizTalk accelerator for SWIFT 和卸除到無效的訊息時，對應於一次的錯誤項目\<*磁碟機*\>: \Labs\Inbound\FlatFile 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3262d-112">Look for an error entry that has a source of BizTalk Accelerator for SWIFT and a time that corresponds to when you dropped the invalid message into the \<*drive*\>:\Labs\Inbound\FlatFile folder.</span></span> <span data-ttu-id="3262d-113">按兩下該錯誤項目。</span><span class="sxs-lookup"><span data-stu-id="3262d-113">Double-click that error entry.</span></span>  
  
7. <span data-ttu-id="3262d-114">在 事件內容 對話方塊中的 錯誤，確認 描述 窗格中失敗的訊息已發佈至 MessageBox，SWIFT 解譯器就會標示**A4SWIFT_Failed**作為 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="3262d-114">In the Event Properties dialog box for the error, verify in the Description pane that the failed message was published to the MessageBox and that the SWIFT Disassembler marked **A4SWIFT_Failed** as **True**.</span></span> <span data-ttu-id="3262d-115">關閉 [事件內容] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3262d-115">Close the Event Properties dialog box.</span></span>  
  
8. <span data-ttu-id="3262d-116">在 [BizTalk Server 管理主控台中，展開**BizTalk Server 管理]**，然後展開**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="3262d-116">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, and then expand **BizTalk Group**.</span></span> <span data-ttu-id="3262d-117">在 **檢視**功能表上，按一下**群組中樞頁面**。</span><span class="sxs-lookup"><span data-stu-id="3262d-117">In the **View** menu, click **Group Hub Page**.</span></span>  
  
9. <span data-ttu-id="3262d-118">在**群組概觀**窗格，請在**分組已擱置服務執行個體**窗格中，按一下 **依應用程式分組**。</span><span class="sxs-lookup"><span data-stu-id="3262d-118">In the **Group Overview** pane, in the **Grouped Suspended Service Instances** pane, click **Grouped by Application**.</span></span>  
  
10. <span data-ttu-id="3262d-119">在 **預覽選取的查詢結果**窗格中，按兩下項目**MT103_FlatFile_ReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="3262d-119">In the **Preview for the selected query result** pane, double-click the entry for **MT103_FlatFile_ReceivePort**.</span></span>  
  
11. <span data-ttu-id="3262d-120">在 服務詳細資料 對話方塊中，按一下**訊息** 索引標籤。按兩下服務名稱的項目**MT103_FlatFile_ReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="3262d-120">In the Service Details dialog box, click the **Messages** tab. Double-click the entry for which the Service Name is **MT103_FlatFile_ReceivePort**.</span></span>  
  
12. <span data-ttu-id="3262d-121">在 [訊息詳細資料] 對話方塊中，按一下**主體**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3262d-121">In the Message Details dialog box, click **Body** in the left pane.</span></span>  
  
13. <span data-ttu-id="3262d-122">確認 [訊息詳細資料] 對話方塊中的 [主體] 窗格中顯示的訊息對應至您在 「 記事本 」 中開啟 MT103_Invalid_Sample.txt。</span><span class="sxs-lookup"><span data-stu-id="3262d-122">Verify that the message displayed in the body pane of the Message Details dialog box corresponds to MT103_Invalid_Sample.txt that you opened in Notepad.</span></span>  
  
    <span data-ttu-id="3262d-123">請繼續進行[第 3 課： 測試 XML 執行個體](../../adapters-and-accelerators/accelerator-swift/lesson-3-testing-an-xml-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="3262d-123">Proceed to [Lesson 3: Testing an XML Instance](../../adapters-and-accelerators/accelerator-swift/lesson-3-testing-an-xml-instance.md).</span></span>